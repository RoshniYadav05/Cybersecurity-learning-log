# NAT (Network Address Translation)

## What is NAT?

NAT (Network Address Translation) is a technique used on routers/firewalls that translates one set of IP addresses into another.

### Main Purpose

NAT was introduced to solve the shortage of IPv4 addresses.

IPv4 provides:

```text
2^32 = 4,294,967,296
```

possible addresses, but because of the rapid growth of the Internet, these addresses are limited.

NAT allows multiple devices to share a small number of public IP addresses.

---

# Why NAT is Needed?

Without NAT:

```text
Every device
=
One Public IP
```

This would quickly exhaust available IPv4 addresses.

With NAT:

```text
Many Private IPs
        ↓
One/Few Public IPs
```

---

# Public vs Private IP Addresses

## Public IP Address

A public IP address:

- Is globally unique.
- Is assigned by an ISP.
- Can communicate over the Internet.
- Is publicly routable.

Example:

```text
66.94.234.18
```

---

## Private IP Address

A private IP address:

- Is not routable on the Internet.
- Is used inside local networks.
- Can be reused by different organizations.

Example:

```text
10.0.0.1
192.168.1.10
172.16.1.5
```

---

# Private IPv4 Address Ranges

### Class A Private Range

```text
10.0.0.0 – 10.255.255.255
```

CIDR:

```text
10.0.0.0/8
```

---

### Class B Private Range

```text
172.16.0.0 – 172.31.255.255
```

CIDR:

```text
172.16.0.0/12
```

---

### Class C Private Range

```text
192.168.0.0 – 192.168.255.255
```

CIDR:

```text
192.168.0.0/16
```

---

# Basic NAT Example

```text
PC1 = 10.0.0.1
PC2 = 10.0.0.2
PC3 = 10.0.0.3

        |
        |
     Router
    (NAT Device)
        |
 Public IP
 67.123.45.67
        |
     Internet
```

Internal devices use private IPs.

Router translates them into a public IP before sending traffic to the Internet.

---

# NAT Translation

NAT can translate:

### Private → Public

Most common.

Used when internal devices access the Internet.

---

### Public → Private

Used when external users need to access internal resources.

Example:

- Web Server
- Mail Server
- CCTV Server

---

# NAT Translation Table

Router maintains a translation table.

Example:

| Private IP | Public IP |
|------------|------------|
| 10.10.0.2 | 25.25.25.10 |
| 10.10.0.3 | 25.25.25.11 |

This mapping allows replies to reach the correct device.

---

# IPv6 and NAT

IPv6 provides:

```text
2^128 addresses
```

which is an enormous address space.

Example IPv6 Address:

```text
FDDC:45F8:34CF:74CD:9DC6:89CD:45DD:67A2
```

Because of the huge address space:

```text
Every device can have its own public address.
```

NAT is not required for address conservation in IPv6.

---

# Types of NAT

1. Static NAT
2. Dynamic NAT
3. NAT Overload (PAT)

---

# 1. Static NAT

## Definition

Static NAT creates a permanent one-to-one mapping between:

```text
Private IP ↔ Public IP
```

Example:

```text
192.168.0.167 ↔ 100.0.0.1
```

---

## Static NAT Mapping

```text
Inside Local  = 192.168.0.167
Inside Global = 100.0.0.1
```

---

### Inside Local

Private address of the host inside the network.

Example:

```text
192.168.0.167
```

---

### Inside Global

Public address representing the inside host on the Internet.

Example:

```text
100.0.0.1
```

---

## Traffic Flow

Before NAT:

```text
Source IP      : 192.168.0.167
Destination IP : 8.8.8.8
```

After NAT:

```text
Source IP      : 100.0.0.1
Destination IP : 8.8.8.8
```

Reply:

```text
Source IP      : 8.8.8.8
Destination IP : 100.0.0.1
```

Router translates it back:

```text
Destination IP : 192.168.0.167
```

---

## Uses of Static NAT

Used for devices that must always be reachable.

Examples:

- Web Servers
- Mail Servers
- CCTV Servers
- Database Servers

---

## Key Point

```text
One Private IP
        ↔
One Public IP
```

Permanent mapping.

---

# 2. Dynamic NAT

## Definition

Dynamic NAT uses a pool of public IP addresses.

Private devices are assigned a public IP dynamically when needed.

---

## Example

Public Pool:

```text
203.31.218.210
203.31.218.211
203.31.218.212
203.31.218.213
```

Internal Hosts:

```text
192.168.0.1
192.168.0.2
192.168.0.3
```

---

## How It Works

When a device accesses the Internet:

```text
192.168.0.1
      ↓
203.31.218.210
```

Another device:

```text
192.168.0.2
      ↓
203.31.218.211
```

Mappings remain until the session ends.

---

## Limitation

If all public IPs in the pool are already in use:

```text
New devices cannot access the Internet.
```

---

## Key Point

```text
Many Private IPs
        ↔
Many Public IPs
```

from a pool.

---

# 3. NAT Overload (PAT)

## Full Form

```text
PAT = Port Address Translation
```

Also called:

```text
NAT Overload
```

---

## Most Common NAT

PAT is the NAT used in:

- Home Routers
- Office Networks
- Wi-Fi Routers

---

## Why PAT?

One public IP is not enough to identify multiple devices.

Therefore PAT uses:

```text
IP Address + Port Number
```

to uniquely identify sessions.

---

## What is a Port?

A port identifies a specific application or service running on a device.

### Formula

```text
IP Address + Port Number
```

Example:

```text
192.168.1.10:443
```

Where:

```text
192.168.1.10 = Device
443          = HTTPS Service
```

---

# Packet Information

When data is sent:

```text
Source IP
Destination IP
Source Port
Destination Port
```

are included in the packet.

---

# Common Well-Known Ports

| Service | Port |
|----------|------|
| HTTP | 80 |
| HTTPS | 443 |
| FTP | 21 |
| SSH | 22 |
| DNS | 53 |

---

# Ephemeral Ports

Temporary ports automatically assigned by the operating system.

Examples:

```text
53001
53002
53003
```

Typical Range:

```text
49152 – 65535
```

These ports change frequently.

---

# PAT Example

Three devices:

```text
Laptop  = 192.168.1.10
Phone   = 192.168.1.11
Tablet  = 192.168.1.12
```

Public IP:

```text
49.36.210.5
```

---

## Original Connections

```text
192.168.1.10:53001
192.168.1.11:53001
192.168.1.12:53001
```

All devices may use the same source port internally.

---

## PAT Translation

Router changes the public ports.

```text
49.36.210.5:3001
49.36.210.5:3002
49.36.210.5:3003
```

---

## PAT Table

| Private IP | Private Port | Public IP | Public Port |
|------------|-------------|-----------|-------------|
| 192.168.1.10 | 53001 | 49.36.210.5 | 3001 |
| 192.168.1.11 | 53001 | 49.36.210.5 | 3002 |
| 192.168.1.12 | 53001 | 49.36.210.5 | 3003 |

---

## Why Port Translation is Needed?

If the router only changed the IP:

```text
49.36.210.5:53001
49.36.210.5:53001
49.36.210.5:53001
```

all sessions would look identical.

Router would not know which device should receive the response.

PAT solves this problem by assigning different public ports.

---

# SNAT (Source NAT)

## Definition

SNAT modifies the source IP address of outgoing traffic.

---

### Example

Before SNAT:

```text
Source IP      : 192.168.1.10
Destination IP : Google Server
```

After SNAT:

```text
Source IP      : 49.36.210.5
Destination IP : Google Server
```

Internet sees:

```text
Request from 49.36.210.5
```

---

### Response

Reply returns to:

```text
49.36.210.5
```

Router translates it back:

```text
192.168.1.10
```

---

## Uses of SNAT

- Home Routers
- Office Networks
- Outbound Traffic
- Firewall NAT Policies

---

# DNAT (Destination NAT)

## Definition

DNAT modifies the destination IP address of incoming traffic.

---

## Example

Public Server Address:

```text
198.51.100.1:8080
```

Actual Internal Server:

```text
192.168.1.100:80
```

---

## DNAT Rule

```text
198.51.100.1:8080
          ↓
192.168.1.100:80
```

---

## Traffic Flow

Internet User:

```text
198.51.100.1:8080
```

Router receives packet.

Router applies DNAT:

```text
192.168.1.100:80
```

Internal server receives the request.

---

## Common Uses of DNAT

- Port Forwarding
- Hosting Websites
- Remote Access Services
- CCTV Access
- Internal Servers

---

# SNAT vs DNAT

| Feature | SNAT | DNAT |
|----------|-------|-------|
| Changes | Source IP | Destination IP |
| Traffic Direction | Outgoing | Incoming |
| Used For | Internet Access | Port Forwarding |
| Common Example | Home Router | Public Web Server |

---

# NAT Terminology

### Inside Local

Private IP of internal host.

Example:

```text
192.168.1.10
```

---

### Inside Global

Public IP representing internal host.

Example:

```text
49.36.210.5
```

---

### Outside Global

Actual public address of external host.

Example:

```text
8.8.8.8
```

---

### Outside Local

External host address as seen internally.

Usually same as Outside Global.

---

# Advantages of NAT

✔ Conserves IPv4 addresses  
✔ Improves address utilization  
✔ Hides internal network structure  
✔ Allows multiple devices to share one public IP  
✔ Reduces public IP requirements

---

# Disadvantages of NAT

✘ Breaks end-to-end connectivity  
✘ Adds processing overhead on routers  
✘ Can cause issues with some applications  
✘ Makes troubleshooting more complex

---

# Quick Interview Questions

### Why was NAT introduced?

To solve IPv4 address exhaustion.

---

### Which NAT type is used in home Wi-Fi routers?

PAT (NAT Overload).

---

### What is PAT?

Port Address Translation.

Allows multiple devices to share one public IP using different port numbers.

---

### Difference between Static and Dynamic NAT?

```text
Static NAT:
1 Private IP ↔ 1 Public IP

Dynamic NAT:
Many Private IPs ↔ Pool of Public IPs
```

---

### What does SNAT change?

Source IP Address.

---

### What does DNAT change?

Destination IP Address.

---

### What is Port Forwarding?

A form of DNAT that forwards incoming traffic to an internal server.

---

### Does IPv6 require NAT?

Generally no, because IPv6 provides a huge address space.

---

# Key Takeaways

✔ NAT translates IP addresses.  
✔ NAT helps conserve IPv4 addresses.  
✔ Private IPs cannot be routed directly on the Internet.  
✔ Static NAT = One-to-One mapping.  
✔ Dynamic NAT = Pool-based mapping.  
✔ PAT/NAT Overload = Many-to-One mapping using ports.  
✔ SNAT changes Source IP.  
✔ DNAT changes Destination IP.  
✔ PAT is the most commonly used NAT in real-world networks.
