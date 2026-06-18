# Ports, Port Numbers

## Overview

A Port is not a physical connection. It is a logical communication endpoint used by operating systems, applications, and network services to exchange information over a network.

Whenever a computer communicates with another computer, it needs:

1. An IP Address → To identify the destination device.
2. A Port Number → To identify the service or application running on that device.

Think of it like this:

```text
IP Address = Building Address
Port Number = Specific Room inside the Building
```

The IP address helps us find the correct server, while the port number helps us find the correct service running on that server.

---

# What is a Port?

A Port is a logical communication channel used by programs and services for network communication.

It allows multiple applications to use the network simultaneously without interfering with each other.

Examples:

- Web Browsing
- Email
- File Transfer
- Remote Login
- Database Connections

All these services use different port numbers.

---

# Port Number Range

Port numbers range from:

```text
0 - 65535
```

Each port number uniquely identifies a specific service or application.

---

# Common Port Number Examples

| Port | Service |
|--------|----------|
| 80 | HTTP |
| 443 | HTTPS |
| 21 | FTP |
| 22 | SSH |
| 25 | SMTP |
| 53 | DNS |
| 110 | POP3 |
| 143 | IMAP |

---

# IP Address and Port Number Together

A complete network connection is identified using:

```text
IP Address + Port Number
```

Example:

```text
43.14.250.12 : 443
```

Where:

- 43.14.250.12 = Server IP Address
- 443 = HTTPS Service

The IP address identifies the server.

The port number identifies which service on that server should handle the request.

---

# How Web Browsing Uses Ports

Suppose you want to open:

```text
google.com
```

### Step 1

DNS converts:

```text
google.com
```

into an IP address.

Example:

```text
142.250.xxx.xxx
```

### Step 2

Since you are opening a web page, the browser automatically uses:

```text
HTTP  → Port 80
HTTPS → Port 443
```

### Step 3

The request is sent to:

```text
142.250.xxx.xxx:443
```

### Step 4

Google's web server receives the request and sends back the webpage.

---

# HTTP and HTTPS Ports

## Port 80

Associated with:

```text
HTTP
(HyperText Transfer Protocol)
```

Used for:

- Regular web pages
- Unencrypted web communication

Example:

```text
http://example.com
```

---

## Port 443

Associated with:

```text
HTTPS
(HyperText Transfer Protocol Secure)
```

Used for:

- Secure web browsing
- Encrypted communication

Example:

```text
https://example.com
```

---

# FTP and Port Numbers

## What is FTP?

FTP stands for:

```text
File Transfer Protocol
```

It is used to transfer files across a network.

---

## FTP Ports

FTP actually uses:

```text
TCP 21 → Control Connection
TCP 20 → Data Transfer (Active Mode)
```

Example:

```text
ftp.example.com
```

The request reaches the FTP service running on Port 21 instead of a web service running on Port 80.

---

# Netstat

## What is Netstat?

Netstat stands for:

```text
Network Statistics
```

It is a command-line utility used to display:

- Active network connections
- Open ports
- Listening ports
- Routing information
- Network statistics

---

## Basic Syntax

```bash
netstat
```

---

## Show Port Numbers

```bash
netstat -n
```

The `-n` option displays actual numerical IP addresses and port numbers instead of resolving hostnames.

Example Output:

```text
Proto   Local Address       Foreign Address      State

TCP     192.168.0.12:52413  142.250.85.17:443   ESTABLISHED
```

### Meaning

```text
192.168.0.12
```

Your computer

```text
52413
```

Temporary client-side port

```text
142.250.85.17
```

Google server

```text
443
```

HTTPS service

```text
ESTABLISHED
```

Connection is active

---

# Port Assignment Authority

Port numbers are assigned and managed by:

**IANA (Internet Assigned Numbers Authority)**

IANA ensures standardization of port assignments across the internet.

---

# Port Categories

The complete range of 0-65535 is divided into three categories.

---

## 1. Well-Known Ports

Range:

```text
0 - 1023
```

Also called:

```text
System Ports
```

These ports are commonly used by standard internet services.

Examples:

| Port | Service |
|--------|----------|
| 20 | FTP Data |
| 21 | FTP Control |
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 53 | DNS |
| 67 | DHCP Server |
| 68 | DHCP Client |
| 69 | TFTP |
| 80 | HTTP |
| 110 | POP3 |
| 123 | NTP |
| 143 | IMAP |
| 161 | SNMP |
| 443 | HTTPS |
| 445 | SMB |

---

## 2. Registered Ports

Range:

```text
1024 - 49151
```

These ports are registered by vendors and software developers for specific applications.

Examples:

| Port | Service |
|--------|----------|
| 1433 | Microsoft SQL Server |
| 1521 | Oracle Database |
| 3306 | MySQL |
| 3389 | RDP |
| 5432 | PostgreSQL |
| 8080 | Alternate HTTP |

---

## 3. Dynamic / Private Ports

Range:

```text
49152 - 65535
```

Also called:

```text
Ephemeral Ports
```

These ports are temporarily assigned by the operating system.

Example:

When your browser opens a website:

```text
Client: 192.168.0.12:63510
Server: 142.250.xxx.xxx:443
```

The browser automatically receives a temporary port like:

```text
63510
```

for that session.

---

# Can a Computer Use Server Ports?

Yes.

Although ports from:

```text
0 - 1023
```

and

```text
1024 - 49151
```

are generally used on servers, your own computer can also use them when acting as a server.

Examples:

- Running a Website
- Running an FTP Server
- Running a Database
- Hosting Applications

Example:

```text
Port 80  → Website
Port 21  → FTP Server
```

In such cases your computer listens for incoming connections.

---

# Example Netstat Output

```text
Proto  Local Address         Foreign Address        State

TCP    192.168.0.12:21       12.34.56.78:49232     LISTENING

TCP    192.168.0.12:80       44.10.250.1:50282     LISTENING

TCP    192.168.0.12:63510    142.250.85.17:443     ESTABLISHED

TCP    192.168.0.12:63502    142.250.85.17:110     ESTABLISHED
```

---

# Common Ports Cheat Sheet

| Port | Protocol | Service |
|--------|-----------|----------|
| 20 | TCP | FTP Data Transfer |
| 21 | TCP | FTP Control |
| 22 | TCP | SSH / SFTP |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP |
| 53 | TCP/UDP | DNS |
| 67 | UDP | DHCP Server |
| 68 | UDP | DHCP Client |
| 69 | UDP | TFTP |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 123 | UDP | NTP |
| 137 | UDP | NetBIOS Name Service |
| 138 | UDP | NetBIOS Datagram Service |
| 139 | TCP | NetBIOS Session Service |
| 143 | TCP | IMAP |
| 161 | UDP | SNMP |
| 389 | TCP/UDP | LDAP |
| 443 | TCP | HTTPS |
| 445 | TCP | SMB |
| 514 | UDP | Syslog |
| 636 | TCP | LDAPS |
| 993 | TCP | IMAPS |
| 995 | TCP | POP3S |
| 1433 | TCP | Microsoft SQL Server |
| 1521 | TCP | Oracle Database |
| 3306 | TCP | MySQL |
| 3389 | TCP | RDP |
| 5432 | TCP | PostgreSQL |
| 5900 | TCP | VNC |
| 8080 | TCP | Alternate HTTP |
