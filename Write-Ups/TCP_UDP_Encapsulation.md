# 🧵 Data Delivery & Communication Protocols

The IP protocol allows us to reach a destination host on the network; the host is identified by its IP address. We need protocols that would enable processes on networked hosts to communicate with each other. There are two transport protocols to achieve that: UDP and TCP (both operate at Layer 4 - ISO OSI Model).

Both UDP (User Datagram Protocol) and TCP (Transmission Control Protocol) are transport layer protocols used for data transmission:

#### 📬 UDP (User Datagram Protocol): 
Provides fast but unreliable communication. It is commonly used for real-time applications like video streaming. UDP is like a regular mail service. The sender sends a parcel without any confirmation of delivery. There is also no tracking or guarantee that the parcel is going to be delivered.

#### 📦 TCP (Transmission Control Protocol): 
Ensures reliable and ordered communication, using acknowledgments and retransmissions if errors occur. TCP works more like a registered mail service. With registered mail, the sender sends a parcel to a recipient, and they're notified when the parcel is delivered. The sender can also track the parcel if it is lost or delayed.

- A TCP connection is established using what’s called a three-way handshake. Two flags are used: <ins>SYN (Synchronise)</ins> and <ins>ACK (Acknowledgment)</ins>. The packets are sent as follows:
   - 🚦 <ins>SYN Packet</ins>: The client initiates the connection by sending a SYN packet to the server. This packet contains the client’s randomly chosen initial sequence number.
   - 🚦 <ins>SYN-ACK Packet</ins>: The server responds to the SYN packet with a SYN-ACK packet, which adds the initial sequence number randomly chosen by the server.
   - 🚦 <ins>ACK Packet</ins>: The three-way handshake is completed as the client sends an ACK packet to acknowledge the reception of the SYN-ACK packet.

---

## 📡 Data Encapsulation

It refers to the process where every layer adds a header (and sometimes a trailer) to the received unit of data and then sends the “encapsulated” unit to the layer below. Encapsulation is an essential concept as it allows each layer to focus on its intended function.

- Application data: It all starts when the user inputs the data they want to send into the application. For example, you write an email or an instant message and hit the send button. The application formats this data and starts sending it according to the application protocol used, using the layer below it, the transport layer.
- Transport protocol segment or datagram: The transport layer, such as TCP or UDP, adds the proper header information and creates the TCP segment (or UDP datagram). This segment is sent to the layer below it, the network layer.
- Network packet: The network layer, i.e. the Internet layer, adds an IP header to the received TCP segment or UDP datagram. Then, this IP packet is sent to the layer below it, the data link layer.
- Data link frame: The Ethernet or WiFi receives the IP packet and adds the proper header and trailer, creating a frame.
- The process is then reversed on the receiving end until the application data is extracted.

## 🔄 The Life of a Packet

Let’s consider the scenario where we search for something on Google.

- On Google's search page, we enter the search query and hit enter.
- Our web browser, using HTTPS, prepares an HTTP request and pushes it to the layer below it, the transport layer.
- The TCP layer needs to **establish a connection via a three-way handshake between our browser and Google's web server**. After establishing the TCP connection, it can send the HTTP request containing the search query. Each TCP segment created is sent to the layer below it, the Internet layer.
- The IP layer **adds the source IP address**, i.e., our computer, and the destination IP address. For this packet to reach the router, our laptop delivers it to the layer below it, the link layer.
- Depending on the protocol, The link layer **adds the proper link layer header and trailer**, and the packet is sent to the router.
- The router **removes the link layer header and trailer, inspects the IP destination, among other fields, and routes the packet to the proper link**. Each router repeats this process until it reaches the router of the target server.
- The steps will then be reversed as the packet reaches the router of the destination network. 

<sub>🔗 References & Resources:
TryHackMe — Networking Concepts | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/networkingconcepts)</sub>
