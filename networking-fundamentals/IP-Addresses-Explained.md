## 🌐 Understanding IP Addressing — From Basics to Network Calculation

Today, I didn’t just study IP Addressing — I understood what “IP” actually means, why it exists, and how it works behind the scenes when we use the Internet.

As a cybersecurity learner, IP Addressing is one of the most important foundations of networking.

## 📌 What is IP?

IP stands for Internet Protocol.

**Internet Protocol is a set of rules that governs how data packets travel from one device to another over a network.**

It decides:

How data is formatted

How it is addressed

How it is sent

How it reaches the correct destination

IP works in a connectionless manner, meaning it sends packets independently without establishing a fixed connection first.

In simple words:
IP is the rulebook that helps data travel across networks.

## 📌 What is IP Addressing?

**IP Addressing is the method of assigning unique addresses to devices so they can be identified and communicate over a network.**

Every device connected to:

Internet

Local network

Wi-Fi

Office network

must have an IP address.

**Without IP addressing, devices cannot communicate.**

Just like every house needs an address for delivery, every device needs an IP address for data delivery.

## 🔎 Logical vs Physical Addressing

Before understanding IP address deeply, it is important to know that addressing in networking is of two types.

**🔹 Physical Address (MAC Address)**

48-bit address

Permanently assigned to NIC (Network Interface Card)

Does not change

Used inside local network

Example:
00:1A:2B:3C:4D:5E

MAC address identifies the physical hardware.

**🔹 Logical Address (IP Address)**

Assigned by ISP or router

Can change

Used for communication over internet

Identifies network location

IP address is logical because it identifies where a device is located in a network.

MAC address identifies “who you are”.
IP address identifies “where you are”.

## 🌍 Now Let’s Understand IP Address

**An IP Address is a unique numerical label assigned to each device connected to a network using Internet Protocol.**

Example:
192.168.1.1

When we open a website:

Our device sends a request using its IP.

The server processes the request.

The server sends data back to our IP address.

So IP address helps in:

Identifying source

Identifying destination

Routing data correctly

Without IP address, data would not know where to go.

## 🌐 Types of IP Address
**🔹 IPv4**

32-bit address

Divided into 4 octets

Each octet = 8 bits

Range of each octet: 0 to 255

Example:
192.168.10.1

Total IPv4 addresses = 2³² = 4,294,967,296

**🔹 IPv6**

128-bit address

Written in hexadecimal

Introduced due to IPv4 exhaustion

## 🔐 Public vs Private IP
**Public IP**

Assigned by ISP

Globally unique

Used on internet

**Private IP**

Used inside local networks.

Private IP ranges:

Class A → 10.0.0.0 – 10.255.255.255
Class B → 172.16.0.0 – 172.31.255.255
Class C → 192.168.0.0 – 192.168.255.255

Private IP cannot be accessed directly from internet.

## 🔁 Static vs Dynamic IP
**Static IP**

Fixed

Does not change

Mostly used for servers

**Dynamic IP**

Automatically assigned

Changes periodically

Managed by DHCP

## IP Address Classes (Classful Addressing)

IP addresses are divided into 5 classes.

**🔹 Class A**

Range: 1.0.0.0 – 126.255.255.255
Default Subnet Mask: 255.0.0.0

127.x.x.x is reserved for loopback.

Example:
11.200.200.200

Network ID:
11.0.0.0

Broadcast ID:
11.255.255.255

Usable hosts:
2²⁴ − 2 = 16,777,214

**🔹 Class B**

Range: 128.0.0.0 – 191.255.255.255
Default Subnet Mask: 255.255.0.0

Example:
150.10.20.30

Network ID:
150.10.0.0

Broadcast ID:
150.10.255.255

Usable hosts:
2¹⁶ − 2 = 65,534

**🔹 Class C**

Range: 192.0.0.0 – 223.255.255.255
Default Subnet Mask: 255.255.255.0

Used for small networks.

**🔹 Class D**

224.0.0.0 – 239.255.255.255
Used for multicast.

**🔹 Class E**

240.0.0.0 – 255.255.255.255
Used for research and experimental purposes.

🧮 How to Find Network ID, Broadcast ID and Number of Hosts

Every IP address has two parts:

Network Portion

Host Portion

Network ID identifies the network.
Broadcast ID sends data to all devices in that network.

These two addresses cannot be assigned to devices.

🧠 Formula to Calculate Usable Hosts

2ⁿ − 2

Where n = number of host bits.

We subtract 2 because:

One address is Network ID

One address is Broadcast ID

**🔁 Loopback Address**

127.0.0.1

Used to test local system.

Command:
ping 127.0.0.1

If reply comes, network stack is working properly.

## 🎯 Final Understanding

IP Addressing is the backbone of networking and cybersecurity.

Understanding IP helps in:

Network configuration

Traffic analysis

Security monitoring

Ethical hacking

This session helped me move from basic definitions to actual calculations and real understanding of how networks are structured.

## 🔗 Learning Resources & Links
This learning log includes a short video walkthrough where I explain the IP Addresses in my own words and connect it to real-world networking and security concepts.

## 🎥 YouTube Video
▶ Watch here: (https://www.youtube.com/watch?v=UgGPrYfV9_E)

## 🔗 LinkedIn Post
📌 I’ve also shared this session and key takeaways on LinkedIn: ▶ View post: LinkedIn – https://www.linkedin.com/feed/update/urn:li:activity:7430611033871982592/?originTrackingId=AdfBRyIJpuMiqXHI9hVp6A%3D%3D

If you’re learning networking or cybersecurity too, feel free to explore, connect, or share feedback — I’d love to grow together🚀.
