# Security Principles and Frameworks

## Overview

Cybersecurity is not only about protecting systems from attacks but also about implementing principles, frameworks, and controls that help organizations manage risks and secure their assets.

This document covers core cybersecurity concepts including Authentication, Authorization, CIA Triad, Security Controls, NIST Cybersecurity Framework (CSF), Security Principles, and Security Audits.

---

# Security Frameworks

Security frameworks provide organizations with structured guidelines and best practices to manage cybersecurity risks.

They act as a roadmap for creating security policies, procedures, and controls that help protect data, systems, and networks.

### Purpose of Security Frameworks

- Mitigate risks and threats
- Protect sensitive information
- Improve security posture
- Standardize security practices
- Support compliance requirements

---

# Security Controls

Security Controls are safeguards designed to reduce specific security risks.

They help organizations:

- Prevent attacks
- Detect threats
- Reduce vulnerabilities
- Protect sensitive assets

### Examples

- Firewalls
- Multi-Factor Authentication (MFA)
- Access Control Systems
- Security Policies
- Antivirus Solutions

---

# Encryption

Encryption is the process of converting readable data (plaintext) into an unreadable format (ciphertext).

Only users with the correct key can decrypt and access the original information.

### Why Encryption is Important

- Protects sensitive information
- Maintains confidentiality
- Secures data during storage and transmission

### Example

```text
Plaintext:
Hello123

Encrypted:
A8$Kz#91Lp
```

---

# Authentication

Authentication is the process of verifying that someone is who they claim to be.

### Common Authentication Factors

#### Something You Know

- Password
- PIN

#### Something You Have

- Security Token
- Mobile Device

#### Something You Are

- Biometrics

### Multi-Factor Authentication (MFA)

MFA requires two or more authentication factors before access is granted.

#### Example

```text
Password + OTP
Password + Fingerprint
```

MFA significantly improves security by adding multiple layers of verification.

---

# Biometrics

Biometrics use unique physical characteristics to verify a person's identity.

### Examples

- Fingerprint Scan
- Facial Recognition
- Iris Scan
- Retina Scan
- Voice Recognition

### Benefits

- Difficult to duplicate
- Convenient authentication method
- Strong identity verification

---

# Social Engineering

Social Engineering is a technique used to manipulate people into revealing sensitive information or performing actions that compromise security.

Instead of attacking technology, attackers exploit human behavior.

### Common Examples

- Phishing Emails
- Vishing (Voice Phishing)
- Smishing (SMS Phishing)
- Impersonation Attacks

### Example

An attacker pretends to be a bank representative and convinces a victim to reveal account credentials.

---

# Authorization

Authorization determines what resources a user is allowed to access after successful authentication.

### Authentication vs Authorization

| Authentication | Authorization |
|---------------|--------------|
| Verifies identity | Determines permissions |
| Who are you? | What can you access? |

### Example

A user successfully logs in to a system but can only access resources assigned to their role.

---

# CIA Triad

The CIA Triad is one of the foundational models of information security.

It helps organizations design security controls and manage risk.

## Confidentiality

Ensures that only authorized users can access sensitive information.

### Examples

- Encryption
- Access Controls
- Data Classification

---

## Integrity

Ensures data remains accurate, authentic, and trustworthy.

### Examples

- Hashing
- Digital Signatures
- File Integrity Monitoring

---

## Availability

Ensures systems and data remain accessible to authorized users whenever needed.

### Examples

- Backups
- Redundant Systems
- Disaster Recovery Planning

---

# NIST Cybersecurity Framework (CSF)

The NIST Cybersecurity Framework (CSF) is a voluntary framework consisting of standards, guidelines, and best practices used to manage cybersecurity risk.

It helps organizations:

- Manage cybersecurity risks
- Improve security posture
- Learn from incidents
- Protect critical assets

---

# NIST CSF Core Functions

## 1. Identify

Understand cybersecurity risks and their impact on organizational assets.

### Activities

- Asset Management
- Risk Assessment
- Threat Identification
- Vulnerability Identification

---

## 2. Protect

Implement safeguards that reduce cybersecurity risks.

### Examples

- Security Policies
- User Awareness Training
- Access Controls
- Encryption

---

## 3. Detect

Identify potential security incidents as quickly as possible.

### Examples

- Security Monitoring
- Log Analysis
- IDS/IPS Solutions
- Alerting Systems

---

## 4. Respond

Take action to contain and manage security incidents.

### Activities

- Incident Analysis
- Containment
- Mitigation
- Communication

---

## 5. Recover

Restore affected systems and return operations to normal.

### Examples

- Backup Restoration
- Disaster Recovery
- Business Continuity Planning

---

# NIST SP 800-53

NIST SP 800-53 provides a catalog of security and privacy controls used to protect information systems.

These controls help organizations maintain:

- Confidentiality
- Integrity
- Availability

and improve their overall security posture.

---

# Core Security Principles

## 1. Minimize Attack Surface Area

Reduce the number of possible attack paths available to attackers.

### Examples

- Disable unnecessary services
- Remove unused applications
- Restrict access to sensitive resources

The fewer attack vectors available, the lower the risk.

---

## 2. Principle of Least Privilege

Users should only receive the minimum permissions necessary to perform their job functions.

### Benefits

- Reduces misuse of privileges
- Limits attacker movement
- Minimizes damage during breaches

### Example

A help desk employee should not have Domain Administrator privileges.

---

## 3. Defense in Depth

Defense in Depth uses multiple security layers rather than relying on a single security control.

### Examples

- MFA
- Firewalls
- IDS/IPS
- Endpoint Protection
- Access Controls

If one layer fails, other layers continue providing protection.

---

## 4. Separation of Duties

Critical responsibilities should be divided among multiple individuals.

This reduces:

- Fraud
- Abuse of privileges
- Unauthorized activities

### Example

The person approving a payment should not be the same person processing it.

---

## 5. Keep Security Simple

Security solutions should be effective and manageable.

Overly complex security implementations often increase the likelihood of configuration mistakes.

---

## 6. Fix Security Issues Correctly

Security vulnerabilities should be fully resolved rather than temporarily patched.

The root cause should always be identified and addressed.

---

# Security Audits

A Security Audit is a formal review of an organization's security controls, policies, and procedures.

The objective is to evaluate whether security measures are functioning as intended.

---

# Internal Security Audits

Internal audits are conducted by members of the organization.

### Purpose

- Identify organizational risks
- Review security controls
- Improve security posture
- Correct compliance issues

---

# Common Elements of an Internal Audit

## 1. Establish Scope and Goals

Determine what systems, departments, or processes will be evaluated.

---

## 2. Conduct Risk Assessment

Identify:

- Threats
- Vulnerabilities
- Potential impacts

Risk assessments help determine what security measures should be implemented.

---

## 3. Perform Control Assessment

Evaluate whether existing controls are functioning effectively.

### Types of Security Controls

#### Administrative Controls

Policies, standards, procedures, and training.

#### Technical Controls

Technology-based safeguards such as:

- Firewalls
- IDS/IPS
- MFA
- Antivirus Solutions

#### Physical Controls

Measures that protect physical assets.

Examples:

- Security Guards
- CCTV Cameras
- Locks
- Access Cards

---

## 4. Assess Compliance

Verify that the organization follows applicable regulations, laws, and internal security requirements.

---

## 5. Communicate Results

Audit findings should be documented and communicated to stakeholders.

A good audit report should:

- Summarize scope and objectives
- Identify risks
- Highlight compliance gaps
- Prioritize findings
- Recommend improvements

---

# Why Internal Audits Matter

Internal audits help organizations:

- Discover security gaps
- Improve controls
- Reduce risk
- Strengthen compliance
- Improve overall security posture

They are one of the most effective ways to identify weaknesses before attackers do.

---

# Key Takeaways

- Security frameworks provide structured approaches to managing cybersecurity risks.
- Authentication verifies identity, while authorization determines permissions.
- Encryption protects sensitive information from unauthorized access.
- The CIA Triad forms the foundation of information security.
- NIST CSF consists of five core functions: Identify, Protect, Detect, Respond, and Recover.
- Defense in Depth relies on multiple layers of security controls.
- Security audits help organizations identify weaknesses and improve security posture.
- Strong cybersecurity depends on people, processes, and technology working together.
