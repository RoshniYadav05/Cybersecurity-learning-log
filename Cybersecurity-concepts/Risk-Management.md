# Threats, Vulnerabilities, Risks, Asset Classification & NIST RMF

## Overview

This document covers some of the most important cybersecurity concepts: Threats, Vulnerabilities, Risks, Asset Classification, Ransomware, and the NIST Risk Management Framework (RMF).

Understanding the relationship between these concepts is essential for identifying and reducing security risks within an organization.

---

# Threat

A threat is any event, person, action, or circumstance that can negatively impact an organization's assets, systems, or data.

Threats can be intentional or accidental.

## Examples of Threats

* Hackers
* Malware
* Ransomware
* Insider Threats
* Phishing Attacks
* Social Engineering
* Fire
* Flood
* Hardware Failure

### Social Engineering

Social engineering is a technique used by attackers to manipulate people into revealing sensitive information or performing actions that compromise security.

Example:

A fake IT support employee calls a user and asks for login credentials.

---

# Phishing

Phishing is one of the most common forms of social engineering.

Attackers send fake emails, messages, or websites that appear legitimate in order to steal sensitive information.

## Goal of Phishing

* Steal usernames and passwords
* Obtain banking information
* Gain unauthorized access
* Deliver malware

### Example

```text
Your account has been suspended.

Click here to verify your account.
```

The victim clicks the link and unknowingly provides credentials to the attacker.

---

# Vulnerability

A vulnerability is a weakness that can be exploited by a threat.

Without a vulnerability, a threat usually cannot cause damage.

## Examples

* Weak passwords
* Outdated software
* Missing security patches
* Misconfigured firewalls
* Open network ports
* Unprotected confidential data

### Important Point

A threat and a vulnerability must both exist for risk to occur.

---

# Risk

Risk is the possibility that a threat will exploit a vulnerability and cause damage to an organization's assets.

## Simple Formula

```text
Risk = Threat + Vulnerability
```

### Example

Threat:
Hacker

Vulnerability:
Weak Password

Risk:
Account Compromise

---

# Difference Between Threat, Vulnerability and Risk

| Term          | Meaning                        |
| ------------- | ------------------------------ |
| Vulnerability | A weakness                     |
| Threat        | A potential danger             |
| Risk          | The chance of damage occurring |

## House Example

### Vulnerability

Broken Door Lock

### Threat

Thief

### Risk

The thief may enter the house and steal valuables.

---

# Asset Classification

Organizations classify assets based on their importance and potential impact if compromised.

---

## Low Risk Assets

Information that is intended for public access and would cause little or no damage if exposed.

### Examples

* Public website content
* Marketing materials
* Public announcements

---

## Medium Risk Assets

Information that is not public and could cause moderate damage if exposed.

### Examples

* Internal reports
* Business plans
* Operational procedures

---

## High Risk Assets

Information protected by regulations, laws, or business requirements.

Compromise of these assets can significantly impact finances, reputation, and operations.

### Examples

* PII (Personally Identifiable Information)
* SPII (Sensitive Personally Identifiable Information)
* Financial Records
* Intellectual Property
* Customer Databases

---

# Ransomware

Ransomware is a type of malware that encrypts an organization's files or systems and demands payment for restoring access.

## Typical Ransomware Process

```text
Infection
    ↓
Encryption
    ↓
Data Locked
    ↓
Ransom Demand
```

## Impacts of Ransomware

* Financial Loss
* Reputation Damage
* Business Disruption
* Data Loss
* Operational Downtime

## Prevention Methods

* Regular Backups
* Multi-Factor Authentication (MFA)
* Security Awareness Training
* Patch Management
* Endpoint Protection Solutions

---

# NIST Risk Management Framework (RMF)

The NIST Risk Management Framework provides a structured process for managing cybersecurity risks.

---

## 1. Prepare

Establish activities necessary to manage security and privacy risks.

### Goal

Create a foundation for effective risk management.

---

## 2. Categorize

Identify and classify systems, assets, and data according to their importance and impact.

### Goal

Understand what needs protection.

---

## 3. Select

Choose appropriate security controls based on organizational requirements and risk levels.

### Examples

* Access Controls
* Encryption
* Logging
* Monitoring Controls

---

## 4. Implement

Deploy and configure the selected security controls.

### Goal

Put security protections into operation.

---

## 5. Assess

Verify that implemented controls are functioning correctly.

### Activities

* Audits
* Security Reviews
* Vulnerability Assessments
* Penetration Testing

---

## 6. Authorize

Management reviews the risks and formally approves system operation.

### Goal

Accept and manage remaining risks.

---

## 7. Monitor

Continuously monitor systems and controls to identify new risks and security issues.

### Activities

* Log Monitoring
* Threat Detection
* Vulnerability Management
* Continuous Security Assessment

---

# Key Takeaways

* A Threat is a potential danger.
* A Vulnerability is a weakness.
* Risk exists when a threat can exploit a vulnerability.
* Asset Classification helps prioritize protection efforts.
* Ransomware is one of the most damaging malware threats.
* NIST RMF provides a structured approach for managing cybersecurity risks.
* Continuous monitoring is essential for maintaining security.
