# DHCP 🎯 (targets correct IP address) or 🛠️ (network tool)

Dynamic Host Configuration Protocol is an application-level protocol that relies on **UDP**; the server listens on UDP port 67, and the client sends from UDP port 68. Our smartphone and laptop are configured to use DHCP by default.

## 👩‍💻 How Your Laptop Connects to Wi-Fi So Easily
Imagine you walk into your favorite coffee shop, get your drink, and open your laptop. You connect to the Wi-Fi, and magically, you're online! You didn't type in any confusing numbers, yet your laptop just knew how to get on the internet. How did this happen? It's thanks to something called DHCP.

## 🤹‍♀️ The Essentials for Network Access
To get online, any device needs a few key pieces of information, like:
- An <ins>IP address</ins>: This is like your device's unique "house number" on that specific network.
- A <ins>"router" or "gateway"</ins> address: This is the address of the device that helps your data leave the local network and go out to the internet (think of it as the post office).
- A <ins>"DNS server"</ins> address: This is like a phonebook for the internet. When you type "https://www.google.com/search?q=google.com," the DNS server translates that name into Google's IP address.

## ♟ The Problem with Doing It Manually
You could manually type in all these numbers every time you connect to a new network, but that would be a huge hassle, especially for phones and laptops that move around a lot. Plus, if two devices accidentally pick the same IP address, they'll both have trouble getting online!

## 🎭 DHCP follows four steps: Discover, Offer, Request, and Acknowledge **(DORA)**:

- 📡 DHCP Discover: The client broadcasts a DHCPDISCOVER message seeking the local DHCP server if one exists.
  - (Your laptop asks): "Is there a DHCP server out there?"
  - Your laptop broadcasts a message to everyone on the network because it doesn't even have an IP address yet! It's like shouting into a crowd.
  - (You'll see it send from 0.0.0.0 to 255.255.255.255 because it has no assigned IP, and to ff:ff:ff:ff:ff:ff for the MAC address to reach everyone.)

- 🎁 DHCP Offer: The server responds with a DHCPOFFER message with an IP address available for the client to accept.
  - The DHCP server responds): "Yes, I'm here! I have an IP address for you: 192.168.66.133!"
  - The DHCP server sees your laptop's request and picks an available IP address, along with other settings like the router's address and DNS server. It then offers these to your laptop
  
- 🙏 DHCP Request: The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP.
  - (Your laptop accepts): "Okay, I'll take 192.168.66.133!"
  - Your laptop sends a message back to the DHCP server confirming that it accepts the offered IP address. It broadcasts this again just to be sure.

- 👍 DHCP Acknowledge: The server responds with a DHCPACK message to confirm that the offered IP address is now assigned to this client.
  - (The DHCP server confirms): "Great! That IP is now officially yours!"
  - The DHCP server sends a final confirmation that the IP address and all other settings are now assigned to your laptop.

<img src="https://github.com/user-attachments/assets/99f09526-689f-4beb-b654-7874d89b700c" alt="DHCP 4 Stages : DORA" width="700" />

## 💎 What you get at the end
At the end of the DHCP process, our device would have received all the configuration needed to access the network/Internet and will have the following :

- The <ins>leased IP address</ins> to access network resources (send and receive data)
- The <ins>gateway to route</ins> our packets outside the local network
- A <ins>DNS server</ins> to resolve domain names (more on this later)
---

# 🔌 ARP (Address resolution Protocol)

## 🧠 How Devices Chat on Your Network
Imagine you want to send a letter to a friend. You know their home address (like an IP address on a network), but to actually deliver the letter, you also need to know their exact mailbox number (like a MAC address). Computers work in a similar way when they communicate on the same local network, like your home Wi-Fi or an office Ethernet cable.

## 🔎 IP Addresses vs. MAC Addresses
- IP Address (Internet Protocol Address): Think of this as the "home address" for your device on the internet. It helps send information across different networks. Example: 192.168.1.100.
- MAC Address (Media Access Control Address): This is like a unique "mailbox number" burned into your device's network card. It's a physical address that helps devices find each other directly on the same local network. Example: 7C:DF:A1:D3:8C:5C.

### 🧩 The Problem: Knowing IP but Needing MAC
When your computer wants to send data (which it wraps into something called an IP packet) to another computer on the same local network (like your laptop talking to your smart TV), it knows the other computer's IP address. But for the data to physically travel over the network (whether it's Wi-Fi or Ethernet), it needs to be put inside a special "envelope" called a data link frame. This envelope needs the destination device's MAC address.

So, how does your computer figure out the other device's MAC address if it only knows its IP address? This is where ARP comes in!

> ARP: The Network's "Find My MAC Address" Service
> ARP (Address Resolution Protocol) is like a detective service on your local network. It helps devices find the MAC address of another device when they only know its IP address.

## ⚙️ Here's how it works in simple steps:

- ARP Request (The Question):
  - Let's say your computer (with IP 192.168.66.89) wants to talk to another computer (with IP 192.168.66.1).
  - Your computer shouts out a question to everyone on the local network: "Hey, who has the IP address 192.168.66.1? Tell 192.168.66.89!"
  - This shout is sent using a special broadcast MAC address (ff:ff:ff:ff:ff:ff), meaning every device on the network hears it.

- ARP Reply (The Answer):
  - Only the device with the IP address 192.168.66.1 will hear that question and recognize its own IP address.
  - It then replies directly to your computer, saying: "That's me! My MAC address is 44:df:65:d8:fe:6c."
  - Once your computer gets this ARP Reply, it now knows both the IP address and the MAC address of the target device. It can then properly create the data link frame and send the IP packet directly to that device's MAC address.

## 🧭 Important to Remember:
- Temporary Knowledge: Devices don't store everyone's MAC address forever. They only look them up when they need to communicate.
- Direct Encapsulation: ARP requests and replies are special; they are put directly into the "data link frame" (Ethernet or Wi-Fi frame) and not inside an IP packet or UDP packet. This shows how fundamental ARP is to getting data moving on the local network.
- Bridge Between Layers: While IP addresses are about "Layer 3" (how data travels across different networks), and MAC addresses are about "Layer 2" (how data travels on a single local network), ARP acts as a bridge, translating between these two types of addresses.
So, even though we often think about communication using IP addresses, ARP is the unsung hero that helps devices find each other's physical locations on the same local network so they can actually exchange information.


---

<sub>🔗 References & Resources:
TryHackMe — Networking Essentials | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/networkingessentials)</sub>

