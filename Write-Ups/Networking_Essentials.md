# 📢 Networking essentials 🚀
Ever wondered how your devices chat online, find each other, or get their internet superpowers automatically? You've come to the right place! This guide breaks down some fundamental networking concepts into simple, digestible pieces.

### Here's what we'll cover in this adventure:
- ⚡️ Dynamic Host Configuration Protocol [(DHCP)](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Networking_Essentials.md#1-dhcp--targets-correct-ip-address-or-%EF%B8%8F-network-tool)
- 📍 Address Resolution Protocol [(ARP)](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Networking_Essentials.md#2--arp-address-resolution-protocol---the-networks-find-my-mac-address-service)
- 🗣️ Internet Control Message Protocol [(ICMP)](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Networking_Essentials.md#3-icmp-the-internets-messenger-for-errors-and-info-)
  - Ping 🏓
  - Traceroute 🗺️
- 🏠 Network Address Translation [(NAT)](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Networking_Essentials.md#4--nat-network-address-translation-)

---

# 1. DHCP 🎯 (targets correct IP address) or 🛠️ (network tool)

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
  - You'll see it send from 0.0.0.0 (Source IP) to 255.255.255.255 (destination IP) because it has no assigned IP, and to ff:ff:ff:ff:ff:ff for the MAC address to reach everyone.

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

# 2. 🔌 ARP (Address resolution Protocol - The Network's "Find My MAC Address" Service)

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
- Bridge Between Layers: While <ins>IP addresses are about "Layer 3" (how data travels across different networks), and MAC addresses are about "Layer 2" (how data travels on a single local network)</ins>, ARP acts as a bridge, translating between these two types of addresses.
So, even though we often think about communication using IP addresses, ARP is the unsung hero that helps devices find each other's physical locations on the same local network so they can actually exchange information.

---

# 3. ICMP: The Internet's Messenger for Errors and Info 📣

Imagine the internet is a vast road network. Sometimes, you need to check if a road is open 🚧, if a destination is reachable 📍, or what path your car takes to get there 🗺️. That's exactly what **ICMP (Internet Control Message Protocol)** does for computers! It's like the internet's built-in system for sending messages about network problems or getting diagnostic information.

Two main tools use ICMP that are super useful for figuring out what's going on with your network:

- ## 1. <ins>Ping</ins>: "Are You There?" 👋
Think of Ping like a game of digital "ping-pong" 🏓

  - How it works:
    -  You send a "ping" (ICMP Echo Request) ✉️: Your computer sends a small message asking, "Are you there?" to another device on the network (like a website server or another computer).
    - The other device "pongs" back (ICMP Echo Reply) ↩️: If the other device is online and willing to talk, it sends a message back saying, "Yes, I'm here!"
    - Measure the time ⏱️: Your computer then measures how long it took for the message to go there and come back. This is called the Round-Trip Time (RTT).

  - What Ping tells you:
    - Is it alive? If you get a reply, you know the other device is online and reachable from your computer. ✅
    - How fast is it? The time it takes for the reply tells you if the connection is quick or slow. 🐌💨
  
  - What can stop it?
    - Offline device 🔌: If the other computer is turned off or disconnected.
    - Firewall blocking 🧱: Security walls (firewalls) can be set up to ignore ping requests to prevent outsiders from easily checking if a system is there.
    - Example:
When you type ping 192.168.11.1, your computer sends four "pings" and then shows you how many came back and how long each took. If it says "0% packet loss," that's great! It means all your messages got through. 🎉
</br>

- ## 2. <ins>Traceroute (or Tracert)</ins>: "Show Me the Way!" 🗺️ </br>
Have you ever wondered how your data travels across the internet to reach a website thousands of miles away? Traceroute (or Tracert on Windows) is your guide! It shows you every "stop" (router) your data takes on its journey.

  - How it works:
Every data packet on the internet has a "Time-to-Live" (TTL) number, like a countdown timer ⏳. Each time the packet passes through a router, this TTL number goes down by one.

    - Starting the journey: Traceroute sends out a series of packets. It starts with a TTL of 1.
    - First stop: The first router it hits will decrement the TTL to 0, then drop the packet and send an ICMP "Time Exceeded" message back to your computer. This tells your computer, "Hey, I was the first stop!" 📍
    - Next stop: Traceroute then sends another packet, this time with a TTL of 2. It passes the first router, goes to the second, which decrements the TTL to 0, drops it, and sends an ICMP "Time Exceeded" message. This reveals the second stop! 📍📍
    - And so on... This process repeats, gradually increasing the TTL, until the packet finally reaches its destination. Each "Time Exceeded" message reveals another router on the path.

  - What Traceroute tells you:
    - The path 🚶‍♂️: You see a list of all the routers (each hop) your data crosses to reach its destination.
    - Location clues 🌍: Sometimes, the names or IP addresses of these routers can even give you hints about their geographic location or the internet providers they belong to.
    - Where problems might be 🛑: If you see a lot of * * * (asterisks), it means a router didn't respond, which could point to a problem or a router configured not to respond to these requests for security reasons.
    - Example:
When you traceroute a website, you'll see a list of numbered "hops." Each number is a router, and you'll see its IP address and how long it took to reach it. It's like seeing every turn your data takes on its trip across the internet! 🛣️

Both Ping and Traceroute are essential tools for anyone trying to understand or fix network issues! 🛠️

---

# 4. 🏠 NAT (Network Address Translation): </br>
The Internet's House Number Hider & Sharer! 🌐 </br>

## The Big Problem: Running Out of Internet Addresses! 😱

Imagine if every single device in the world (your phone, laptop, smart TV, security camera, even your smart fridge!) needed its own unique public "internet address" (an IP address) to get online. We quickly realized we don't have enough addresses for everyone using the old system (IPv4 addresses) because there are billions of devices connecting to the internet! 😬

## The Smart Solution: NAT! 💡
NAT (Network Address Translation) is like having a single "public house number" for your entire building (your home or a company's network), even though many different people live inside (your devices).

- One Public Address, Many Private Devices: Instead of each of your 20 computers at a company needing its own special public internet address, NAT allows them all to share just one (or a few) public IP address. This saves a ton of those precious internet addresses!
- (Think of it: it's like a big apartment building only needing one street address, even though dozens of families live there. Your router acts as the front desk!)

### How NAT Works its Magic (The "Translation Table"): ✨
Your router, which typically handles NAT, has a special "translation table" (like a secret decoder ring 🕵️). This table keeps track of all the internal conversations happening within your private network and matches them up with the shared public internet address.

### Inside vs. Outside:

- Inside (Private): Your devices have "private" IP addresses (like 192.168.0.129). These addresses are only used within your home or company network and aren't visible directly on the public internet.
- Outside (Public): Your router has one "public" IP address (like 212.3.4.5) that the rest of the internet sees.

### The Translator: When your laptop (e.g., private IP 192.168.0.129 sending from "port" 15401) wants to visit a website:
- It sends its request to your router.
- Your NAT-enabled router changes the "return address" on your laptop's request. It makes it look like the request is coming from the router's public IP address (e.g., 212.3.4.5) and a new, unique "port number" (e.g., 19273) it picks for this specific connection.
- When the website sends its reply back to 212.3.4.5 on 19273, your router looks at its translation table, sees that 19273 maps back to your laptop's private IP 192.168.0.129 and port 15401, and forwards the reply directly to your laptop! 🔄

<img src="https://github.com/user-attachments/assets/6bde7ad0-0a70-4183-9972-095cdf3c39bf" alt="NAT" width="700" />

### The Result: </br>
From the website's perspective, it only sees your router's public IP address. It has no idea how many devices are hiding behind it! This makes the internet's limited address supply go much, much further.

---

<sub>🔗 References & Resources:
TryHackMe — Networking Essentials | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/networkingessentials)</sub>

