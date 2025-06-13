# 🦈 Wireshark Packet Analysis (PCAP)

- Wireshark's [Basics📎](https://github.com/Dee-Techie/Cybersecurity-Portfolio/edit/main/Write-Ups/Packet_Capture_and_Analysis.md#-wiresharks-basics)
- Wireshark's [Advanced Features📎](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Packet_Capture_and_Analysis.md#-wiresharks-advanced-features)

## 📚 Overview

Wireshark is a powerful open-source, cross-platform network packet analyzer used to:

* Troubleshoot network issues
* Detect suspicious or malicious traffic
* Analyze network protocols (headers, payloads, etc.)

> ⚠️ **Note:** Wireshark is **not** an Intrusion Detection System (IDS). It only captures and displays traffic. Effective use requires analyst expertise.

---

## 🔧 Interface & Core Features

### 1. 🧰 Interface Overview

* **Toolbar:** Access filters, start/stop capture, and export tools.
* **Display Filter Bar:** Refine views using display filters.
* **Recent Files:** Quick access to previously opened PCAPs.
* **Capture Filter & Interfaces:** Set filters before capture; choose interfaces (e.g., `eth0`, `lo`, `ens33`).
* **Status Bar:** Shows packet stats, profile info.

![Wireshark Interface](https://github.com/user-attachments/assets/88f95b71-8a97-490e-9d65-69e191cb5993)

### 2. 📂 Loading PCAP Files

* Open via **Recent Files**, **File > Open**, or drag-and-drop.

![Loading PCAP](https://github.com/user-attachments/assets/2f303251-a73e-4f9b-aece-15d3d0cf1bab)

### 3. 🎨 Packet Coloring Rules

Helps highlight and categorize packet types.

* **Temporary Rules:** Session-based, created via right-click or View → Conversation Filter.
* **Permanent Rules:** Persist via View → Coloring Rules.
* **Toggle Coloring:** View → Colorize Packet List.
* **Custom Rules:** Use filters to colorize specific traffic (e.g., HTTP GET).

![Coloring Rules](https://github.com/user-attachments/assets/24c1dbb9-d155-4700-a98d-8a00d663a0ed)

### 4. 🚦 Capturing Traffic

* **Blue Shark:** Start capture
* **Red Square:** Stop capture
* **Green Arrow:** Restart capture
* **Status Bar:** Shows selected interface & packet count

![Traffic Sniffing](https://github.com/user-attachments/assets/193121ae-5ba9-405f-bbcd-140c2dc01a56)

### 5. 🧪 Packet Dissection

Clicking on a packet shows its breakdown:

| **Layer**       | **Description**                         |
| --------------- | --------------------------------------- |
| Frame           | Frame number, timestamp                 |
| MAC             | Source & Destination MAC addresses (L2) |
| IP              | Source & Destination IP addresses (L3)  |
| TCP/UDP         | Transport layer info like ports (L4)    |
| Protocol Errors | Retransmissions, issues (L4)            |
| App Protocol    | Protocol (HTTP, FTP, SMB, etc.) (L7)    |
| App Data        | Application payload data                |

![Packet Dissection](https://github.com/user-attachments/assets/afbb3885-22e4-4dd5-92ba-27633bd4bd0a)

---

## 🧰 Utilities & Advanced Analysis

### 6. 📦 Packet Utilities

* **Unique Packet Numbers:** Easy reference
* **Navigation Tools:** Jump to packet, follow conversations
* **Search Options:**

  * Display filters
  * Hex values
  * Strings
  * Regex
* **Marking Packets:** Temporary, not saved
* **Adding Comments:** Persistent across saves
* **Export Tools:**

  * File → Export Specified Packets
  * File → Export Objects (HTTP, SMB, TFTP)
* **Timestamps:** View → Time Display Format (UTC, seconds, etc.)
* **Expert Info:** Analyze → Expert Information for severity flags

| Severity | Color  | Description              |
| -------- | ------ | ------------------------ |
| Chat     | Blue   | Normal traffic           |
| Note     | Cyan   | Notable but not critical |
| Warn     | Yellow | Minor issues             |
| Error    | Red    | Malformed or problematic |

---

## 🔍 Filtering Traffic

### 7. 🧪 Filter Types

* **Capture Filters:** Set **before** capture; limits what is recorded.
* **Display Filters:** Set **after** capture; limits what is shown.

### 🔎 Filtering Methods

* **Apply as Filter:** Right-click → Apply → auto-applies filter.
* **Prepare as Filter:** Right-click → Prepare → modify before applying.
* **Conversation Filter:** Isolate full stream (IP + Port).
* **Colorize Conversation:** Highlights traffic without filtering it out.
* **Apply as Column:** Adds selected value as a visible column.
* **Follow Stream:** Reconstructs application data (chat, creds, etc.)

![Follow Stream](https://github.com/user-attachments/assets/da382ebe-00c6-4934-9eff-bc49eabc6605)

> 🧹 **Reset Filters:** Click ❌ in the Display Filter Bar.

---
## 🧠 Mastering Wireshark – Advanced Features & Filtering

### 📊 Wireshark Statistics Toolkit

Wireshark offers a rich set of statistical views to help analyze captured traffic patterns, endpoints, and protocol behavior.

### Key Tools:

- **Resolved Addresses**  
  Maps IPs to hostnames via DNS responses.  
  `Menu: Statistics → Resolved Addresses`

- **Protocol Hierarchy**  
  Visualizes all protocols with usage metrics (counts and %).  
  `Menu: Statistics → Protocol Hierarchy`

- **Conversations**  
  Displays bi-directional traffic between endpoints (Ethernet/IP/TCP/UDP).  
  `Menu: Statistics → Conversations`

- **Endpoints**  
  Lists unique nodes by layer. Useful for identifying source/destination devices.  
  `Menu: Statistics → Endpoints`
![image](https://github.com/user-attachments/assets/0322b7b1-b540-4aed-9b44-f34dc7e8f836)

### 🌍 Name Resolution & GeoIP

- **MAC Name Resolution**: Resolves MAC addresses to vendors (based on OUI).
- **IP/Port Name Resolution**: Enable in `Edit → Preferences → Name Resolution`.
- **GeoIP Mapping**: Requires [MaxMind DB](https://dev.maxmind.com/geoip/docs/databases). Setup under:
  `Edit → Preferences → Name Resolution → MaxMind database directories`.

Once configured, Wireshark shows geographic data in conversation and endpoint views.

---

### 🌐 Protocol-specific Stats

- **IPv4 & IPv6**  
  Separate traffic stats per IP version.  
  `Menu: Statistics → IPvX Statistics`

- **DNS Stats**  
  View query types, response codes, and more.  
  `Menu: Statistics → DNS`

- **HTTP Stats**  
  Inspect request methods, response codes, and URIs.  
  `Menu: Statistics → HTTP`

---

## 🎯 Advanced Packet Filtering

Wireshark supports two filter types: **Capture Filters** (set before capture) and **Display Filters** (used during/after capture).

---

### 🔐 Capture Filters (BPF Syntax)

- Lightweight filters applied *before* packet capture.
- Syntax is limited to basic protocol/port/host-based rules.
- Example: `tcp port 80` (captures only HTTP traffic)
- `Menu: Capture → Capture Filters`

**Filter Building Blocks**:

| Type       | Example            |
|------------|--------------------|
| Protocol   | `ip`, `tcp`, `udp` |
| Host/IP    | `host 192.168.1.10`|
| Port       | `port 443`         |
| Net Range  | `net 192.168.0.0/16`|
| Direction  | `src`, `dst`, `src or dst` |

> ⚠️ Use capture filters carefully—if a filter misses traffic, you can’t recover it later.

---

### 👓 Display Filters (Post-Capture)

Display filters are Wireshark’s true power feature—rich, flexible, and user-friendly.

- Filter captured traffic live or post-analysis.
- Syntax supports 3000+ protocols.
- Example: `tcp.port == 443`
- `Menu: Analyze → Display Filters`

---

## ⚙️ Operators in Display Filters

### 🧮 Comparison Operators

| Operation           | Symbol | Example                        |
|---------------------|--------|--------------------------------|
| Equal               | `==`   | `ip.src == 192.168.1.10`       |
| Not Equal           | `!=`   | `ip.dst != 10.0.0.1`           |
| Greater Than        | `>`    | `ip.ttl > 100`                 |
| Less Than           | `<`    | `ip.ttl < 10`                  |
| Greater or Equal    | `>=`   | `ip.ttl >= 64`                 |
| Less or Equal       | `<=`   | `ip.ttl <= 128`                |

> Supports both decimal (`128`) and hex (`0x80`) values.

---

### 🔗 Logical Operators

| Operation | Symbol | Example                                                   |
|-----------|--------|-----------------------------------------------------------|
| AND       | `&&`   | `(ip.src == 192.168.1.10) && (tcp.port == 80)`            |
| OR        | `||`   | `(ip.dst == 8.8.8.8) || (ip.dst == 1.1.1.1)`              |
| NOT       | `!`    | `!(tcp.flags.syn == 1 && tcp.flags.ack == 1)`            |

> 🔄 Prefer using `!(expr)` instead of `!=` for clarity.

---

### 🎨 Filter Toolbar Tips

- **Autocomplete** assists with valid filter fields.
- **Lowercase** is recommended for filter keywords.
- **Color Indicators**:
  - 🟢 Green: Valid filter
  - 🟡 Yellow: Partially valid
  - 🔴 Red: Invalid or unrecognized filter

---

## 🌐 Common Protocol Filters

### 📦 IP (Network Layer)

| Filter                      | Meaning                              |
|-----------------------------|--------------------------------------|
| `ip`                        | All IP traffic                       |
| `ip.addr == 192.168.1.1`    | Any packet to/from this IP           |
| `ip.src == 192.168.1.10`    | Source IP filter                     |
| `ip.dst == 192.168.1.20`    | Destination IP filter                |
| `ip.addr == 10.0.0.0/8`     | CIDR match for subnets               |

---

### 🚪 TCP/UDP (Transport Layer)

| Filter                      | Description                          |
|-----------------------------|--------------------------------------|
| `tcp.port == 80`            | All HTTP (port 80) traffic           |
| `udp.port == 53`            | All DNS queries/responses            |
| `tcp.srcport == 443`        | TLS traffic from server              |
| `udp.dstport == 5353`       | Multicast DNS to port 5353           |

---

### 🌍 HTTP & DNS (Application Layer)

| Filter                          | Description                         |
|----------------------------------|-------------------------------------|
| `http`                          | All HTTP packets                    |
| `http.request.method == "GET"`  | HTTP GET requests                   |
| `http.response.code == 404`     | HTTP 404 Not Found                  |
| `dns`                           | All DNS traffic                     |
| `dns.flags.response == 1`       | DNS responses only                  |
| `dns.qry.name == "google.com"`  | Queries for `google.com`            |

---

## 🧰 Display Filter Expression Tool

- Launch: `Analyze → Display Filter Expression`
- Helpful for:
  - Browsing protocol fields
  - Matching correct data types
  - Exploring predefined values

> 🛠 Ideal for beginners—acts like a GUI filter builder.

---

## 🧠 Advanced Filter Functions

### 🔍 Keyword & Pattern Matching

| Operator   | Purpose                             | Example                                    |
|------------|-------------------------------------|--------------------------------------------|
| `contains` | Checks for a substring (case-sensitive) | `http.server contains "Apache"`       |
| `matches`  | Regex match (case-insensitive)         | `http.host matches "\.(php|html)$"`     |
| `in`       | Set membership                        | `tcp.port in {80 443 8080}`             |

---

### 🔤 String Functions

| Function      | Description                        | Example                                       |
|---------------|------------------------------------|-----------------------------------------------|
| `upper()`     | Converts to uppercase              | `upper(http.server) contains "NGINX"`         |
| `lower()`     | Converts to lowercase              | `lower(http.server) contains "nginx"`         |
| `string()`    | Casts to string (use with regex)   | `string(frame.number) matches "[13579]$"`     |

---

## ⭐ Filter Bookmarks & Profiles

### 🔖 Bookmarks & Filter Buttons

- Save frequent filters as buttons via the filter toolbar.
- Quickly switch views without rewriting complex filters.

### 👤 Profiles

Profiles store:
- Filter buttons
- Colouring rules
- Layout preferences

Create/manage under:
- `Edit → Configuration Profiles`
- Or: Use the bottom-right corner of the status bar

> 🎯 Great for switching between general, malware, DNS, or HTTP inspection setups.

---

## ✅ Key Takeaways

- Wireshark filtering is essential for focused, efficient packet analysis.
- Use **capture filters** to limit what gets recorded.
- Use **display filters** to drill into specific data post-capture.
- Mastering comparison and logical operators unlocks powerful filtering combos.
- Tools like GeoIP, stats dashboards, and filter expressions enhance real-world analysis.

---

## 🔗 References & Resources

- [Wireshark - The Basics (TryHackMe)](https://tryhackme.com/room/wiresharkthebasics)  
- [Wireshark Packet Operations (TryHackMe)](https://tryhackme.com/room/wiresharkpacketoperations)  
- [Wireshark Filters Cheat Sheet](https://cheatography.com/wireshark/)  
- [Sample PCAPs for Practice](https://www.malware-traffic-analysis.net/)
