# 🦈 Wireshark Packet Analysis (PCAP)

## Background
Wireshark is one of the best - open-source, cross-platform network packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP). 

---

## 🛡️ Real-World Application
Wireshark serves several key purposes:

- Troubleshooting network issues like congestion or failure points.
- Identifying security threats such as suspicious traffic or rogue devices.
- Analyzing network protocols by examining headers, payloads, and response codes.

> ⚠️ Wireshark is **not** an Intrusion Detection System (IDS). It doesn’t alter or block traffic—its strength lies in visibility. Accurate detection depends on the analyst’s expertise and ability to interpret packet data.

---

## 📷 Wireshark's Basics

### 1. 🧰 Wireshark main Interface Overview :
  - Toolbar: Offers quick access to core functions like filtering, capturing, exporting, and merging packets.
  - Display Filter Bar: Main area for entering display filters to refine packet views.
  - Recent Files: Shows recently opened capture files; double-click to reopen.
  - Capture Filter & Sniffing Interfaces: Set filters to limit traffic before capturing + Lists available network interfaces (e.g., `eth0`, `lo`, `ens33`) for live traffic capture.
  - Status Bar: Displays capture stats, profile in use, and packet counts.

<img alt="Wireshark's main GUI" src="https://github.com/user-attachments/assets/88f95b71-8a97-490e-9d65-69e191cb5993" />

### 2. 📦 Next comes - Loading PCAP files </br>

There are a few ways to load a PCAP file - you can either load a recently open file from "Recent files" section, use the "File" menu, drag and drop the file, or double-click on the file to load a pcap.
</br>

<img alt="Loading PCAP files" src="https://github.com/user-attachments/assets/2f303251-a73e-4f9b-aece-15d3d0cf1bab" /></br>

### 3.🩸 Coloring Rules for Packets </br>

Coloring highlights important or unusual traffic (e.g., why most packets may appear green by default). It makes scanning captures more efficient.

Types of Coloring Rules:
- Temporary Rules:
  - Active only during the current session.
  - Created via Right-click or View → Conversation Filter.
- Permanent Rules:
  - Saved in the user profile and persist between sessions.
  - Created via View → Coloring Rules or Right-click.

✅ We can toggle coloring on/off using View → Colorize Packet List.</br>
✅ We can define your own color rules using display filters to highlight specific traffic (e.g., HTTP GET requests, DNS errors, etc.).</br>

<img alt="Coloring Rules" src="https://github.com/user-attachments/assets/24c1dbb9-d155-4700-a98d-8a00d663a0ed" />

### 4.🚦 Traffic Sniffing </br>

The blue "shark button" starts network sniffing (capturing traffic), the red button stops the sniffing, and the green button restarts the sniffing process. In addition, the status bar also provides the used sniffing interface and the number of collected packets.

<img alt="Traffic Sniffing" src="https://github.com/user-attachments/assets/193121ae-5ba9-405f-bbcd-140c2dc01a56" /></br>

### 5. 🧪 Packet Dissection

Packet dissection (or protocol dissection) refers to analyzing packet data by decoding its protocol layers. Wireshark supports hundreds of protocols and allows custom dissector scripts. It uses the OSI model to break down packets.

Clicking on a packet in the **Packet List Pane** reveals its detailed breakdown in the **Details Pane**, and highlights the relevant bytes in the **Packet Bytes Pane**.

Each packet may contain 5–7 protocol layers. Here's a quick overview using an HTTP packet:
  | **Layer**           | **Description**                                                                 |
  |---------------------|---------------------------------------------------------------------------------|
  | **Frame (Layer 1)** | Basic packet info (frame number, timestamp, physical layer data).              |
  | **MAC (Layer 2)**   | Source & destination MAC addresses (Data Link Layer).                          |
  | **IP (Layer 3)**    | Source & destination IP addresses (Network Layer).                             |
  | **Protocol (L4)**   | TCP/UDP headers, ports (Transport Layer).                                      |
  | **Protocol Errors** | Info on reassembly, retransmissions (part of Layer 4).                         |
  | **App Protocol**    | Protocol used: HTTP, FTP, SMB, etc. (Application Layer).                       |
  | **App Data**        | Data exchanged by the application (payload-level insight).                     |


### 6. 📦 Wireshark Packet Utilities
- Each packet is assigned a unique number, making it easier to track and revisit specific events during analysis.
- Use the **Go** menu or toolbar to jump to a specific packet, follow conversations, or navigate through sessions.
- Use `Edit → Find Packet` to search for packets by content using:
  - **Display filters**
  - **Hex values**
  - **Strings**
  - **Regex** (Regular Expression)
  - Search can target: Packet List, Details, or Bytes pane.
- Market Packets: Right-click or use `Edit` to mark packets for review. Marked packets appear in black but are session-based and not saved.
- Add comments to packets for documentation or team handoff. Unlike marks, comments are saved in the capture file.
- Export selected packets via `File → Export Specified Packets` to isolate relevant data for deeper analysis or sharing.
- Extract files from streams like HTTP, SMB, TFTP using `File → Export Objects`.
- Adjust timestamp display via `View → Time Display Format`. Common options include:
  - Seconds since capture
  - UTC time
- In addition, Wireshark highlights protocol issues by severity:

| Severity | Color  | Description                          |
|----------|--------|--------------------------------------|
| Chat     | Blue   | Standard protocol flow               |
| Note     | Cyan   | Notable events                       |
| Warn     | Yellow | Unusual behavior or minor errors     |
| Error    | Red    | Malformed or problematic packets     |

You can view details under `Analyze → Expert Information`.

### 🔍 Packet Filtering in Wireshark

Wireshark offers two types of filters:

- **Capture Filters**: Apply before traffic is collected (for live sniffing).
- **Display Filters**: Apply after capture, to narrow down visible traffic for analysis.

#### 🧪 Filter Methods

#### ➤ Apply as Filter
Right-click on a field → **Apply as Filter**  
Wireshark auto-generates and applies a display filter for that specific value.

#### ➤ Prepare as Filter
Right-click on a field → **Prepare as Filter**  
Generates the filter query but does not apply it until you press **Enter** or modify with **AND/OR**.

#### ➤ Conversation Filter
Right-click on a packet → **Conversation Filter**  
Filters all related packets in the same session (e.g., IP + Port). Useful for tracing a full conversation.

#### ➤ Colourise Conversation
Right-click → **Colorize Conversation**  
Highlights related packets without filtering them out. Useful for visually grouping traffic without losing context.

#### ➤ Apply as Column
Right-click on a value → **Apply as Column**  
Adds the selected value as a visible column in the packet list pane for easier comparison across packets.
![image](https://github.com/user-attachments/assets/b988eb49-d866-4558-b0cd-42b11b9cec7e)

#### ➤ Follow Stream
Right-click → **Follow [TCP/UDP/HTTP] Stream**  
Reconstructs application-level data from packet streams (e.g., chat logs, credentials). Opens in a separate window and auto-applies a stream-specific display filter.

> **Note:** To reset filters, click the ❌ on the Display Filter bar.

---

## 🧠 Insights / What I Learned
- Wireshark filtering is powerful for narrowing down traffic.
- Reconstructing TCP streams reveals credentials in cleartext (in insecure protocols).
- Learned how to correlate timestamps with suspicious actions.


---

<sub> 🔗 References & Resources: </sub>
- <sub>TryHackMe —  Wireshark - the basics | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/wiresharkthebasics)
- <sub>[Wireshark Filters Cheat Sheet](https://cheatography.com/wireshark/)
- <sub>[Sample PCAPs](https://www.malware-traffic-analysis.net/) </sub>
