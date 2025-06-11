# Project Journal

## Initial septup

After installing Python, a test webpage called `index.html` was generated using Copilot.

The webpage was served using:

```sh
python -m http.server 8000
```

## Creating firewall rules

By default, all incoming traffic is blocked by the Windows Firewall unless explicitely allowed.

A rule called "Python Webserver" was created to open incomming TCP traffic throught port 8000.

An inbound rule was created in the EC2 instance security group so traffic could pass from the public Internet.

The server was reacheabled using the `curl` command from both the local server and outsite the EC2 instance's VPC:

```sh
curl http://127.0.0.1:8000
```

![](assets/win-firewall.png)

Proof of working Python Webserver from inside (127.0.0.1) and outside the VPC (redacted public IP).
