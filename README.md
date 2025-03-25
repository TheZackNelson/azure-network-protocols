<p align="center">
  <img src="https://i.imgur.com/Ua7udoS.png" alt="Azure Traffic Examination"/>
</p>

<h1 align="center">Azure Network Protocols and Network Security Groups (NSGs)</h1>

In this lab, you'll explore how different network protocols behave between Azure virtual machines and use **Wireshark** to inspect that traffic. You'll also experiment with **Network Security Groups (NSGs)** to control which types of traffic are allowed or blocked.

---

<h2>🎥 Video Demonstration</h2>

- ### [YouTube: Azure VMs, Wireshark, and NSG Traffic Analysis](https://www.youtube.com) *(Coming Soon)*

---

<h2>🧰 Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines & Networking)
- Remote Desktop Protocol (RDP)
- SSH Terminal (Ubuntu)
- Wireshark (Network Protocol Analyzer)
- Network Security Groups (NSGs)

---

<h2>🖥️ Operating Systems Used</h2>

- Windows 10 Pro (21H2) — For capturing and analyzing packets  
- Ubuntu Server 20.04 LTS — For generating Linux-side traffic

---

<h2>📦 Lab Objectives</h2>

- Deploy two VMs in Azure within the same virtual network
- Install and configure **Wireshark** on the Windows VM
- Generate traffic using various protocols (ICMP, SSH, HTTP, DNS, RDP)
- Use NSGs to allow or block traffic types
- Observe how filtered packets appear (or don’t) in Wireshark

---

<h2>⚙️ Lab Setup & Execution</h2>

### ✅ Step 1: Deploy Two Azure VMs

- **VM 1 (Windows 10)**  
  Name: `Win-VM`  
  Used for capturing and inspecting traffic with **Wireshark**

- **VM 2 (Ubuntu 20.04)**  
  Name: `Linux-VM`  
  Used to generate traffic toward the Windows VM

- Place both VMs in the **same Virtual Network and Subnet**

---

### ✅ Step 2: Install Wireshark on Windows VM

- Log in to `Win-VM` via RDP
- Download and install **Wireshark**
- Launch Wireshark and select the primary Ethernet interface for capture
- Begin capturing traffic

---

### ✅ Step 3: Generate and Observe Traffic

From **Linux-VM**:

- Ping the Windows VM using `ping <private IP>`
- Attempt an SSH connection to Windows VM (will fail, but still sends traffic)
- Use `curl` to make HTTP requests to the Windows VM
- Run `nslookup` or `dig` to test DNS queries (if a DNS service is set up)

From **Win-VM**:

- Observe ICMP, TCP handshakes, DNS requests, and HTTP packets in Wireshark
- Apply filters like:
  - `icmp`
  - `tcp.port == 22` (SSH)
  - `tcp.port == 80` (HTTP)
  - `dns`

---

### ✅ Step 4: Modify Network Security Groups (NSGs)

- In Azure Portal, go to **NSG > Inbound Rules**
- Add or remove rules to block/allow protocols:
  - Block ICMP by removing the rule or setting Deny All Inbound
  - Allow port 80 (HTTP) or 22 (SSH)
  - Observe behavior in **real time** with Wireshark

---

<h2>🔍 Key Observations</h2>

- ICMP (ping) traffic disappears from Wireshark when blocked by NSG
- TCP handshake (SYN, SYN-ACK, ACK) is visible for allowed protocols
- DNS traffic uses UDP port 53 and can be filtered easily
- NSGs apply at the **subnet or NIC level**, not inside the OS
- Wireshark helps **visually confirm** whether packets are being dropped or allowed

---

<h2>📚 Real-World Application</h2>

This lab reinforces the importance of:

- Network protocol fundamentals (ICMP, TCP, UDP)
- Understanding firewall behavior in cloud environments
- Packet-level analysis using Wireshark
- Cloud security basics using NSGs

---

<h2>💡 Final Thoughts</h2>

If you're pursuing a career in networking, cloud administration, or cybersecurity, these labs are excellent practice. Do them multiple times until you can deploy and troubleshoot traffic from memory.

Want more practice?
- Try adding a third VM with a web server
- Use port scanning tools to test NSG limits
- Set up logging with Azure Network Watcher

---

<h2>📬 Questions or Issues?</h2>

Open an issue in this repo or comment on the walkthrough video if you need help or want to share your own setup!

---
