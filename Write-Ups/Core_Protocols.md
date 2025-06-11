# 🕹⚓ Networking Core Protocols

## 🌐 DNS: The Internet's Phonebook! 📚 </br>
Instead of memorizing complicated IP addresses (like 172.17.2.172), DNS lets you use easy-to-remember names like google.com. When you type a website name into your browser, DNS works behind the scenes to find the correct IP address so your computer knows where to go.

### How DNS Works (Quickly!): 🏃‍♀️ </br>
DNS primarily uses UDP port 53 for its lookups. Think of it like a quick, single question and answer. If it needs to send larger information, it can use TCP port 53 as a backup.

### Common DNS Record Types (The "Entries" in the Phonebook): 📝
DNS stores different types of information, called "records," for each domain name. Here are the most common ones:

- A Record (Address): This is the most basic entry. It simply maps a website name (like example.com) to its IPv4 address (the standard internet address we're all familiar with).
Example: example.com → 172.17.2.172

- AAAA Record (Quad-A Address): Just like the A record, but for IPv6 addresses. IPv6 is the newer, much larger set of internet addresses designed for all the billions of new devices coming online.
Example: example.com → 2001:0db8:85a3:0000:0000:8a2e:0370:7334

- CNAME Record (Canonical Name): This record lets you point one domain name to another domain name. It's like having an alias!
Example: www.example.com could point to example.com. So, if you type www.example.com, DNS first tells your computer to look up example.com instead.

- MX Record (Mail Exchange): This one is special for email! When you send an email to test@example.com, your mail server uses the MX record to find out which specific server handles emails for example.com.
Example: It tells your mail server, "Send emails for example.com to mail.example.com." 📧

### Putting it Together:
When you type example.com in your browser, DNS helps it find the A record (or AAAA record) to get the IP address. But when you send an email, it looks for the MX record to find the right mail server.

> Command Line Lookup: nslookup 💻
If you're curious and want to look up this information yourself, you can use a command-line tool like nslookup. For instance, typing nslookup example.com will show you its IP address right in your terminal!

---

## 🔑 Domain Name Registration: Owning Your Corner of the Internet!
We've learned how DNS translates easy-to-remember website names (like example.com) into IP addresses. But who gets to decide what IP address example.com points to? And how do you get your own yourwebsite.com?

### Owning a Domain Name: Your Internet Authority! ✨
When you register a domain name (like example.com), you essentially "buy" the right to use that name for a period (usually one or more years). This grants you the authority to set up all its DNS records – like the A records (which IP address the website lives on), AAAA records (for IPv6 addresses), and MX records (for email servers), among others. It's like getting the official deed to your internet property! 🏡

### The "Who Is" Behind the Website: WHOIS Records 🕵️‍♀️
Part of registering a domain means providing accurate contact information about yourself or your organization. This info is then stored in something called WHOIS records.

> What is WHOIS? It's pronounced "who-is," and it's a publicly accessible database that contains details about who owns a domain name. Think of it as a public registry for domain ownership.

### What info does it show? A WHOIS record typically includes:

- The registrant's name (the owner).
- Their address.
- Their phone number.
- Their email address.
- When the domain was created and last updated.
- When it's set to expire.
- The domain registrar (the company you bought the domain from, like GoDaddy or Namecheap).

### Privacy Options: </br>
Worried about your personal details being public? Don't fret! Most domain registrars offer privacy services. For a small fee, they can hide your personal contact information from the public WHOIS records, replacing it with their own generic contact details. This is great for privacy-conscious individuals or small businesses. 🤫

### How to Look Up WHOIS Records:
You can easily look up WHOIS information for almost any registered domain name.
- Online Services: Many websites offer free WHOIS lookup tools. Just search for "WHOIS lookup" online.
- Command Line: If you're using a Linux system, you can use the whois command directly in your terminal. For example, whois example.com would show you its details. 💻
So, while DNS makes it easy to remember website names, domain registration and WHOIS records are the foundational pieces that ensure accountability and ownership of those names on the vast internet.

---

## 🗣️ HTTP: The Web's Plain Talk 💬 </br>
HTTP is the web's basic language for your browser and web servers to chat. It's like talking in plain text – everyone can understand. The big catch? No encryption, so data sent over HTTP isn't private. 🚫🔒

## 🔒 HTTPS: The Web's Secure Chat 🤫 </br>
HTTPS is simply HTTP with a security upgrade using SSL/TLS encryption. It's like talking in a secret code – only your browser and the server understand. This protects sensitive info like passwords and credit cards. Look for the padlock icon! ✅

## 🎯 Web "Commands" (Methods): What Your Browser Asks For </br>
When your browser talks HTTP/S, it uses these "commands" to tell the server what to do:

- GET ➡️: Retrieve data. "Give me this webpage!" (e.g., loading a website).
- POST ✍️: Send data to create/process. "Here's a new comment to add." (e.g., submitting a form, creating a user).
- PUT 🔄: Update/replace data completely. "Replace this whole file with my new version." (e.g., updating an entire profile).
- DELETE 🗑️: Remove data. "Delete this picture." (e.g., deleting a photo).
- PATCH ✂️: Partially update data. "Just change my email address." (e.g., changing only one field).
- HEAD 📋: Get only headers. "Just tell me the page's info, don't send the whole page." (e.g., checking if a file exists).
