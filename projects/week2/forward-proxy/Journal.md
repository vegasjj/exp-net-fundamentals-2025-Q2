# Forward Proxy with Squid

## Environment

An AWS EC2 instance running Ubuntu with the **squid** package installed was used to set up the web proxy server for this proof of concept.

Two more EC2 instances running Windows Server 2025 were deployed:

- Client proxy – no public IP; all Internet requests are sent through the web proxy server.  
- Jump box – RDP bastion host used to reach the proxy client as it lacks a public IP.

## Deployment

The focus of this proof of concept was to set up a basic **web proxy**. Once you have a working configuration in place we can move on to adding web content filtering and caching (which is the real need from the client).

Having followed the instructions in the [README](./README.md) to set up the web proxy, the next step was to test the internet connectivity from the proxy client.

As you can see in the image below, the jump box was accessed from the internet and from there an RDP session was used to connect to the **proxy client** private interface (10.100.123.141).

![Proxy client being accessed from a Windows jump box](./assets/forward-proxy-3.png)

Above, you can also see the proxy settings pointing the web proxy server private interface 10.200.123.139 on port 3128.

Next, internet connectivity was tested by navigating to the [exampro.co](https://exampro.co) webpage:

![Proxy client accessing the internet](./assets/forward-proxy-2.png)

On the web proxy server, the squid traffic was monitored to capture the client proxy activity. In the image below, you can see the line that shows the proxy client IP 10.100.123.141 being redirected to the [exampro.co](https://exampro.co) webpage.

![Proxy server capturing squid logs](./assets/forward-proxy-1.png)

Also, on the networking configuration for the web proxy server (on the AWS console), it was necessary to **disable the source/destination check** so that the proxy could forward traffic coming from the client proxy without being drop (remember: the web proxy server only forwards packets; it is not the final destination.)


![AWS console showing networking configuration](./assets/forward-proxy-4.png)

Let me know when you have completed these steps to continue with more complex features.
