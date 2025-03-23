<p align="center">
  <img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1 align="center">Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>

In this tutorial, we observe various network traffic between Azure Virtual Machines using Wireshark and analyze how Network Security Groups (NSGs) impact that traffic. This lab demonstrates how protocols behave and how NSGs control traffic flow in a cloud environment.

---

<h2>🎥 Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com) 

---

<h2>🧰 Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Protocol (RDP)
- Ubuntu Terminal (SSH)
- Network Protocols: ICMP, DNS, HTTP/HTTPS, RDP, SSH
- Wireshark (Network Protocol Analyzer)

---

<h2>🖥️ Operating Systems Used</h2>

- Windows 10 Pro (21H2)
- Ubuntu Server 20.04 LTS

---

<h2>📋 High-Level Steps</h2>

- Deploy two Virtual Machines in Azure (Windows and Linux)
- Install and configure Wireshark on the Windows VM
- Initiate traffic between the two VMs (ICMP, SSH, HTTP, DNS)
- Modify NSG rules and observe blocked/allowed traffic in real time

---

<h2>🔍 Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/Ez5xgrs.png" height="80%" width="80%" alt="VM Deployment"/>
</p>
<p>
<strong>Step 1: Deploy Azure Virtual Machines</strong><br />
Create a Windows 10 VM and an Ubuntu 20.04 VM in the same virtual network. Assign each VM a Network Security Group (NSG) and open the necessary ports (RDP for Windows, SSH for Linux, ICMP via custom rules).
</p>
<br />

<p>
<img src="https://i.imgur.com/FIl9ZfM.png" height="80%" width="80%" alt="Wireshark Setup"/>
</p>
<p>
<strong>Step 2: Capture Network Traffic</strong><br />
Install Wireshark on the Windows VM. Start a capture on the active network interface. From the Ubuntu VM, ping the Windows VM’s private IP and initiate connections (SSH, DNS, HTTP) to generate observable traffic in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/sZ0NVQn.png" height="80%" width="80%" alt="NSG Rules Modification"/>
</p>
<p>
<strong>Step 3: Experiment with NSG Rules</strong><br />
Using the Azure Portal, add or remove NSG rules to allow or block specific traffic types (e.g., deny ICMP or allow port 80). Observe how blocked packets appear in Wireshark (e.g., unreachable messages or dropped connections).
</p>
<br />

<p>
<img src="https://i.imgur.com/xQ2EULI.png" height="80%" width="80%" alt="Protocol Filtering"/>
</p>
<p>
<strong>Step 4: Analyze Protocol Behavior</strong><br />
Filter captured packets in Wireshark using filters such as `icmp`, `tcp.port==22`, or `dns`. Examine packet headers, source/destination IPs, protocol handshakes, and analyze how traffic changes based on NSG configurations.
</p>

---

<h2>💡 Key Observations</h2>

- NSGs act as virtual firewalls at the subnet or NIC level.
- Denied traffic does not appear on the receiving VM but may generate ICMP unreachable responses.
- Wireshark helps visualize protocol behavior, packet size, and latency.
- ICMP, DNS, and HTTP are great for basic traffic tests; RDP and SSH help validate secure access controls.

---

<h2>📬 Questions or Issues?</h2>

Open an issue in this repo or comment on the video walkthrough for help or suggestions!

---
