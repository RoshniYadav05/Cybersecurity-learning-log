# Simple Mail Transfer Protocol (SMTP)

## Overview

SMTP (Simple Mail Transfer Protocol) is an Application Layer protocol used for sending email messages across networks.

SMTP is responsible for transferring emails from:

* A user's email client to a mail server
* One mail server to another mail server

SMTP is only used for **sending emails**. To receive emails, protocols such as **POP3 (Post Office Protocol v3)** and **IMAP (Internet Message Access Protocol)** are used.

---

# Key Features of SMTP

* Application Layer Protocol
* Used for sending emails
* Works using a Client-Server architecture
* Uses TCP for reliable communication
* SMTP is a Push Protocol
* Messages are transferred in 7-bit ASCII format
* Supports mail transfer between different mail servers

---

# SMTP Ports

| Port    | Purpose                                          |
| ------- | ------------------------------------------------ |
| TCP 25  | Standard SMTP communication between mail servers |
| TCP 465 | SMTP over SSL/TLS (Secure SMTP)                  |
| TCP 587 | SMTP Message Submission with STARTTLS            |

### Note

* Port 25 is primarily used for server-to-server communication.
* Modern email providers commonly use ports 465 and 587 for secure email transmission.

---

# Why SMTP is Called a Push Protocol

SMTP pushes email messages from the sender to the receiving mail server.

Example:

```text
Sender → Mail Server → Recipient Mail Server
```

SMTP does not retrieve emails from a mailbox.

For receiving emails:

* POP3 is used to download emails
* IMAP is used to synchronize emails across devices

---

# SMTP Architecture

SMTP follows a Client-Server Model.

```text
+-----------+
|  Sender   |
+-----------+
      |
      v
+-----------+
| User Agent|
| (Gmail,   |
| Outlook)  |
+-----------+
      |
      v
+-----------+
| MTA Client|
+-----------+
      |
      | TCP Port 25
      v
+-----------+
| MTA Server|
+-----------+
      |
      v
+----------------+
| Recipient Mail |
|     Mailbox    |
+----------------+
      |
      v
+-----------+
| Receiver  |
+-----------+
```

---

# SMTP Components

## 1. User Agent (UA)

A User Agent is the software used by users to compose, send, receive, and manage emails.

Examples:

* Gmail
* Outlook
* Thunderbird

Functions:

* Creates email messages
* Sends messages to the mail server
* Displays received emails

---

## 2. Mail Transfer Agent (MTA)

The Mail Transfer Agent is responsible for transferring email messages between mail servers.

Functions:

* Routing emails
* Forwarding emails
* Delivering emails to destination servers

Examples:

* Postfix
* Sendmail
* Microsoft Exchange

---

## 3. Mail Queue

A temporary storage area where emails are held before being delivered.

Why it is needed:

* Large numbers of emails may be sent simultaneously
* Destination server may be temporarily unavailable
* Network congestion may occur

---

## 4. Recipient Mailbox

A mailbox stores emails until the recipient accesses them using IMAP or POP3.

---

# SMTP Communication Process

SMTP communication occurs in three phases:

## Phase 1: Connection Establishment

The SMTP client establishes a TCP connection with the SMTP server.

### Example

```text
Server → 220 Service Ready
Client → HELO mail.example.com
Server → 250 OK
```

---

## Phase 2: Mail Transfer

The actual email transfer takes place.

### Example

```text
MAIL FROM:<sender@example.com>
250 OK

RCPT TO:<receiver@example.com>
250 OK

DATA
354 Start Mail Input

Subject: Test Mail

Hello World

.
250 Message Accepted
```

---

## Phase 3: Connection Termination

After successful delivery, the session is closed.

### Example

```text
QUIT
221 Service Closing Transmission Channel
```

---

# SMTP Commands

SMTP uses commands to communicate between the client and server.

---

## HELO

Initiates a connection between the client and server.

Example:

```text
HELO example.com
```

Purpose:

* Starts SMTP communication
* Identifies the sending host

---

## EHLO

Extended version of HELO.

Example:

```text
EHLO example.com
```

Purpose:

* Starts communication
* Requests supported SMTP extensions

Common extensions include:

* STARTTLS
* AUTH
* SIZE

---

## MAIL FROM

Identifies the sender's email address.

Example:

```text
MAIL FROM:<roshni@example.com>
```

Purpose:

* Specifies who is sending the email

---

## RCPT TO

Identifies the intended recipient.

Example:

```text
RCPT TO:<user@example.com>
```

Purpose:

* Specifies the recipient address

---

## DATA

Indicates the start of the email content.

Example:

```text
DATA
```

The email body follows this command.

The message ends with:

```text
.
```

(single period on a separate line)

Purpose:

* Transfers email headers and body

---

## RSET

Resets the current SMTP session.

Purpose:

* Clears mail transaction information
* Used when an error occurs

---

## NOOP

No Operation command.

Purpose:

* Checks whether the server is still responsive
* Similar to a keep-alive request

Example:

```text
NOOP
```

---

## QUIT

Terminates the SMTP session.

Example:

```text
QUIT
```

Purpose:

* Gracefully closes the connection

---

# SMTP Response Codes

SMTP servers respond with status codes.

---

## Positive Completion Replies

| Code | Meaning                                 |
| ---- | --------------------------------------- |
| 211  | System Status                           |
| 214  | Help Message                            |
| 220  | Service Ready                           |
| 221  | Service Closing Connection              |
| 250  | Requested Action Completed Successfully |

---

## Transient Negative Completion Replies

Temporary failures.

| Code | Meaning                  |
| ---- | ------------------------ |
| 421  | Service Not Available    |
| 450  | Mailbox Unavailable      |
| 451  | Requested Action Aborted |

The client can retry later.

---

## Permanent Negative Completion Replies

Permanent failures.

| Code | Meaning                     |
| ---- | --------------------------- |
| 500  | Syntax Error                |
| 550  | Mailbox Not Found           |
| 552  | Storage Allocation Exceeded |
| 554  | Transaction Failed          |

The request must be corrected before retrying.

---

# SMTP Example Flow

```text
Client                     Server
  |                           |
  |------ HELO -------------> |
  | <----- 250 OK ----------- |
  |                           |
  |------ MAIL FROM --------> |
  | <----- 250 OK ----------- |
  |                           |
  |------ RCPT TO ----------> |
  | <----- 250 OK ----------- |
  |                           |
  |------ DATA -------------> |
  | <----- 354 Start Mail --- |
  |------ Message ----------> |
  |------ . ----------------> |
  | <----- 250 OK ----------- |
  |                           |
  |------ QUIT -------------> |
  | <----- 221 Bye ---------- |
```

---

# SMTP Security Considerations

SMTP by itself does not provide encryption.

Modern email systems secure SMTP communication using:

* SSL/TLS Encryption
* STARTTLS
* SMTP Authentication (SMTP AUTH)
* SPF (Sender Policy Framework)
* DKIM (DomainKeys Identified Mail)
* DMARC (Domain-based Message Authentication, Reporting and Conformance)

These mechanisms help prevent:

* Email Spoofing
* Unauthorized Relaying
* Phishing Attacks
* Message Tampering

---

# SMTP vs POP3 vs IMAP

| Protocol | Purpose                     | Default Port |
| -------- | --------------------------- | ------------ |
| SMTP     | Send Email                  | 25, 465, 587 |
| POP3     | Receive & Download Email    | 110          |
| IMAP     | Receive & Synchronize Email | 143          |

---

# Key Takeaways

* SMTP stands for Simple Mail Transfer Protocol.
* SMTP is responsible for sending emails.
* SMTP operates at the Application Layer.
* SMTP uses TCP for reliable communication.
* Standard SMTP uses TCP Port 25.
* SMTP is a Push Protocol.
* HELO/EHLO initiates communication.
* MAIL FROM identifies the sender.
* RCPT TO identifies the recipient.
* DATA contains the email content.
* QUIT terminates the SMTP session.
* SMTP works together with POP3 and IMAP to provide complete email communication.
