# ARP (Address Resolution Protocol)

ARP (Address Resolution Protocol) is used to find the **MAC Address** of a device when its **IP Address** is already known.

### Simple Definition

```text
Known = IP Address
Need = MAC Address
Solution = ARP
```

Example:

```text
IP Address = 192.168.1.10
MAC Address = ?
```

ARP helps discover the MAC address associated with that IP.

---

# Why ARP is Required?

Communication on a LAN happens using MAC addresses.

Even if a device knows the destination IP address, it cannot send the frame until it knows the destination MAC address.

```text
IP Layer → Knows IP Address
Data Link Layer → Needs MAC Address
```

Therefore ARP acts as a bridge between Layer 3 and Layer 2.

---

# ARP Characteristics

- ARP is used in IPv4 networks.
- ARP works within the same broadcast domain.
- ARP is mainly associated with the Data Link Layer (Layer 2).
- ARP Request is Broadcast.
- ARP Reply is Unicast.
- Routers do not forward ARP Broadcasts.
- ARP is never generated for devices on a different network.

---

# ARP Request and Reply

## ARP Request

Broadcast Message

```text
Who has IP 192.168.1.10?
Tell 192.168.1.5
```

Destination MAC:

```text
FF:FF:FF:FF:FF:FF
```

(Broadcast MAC Address)

---

## ARP Reply

Unicast Message

```text
192.168.1.10 is at
AA:BB:CC:DD:EE:FF
```

Sent directly to the requester.

---

# Types of ARP

1. ARP
2. Proxy ARP
3. Reverse ARP (RARP)
4. Gratuitous ARP (GARP)

---

# ARP Packet Format

```text
-------------------------------------------------
| Hardware Type | Protocol Type                |
-------------------------------------------------
| Hardware Len  | Protocol Len | Operation     |
-------------------------------------------------
| Sender Hardware Address (SHA)                |
-------------------------------------------------
| Sender Protocol Address (SPA)                |
-------------------------------------------------
| Target Hardware Address (THA)                |
-------------------------------------------------
| Target Protocol Address (TPA)                |
-------------------------------------------------
```

---

# ARP Header Fields

## 1. Hardware Type (HTYPE)

Specifies network technology.

Examples:

- Ethernet = 1
- Wi-Fi
- Fiber Network

Most Ethernet networks use:

```text
Hardware Type = 1
```

---

## 2. Protocol Type (PTYPE)

Specifies the Layer 3 protocol.

For IPv4:

```text
0x0800
```

Meaning:

```text
ARP is resolving an IPv4 address.
```

---

## 3. Hardware Length (HLEN)

Length of MAC address.

Ethernet MAC Address:

```text
48 bits = 6 bytes
```

Therefore:

```text
HLEN = 6
```

---

## 4. Protocol Length (PLEN)

Length of IP address.

IPv4 Address:

```text
32 bits = 4 bytes
```

Therefore:

```text
PLEN = 4
```

---

## 5. Operation (Opcode)

Defines Request or Reply.

### ARP Request

```text
Opcode = 1
```

### ARP Reply

```text
Opcode = 2
```

---

## 6. Sender Hardware Address (SHA)

Sender's MAC Address.

Example:

```text
AA:BB:CC:DD:EE:FF
```

---

## 7. Sender Protocol Address (SPA)

Sender's IP Address.

Example:

```text
192.168.1.5
```

---

## 8. Target Hardware Address (THA)

Destination MAC Address.

In ARP Request:

```text
00:00:00:00:00:00
```

because MAC is not known yet.

---

## 9. Target Protocol Address (TPA)

Destination IP Address whose MAC is required.

Example:

```text
192.168.1.10
```

---

# ARP Process (Same Network)

Consider:

```text
PC-A = 10.0.0.4
PC-B = 10.0.0.3
PC-C = 10.0.0.2
PC-D = 10.0.0.1
```

All connected to a switch.

---

## Step 1

PC-A wants to communicate with PC-C.

```text
Source IP = 10.0.0.4
Destination IP = 10.0.0.2
```

PC-A knows destination IP but not MAC.

---

## Step 2

PC-A sends ARP Request.

```text
Who has 10.0.0.2 ?
Tell 10.0.0.4
```

Destination MAC:

```text
FF:FF:FF:FF:FF:FF
```

Broadcast to everyone.

---

## Step 3

Switch floods the broadcast frame.

Every device receives it.

---

## Step 4

All devices check:

```text
Is 10.0.0.2 my IP?
```

Only PC-C matches.

---

## Step 5

PC-C sends ARP Reply.

```text
10.0.0.2 is at
AA:AA:AA:AA:AA:AA
```

Reply is Unicast.

---

## Step 6

PC-A stores entry in ARP Cache.

```text
10.0.0.2 → AA:AA:AA:AA:AA:AA
```

---

## Step 7

Communication starts.

```text
Source MAC = A
Destination MAC = C
```

---

# ARP Cache

ARP mappings are stored locally.

View ARP Cache:

### Windows

```cmd
arp -a
```

### Linux

```bash
ip neigh
```

or

```bash
arp -n
```

---

# ARP for Different Networks

Consider:

```text
PC1 = 10.0.0.1

Router Interface 1 = 10.0.0.2

Router Interface 2 = 20.0.0.2

PC2 = 20.0.0.1
```

PC1 wants to communicate with PC2.

---

## Important Rule

ARP never resolves MAC addresses across different networks.

❌ Wrong

```text
PC1 asks:
Who has 20.0.0.1?
```

This will not happen.

---

## What Actually Happens?

PC1 realizes destination is on another network.

So PC1 ARPs for:

```text
Default Gateway
10.0.0.2
```

---

## Router Responds

```text
10.0.0.2 is at MAC-C
```

---

## PC1 Sends Data

```text
Source IP = 10.0.0.1
Destination IP = 20.0.0.1

Source MAC = A
Destination MAC = Router
```

---

## Router Processing

Router removes old Layer 2 header.

Creates a new Layer 2 frame.

```text
Source MAC = Router
Destination MAC = PC2
```

IP addresses remain unchanged.

```text
Source IP = 10.0.0.1
Destination IP = 20.0.0.1
```

# Proxy ARP

Proxy ARP allows a router or another device to answer ARP requests on behalf of another host.

Example:

```text
PC1 ---- Router ---- PC2
```

PC1 asks:

```text
Who has 192.168.1.69 ?
```

Router replies:

```text
I have it.
Use my MAC address.
```

PC1 sends data to router.

Router forwards it to actual destination.

---

# Why Proxy ARP is Used?

- Network Migration
- Special Routing Scenarios
- Legacy Networks
- Some Subnetting Designs

---

# Reverse ARP (RARP)

Reverse ARP performs the opposite operation.

```text
Known = MAC Address
Need = IP Address
```

Used historically by diskless workstations.

Now mostly replaced by:

- DHCP
- BOOTP

---

# Gratuitous ARP (GARP)

A host sends an ARP request for its own IP address.

Example:

```text
Who has 192.168.1.10?
Tell 192.168.1.10
```

Source IP and Target IP are the same.

---

# Why Gratuitous ARP is Used?

## 1. Detect Duplicate IP Addresses

Checks whether another device is already using the same IP.

---

## 2. Update ARP Tables

Updates neighboring devices with a new MAC address.

---

## 3. High Availability Protocols

Used in:

- HSRP
- VRRP
- Failover Systems

---

# ARP Security Issues

## ARP Spoofing / ARP Poisoning

An attacker sends fake ARP replies.

Example:

```text
Gateway IP → Attacker MAC
```

Victim updates ARP table incorrectly.

Result:

- Traffic Interception
- Man-in-the-Middle Attack
- Credential Theft

---

# Protection Against ARP Attacks

- Dynamic ARP Inspection (DAI)
- Port Security
- Static ARP Entries
- VLAN Segmentation
- Network Monitoring

---

# IPv6 and ARP

ARP is not used in IPv6.

IPv6 uses:

```text
Neighbor Discovery Protocol (NDP)
```

which works through ICMPv6.

# Key Takeaways

✔ ARP resolves IP Address to MAC Address.  
✔ Used only in IPv4.  
✔ ARP Request = Broadcast.  
✔ ARP Reply = Unicast.  
✔ Works only within the same network.  
✔ Routers do not forward ARP Broadcasts.  
✔ ARP Cache stores learned mappings.  
✔ Proxy ARP allows routers to answer ARP requests.  
✔ Gratuitous ARP detects duplicate IP addresses.  
✔ ARP is vulnerable to ARP Spoofing/Poisoning attacks.  
✔ IPv6 uses NDP instead of ARP.
