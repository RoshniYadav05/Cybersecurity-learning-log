# File Transfer Protocol (FTP)

## Overview

File Transfer Protocol (FTP) is an Application Layer protocol used to transfer files between computers over a network. It follows the Client-Server architecture and works on top of TCP, which makes it a connection-oriented and reliable protocol.

FTP is primarily used for:

- Uploading files to a remote server
- Downloading files from a remote server
- Sharing files between systems
- Managing files and directories on remote hosts

One unique feature of FTP is that it uses **two separate TCP connections simultaneously**:

1. Control Connection
2. Data Connection

This separation allows commands and file transfers to occur independently. :contentReference[oaicite:0]{index=0}

---

# FTP Architecture

In an FTP environment:

- Files are stored on an FTP Server.
- Multiple users can connect to the server through the Internet or a private network.
- Users access files using FTP Client applications.
- The client requests files, and the server responds by sending or receiving data.

### Common FTP Clients

Some commonly used FTP client applications are:

- FileZilla
- WinSCP
- Cyberduck
- gFTP

---

# How FTP Works

FTP follows the Client-Server model.

1. User opens an FTP Client.
2. Client connects to the FTP Server.
3. Authentication is performed (Username and Password).
4. User uploads or downloads files.
5. Server stores or retrieves the requested files.

```
User → FTP Client → Internet/TCP-IP → FTP Server → Files
```

---

# FTP Connections

FTP establishes two separate TCP connections.

## 1. Control Connection

The Control Connection is responsible for sending control information such as:

- Username
- Password
- Commands
- Directory navigation requests
- File retrieval requests
- File storage requests

### Characteristics

- Remains active throughout the session
- Handles communication between client and server
- Uses TCP Port 21

```
Control Connection → TCP Port 21
```

The control channel remains active until the FTP session is terminated. :contentReference[oaicite:1]{index=1}

---

## 2. Data Connection

The Data Connection is responsible for transferring the actual file data.

### Characteristics

- Transfers files between client and server
- Opened when file transfer is required
- Uses TCP Port 20 (traditional active FTP)

```
Data Connection → TCP Port 20
```

Actual file contents travel through this connection. :contentReference[oaicite:2]{index=2}

---

# FTP Security

Traditional FTP is not considered a secure protocol because:

- Data is sent in plain text
- Usernames are sent in plain text
- Passwords are sent in plain text
- Traffic is not encrypted

An attacker intercepting the communication may be able to read transferred data.

Because of this limitation, secure alternatives such as SFTP and FTPS are preferred today. :contentReference[oaicite:3]{index=3}

---

# Anonymous FTP

Many FTP servers allow Anonymous Access.

In Anonymous FTP:

- No personal account is required
- Username may be anonymous
- Password may not be required

However, organizations can also configure authentication using:

- Username
- Password

to restrict access to authorized users only.

---

# FTP Data Structures

FTP supports different ways of organizing data.

## 1. File Structure

In File Structure:

- No internal structure is defined.
- File is treated as a continuous sequence of bytes.

Example:

```
Document.txt
Image.png
Video.mp4
```

The data is stored exactly as a stream of bytes.

---

## 2. Record Structure

In Record Structure:

- Data is divided into records.
- Records are stored sequentially.
- Each record maintains its own boundary.

Example:

```
Record 1
Record 2
Record 3
Record 4
```

---

## 3. Page Structure

In Page Structure:

- Data is divided into pages.
- Each page can be indexed independently.
- Pages may contain page numbers.

Example:

```
Page 1
Page 2
Page 3
Page 4
```

---

# FTP Transmission Modes

Transmission mode defines how data is sent between client and server.

## 1. Stream Mode

In Stream Mode:

- Data is transmitted as a continuous stream of bytes.
- Most commonly used transmission method.

Example:

```
Byte → Byte → Byte → Byte → Byte
```

---

## 2. Block Mode

In Block Mode:

- Data is divided into blocks before transmission.
- Each block is transferred separately.

Example:

```
Block 1 → Block 2 → Block 3 → Block 4
```

Useful when large amounts of data need structured transfer.

---

## 3. Compressed Mode

In Compressed Mode:

- Data is compressed before transmission.
- Reduces bandwidth consumption.
- Commonly used for large file transfers.

Example:

```
Large File
      ↓
 Compression
      ↓
 Transfer
      ↓
 Decompression
```

---

# FTP Commands

FTP can be accessed through command-line interfaces or graphical applications.

Commands are generally grouped into:

1. File Transfer Commands
2. Connection Commands
3. Session Termination Commands

---

## File Transfer Commands

### GET

Downloads a file from a remote server.

```bash
GET filename
```

Example:

```bash
GET report.pdf
```

---

### PUT

Uploads a file to a remote server.

```bash
PUT filename
```

Example:

```bash
PUT backup.zip
```

---

### SEND

Transfers a single file.

```bash
SEND filename
```

---

## Connection Commands

### USER

Sends the username to the server.

```bash
USER roshni
```

---

### PASS

Sends the user's password.

```bash
PASS ********
```

---

### OPEN

Opens a connection to an FTP server.

```bash
OPEN ftp.example.com
```

---

## Session Termination Commands

### CLOSE

Closes the current FTP connection.

```bash
CLOSE
```

---

### QUIT

Terminates the FTP session completely.

```bash
QUIT
```

---

# SFTP (Secure File Transfer Protocol)

SFTP is a secure alternative to FTP.

Unlike traditional FTP, SFTP encrypts all communication between the client and server.

### Features

- Encrypted communication
- Secure authentication
- Data confidentiality
- Protection against packet sniffing

### Port Number

```
TCP Port 22
```

### Security Technology

SFTP uses:

- SSH (Secure Shell)

for secure file transfer. :contentReference[oaicite:4]{index=4}

---

# FTP vs SFTP

| Feature | FTP | SFTP |
|----------|----------|----------|
| Security | Not Secure | Secure |
| Encryption | No | Yes |
| Protocol Base | TCP | SSH |
| Authentication Protection | No | Yes |
| Data Protection | No | Yes |
| Default Port | TCP 20/21 | TCP 22 |
| Data Transfer | Plain Text | Encrypted |
| Reliability | Reliable | Reliable and Secure |

---

# Key Points to Remember

- FTP is an Application Layer protocol.
- FTP uses the Client-Server model.
- FTP uses TCP.
- FTP establishes two connections:
  - Control Connection (Port 21)
  - Data Connection (Port 20)
- FTP is not encrypted by default.
- Anonymous FTP allows file access without normal authentication.
- FTP supports File, Record, and Page structures.
- FTP supports Stream, Block, and Compressed transmission modes.
- SFTP is the secure version used in modern environments.
- SFTP uses SSH and TCP Port 22.
