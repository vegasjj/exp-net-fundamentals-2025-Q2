# 🌐 EXP-NET-FUNDAMENTALS-2025-Q2

Welcome to my repository for the **Networking Fundamentals Bootcamp (Q2 2025)** organized by **ExamPro**.  
Here you’ll find all of my diagrams, notes and hands-on labs made in Linux, Windows, AWS, Azure and more.

---

## 🗂️ Repository Structure

```txt
.
├── projects/
│   └── week1/
│       ├── Diagramming/            # Active Directory extension to Azure Diagram
│       ├── env-automation/         # AWS VPC automation with CloudFormation
│       ├── cloud-networking/       # AWS VPC peering and Azure VNet Peering
│       ├── linux-firewall-rules/   # Linux firewall labs (iptables, python webserver)
│       ├── linux-networking/       # Linux networking basics (curl, wget, resolvectl)
│       ├── packet-tracer/          # Basic network model with Cisco Packet Tracer
│       ├── windows-firewall-rules/ # Windows firewall rules for a Python webserver
│       └── windows-networking/     # Windows networking commands (tracert, netstat,etc. )
│   └── week2/
│       ├── forward-proxy-with-squid/      # Squid web proxy server PoC
│       ├── load-balancer-with-haproxy/    # HAProxy load balancer PoC
│       ├── reverse-proxy-with-squid/      # Squid reverse web proxy PoC
│       └── trafficflow-with-wireshark/    # Wireshark traffic flow demo
├── README.md                       # ← you are here!
```

## ✍️ Week 1 Journal Highlights

| Key Activity                                 | Take-away                                                                 |
| -------------------------------------------- | ------------------------------------------------------------------------- |
| **Active Directory extension to Azure Diagram** | Designed high level diagram with a possible solution and a video explanation.                                    |
| **Custom VPC with public & private subnets** | Deployed entirely with CloudFormation.                                    |
| **Cisco Packet Tracer network model**      | Basic network model depicting two clients PCs, A DHCP server, an app server, a switch and a router.                                    |
| **Windows networking deep-dive**             | Explored *ipconfig*, *route print*, *netstat*, plus HTTP hosting.         |
| **Firewalling on Linux**                     | **Iptables** rules created to allow access to a Python web server and improve security hardening. |
| **AWS VPC Peering**             | Route tables created and configured to allow inter-VPC traffic.      |
| **Multi-cloud VPC exploration**              | Replicated equivalent VNet peering in Azure.                |

---

## ✍️ Week 2 Journal Highlights

| Lab / Topic                  | Summary                                                                                                                                                                                                 |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------                      |
| **DHCP Packet Analysis with Wireshark** | Analyzed full DORA cycle importing a DHCP request captured in a .pcap file.              |
| **Forward Proxy (Squid)**    | Deployed Squid on Ubuntu EC2 (private subnet). Allowed HTTP/HTTPS from Windows EC2 (`10.200.123.128/28`) via port 3128; demonstrated internet egress without direct public IP.                          |
| **Reverse Proxy (IIS)**    | Used IIS to expose an internal Windows web service on Windows EC2 to the internet. External requests hit Ubuntu proxy first, then forward to Windows via private IP.                                          |
| **HAProxy Load Balancer**    | Explored configuration on Ubuntu EC2; undetermined issued prevented the server behind the load balancer to be reached from the Windows client (trouble shooting included).                                                       |

---

## 📌 How to Use This Repo

1. **Clone & explore**:

   ```bash
   git clone https://github.com/vegasjj/exp-net-fundamentals-2025-Q2
   cd exp-net-fundamentals-2025-Q2
   ```

2. **Reproduce a lab**: open the corresponding subdirectory (e.g., `projects/week2/forward-proxy-with-squid`) and follow its `README.md` to setup the environment.
3. **View diagrams and screenshots**: all visual assets live in each `/assets` folder.
4. **Read walkthroughs and notes**: notes, steps taken and troubleshooting  are under each project `Journal.md`.
