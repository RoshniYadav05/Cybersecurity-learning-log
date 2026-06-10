# Logs, SIEM and Incident Response

## Overview

In cybersecurity, logs are one of the most important sources of information. Security teams use logs to monitor systems, investigate suspicious activities, detect attacks, and respond to security incidents.

A **log** is a record of events that occur within an organization's systems, applications, and networks.

---

# What are Logs?

Logs provide detailed information about activities occurring within a system or network.

### Examples of Logged Events

* User logins
* Failed login attempts
* File access events
* Network connections
* System errors
* Security alerts

By monitoring logs, security teams can identify vulnerabilities, suspicious behavior, and potential security breaches.

---

# Common Log Sources

## 1. Firewall Logs

Firewall logs record incoming and outgoing network traffic.

These logs contain information about:

* Allowed connections
* Blocked connections
* Source IP addresses
* Destination IP addresses
* Ports and protocols used

### Example

```text
192.168.1.10 → 8.8.8.8 : Allowed
192.168.1.15 → 10.0.0.5 : Blocked
```

Firewall logs help security teams identify unauthorized access attempts and suspicious network activity.

---

## 2. Network Logs

Network logs record activities occurring across network devices and systems.

They provide information about:

* Devices joining the network
* Devices leaving the network
* Communication between systems
* Network services being accessed

### Example

```text
Laptop-A connected to Wi-Fi
Server-01 communicated with Database-01
```

Network logs help analysts understand network behavior and identify unusual communications.

---

## 3. Server Logs

Server logs record events related to servers and hosted services.

These may include:

* Website activity
* Email services
* File server access
* User authentication attempts

### Example

```text
User: roshni
Action: Login
Status: Success
Time: 10:30 AM
```

Server logs are useful when investigating unauthorized access or suspicious account activity.

---

# Why Logs are Important

Logs help security teams:

* Detect cyber attacks
* Identify vulnerabilities
* Investigate incidents
* Monitor system activity
* Maintain compliance requirements

Without logs, it becomes extremely difficult to determine what happened during a security incident.

---

# What is SIEM?

**SIEM (Security Information and Event Management)** is a security solution that collects, stores, analyzes, and monitors log data from multiple sources within an organization.

A SIEM platform provides centralized visibility into security events occurring across an organization's infrastructure.

---

# Features of SIEM

## Centralized Log Collection

SIEM gathers logs from:

* Firewalls
* Servers
* Endpoints
* Applications
* Network devices

All logs are stored in a centralized location for easier monitoring and investigation.

---

## Real-Time Monitoring

SIEM continuously monitors incoming logs and events.

This allows security teams to identify suspicious activities as they occur.

### Example

```text
500 failed login attempts
within 5 minutes
```

The SIEM immediately generates an alert.

---

## Event Correlation

SIEM correlates events from multiple log sources to identify patterns that may indicate an attack.

### Example

A SIEM may correlate:

* Multiple failed logins
* Login from an unusual location
* Login outside business hours

and generate a security alert.

---

## Automated Alerts

SIEM automatically notifies security analysts when suspicious activity is detected.

### Example

```text
Alert:
Possible Brute Force Attack Detected
```

---

# SIEM Dashboards

SIEM tools provide dashboards that display security information visually.

Dashboards may contain:

* Charts
* Graphs
* Tables
* Security Alerts
* Performance Metrics

This helps analysts quickly understand the security posture of the organization.

---

# SIEM Dashboard Example

Imagine a security analyst receives an alert regarding suspicious login activity.

Using the SIEM dashboard, the analyst discovers:

* More than 500 login attempts occurred within 5 minutes.
* Login attempts originated from unusual geographic locations.
* Activity occurred outside the user's normal working hours.

By reviewing the dashboard, the analyst can quickly determine that the activity is suspicious and requires investigation.

---

# Metrics

Metrics are measurable values used to evaluate system and security performance.

### Examples

* Response Time
* Availability
* Failure Rate
* Detection Time
* Incident Resolution Time

SIEM dashboards can be customized to display different metrics for different teams and stakeholders.

---

# Types of SIEM Solutions

## 1. Self-Hosted SIEM

Self-hosted SIEM solutions are installed and maintained by the organization's own IT or Security Team.

### Characteristics

* Full control over infrastructure
* Data remains within the organization
* Requires maintenance and administration

### Best For

Organizations that need complete control over sensitive data.

---

## 2. Cloud-Hosted SIEM

Cloud-hosted SIEM solutions are managed by a third-party provider.

### Characteristics

* Minimal infrastructure management
* Faster deployment
* Easier scalability

### Best For

Organizations that do not want to maintain their own infrastructure.

---

## 3. Hybrid SIEM

A Hybrid SIEM combines both self-hosted and cloud-hosted approaches.

### Benefits

* Cloud scalability
* Greater control over sensitive data
* Flexible deployment options

---

# Popular SIEM Tools

## Splunk

Splunk is a data analytics platform used for collecting, searching, monitoring, and analyzing machine-generated data.

### Splunk Enterprise

Splunk Enterprise is a self-hosted SIEM solution that helps organizations:

* Collect logs
* Analyze events
* Detect threats
* Generate real-time alerts

### Splunk Cloud

Splunk Cloud is a cloud-hosted version of Splunk.

It allows organizations to:

* Collect logs
* Monitor activity
* Search events
* Analyze security data

without maintaining their own infrastructure.

---

## Chronicle

Chronicle is a cloud-native security analytics platform.

### Features

* Log collection
* Security monitoring
* Data analysis
* Threat investigation

Cloud-native platforms are designed specifically to take advantage of cloud computing capabilities such as:

* Scalability
* Flexibility
* High Availability

---

# What is a Playbook?

A **Playbook** is a documented set of procedures that defines how a security team should respond to specific situations.

It provides step-by-step guidance for handling security events and incidents.

---

# Why Playbooks are Important

Playbooks help organizations:

* Respond consistently
* Reduce response time
* Improve efficiency
* Reduce human errors
* Follow standardized procedures

Regardless of who handles the incident, the response process remains consistent.

---

# Types of Playbooks

Common playbooks include:

* Incident Response Playbooks
* Security Alert Playbooks
* Team-Specific Playbooks
* Product-Specific Playbooks

---

# Incident Response

Incident Response is the process of identifying, containing, investigating, and recovering from a security incident.

### Primary Goals

* Minimize damage
* Reduce business impact
* Restore operations quickly

---

# Incident Response Playbook

An Incident Response Playbook provides a structured approach for handling security incidents from beginning to end.

---

# Incident Response Lifecycle

## 1. Preparation

Preparation is the foundation of a successful incident response program.

Organizations should:

* Create security policies
* Develop response procedures
* Define communication plans
* Train employees
* Conduct security awareness programs
* Prepare response teams

The better the preparation, the faster and more effective the incident response process will be.

---

## 2. Identification

The organization identifies whether a security incident has occurred.

Activities include:

* Reviewing alerts
* Analyzing logs
* Validating suspicious activity
* Determining incident scope

---

## 3. Containment

The goal is to limit the damage caused by the incident.

Examples:

* Isolating infected systems
* Blocking malicious IP addresses
* Disabling compromised accounts

---

## 4. Eradication

The root cause of the incident is removed.

Examples:

* Removing malware
* Closing vulnerabilities
* Deleting malicious files
* Applying security patches

---

## 5. Recovery

Systems are restored to normal operations.

Activities include:

* Restoring backups
* Monitoring systems
* Returning services to production

---

## 6. Lessons Learned

After the incident is resolved, teams review what happened.

Objectives:

* Identify gaps in security controls
* Improve response procedures
* Update playbooks
* Prevent future incidents

---

# Key Takeaways

* Logs are records of events occurring in systems and networks.
* Common log sources include Firewall Logs, Network Logs, and Server Logs.
* SIEM centralizes and analyzes log data.
* SIEM provides real-time monitoring, event correlation, dashboards, and automated alerts.
* Splunk and Chronicle are popular SIEM platforms.
* Playbooks provide standardized incident response procedures.
* Incident Response helps organizations detect, contain, eradicate, and recover from security incidents.
* Preparation is the first and most important phase of Incident Response.
* Effective log monitoring is a critical skill for SOC Analysts and Blue Team professionals.
