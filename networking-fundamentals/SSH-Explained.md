# SSH (Secure Shell)

## What is SSH?

SSH (Secure Shell) is a **network protocol** that is used to securely connect to and control remote machines over an insecure network.

In simple words, SSH creates a **private and encrypted communication** between two computers.

It is mainly used to:

- Remotely manage servers.
- Transfer files securely.
- Run commands on another computer without physically being there.

---

## SSH vs VPN

VPN provides a **secure connection** for an entire network.

SSH provides a **secure connection** between a client and a remote machine.

---

## SSH vs Telnet

SSH is similar to **Telnet**, but it is much more secure.

In Telnet:

- Messages are sent as **plain text**.
- Anyone capturing the traffic can read the data.

In SSH:

- All communication is **encrypted**.
- The transmitted data cannot be easily read by attackers.

This is why Telnet has mostly been replaced by SSH.

---

## SSH Connection

Before any communication starts, SSH first establishes a **TCP connection**.

- Default Port: **22 (TCP)**

After the TCP connection is established, SSH creates an encrypted tunnel between the client and the server.

```text
SSH Client
     │
     │ TCP Port 22
     ▼
===========================
      SSH Tunnel
   (Strong Encryption)
===========================
     ▲
     │
SSH Server
```

All communication travels through this encrypted tunnel.

---

# Cryptography in SSH

SSH relies on **Cryptography** to provide secure communication.

It mainly uses two types of encryption.

## 1. Asymmetric Encryption

Used during the **initial handshake**.

Purpose:

- Securely establish the connection.
- Exchange information safely before communication begins.

---

## 2. Symmetric Encryption

Used for **actual data transfer**.

Purpose:

- Encrypt all commands.
- Encrypt responses.
- Encrypt file transfers.

Symmetric encryption is faster than asymmetric encryption, which is why SSH switches to it after the handshake is complete.

---

# SSH Key Exchange

In an SSH connection, both the **client** and the **server** use a **Public Key Key Exchange Algorithm**.

The purpose of this algorithm is to establish a **shared secret key**.

This shared secret key will later be used for secure communication.

---

## Key Exchange Process

During the key exchange:

- The SSH client and SSH server exchange information using **public keys**.
- Both sides independently calculate the **same shared secret key**.
- The shared secret key is **never sent across the network**.

Example:

```text
SSH Client                                 SSH Server

        Hello!
           ---------------------------->

                 Encrypt using
                  Public Key
           ---------------------------->

                               Decrypt using
                                Private Key

```

---

# Public Key and Private Key

Every SSH server has a **Public Key** and a **Private Key**.

## Public Key

- Can be shared freely.
- It is used to encrypt information.
- Think of it like a lock that anyone can use.

## Private Key

- Must always be kept secret.
- It is used to decrypt information.
- Only the matching private key can unlock data encrypted using the public key.

Think of it like this:

> The **Public Key** is a lock that anyone can use to lock a box, but only the **Private Key** can unlock it.

---

# SSH Handshake

During the SSH handshake:

- Both the client and the server exchange information using their public keys.
- Both sides generate the **same shared secret key** independently.
- The shared secret key is **never transmitted over the network**.

This process is known as **Ephemeral Key Exchange**.

---

# Shared Secret Key

The shared secret key is:

- Temporary.
- Created only for the current SSH session.
- Deleted after the session ends.

Every new SSH connection creates a **new shared secret key**.

This improves security because each session uses a different encryption key.

---

# Important Point

Although the client and server never send the shared secret key over the network, both of them calculate **exactly the same key** independently.

This key is then used for encrypting and decrypting all communication during that SSH session.

---

# Key-Based Authentication in SSH

Both the client and the server use the **same shared session key** to encrypt and decrypt data after the SSH handshake.

Before the encrypted tunnel is created, SSH performs an **authentication check**.

SSH commonly uses **Key-Based Authentication**.

---

# Key-Based Authentication

The client has:

- Public Key
- Private Key

The server stores the client's **Public Key** inside:

```text
~/.ssh/authorized_keys
```

The Private Key always stays on the client machine.

---

# Authentication Process

## Step 1

Generate a Public Key and Private Key pair on the client.

```text
Client

Public Key
Private Key
```

---

## Step 2

Copy the **Public Key** to the server.

The server stores it in:

```text
~/.ssh/authorized_keys
```

Only the **Public Key** is copied.

The **Private Key is never copied**.

---

## Step 3

The SSH Client starts an SSH connection.

```text
SSH Client
      │
      │ Initiate SSH Connection
      ▼
SSH Daemon (Server)
```

---

## Step 4

The server sends a challenge.

The client proves its ownership by using its **Private Key** to answer the challenge.

Since the server already has the matching Public Key, it can verify the response.

If the verification is successful, authentication is completed.

---

# Advantages of Key-Based Authentication

- No sensitive information travels across the network.
- Private keys are much harder to brute-force than passwords.
- We can automate scripts and deployments without typing credentials.

  # Example: Using SSH with GitHub

Instead of using a password every time you push code to GitHub:

1. Add your **Public Key** to your GitHub account.
2. When you push the code, GitHub checks your **Public Key**.
3. It verifies that it matches your **Private Key**.
4. If it matches, GitHub allows the code to be pushed.

This provides **seamless authentication** without entering a password every time.

---

# Local Port Forwarding

## Bastion Host

A **Bastion Host** is a publicly accessible server that sits in front of a private network.

It acts like a **secure gateway**.

- SSH first connects to the Bastion Host.
- The Bastion Host then forwards the traffic to internal resources inside the private network.

---

## Working

```text
Client
┌─────────────────────────┐
│ Local SSH Client        │
│ Listens on Port 3306    │
└──────────┬──────────────┘
           │
      SSH Tunnel
      (Encrypted)
           │
           ▼
┌─────────────────────────┐
│ Bastion Host            │
│ SSH Server              │
│ Public + Private        │
│ Interfaces              │
└──────────┬──────────────┘
           │
           ▼
┌─────────────────────────┐
│ Remote MySQL Server     │
│ Listening on Port 3306  │
└─────────────────────────┘
```

Local access:

```bash
curl localhost:3306
```

The request travels through the encrypted SSH tunnel to the Bastion Host and is then forwarded to the remote MySQL server inside the private network.

# SSH Protocol Stack

SSH is built on multiple protocol layers.

```text
+------------------------------------------------------+
| SSH User Authentication Protocol                     |
| → Authenticates the client (user) to the server      |
+------------------------------------------------------+
| SSH Connection Protocol                              |
| → Multiplexes the encrypted tunnel into several      |
|   logical channels                                   |
+------------------------------------------------------+
| SSH Transport Layer Protocol                         |
| → Provides server authentication, confidentiality,   |
|   integrity and compression                          |
+------------------------------------------------------+
| TCP                                                  |
+------------------------------------------------------+
| IP                                                   |
+------------------------------------------------------+
```

---

# SSH focuses on 3 main functions

- Host Keys
- Packet Exchange
- Key Generation

---

# Host Keys

Server authentication happens at the **Transport Layer**.

The server proves its identity by using its **Public/Private Key Pair**.

A server can have multiple host keys using different asymmetric encryption algorithms.

---

# SSH Transport Layer

The Transport Layer performs the following steps:

### 1. Establish TCP Connection

A TCP connection is established between the client and the server.

---

### 2. Identification String Exchange

Both client and server exchange their SSH version information.

Example:

```text
SSH Protocol Version
Software Version
```

Each identification string ends with:

```text
CR LF
(Carriage Return + Line Feed)
```

---

### 3. Algorithm Negotiation

The client and server negotiate which encryption, hashing, key exchange and authentication algorithms will be used for the session.

---

### 4. SSH Key Exchange

The client and server perform the SSH key exchange process to establish a shared secret key.

# End of Key Exchange

After the key exchange is completed:

- End of Key Exchange
- Service Request

---

# Key Generation

The keys used for **encryption** and **MAC (Message Authentication Code)** are generated from the **shared secret key (K)**.

---

# SSH User Authentication Protocol

The SSH User Authentication Protocol handles:

- Message Types and Formats
- Message Exchange
- Authentication Methods

---

# SSH Connection Protocol

The SSH Connection Protocol is responsible for:

- Channel Mechanism
- Channel Types
- Port Forwarding

---

# HTTP Methods – HEAD and OPTIONS

> These methods are **less commonly used**.

## HEAD

The **HEAD** method is like a lightweight version of **GET**.

- Retrieves only the **headers** from the server.
- Skips the actual **response body**.
- Useful when we only need to check whether a resource exists or get metadata about it **without downloading the entire content**.

---

## OPTIONS

The **OPTIONS** method describes the available operations for a resource.

It is commonly used in **CORS (Cross-Origin Resource Sharing)** during the **pre-flight request**.

Before sending the actual request, the browser sends an **OPTIONS** request to ask the server what operations are allowed.
