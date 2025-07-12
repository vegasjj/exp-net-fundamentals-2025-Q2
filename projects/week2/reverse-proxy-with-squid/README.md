# Deploying Reverse Proxy with Squid on Ubuntu

The steps detailed here assume **squid** is already installed with a basic configuration. If you need to set it up [follow these instructions](../forward-proxy-with-squid/README.md).

## Reverse Proxy Setup

To show the current squid configuration (filtering commented and blank lines), run:

```sh
cat /etc/squid/squid.conf | grep -v '^#' | grep -v '^$'
```

Below, you can see  the output of a working configuration for a reverse web proxy pointing to an IIS server:

```sh
acl localnet src 10.200.123.128/28
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 443         # https
acl Safe_ports port 8080        # ← Add this line
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
include /etc/squid/conf.d/*.conf
http_access allow localnet
# http_access deny all          # ← Remove or comment this line
http_port 3128
access_log daemon:/var/log/squid/access.log squid
coredump_dir /var/spool/squid
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern \/(Packages|Sources)(|\.bz2|\.gz|\.xz)$ 0 0% 0 refresh-ims
refresh_pattern \/Release(|\.gpg)$ 0 0% 0 refresh-ims
refresh_pattern \/InRelease$ 0 0% 0 refresh-ims
refresh_pattern \/(Translation-.*)(|\.bz2|\.gz|\.xz)$ 0 0% 0 refresh-ims
refresh_pattern .               0       20%     4320
# Add all lines from here
# Listening port for reverse proxy
http_port 8080 accel vhost
# Origin server to which the reverse proxy redirect clients. Replace the IP with your own origin server
cache_peer 10.200.123.141 parent 80 0 no-query originserver name=iis-server
# Client requests to the proxy-demo domain will be allowed
acl site dstdomain proxy-demo
# Requests made to proxy-demo will be allowed to be served to the origin server: iis-server 
http_access allow site
cache_peer_access iis-server allow site
# Deny everything else
http_access deny all
```

If you installed and configured squid with the instructions provided in this repo, you only need to add or remove the lines specified in the above code snippet as these are the ones relevant to the reverse proxy setup.

**Important**: make sure you move the line ```http_access deny all``` to the bottom of the file; otherwise you would not be able to connect to the origin server.

Restart the squid service to apply the changes:

```sh
sudo systemctl reload squid
```
