# 🌐 Understanding Subnetting

## 📖 Introduction

Subnetting is one of the most important concepts in networking. It is the process of dividing a large network into smaller and more manageable networks called **subnets**.

Instead of placing all devices in a single network, subnetting helps organize devices into separate logical networks, making the network more efficient, scalable, and secure.

**Subnetting = Dividing one large network into multiple smaller networks.**


## 🎯 Why Do We Need Subnetting?

As networks grow, managing all devices within a single network becomes difficult.

Without subnetting, organizations may face:

* Increased broadcast traffic
* Poor network performance
* Wastage of IP addresses
* Difficult troubleshooting
* Limited scalability

Subnetting helps overcome these challenges by creating smaller network segments that are easier to manage and monitor.

## 🧠 Key Concepts

### 1. Network ID

The Network ID identifies the network itself.

**Example:**

192.168.1.0/24

Network ID:

192.168.1.0

All devices within the subnet belong to this network.


### 2. Host ID

The Host ID identifies individual devices inside a network.

**Examples:**

192.168.1.10
192.168.1.25
192.168.1.100

These addresses represent hosts within the same subnet.

### 3. Subnet Mask

A subnet mask determines which part of an IP address belongs to the network and which part belongs to the host.

| CIDR | Subnet Mask     |
| ---- | --------------- |
| /24  | 255.255.255.0   |
| /25  | 255.255.255.128 |
| /26  | 255.255.255.192 |
| /27  | 255.255.255.224 |
| /28  | 255.255.255.240 |
| /30  | 255.255.255.252 |


## 📌 Understanding CIDR Notation

CIDR (Classless Inter-Domain Routing) is a compact method of representing subnet masks.

**Example:**

192.168.1.0/24

The **/24** indicates that the first 24 bits belong to the network portion, while the remaining bits are used for hosts.


## ⚙️ How Subnetting Works

### Step 1: Identify Requirements

Determine:

* Number of required subnets
* Number of required hosts per subnet

### Step 2: Borrow Host Bits

Host bits can be converted into network bits to create additional subnets.

**Formula:**

2^n ≥ Required Subnets

Where:

* n = Number of borrowed bits

### Step 3: Calculate Host Capacity

**Formula:**

2^h - 2

Where:

* h = Remaining host bits

The subtraction of 2 accounts for:

* Network Address
* Broadcast Address


## 📡 Network Address vs Broadcast Address

Every subnet contains two reserved addresses.

### Network Address

The first address of the subnet.

**Example:**

192.168.1.0

### Broadcast Address

The last address of the subnet.

**Example:**

192.168.1.255

These addresses cannot be assigned to hosts.


## 🔍 Example: Understanding a /30 Subnet

A /30 subnet is commonly used for point-to-point communication between routers.

**Example:**

192.168.1.0/30

Host Calculation:

2^(32-30) - 2
= 2^2 - 2
= 2 usable hosts

| Type              | Address     |
| ----------------- | ----------- |
| Network Address   | 192.168.1.0 |
| Host 1            | 192.168.1.1 |
| Host 2            | 192.168.1.2 |
| Broadcast Address | 192.168.1.3 |

Because only two devices require IP addresses, /30 networks are ideal for router-to-router communication.


## 🌍 Real-World Applications

Subnetting is widely used in:

* Enterprise Networks
* Data Centers
* VLAN Segmentation
* Security Operations Centers (SOC)
* Firewall Policy Design
* Network Access Control (NAC)
* Cloud Infrastructure
* Security Monitoring Platforms

For cybersecurity professionals, subnetting is essential because it helps in:

* Log Analysis
* Threat Hunting
* Incident Response
* SIEM Monitoring
* Firewall Rule Creation
* Network Segmentation


## 📚 What I Learned

Through subnetting, I learned how to:

* Identify Network and Host portions of an IP address
* Understand CIDR notation
* Calculate subnet masks
* Determine Network and Broadcast addresses
* Calculate usable host capacity
* Create multiple subnets from a single network
* Design more efficient and scalable networks


## 🎯 Conclusion

Subnetting is a fundamental networking skill that enables efficient IP address management, improves network performance, and strengthens security through proper network segmentation.

Whether working in Networking, Cloud Computing, System Administration, or Cybersecurity, understanding subnetting is essential because many real-world technologies rely on effective network design and IP allocation.

### 👨‍💻 Author Notes

This documentation was created as part of my Networking Fundamentals learning journey.

