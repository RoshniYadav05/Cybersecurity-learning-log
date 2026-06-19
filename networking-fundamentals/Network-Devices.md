# Network Devices: Hub, Repeater, Bridge, Switch, Router & Gateway

## Overview

Network devices are hardware components used to connect computers, servers, and networks together. Each device operates at a specific layer of the OSI Model and performs different functions for forwarding, filtering, regenerating, or routing data.

Understanding these devices is important for Network Engineers, System Administrators, SOC Analysts, and Cybersecurity Professionals.

---

# Network Devices and OSI Layers

| OSI Layer | Device |
|------------|----------|
| Application | Gateway |
| Presentation | Gateway |
| Session | Gateway |
| Transport | Gateway |
| Network | Router / Layer 3 Switch |
| Data Link | Bridge / Switch |
| Physical | Hub / Repeater |

---

# 1. Hub

## What is a Hub?

A Hub is a networking device that sends incoming data to every connected device because it cannot identify the intended destination.

It simply receives signals and broadcasts them to all connected systems.

---

## Characteristics of Hub

- Layer 1 (Physical Layer) Device
- Works with Electrical Signals / Bits
- Cannot read MAC Addresses
- Cannot store MAC Tables
- Always Broadcasts Traffic
- Single Collision Domain
- Half Duplex Communication
- Commonly used in Star Topology
- Considered a LAN Device

---

## How Hub Works

Suppose PC1 sends data to PC3.

```text
PC1 → Hub
```

The Hub does not know where PC3 is located.

Therefore it sends the data to:

```text
PC2
PC3
PC4
All Connected Devices
```

Only the intended device accepts the data.

All other devices discard it.

---

## Collision in Hub

Since all devices share the same communication medium:

```text
One Device Sends
Another Device Sends
Same Time
```

This causes:

```text
Collision
```

As a result:

- Network becomes slower
- More retransmissions occur
- Performance decreases

---

## Collision Domain

A Hub creates:

```text
Single Collision Domain
```

Meaning all connected devices share the same communication channel.

---

## Types of Hub

### Active Hub

An Active Hub regenerates and amplifies signals before forwarding them.

Features:

- Requires Power Supply
- Regenerates Signal
- Extends Transmission Distance

---

### Passive Hub

A Passive Hub simply forwards signals.

Features:

- Does Not Regenerate Signals
- No Signal Amplification
- Does Not Require Signal Processing

---

## Advantages

- Cheap
- Easy to Install
- Simple Device

---

## Disadvantages

- High Collisions
- Low Security
- Inefficient Bandwidth Usage
- Broadcasts Everything

---

# 2. Repeater

## What is a Repeater?

A Repeater is a Layer 1 device used to regenerate weak signals and extend network distance.

---

## Purpose

As data travels through cables:

```text
Signal Strength ↓
```

The signal becomes weaker.

A Repeater:

```text
Receives Signal
↓
Regenerates Signal
↓
Transmits Again
```

---

## Characteristics

- Physical Layer Device
- Regenerates Signals
- Extends Network Distance
- Does Not Read MAC Addresses
- Does Not Filter Traffic

---

## Benefits

- Prevents Signal Loss
- Improves Long-Distance Communication
- Increases Transmission Range

---

# 3. Bridge

## What is a Bridge?

A Bridge is a Layer 2 device that inspects incoming traffic and decides whether to forward or reject frames.

Unlike a Hub, a Bridge can examine MAC addresses.

---

## Characteristics

- Layer 2 Device
- Intelligent Device
- Uses MAC Addresses
- Filters Traffic
- Connects Multiple LAN Segments
- Reduces Unnecessary Traffic

---

## How Bridge Works

Bridge checks:

```text
Source MAC Address
Destination MAC Address
```

Then decides:

```text
Forward Frame
OR
Reject Frame
```

---

## Bridge Table

A Bridge maintains a table containing:

| Port | MAC Address |
|--------|-------------|
| 1 | Device A |
| 2 | Device H |

This helps it decide where traffic should be forwarded.

---

## Collision Domains

A Bridge divides a LAN into multiple segments.

Example:

```text
Segment A ← Bridge → Segment B
```

Result:

```text
2 Collision Domains
```

This reduces collisions and improves performance.

---

## Broadcast Behavior

A Bridge can still forward broadcast traffic.

If the destination is unknown, it may temporarily flood traffic until it learns the correct MAC address.

---

## Advantages

- Filters Traffic
- Reduces Collisions
- Improves Performance

---

## Disadvantages

- Limited Number of Ports
- Slower than Modern Switches

---

# Bridge vs Switch

> A Switch is essentially an advanced Multi-Port Bridge.

---

# 4. Switch

## What is a Switch?

A Switch is a Layer 2 networking device that forwards data using MAC addresses.

Instead of broadcasting traffic everywhere, it sends data only to the intended destination.

---

## Characteristics

- Layer 2 Device
- Full Duplex Communication
- Maintains CAM Table
- Supports Unicast, Broadcast, and Multicast
- Uses MAC Addresses
- Multi-Port Bridge
- Common Port Counts:
  - 8 Ports
  - 16 Ports
  - 24 Ports
  - 48 Ports

---

## CAM Table

CAM stands for:

```text
Content Addressable Memory
```

Example:

| Port | MAC Address |
|--------|-------------|
| 1 | A |
| 8 | H |

The switch learns which MAC address is connected to which port.

---

## How Switch Works

### First Communication

Switch does not know destination MAC.

Therefore:

```text
Broadcast (Flooding)
```

occurs.

---

### After Learning

Switch updates its CAM Table.

Future communication becomes:

```text
Unicast
```

Only the correct port receives the frame.

---

## Collision Domains

Each switch port creates a separate collision domain.

Example:

```text
48-Port Switch
=
48 Collision Domains
```

This greatly improves performance.

---

## Broadcast Domain

A normal Layer 2 switch creates:

```text
One Broadcast Domain
```

unless VLANs are configured.

---

## Switching Methods

### 1. Store and Forward Switching

The switch:

1. Receives Complete Frame
2. Stores Frame
3. Performs Error Checking
4. Forwards Frame

Advantages:

- Reliable
- Error Detection

Disadvantages:

- Slightly Slower

---

### 2. Cut-Through Switching

The switch reads only the destination MAC address and immediately begins forwarding.

Advantages:

- Very Fast
- Low Latency

Disadvantages:

- No Error Checking

---

### 3. Fragment-Free Switching

A combination of Store-and-Forward and Cut-Through.

Process:

1. Checks First 64 Bytes
2. Looks for Collision Fragments
3. Forwards Frame

Advantages:

- Faster than Store-and-Forward
- More Reliable than Cut-Through

---

### 4. Adaptive Switching

Adaptive Switching automatically changes switching methods depending on network conditions.

Example:

```text
Low Errors → Cut-Through

High Errors → Store-and-Forward
```

---

## Advantages

- High Performance
- Dedicated Bandwidth
- Low Collisions
- Efficient Traffic Management

---

## Disadvantages

- More Expensive than Hub
- Requires MAC Learning

---

# 5. Router

## What is a Router?

A Router is a Layer 3 device used to connect two or more different networks.

It forwards packets using IP addresses.

---

## Characteristics

- Layer 3 Device
- WAN Device
- Internetworking Device
- Uses IP Addresses
- Maintains Routing Table
- Forwards Packets
- Connects Different Networks

---

## How Router Works

Routers examine:

```text
Destination IP Address
```

and determine the best path for packet delivery.

---

## Routing Table

Example:

| Port | Network ID |
|--------|------------|
| 1 | 10.0.0.0 |
| 2 | 192.168.1.0 |

The Router uses this table to determine where packets should be forwarded.

---

## Broadcast Domains

Each router interface creates:

```text
Separate Broadcast Domain
```

This prevents broadcasts from spreading between networks.

---

## Example

Network 1:

```text
10.0.0.0/24
```

Network 2:

```text
192.168.1.0/24
```

Devices from these two networks cannot communicate directly.

A Router is required to route traffic between them.

---

## Router vs Switch

| Feature | Switch | Router |
|----------|---------|---------|
| OSI Layer | Layer 2 | Layer 3 |
| Address Used | MAC Address | IP Address |
| Data Unit | Frame | Packet |
| Connects | Same Network | Different Networks |
| Table Used | CAM Table | Routing Table |
| Broadcast Domain | One | One Per Interface |

---

# 6. Gateway

## What is a Gateway?

A Gateway is a device that acts as an entry point and exit point between networks.

It allows communication between networks that may use different protocols, architectures, or technologies.

---

## Characteristics

- Entry Point of Network
- Exit Point of Network
- Protocol Conversion
- Network Translation
- Often Works at Higher OSI Layers
- Commonly Deployed on Servers

---

## Gateway Functions

A Gateway can:

- Translate Protocols
- Connect Dissimilar Networks
- Enable Cross-Platform Communication
- Provide Access to External Networks

---

## Types of Gateway

### Network Gateway

Used to connect different networks.

Example:

```text
Home Router
```

acts as a default gateway.

---

### Application Gateway

Works at higher layers and understands application protocols.

Examples:

- Proxy Servers
- Email Gateways
- API Gateways

---

## Why Gateway is Important

Without a Gateway:

```text
Internal Network
❌
External Network
```

Communication would not be possible.

---

# Quick Comparison Table

| Device | OSI Layer | Uses |
|----------|-----------|------|
| Hub | Layer 1 | Broadcast Signals |
| Repeater | Layer 1 | Regenerate Signals |
| Bridge | Layer 2 | Filter Frames |
| Switch | Layer 2 | Forward Frames Using MAC |
| Router | Layer 3 | Route Packets Using IP |
| Gateway | Multiple Layers | Connect Different Networks/Protocols |
