# DHCP 🎯 (targets correct IP address) or 🛠️ (network tool)

Dynamic Host Configuration Protocol is an application-level protocol that relies on **UDP**; the server listens on UDP port 67, and the client sends from UDP port 68. Our smartphone and laptop are configured to use DHCP by default.

When we connect a device to a new network, we need to set up network settings like IP addresses. Manually setting these is fine for servers because they usually stay in one place. But for most devices, especially mobile ones, it’s better to have an automatic setup. This saves time and avoids problems like IP address conflicts, which happen when two devices use the same address and can’t access the network properly. The solution to this is using DHCP, which automatically assigns network settings to devices.

DHCP follows four steps: Discover, Offer, Request, and Acknowledge (DORA):

- DHCP Discover: The client broadcasts a DHCPDISCOVER message seeking the local DHCP server if one exists.
- DHCP Offer: The server responds with a DHCPOFFER message with an IP address available for the client to accept.
- DHCP Request: The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP.
- DHCP Acknowledge: The server responds with a DHCPACK message to confirm that the offered IP address is now assigned to this client.
