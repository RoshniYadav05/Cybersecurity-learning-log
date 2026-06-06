# Dynamic Host Configuration Protocol (DHCP)

## Overview

Dynamic Host Configuration Protocol (DHCP) is an Application Layer protocol that automatically assigns IP addresses and other network configuration parameters to devices on a network.

Without DHCP, administrators would have to manually configure IP addresses on every device. As networks grow larger, this becomes difficult, time-consuming, and prone to configuration errors.

DHCP solves this problem by dynamically assigning network settings whenever a new device joins the network.

---

## What is DHCP?

DHCP stands for **Dynamic Host Configuration Protocol**.

It is a client-server protocol used to automatically provide:

- IP Address
- Subnet Mask
- Default Gateway
- DNS Server Address
- Domain Name
- WINS Server Address (Windows Networks)

DHCP operates at the **Application Layer** of the TCP/IP protocol suite.

---

## Why DHCP is Needed

Imagine a network with only 5–10 devices.

An administrator can manually assign IP addresses to each device.

Example:

```text
PC1 → 192.168.1.10
PC2 → 192.168.1.11
PC3 → 192.168.1.12
```

This approach works for small networks.

However, in large organizations containing hundreds or thousands of devices:

- Manual configuration becomes difficult
- IP conflicts may occur
- Human errors increase
- Device management becomes complex

DHCP automates the entire process.

Whenever a new device joins the network, DHCP automatically provides all required network settings.

---

## DHCP Characteristics

- Based on Client-Server Architecture
- Operates at the Application Layer
- Automatically assigns IP addresses
- Reduces administrative workload
- Prevents IP address conflicts
- Simplifies network management

---

## Dynamic IP Address

An IP address assigned by a DHCP server is known as a **Dynamic IP Address**.

Unlike Static IP Addresses, Dynamic IPs may change whenever:

- Lease expires
- Device reconnects
- DHCP server reallocates addresses

---

## DHCP Ports

DHCP uses UDP communication.

| Device | Port |
|----------|----------|
| DHCP Server | UDP 67 |
| DHCP Client | UDP 68 |

### Communication Flow

```text
Client (UDP 68)
        │
        ▼
Server (UDP 67)
```

The client sends requests using Port 68 and the server listens on Port 67.

---

## BOOTP and DHCP

Before DHCP, BOOTP (Bootstrap Protocol) was used to provide IP information to devices.

BOOTP required administrators to manually configure device MAC addresses and IP mappings.

DHCP is considered an enhanced version of BOOTP because:

- It automatically assigns addresses
- Supports leasing
- Reduces manual configuration
- Provides additional network parameters

---

# DHCP Server Can Provide

A DHCP server can automatically provide:

### 1. IP Address

Example:

```text
192.168.1.100
```

---

### 2. Subnet Mask

Example:

```text
255.255.255.0
```

---

### 3. Default Gateway

Example:

```text
192.168.1.1
```

---

### 4. Domain Name

Example:

```text
company.local
```

---

### 5. DNS Server Address

Example:

```text
8.8.8.8
```

---

### 6. WINS Server Address

Used in Windows-based environments for hostname resolution.

---

# DORA Process

DHCP uses a four-step process known as **DORA**.

DORA stands for:

```text
D → Discover
O → Offer
R → Request
A → Acknowledge
```

This process allows a client and DHCP server to communicate and establish an IP address lease.

---

## Step 1: DHCP Discover

When a new device joins the network, it does not have an IP address.

The client broadcasts a DHCP Discover message searching for available DHCP servers.

### Layer 2 Broadcast

```text
FF:FF:FF:FF:FF:FF
```

### Layer 3 Broadcast

```text
255.255.255.255
```

### Source Port

```text
68
```

### Destination Port

```text
67
```

Since the client does not know where the DHCP server is located, it broadcasts the request to the entire network.

---

## Step 2: DHCP Offer

After receiving the Discover message, the DHCP server responds with a DHCP Offer.

The offer contains:

- Available IP Address
- Subnet Mask
- Lease Duration
- Default Gateway
- DNS Information

Example:

```text
Offered IP = 192.168.1.100
```

If multiple DHCP servers exist, the client may receive multiple offers.

---

## Step 3: DHCP Request

The client selects one of the offered addresses and broadcasts a DHCP Request.

This informs all DHCP servers which offer was accepted.

The request contains:

- Requested IP Address
- Selected DHCP Server Information

---

## Step 4: DHCP Acknowledge (ACK)

The DHCP server confirms the assignment and sends a DHCP ACK message.

The ACK contains:

- Assigned IP Address
- Lease Time
- Subnet Mask
- Gateway Information
- DNS Information

At this stage, the client is allowed to use the assigned IP address.

---

## DORA Workflow

```text
Client
   │
   │ DHCP Discover
   ▼
DHCP Server

Client
   ▲
   │ DHCP Offer
   │
DHCP Server

Client
   │ DHCP Request
   ▼
DHCP Server

Client
   ▲
   │ DHCP ACK
   │
DHCP Server
```

---

# DHCP Lease

A DHCP-assigned IP address is not permanent.

It is assigned for a specific period called a **Lease Time**.

Examples:

- 1 Hour
- 8 Hours
- 24 Hours
- 7 Days

After the lease expires, the client must renew the address.

---

# DHCP Scope

A Scope is a range of IP addresses that a DHCP server can allocate to clients.

Example:

```text
192.168.1.100 – 192.168.1.200
```

The DHCP server can only assign addresses from this range.

### Example Scope

```text
Network: 192.168.1.0/24

Available Range:
192.168.1.100 - 192.168.1.200
```

Administrators define scopes while configuring DHCP.

---

# Superscope

A Superscope is a collection of multiple scopes managed together by a DHCP server.

It allows clients to obtain addresses from different scopes that belong to the same administrative group.

Example:

```text
Scope 1:
192.168.1.0/24

Scope 2:
192.168.2.0/24

Scope 3:
192.168.3.0/24
```

All three scopes can be grouped into a single Superscope.

---

## When Superscope is Used

### 1. IP Address Exhaustion

When the existing scope runs out of available addresses.

Example:

```text
192.168.1.0/24
```

All addresses become allocated.

A new scope can be added using a Superscope.

---

### 2. Multiple Logical Networks on the Same Physical Network

When multiple subnets exist on a single network segment.

---

### 3. Network Migration

When clients must gradually move from one subnet to another.

Example:

```text
Old Range:
192.168.1.0/24

New Range:
192.168.2.0/24
```

A Superscope helps manage both ranges during migration.

---

# DHCP 80/20 Rule

Large organizations often deploy multiple DHCP servers for redundancy and fault tolerance.

The 80/20 Rule suggests:

### Primary DHCP Server

Receives:

```text
80% of IP Addresses
```

### Secondary DHCP Server

Receives:

```text
20% of IP Addresses
```

This ensures service availability if one DHCP server becomes unavailable.

Example:

```text
Primary DHCP:
192.168.1.1 - 192.168.1.200

Secondary DHCP:
192.168.1.201 - 192.168.1.250
```

---

# Advantages of DHCP

- Automatic IP Assignment
- Centralized Management
- Reduces Configuration Errors
- Prevents Duplicate IP Addresses
- Easy Network Expansion
- Simplifies Administration
- Supports Large Networks

---

# Key Takeaways

- DHCP stands for Dynamic Host Configuration Protocol.
- DHCP operates at the Application Layer.
- DHCP automatically assigns IP addresses and network settings.
- DHCP uses UDP Port 67 and UDP Port 68.
- DHCP follows the DORA process.
- DHCP addresses are leased temporarily.
- Scope defines the IP range available for allocation.
- Superscope combines multiple scopes.
- DHCP evolved from BOOTP.
- The 80/20 Rule improves DHCP availability.

---

## What I Learned

- DHCP fundamentals and architecture
- Dynamic vs Static IP Addressing
- DHCP Ports and Communication
- BOOTP vs DHCP
- DORA Process
- DHCP Lease Mechanism
- Scope and Superscope
- DHCP High Availability (80/20 Rule)
- DHCP Configuration Parameters
