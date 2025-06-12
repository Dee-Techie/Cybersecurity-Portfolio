# Lab : 🦈 Wireshark Packet Analysis (PCAP)

## Background
Wireshark is one of the best - open-source, cross-platform network packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP). 

---

## 📝 Objective
Analyze network traffic using Wireshark to identify protocols, reconstruct sessions, and detect suspicious activity.

---

## 🧰 Tools Used
- Wireshark 🦈
- PCAP Files
- Zeek / TCPDump

---

## 🔬 Key Concepts
- Packet inspection (TCP/IP stack)
- Protocol analysis (HTTP, DNS, FTP, etc.)
- Stream reassembly
- Signature-based detection

---

## 🛡️ Real-World Application
Wireshark is one of the most potent traffic analyser tools available in the wild. There are multiple purposes for its use:

- Detecting and troubleshooting network problems, such as network load failure points and congestion.
- Detecting security anomalies, such as rogue hosts, abnormal port usage, and suspicious traffic.
- Investigating and learning protocol details, such as response codes and payload data.

> Wireshark is not an Intrusion Detection System (IDS). It only allows analysts to discover and investigate the packets in depth. It also doesn't modify packets; it reads them. Hence, detecting any anomaly or network problem highly relies on the analyst's knowledge and investigation skills.
---

## 📷 Screenshots

- Wireshark's Main GUI
  <img src="https://github.com/user-attachments/assets/88f95b71-8a97-490e-9d65-69e191cb5993" alt="Wireshark Interface" width="4500" />


- Packet dissection
- Stream reconstruction
- Detected anomalies

---

## 🧠 Insights / What I Learned
- Wireshark filtering is powerful for narrowing down traffic.
- Reconstructing TCP streams reveals credentials in cleartext (in insecure protocols).
- Learned how to correlate timestamps with suspicious actions.

---

## 🧪 Lab Tasks / Walkthrough
> Step-by-step walkthrough (optional, but useful if this is your GitHub or Notion)

1. Load PCAP file
2. Apply filters: `http`, `tcp.port == 80`, `dns`
3. Follow TCP stream
4. Identify user credentials or suspicious patterns

---

<sub> 🔗 References & Resources: </sub>
- <sub>TryHackMe —  Wireshark - the basics | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/wiresharkthebasics)
- <sub>[Wireshark Filters Cheat Sheet](https://cheatography.com/wireshark/)
- <sub>[Sample PCAPs](https://www.malware-traffic-analysis.net/) </sub>
