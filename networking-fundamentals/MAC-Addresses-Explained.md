## 📌 MAC Address (Media Access Control Address)
**🔹 What is a MAC Address?**

A MAC Address (Media Access Control Address) is a unique physical address assigned to a device’s network interface (NIC).

👉 It is used to identify a device uniquely in a network
👉 Think of it like a permanent identity of your device hardware.
👉 It is also called:

**Physical Address**
**Hardware Address**

💡 Main purpose:
Devices can communicate with each other inside a network

**🔹 Why do we need MAC Address?**
In networking:
IP Address (logical address) can change

MAC Address (physical address) does NOT change

💡 So even if your IP changes, your device can still be uniquely identified using MAC address.
👉 So MAC address is more permanent identity

**🔹 MAC Address belongs to NIC (Important)**

👉 MAC address is not of laptop directly
👉 It belongs to NIC (Network Interface Card)

**👉 Example:**
WiFi card → has its own MAC
Ethernet port → has its own MAC
Bluetooth → also has MAC

💡 So if a device has multiple NICs → it will have multiple MAC addresses

**🔹 What is NIC?**

NIC (Network Interface Card) is the hardware that helps your device connect to a network.

👉 Example:
WiFi connection
Ethernet cable (RJ45)
Bluetooth

👉 If a device has multiple NICs → it will have multiple MAC addresses

**🔹 MAC Address Size**

MAC Address = 48 bits
48 bits = 6 bytes

**🔹 Structure of MAC Address**

MAC Address is divided into 2 parts:

**1. OUI (Organizational Unique Identifier)**

First 24 bits (3 bytes)

Identifies the company/vendor

Assigned by a global authority-IANA

👉 Example:

Dell, Lenovo, Apple → each has unique OUI

**2. Vendor Specific Part**

Last 24 bits

Assigned by the company

Makes each device unique

**🔹 Who assigns MAC Address?**

A global organization called IANA (Internet Assigned Numbers Authority) assigns OUI to companies.

👉 Companies like Dell, Lenovo cannot randomly choose OUI
👉 This ensures global uniqueness

**🔹 MAC Address Uniqueness**

✔ MAC Address is globally unique
✔ No two devices should have the same MAC

💡 Unless manually changed (MAC spoofing)

**🔹 MAC Address Format**

MAC Address is written in Hexadecimal (base 16)
Example: 34:AB:CD:EF:69:49

**Different Representations**

Windows / Linux: 34:AB:CD:EF:69:49

Mobile / some systems: 34-AB-CD-EF-69-49

Cisco devices: 34AB.CDEF.6949

💡 Format changes, but value same

**🔹 Why Hexadecimal?**

1 Hex digit = 4 bits

12 Hex digits = 48 bits

👉 Easy to read compared to binary

**🔹 Binary Conversion** 

Each hex value = 4 bits

Example:

A = 1010
E = 1110

So:

AE → 1010 1110

**🔹 Switch & Router MAC Behavior**
**🔸 Switch**
Has a MAC address
But mainly uses MAC table to forward data
Each port does NOT have separate MAC (generally switch uses one)

**🔸 Router**
Each interface has different MAC address
👉 Means:
Each port → different MAC

**🔹 Broadcast MAC Address**
Address:
FF:FF:FF:FF:FF:FF
Meaning:

👉 "Send this data to all devices in the network"

**🔹 Why Broadcast is used?**

When device does not know MAC address:

👉 It sends ARP request

Message goes to all devices

All devices receive it

Only correct device replies

💡 This is how devices find each other

**🔹 Simple Flow (Real Understanding)**

Device wants to send data

It knows IP but not MAC

Sends broadcast (FF:FF:FF:FF:FF:FF)

All devices receive it

Only the correct device replies

Communication starts

**🔹 Key Points to Remember**

✔ MAC Address = Physical Address
✔ Stored in NIC
✔ 48 bits (6 bytes)
✔ Written in Hexadecimal
✔ First 24 bits → Company (OUI)
✔ Last 24 bits → Device specific
✔ Globally unique
✔ Used inside local network
✔ Broadcast MAC → FF:FF:FF:FF:FF:FF

**🔹 Final Understanding**

👉 MAC Address is the real identity of your device inside a network
👉 It works at Data Link Layer (Layer 2)
👉 Without MAC address, devices cannot communicate in a LAN

## 🔗 Learning Resources & Links
This learning log includes a short video walkthrough where I explain the MAC Addresses in my own words and connect it to real-world networking and security concepts.

## 🎥 YouTube Video
▶ Watch here: (https://youtu.be/kf0baEWCMj0)

## 🔗 LinkedIn Post
📌 I’ve also shared this session and key takeaways on LinkedIn: ▶ View post: LinkedIn – 

If you’re learning networking or cybersecurity too, feel free to explore, connect, or share feedback — I’d love to grow together🚀.
