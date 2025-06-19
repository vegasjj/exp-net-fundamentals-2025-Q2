# Project Journal

Using redhat linux for proof of concept.

Firewlld must be disable to prevent it for starting at boot which can conflict with iptables rules.

Iptables doesnt need explicit incomming traffic rules to allow access to port 8080 where the python webserver is running.

Port 8080 must be allow in the AWS level with the security group just like we did with Windows.

A rules was added to silently drop traffic to 8080 (recommended over "reject" because it doesn't confirm existence to potential port scanning)

We will attempt to redirect traffic from port 7000 to port 8080 externally while keeping the drop rule in place.