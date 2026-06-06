# Domain Name System (DNS)

## Overview

DNS (Domain Name System) is a distributed naming service used to translate domain names into IP addresses and vice versa. It allows users to access websites using easy-to-remember names instead of numerical IP addresses.

Example:

www.google.com → 142.250.x.x

DNS operates at the Application Layer of the TCP/IP model.

---

## Why DNS is Needed

Before DNS was introduced, hostname-to-IP mappings were stored in a text file called `hosts.txt`.

As networks grew larger, maintaining and updating this file became difficult. DNS solved this problem by providing a hierarchical and distributed naming system.

---

## DNS Ports

DNS uses Port 53 for communication.

| Protocol | Port |
|-----------|------|
| UDP | 53 |
| TCP | 53 |

### UDP Port 53
Used for standard DNS queries because it is faster.

### TCP Port 53
Used for:
- Zone transfers
- Large DNS responses
- Reliable communication

---

## DNS Lookups

### Forward Lookup

Converts a domain name into an IP address.

Example:

```text
www.google.com → 142.250.x.x
```

### Reverse Lookup

Converts an IP address into a domain name.

Example:

```text
142.250.x.x → www.google.com
```

---

## Top-Level Domains (TLDs)

### Generic Top-Level Domains (gTLD)

- .com
- .org
- .net
- .edu
- .mil

### Country Code Top-Level Domains (ccTLD)

- .in
- .uk
- .us
- .jp

---

## DNS Namespace

A namespace is a method of organizing domain names so that every hostname remains unique.

### Flat Namespace

In a Flat Namespace, all names exist at the same level.

Example:

```text
Riya
Aman
Vikas
Sahil
Pinky
```

#### Limitation

As the number of hosts increases, managing unique names becomes difficult.

---

### Hierarchical Namespace

DNS uses a Hierarchical Namespace.

Example:

```text
XYZ Company
│
├── Admin
│   ├── Riya
│   └── Aman
│
├── Marketing
│   ├── Sahil
│   └── Pinky
│
└── IT
    ├── Vikas
    └── Vipul
```

#### Advantages

- Easy to manage
- Scalable
- Organized structure
- Suitable for large networks

---

## DNS Hierarchy

DNS follows a hierarchical structure:

```text
Root Server
     │
     ▼
TLD Server
     │
     ▼
Authoritative Server
```

---

### Root Name Server

The Root Name Server is the highest level in the DNS hierarchy.

Responsibilities:

- Receives DNS requests
- Directs queries to the correct TLD server
- Maintains information about top-level domains

There are 13 logical root server clusters worldwide (A–M).

---

### Top-Level Domain (TLD) Server

Responsible for managing domain extensions such as:

- .com
- .org
- .net
- .edu
- .in
- .uk

Responsibilities:

- Knows which Authoritative Server manages a domain
- Directs requests to the appropriate Authoritative Server

---

### Authoritative Name Server

The Authoritative Name Server stores actual DNS records.

Responsibilities:

- Stores hostname records
- Stores IP addresses
- Returns final answers to DNS queries

It acts as the source of truth for a domain.

---

## DNS Resolution Process

When a user enters:

```text
www.google.com
```

The following process takes place:

### Step 1
The user sends a DNS request to the local DNS Resolver.

### Step 2
If the answer is not available in cache, the Resolver contacts a Root Server.

### Step 3
The Root Server responds with the address of the appropriate TLD Server.

### Step 4
The Resolver contacts the TLD Server.

### Step 5
The TLD Server returns the Authoritative Name Server.

### Step 6
The Resolver contacts the Authoritative Server.

### Step 7
The Authoritative Server returns the requested IP address.

### Step 8
The Resolver caches the result and sends the answer back to the user.

### DNS Resolution Flow

```text
User
 │
 ▼
DNS Resolver
 │
 ▼
Root Server
 │
 ▼
TLD Server
 │
 ▼
Authoritative Server
 │
 ▼
IP Address Returned
```

---

## Recursive Query

In a Recursive Query, the DNS Resolver performs all lookups on behalf of the client and returns the final answer.

```text
Client
  │
  ▼
Resolver
  │
  ▼
Final Answer
```

---

## Iterative Query

In an Iterative Query, the DNS server provides referrals instead of the final answer.

```text
Client
  │
  ▼
Root Server
  │
  ▼
TLD Server
  │
  ▼
Authoritative Server
```

The client follows each referral until the final answer is found.

---

## Fully Qualified Domain Name (FQDN)

An FQDN contains the complete path from the host to the root domain.

Example:

```text
server1.google.com.
```

Characteristics:

- Complete domain name
- Includes every level in the hierarchy
- Ends with the root domain (.)

---

## Partially Qualified Domain Name (PQDN)

A PQDN does not contain the complete path to the root domain.

Example:

```text
server1.google.com
```

Characteristics:

- Relative naming format
- Root domain is not explicitly included
- Commonly used by users

---

## DNS and Cybersecurity

DNS is one of the most targeted protocols in cybersecurity.

Common attacks include:

- DNS Spoofing
- DNS Cache Poisoning
- Domain Hijacking
- DNS Tunneling
- Command and Control (C2) Communication

Understanding DNS is essential for SOC Analysts, Network Engineers, and Security Professionals.

---

## Key Takeaways

- DNS translates domain names into IP addresses.
- DNS operates at the Application Layer.
- DNS uses TCP and UDP Port 53.
- DNS supports Forward and Reverse Lookups.
- DNS uses a Hierarchical Namespace.
- DNS consists of Root, TLD, and Authoritative Servers.
- DNS can perform Recursive and Iterative Queries.
- FQDN contains the complete domain path including the root domain.

---

## What I Learned

- DNS fundamentals and architecture
- DNS lookup process
- Forward and Reverse DNS resolution
- Flat and Hierarchical Namespace
- Root, TLD, and Authoritative Servers
- Recursive and Iterative Queries
- DNS Resolution Workflow
- FQDN and PQDN concepts
