# Types of Networks

A network can be classified based on the geographical area it covers and the number of devices connected to it.

---

# LAN (Local Area Network)

## What is LAN?

A LAN (Local Area Network) is a group of computers, servers, printers, and other network devices connected together within a limited geographical area such as:

- Home
- Office
- School
- College
- Single Building
- Campus Floor

Usually all devices belong to the same organization or owner.

---

## Characteristics of LAN

- Highest speed among common network types.
- Most secure network because it is privately managed.
- Usually covers a small area.
- Most communication happens through switches.
- Routers are generally not required for communication within the same LAN.
- Low latency.
- Easier to manage and troubleshoot.

---

## Devices Used in LAN

- Switch
- Access Point (Wireless LAN)
- Ethernet Cable
- Network Interface Card (NIC)

Sometimes:

- Router (for Internet access)
- Firewall

---

## Transmission Media

LAN can use:

### Wired

- Twisted Pair Cable (UTP/STP)
- Ethernet Cable
- Fiber Optic Cable

### Wireless

- Wi-Fi (WLAN)

---

## Example

If two computers are connected in the same building and communicate directly through a switch, Wi-Fi, or Ethernet cable without needing long-distance routing, it is a LAN.

```text
PC1 ── Switch ── PC2
```

---

## Advantages

- High speed
- Low cost
- Easy maintenance
- Better security
- Fast file sharing

---

## Disadvantages

- Limited geographical coverage
- Requires local infrastructure

---

# MAN (Metropolitan Area Network)

## What is MAN?

A MAN (Metropolitan Area Network) is a network that covers a city or large metropolitan area.

It is larger than a LAN but smaller than a WAN.

---

## Characteristics of MAN

- Connects multiple LANs.
- Covers an entire city or large town.
- Moderate speed.
- Usually managed by telecom providers, governments, or large organizations.
- Uses high-speed backbone links.

---

## Devices Used

- Routers
- Layer-3 Switches
- Fiber Optic Infrastructure

---

## Transmission Media

- Fiber Optic Cable
- Ethernet Links
- Wireless Point-to-Point Links

---

## Example

A university connecting multiple campuses across the same city.

```text
Campus A
     │
Fiber Link
     │
Campus B
     │
Fiber Link
     │
Campus C
```

---

## Advantages

- Connects multiple LANs efficiently.
- Faster than WAN.
- Good for city-wide connectivity.

---

## Disadvantages

- More expensive than LAN.
- Complex management.

---

# WAN (Wide Area Network)

## What is WAN?

A WAN (Wide Area Network) connects devices, LANs, or MANs across large geographical distances such as:

- Different cities
- Different states
- Different countries
- Entire continents

The Internet is the largest WAN in the world.

---

## Characteristics of WAN

- Covers the largest geographical area.
- Uses routers extensively.
- Lower speed compared to LAN.
- Higher latency.
- More vulnerable than LAN because traffic often travels through public networks.
- More expensive to maintain.

---

## Devices Used

- Routers
- Firewalls
- WAN Accelerators
- Modems
- Multiprotocol Network Devices

---

## Transmission Media

- Fiber Optic Cables
- Leased Lines
- MPLS Links
- Microwave Links
- Cellular Networks (4G/5G)
- Satellite Communication

---

## Example

When a computer in Mumbai accesses a server in the United States through the Internet, the communication occurs over a WAN.

```text
Computer (India)
       │
Internet
       │
Server (USA)
```

---

## Advantages

- Global connectivity
- Remote access
- Cloud service access
- Connects multiple branches

---

## Disadvantages

- Higher cost
- Higher latency
- More security risks
- Complex administration

---

# Comparison: LAN vs MAN vs WAN

| Feature | LAN | MAN | WAN |
|----------|----------|----------|----------|
| Full Form | Local Area Network | Metropolitan Area Network | Wide Area Network |
| Coverage | Building / Office | City | Country / World |
| Speed | Highest | Moderate | Lowest |
| Cost | Low | Medium | High |
| Security | High | Medium | Lower |
| Latency | Very Low | Low | Higher |
| Main Device | Switch | Router + Switch | Router |
| Transmission Media | Ethernet, Wi-Fi | Fiber, Ethernet | Fiber, Satellite, Internet |
| Example | Office Network | City-wide University Network | Internet |

---

# Other Types of Networks

Besides LAN, MAN, and WAN, there are several specialized network types.

---

# PAN (Personal Area Network)

A small network around a single person.

### Range

Usually within 10 meters.

### Examples

- Bluetooth Headphones
- Smart Watch
- Mobile Hotspot
- Wireless Keyboard & Mouse

```text
Phone ← Bluetooth → Earbuds
```

---

# CAN (Campus Area Network)

A network that connects multiple LANs within a campus.

### Examples

- University Campus
- Corporate Campus
- Military Base

### Coverage

1–10 kilometers typically.

```text
Building A
     │
Building B
     │
Building C
```

---

# HAN (Home Area Network)

A network inside a home.

### Devices

- Smartphones
- Smart TVs
- Laptops
- Wi-Fi Routers
- Smart Home Devices

### Example

```text
Home Router
   │
 ├── Laptop
 ├── Phone
 ├── TV
 └── Smart Speaker
```

---

# WLAN (Wireless Local Area Network)

A LAN that uses wireless communication instead of cables.

### Technologies

- Wi-Fi
- IEEE 802.11 Standards

### Example

Home Wi-Fi network.

```text
Router )))) Laptop
Router )))) Mobile
```

---

# SAN (Storage Area Network)

A dedicated high-speed network used to connect servers and storage devices.

### Used In

- Data Centers
- Enterprise Environments
- Cloud Providers

### Benefits

- Fast storage access
- Centralized storage management
- High availability

---

# Quick Memory Trick

```text
PAN  → Person
HAN  → Home
LAN  → Building
CAN  → Campus
MAN  → City
WAN  → Country/World
SAN  → Storage
```
