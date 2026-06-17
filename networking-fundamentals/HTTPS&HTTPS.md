# HTTP & HTTPS

HTTP and HTTPS are application layer protocols used for communication between a web browser (client) and a web server.

They allow the exchange of information such as web pages, images, videos, forms, and API data over the Internet.

---

# What is HTTP?

**HTTP (HyperText Transfer Protocol)** is a protocol used to transfer web pages and other resources between a client and a server.

- Application Layer Protocol
- Follows Client-Server Architecture
- Stateless Protocol
- Uses TCP for reliable communication
- Data is transferred in Plain Text
- Not Secure

---

# What is HTTPS?

**HTTPS (HyperText Transfer Protocol Secure)** is the secure version of HTTP.

It uses SSL/TLS encryption to protect data exchanged between the client and the server.

- Application Layer Protocol
- Secure Version of HTTP
- Uses SSL/TLS Encryption
- Protects Confidential Data
- Uses TCP for communication
- Provides Authentication, Integrity, and Confidentiality

---

# Why Do We Need HTTP/HTTPS?

These protocols allow communication between:

```text
Web Browser (Client) <------> Web Server
```

Examples:

- Browser → Chrome, Firefox, Edge
- Server → Google, Facebook, Amazon, YouTube

Without HTTP/HTTPS, a browser would not know how to request or receive web pages.

---

# Components of an HTTP-Based System

```text
Client  <---->  Proxy  <---->  Proxy  <---->  Server
```

### Client

The device or application that sends requests.

Examples:

- Google Chrome
- Mozilla Firefox
- Microsoft Edge
- Safari

The client initiates communication.

---

### User Agent

A User Agent is software acting on behalf of the user.

Examples:

- Web Browser
- Mobile Browser
- API Client

The browser is the most common user agent.

---

### Server

A server receives requests and sends responses.

A server may appear as a single machine but often consists of multiple servers working together behind the scenes.

Examples:

- Facebook Web Server
- Google Web Server
- Amazon Web Server

---

### Proxy

A proxy is an intermediary device or software between the client and the server.

It forwards requests and responses.

Proxies can exist as:

- Proxy Servers
- Firewalls
- Gateways
- Load Balancers
- Reverse Proxies

---

# Functions of a Proxy

## 1. Caching

Stores frequently requested data.

Benefits:

- Faster browsing
- Reduced bandwidth usage
- Reduced server load

Example:

```text
User requests a website
↓
Proxy already has a cached copy
↓
Returns page immediately
```

---

## 2. Filtering

Filters unwanted or malicious traffic.

Examples:

- Firewall Rules
- URL Filtering
- Content Filtering
- Antivirus Scanning

Benefits:

- Increased Security
- Access Control

---

## 3. Load Balancing

Distributes incoming requests among multiple servers.

```text
Client Requests
        ↓
 Load Balancer
   ↓    ↓    ↓
Server1 Server2 Server3
```

Benefits:

- Prevents Server Overload
- Improves Availability
- Better Performance

---

## 4. Authentication

Controls access to resources.

Examples:

- Username & Password
- Multi-Factor Authentication (MFA)
- Token-Based Authentication

---

## 5. Logging

Stores historical information about requests and activities.

Examples:

- User Activity Logs
- Access Logs
- Security Logs

Benefits:

- Monitoring
- Troubleshooting
- Incident Response

---

# HTTP Client-Server Communication

## Step 1

Client sends request.

```text
GET /index.html
```

## Step 2

Server processes request.

## Step 3

Server sends response.

```text
HTTP/1.1 200 OK
```

## Step 4

Browser displays webpage.

---

# Stateless Nature of HTTP

HTTP is a **stateless protocol**.

This means:

- Server does not remember previous requests.
- Every request is treated independently.
- Refreshing a page sends a new request.

Example:

```text
Request 1 → Login Page

Request 2 → Home Page

Request 3 → Profile Page
```

Server treats each request separately.

---

# How Sessions Are Maintained?

Although HTTP is stateless, websites maintain sessions using:

- Cookies
- Session IDs
- Tokens
- Local Storage

Example:

```text
Online Shopping Cart
```

Without cookies, your cart would be lost after every request.

Therefore:

✔ HTTP is Stateless  
✔ Applications can create Stateful Sessions

---

# HTTP Security Problem

HTTP transfers data in plain text.

An attacker intercepting traffic can read:

- Usernames
- Passwords
- Banking Information
- Personal Data

```text
Client ---- Plain Text ---- Server
```

---

# HTTPS Solution

HTTPS encrypts communication using SSL/TLS.

```text
Client ==== Encrypted Data ==== Server
```

Even if traffic is intercepted, attackers cannot easily read the data.

---

# SSL/TLS Certificate

HTTPS requires an SSL/TLS Certificate.

Certificate provides:

1. Authentication
2. Encryption
3. Data Integrity

The browser verifies the certificate before establishing secure communication.

---

# HTTP vs HTTPS

| Feature | HTTP | HTTPS |
|----------|----------|----------|
| Full Form | HyperText Transfer Protocol | HyperText Transfer Protocol Secure |
| Security | Not Secure | Secure |
| Encryption | No | Yes (SSL/TLS) |
| Data Transfer | Plain Text | Encrypted |
| Certificate Required | No | Yes |
| Authentication | No | Yes |
| Data Integrity | No | Yes |
| URL Prefix | http:// | https:// |
| Default Port | 80 | 443 |
| Confidentiality | No | Yes |

---

# Ports Used

## HTTP

```text
Port 80
```

Default port for unsecured web communication.

---

## HTTPS

```text
Port 443
```

Default port for secure web communication.

---

# TCP and HTTP/HTTPS

Both HTTP and HTTPS use TCP.

TCP provides:

- Reliable Delivery
- Acknowledgments (ACK)
- Error Recovery
- Ordered Delivery
- Connection-Oriented Communication

This ensures web pages load correctly and completely.

---

# HTTP Request Methods

## GET

Retrieve data.

```text
GET /products
```

---

## POST

Send data to server.

```text
POST /login
```

---

## PUT

Update existing resource.

```text
PUT /user/1
```

---

## DELETE

Delete resource.

```text
DELETE /user/1
```

---

# HTTP Status Codes

## 200 Series – Success

```text
200 OK
201 Created
```

---

## 300 Series – Redirection

```text
301 Moved Permanently
302 Found
```

---

## 400 Series – Client Errors

```text
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
```

---

## 500 Series – Server Errors

```text
500 Internal Server Error
503 Service Unavailable
```

---

# Real-Life Example

When you visit:

```text
https://www.google.com
```

1. Browser sends HTTPS request.
2. TLS Handshake occurs.
3. Certificate is verified.
4. Encrypted connection is established.
5. Browser requests webpage.
6. Google sends encrypted response.
7. Browser displays webpage.
