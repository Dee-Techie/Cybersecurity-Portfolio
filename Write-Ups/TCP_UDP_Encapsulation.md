#🧵 Data Delivery & Communication Protocols

The IP protocol allows us to reach a destination host on the network; the host is identified by its IP address. We need protocols that would enable processes on networked hosts to communicate with each other. There are two transport protocols to achieve that: UDP and TCP (both operate at Layer 4 - ISO OSI Model).

Both UDP (User Datagram Protocol) and TCP (Transmission Control Protocol) are transport layer protocols used for data transmission:

#### 📬 UDP (User Datagram Protocol): 
Provides fast but unreliable communication. It is commonly used for real-time applications like video streaming. UDP is like a regular mail service. The sender sends a parcel without any confirmation of delivery. There is also no tracking or guarantee that the parcel is going to be delivered.

#### 📦 TCP (Transmission Control Protocol): 
Ensures reliable and ordered communication, using acknowledgments and retransmissions if errors occur. TCP works more like a registered mail service. With registered mail, the sender sends a parcel to a recipient, and they're notified when the parcel is delivered. The sender can also track the parcel if it is lost or delayed.

- A TCP connection is established using what’s called a three-way handshake. Two flags are used: SYN (Synchronise) and ACK (Acknowledgment). The packets are sent as follows:
   - <ins>SYN Packet</ins>: The client initiates the connection by sending a SYN packet to the server. This packet contains the client’s randomly chosen initial sequence number.
   - <ins>SYN-ACK Packet</ins>: The server responds to the SYN packet with a SYN-ACK packet, which adds the initial sequence number randomly chosen by the server.
   - <ins>ACK Packet</ins>: The three-way handshake is completed as the client sends an ACK packet to acknowledge the reception of the SYN-ACK packet.
