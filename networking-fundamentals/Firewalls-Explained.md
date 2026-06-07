# Firewalls

## Overview

A Firewall is a security device (software, hardware, or both) that acts as a digital gatekeeper for network security.

Its main job is to monitor and control network traffic entering and leaving a network. Based on predefined rules and policies, it decides whether traffic should be allowed or blocked.

Think of a firewall as a traffic cop standing at the entrance of a network, deciding which traffic can pass through and which traffic should be stopped.

---

## What Does a Firewall Do?

A firewall:

- Monitors network traffic
- Inspects incoming and outgoing connections
- Applies security rules and policies
- Allows legitimate traffic
- Blocks unauthorized or suspicious traffic

The firewall examines traffic and makes decisions according to rules configured by administrators.

---

## Ingress vs Egress Traffic

### Ingress Traffic
Data coming **into** a network.

**Example:** Opening a website and receiving its contents.

### Egress Traffic
Data going **out of** a network.

**Example:** Sending an email or uploading a file.

---

## Where Does a Firewall Sit?

A firewall is commonly placed at the edge of a network, between the internal network and external networks such as the Internet.

```text
Internet
    |
    v
+-----------+
| Firewall  |
+-----------+
    |
    v
+-----------+
| Internal  |
| Network   |
+-----------+
```

This placement helps protect internal systems from external threats.

---

# Types of Firewalls

## 1. Packet Filtering Firewall

A Packet Filtering Firewall examines packets based on information such as:

- Source IP Address
- Destination IP Address
- Protocol
- Port Number

It makes decisions using predefined rules without looking deeply into the packet contents.

### Example

Allow:
- HTTP (Port 80)
- HTTPS (Port 443)

Block:
- Telnet (Port 23)

### Pros

- Fast
- Simple
- Low resource usage

### Cons

- Limited visibility into traffic
- Cannot inspect application data deeply

---

## 2. Stateful Inspection Firewall

A Stateful Firewall keeps track of active connections and understands the state of network sessions.

Instead of checking packets individually, it determines whether a packet belongs to an already established and trusted connection.

### Example

If a user initiates a web request, the returning response traffic is automatically allowed because it belongs to an existing session.

### Pros

- More secure than packet filtering
- Tracks connection states
- Better traffic awareness

### Cons

- Uses more memory and processing power
- More complex than basic packet filtering

---

## 3. Proxy Firewall (Application-Level Gateway)

A Proxy Firewall acts as an intermediary between users and external resources.

Instead of directly communicating with a website or service, the user's request is first sent to the proxy firewall.

The firewall:

- Intercepts the request
- Inspects the content
- Checks policies
- Allows or blocks the request

### Analogy

Think of it like a receptionist or concierge who receives requests, checks them, and then decides whether they should be forwarded.

### Example

When a user tries to visit a website:

1. User sends a request.
2. Proxy receives the request.
3. Proxy examines the content.
4. If allowed, the request is forwarded.
5. If not allowed, the request is blocked.

### Features

- Deep Packet Inspection (DPI)
- Content Filtering
- Application-Aware Security
- Request Handling

### Pros

- Strong security
- Detailed traffic inspection
- Content filtering capabilities

### Cons

- Higher latency
- Performance overhead
- Application-specific configuration

---

## 4. Next-Generation Firewall (NGFW)

A Next-Generation Firewall combines traditional firewall capabilities with advanced security features.

### Additional Features

- Intrusion Prevention System (IPS)
- Application Control
- Deep Packet Inspection
- Threat Intelligence
- User Awareness
- Behavioral Analysis

### Analogy

A highly intelligent security guard that not only checks IDs but also analyzes behavior and identifies suspicious activity.

### Pros

- Comprehensive security
- Better threat detection
- Protection against modern attacks
- Application-level visibility

### Cons

- Higher cost
- More complex deployment
- Resource intensive (CPU, RAM, storage)

### How NGFWs Improve Security

NGFWs continuously monitor and profile traffic patterns.

If suspicious behavior is detected, they can take action automatically because many include built-in Intrusion Prevention capabilities.

---

# How Firewalls Work

## Rules and Policies

Firewalls process traffic according to a set of rules.

Rules are usually evaluated in a top-down order.

Once a packet matches a rule, the associated action is immediately applied.

---

## Anatomy of a Firewall Rule

A firewall rule generally contains:

### Source

- IP Address
- Network
- User

### Destination

- IP Address
- Network
- Service

### Protocol

- TCP
- UDP
- ICMP

### Port

Examples:

- 80 (HTTP)
- 443 (HTTPS)
- 22 (SSH)

### Action

- Allow
- Deny
- Reject
- Drop

---

## Deny vs Reject vs Drop

### Deny

The traffic is not permitted according to policy.

### Reject

The firewall blocks the traffic and sends a response indicating access was denied.

### Drop

The firewall silently discards the traffic without sending any response.

This makes it harder for attackers to determine whether a host exists behind the firewall.

---

## Implicit Deny

A common firewall principle is:

> "Anything not explicitly allowed is denied."

Any traffic that does not match an allow rule is automatically blocked.

---

# Firewall Management

Proper firewall management is critical.

Best practices include:

- Regular rule reviews
- Removing unnecessary rules
- Updating firmware and software
- Monitoring logs
- Auditing configurations

Good management helps reduce vulnerabilities and configuration mistakes.

---

# Benefits of Firewalls

### Access Control

Prevents unauthorized access to systems and networks.

### Threat Protection

Can block:

- Port scans
- Denial-of-Service (DoS) attempts
- Certain malware activity

### Policy Enforcement

Ensures users and systems follow organizational security policies.

### Logging and Auditing

Provides traffic records that can be used for:

- Investigations
- Troubleshooting
- Security monitoring
- Compliance purposes

---

# Limitations of Firewalls

### Not a Silver Bullet

A firewall is only one layer of defense and cannot provide complete security by itself.

### Insider Threats

Less effective against malicious actions performed by trusted internal users.

### Sophisticated Attacks

Advanced threats such as:

- Advanced Persistent Threats (APTs)
- Zero-Day Exploits

may bypass firewall protections.

### Misconfiguration Risks

A poorly configured firewall can introduce significant security risks.

### Cannot Fully Protect Against

- Phishing attacks
- Social engineering
- Malware delivered through allowed traffic
- User mistakes

---

# Key Takeaways

- Firewalls act as digital gatekeepers for networks.
- They inspect and control ingress and egress traffic.
- Different firewall types provide different levels of visibility and protection.
- Rules determine whether traffic is allowed or blocked.
- NGFWs provide advanced protection through application awareness and threat intelligence.
- Firewalls are essential but should be used as part of a layered security strategy.
