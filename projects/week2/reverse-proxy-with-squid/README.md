# Deploying Reverse Proxy with Squid on Ubuntu

The steps detailed here assume **squid** is already installed with a basic configuration. If you need to set it up go to [this README](../forward-proxy-with-squid/README.md).

## Reverse Proxy Setup

To show the current Squid configuration (filtering commented and blank lines), run:

```sh
cat /etc/squid/squid.conf | grep -v '^#' | grep -v '^$'
```

Below, you can see  the output of a working configuration for a reverse web proxy pointing to an IIS server:

```sh
acl Safe_ports port 8080        # reverse proxy
http_port 8080 accel vhost
cache_peer 10.200.123.141 parent 80 0 no-query originserver name=iis-server
acl our_sites dstdomain proxy-demo
cache_peer_access iis-server allow our_sites
cache_peer_access iis-server deny all
http_access deny our_sites
```

Second setup:

```sh
acl Safe_ports port 8080        # reverse proxy
# http_access deny all
http_port 8080 accel vhost
cache_peer 10.200.123.141 parent 80 0 no-query originserver name=iis-server
acl site dstdomain proxy-demo
http_access allow all
cache_peer_access iis-server allow site
```

Restart the squid service to apply the changes:

```sh
sudo systemctl stop squid
sudo systemctl start squid
```
