# 🚦 Routing Protocols: The Internet's GPS System 🗺️ </br>

Welcome to the world of routing! This section explains how your data finds its way across the internet, guided by clever systems called routing protocols. I have covered 4 most commonly used protocols here :
- OSPF [(Open Shortest Path First)](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Routing_Protocols.md#1-ospf-open-shortest-path-first--)
- EIGRP [(Enhanced Interior Gateway Routing Protocol)](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Routing_Protocols.md#2-eigrp-enhanced-interior-gateway-routing-protocol--)
- BGP [(Border Gateway Protocol)](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Routing_Protocols.md#3-bgp-border-gateway-protocol--)
-  RIP [(Routing Information Protocol)](https://github.com/Dee-Techie/Cybersecurity-Portfolio/blob/main/Write-Ups/Routing_Protocols.md#4-rip-routing-information-protocol-%EF%B8%8F-)

Imagine the internet as a massive road network. For your data (like an email or a video stream) to get from your computer to its destination, it needs directions! That's where routing protocols come in. They are like smart GPS systems that help routers (the traffic cops of the internet) figure out the best and most efficient paths for data to travel.

Let's look at some of the most common ones:

## 1. OSPF (Open Shortest Path First) 🧭 </br>
Think of it like: A detailed map-making club for a local neighborhood or a single company campus. 🏘️

### What it does: </br>
OSPF routers all work together to build a complete and accurate map of their entire connected network. They constantly share updates about the "health" and "speed" of their roads (network links).

### Why it's good: </br>
Because every router has a full map, they can quickly calculate the absolute best (shortest and fastest) way to send data to any destination within that network. It's very efficient for medium to large networks.

---

## 2. EIGRP (Enhanced Interior Gateway Routing Protocol) 🧠 </br>
Think of it like: A smart, private delivery service that knows the best routes for its own company's vehicles. 🛣️

### What it does: </br>
EIGRP is special because it's mostly used by Cisco (a big networking company) equipment. Routers using EIGRP share more than just simple map info; they also consider things like road capacity (bandwidth) and potential delays when deciding the best path.

### Why it's good: </br>
It combines the best features of simpler and more complex routing methods, making it very fast and efficient for Cisco-heavy networks.

---

## 3. BGP (Border Gateway Protocol) 🌐 </br>
Think of it like: The global air traffic control system for the entire Internet! ✈️

### What it does: </br>
BGP is the most important routing protocol for the Internet itself. It's what allows huge, separate networks (like your Internet Service Provider's network, Google's network, or Facebook's network) to talk to each other and exchange massive amounts of data.

### Why it's good: </br>
Instead of making detailed maps, BGP focuses on sharing "reachability information" – essentially, telling other big networks: "Hey, I can get to these parts of the internet, and here's how you can send data through me." This ensures data can hop between different parts of the vast global internet reliably.

---

## 4. RIP (Routing Information Protocol) 🚶‍♂️ </br>
Think of it like: A simple "hop-scotch" game to find the shortest path. 📏

### What it does: </br>
RIP is one of the oldest and simplest routing protocols. Routers using RIP share information by simply counting "hops" – meaning, how many other routers they need to go through to reach a destination.

### Why it's good: </br>
It's easy to set up and works well for very small, simple networks.
Limitations: It can be slow to react to changes, and it only cares about the fewest hops, not necessarily the fastest path. If a path with 2 hops is congested and a path with 3 hops is clear, RIP might still choose the 2-hop congested path.

---

<sub>🔗 References & Resources:
TryHackMe — Networking Essentials | Cyber Security 101 (THM) [TryHackMe](https://tryhackme.com/room/networkingessentials)</sub>

