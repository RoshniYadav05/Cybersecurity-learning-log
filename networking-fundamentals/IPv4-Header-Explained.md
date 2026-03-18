## 🌐 Understanding IPv4 Header — How Data Packets Actually Travel

Today, I moved one step deeper into networking fundamentals by understanding the IPv4 Header.

Earlier, I knew that data travels in packets across networks, but this time I learned what information exists inside a packet before it even starts its journey.

As a cybersecurity learner, understanding packet structure is extremely important because network analysis, packet inspection, and traffic monitoring all depend on it.

## 📌 What is an IPv4 Header?

Whenever data is sent over the internet, it is broken into small units called IP packets.

Each packet contains two main parts:

## Header

Data (Payload)

The IPv4 Header contains control information required for delivering the packet from source to destination.

**In simple words:**

The IPv4 header acts like a delivery label attached to every data packet.

Without this header, routers would not know:

where the packet came from

where it should go

how long it should survive in the network

## 📦 Structure of IPv4 Header

The IPv4 header has a minimum size of __20 bytes__ and can extend up to __60 bytes__ depending on options.

It consists of multiple fields, each performing a specific task during packet transmission.

## 🔹 Version Field

This field defines which IP version is being used.

For IPv4:

**Version = 4**

It helps networking devices understand how to interpret the packet format.

## 🔹 Internet Header Length (IHL)

This field tells the size of the header.

Since headers may contain optional fields, routers must know where:

header ends

actual data begins

Minimum value → 20 bytes.

## 🔹 Type of Service (ToS)

This field defines priority and quality of service for packets.

It helps routers decide:

which packet should be processed faster

delay-sensitive traffic handling

Example:

Voice calls

Video streaming

Normal data transfer

## 🔹 Total Length

This field represents the complete packet size, including:

Header + Data

Maximum packet size:

65,535 bytes

This helps devices understand how much data they are receiving.

## 🔹 Identification Field

Every packet gets a unique identification number.

Why?

Because sometimes large packets are divided into smaller fragments during transmission.

This ID helps the receiver reassemble fragments correctly.

## 🔹 Flags Field

Flags control packet fragmentation.

Main purposes:

Allow fragmentation

Prevent fragmentation

Indicate more fragments

It basically tells routers how packet splitting should behave.

## 🔹 Fragment Offset

When fragmentation happens, this field tells:

the position of each fragment in the original packet.

So packets can be rebuilt in correct order.

⏳ Time To Live (TTL)

One of the most important fields.

TTL defines how many routers (hops) a packet can pass through.

Each router decreases TTL by 1.

If TTL becomes 0 → packet is discarded.

Purpose:
✅ Prevent infinite looping of packets in networks.

Example:

ping uses TTL to measure hops
## 🔹 Protocol Field

This field tells which upper-layer protocol should receive the packet.

Examples:

TCP → 6

UDP → 17

ICMP → 1

So the system knows where to forward received data.

## 🔹 Header Checksum

Used for error detection.

It verifies whether the header was damaged during transmission.

If checksum fails → packet gets discarded.

## 🌍 Source IP Address

Contains sender's IP address.

Identifies:

Who sent the packet.

## 🎯 Destination IP Address

Contains receiver's IP address.

Identifies:

Where packet must reach.

Routing decisions mainly depend on this field.

## ⚙️ Options & Padding

Optional section used for:

testing

debugging

special routing instructions

Padding ensures header size remains properly aligned.

## 🔄 Packet Flow Understanding

After learning IPv4 header, I understood that:

Sender creates packet.

Header information is attached.

Routers read header fields.

TTL decreases at every hop.

Packet reaches destination.

Fragments are reassembled.

All routing intelligence depends on header information.

## 🔗 Learning Resources & Links
This learning log includes a short video walkthrough where I explain the IPv4 Header in my own words and connect it to real-world networking and security concepts.

## 🎥 YouTube Video
▶ Watch here: (https://youtu.be/j8VdbKhLU-o)

## 🔗 LinkedIn Post
📌 I’ve also shared this session and key takeaways on LinkedIn: ▶ View post: LinkedIn – https://www.linkedin.com/feed/update/urn:li:activity:7433450786472214528/?originTrackingId=8dXDcSOH5KbhG2habeX4%2FA%3D%3D

If you’re learning networking or cybersecurity too, feel free to explore, connect, or share feedback — I’d love to grow together🚀.
