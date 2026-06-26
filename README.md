<div align="center">

# 🛡️ Wazuh XDR, SOAR & Threat Intelligence Lab

### Threat Intelligence & Threat Hunting Project

Wazuh SIEM • XDR Detection • SOAR Automation • Threat Intelligence Integration

![Wazuh](https://img.shields.io/badge/Wazuh-SIEM-blue)
![XDR](https://img.shields.io/badge/XDR-Detection-red)
![SOAR](https://img.shields.io/badge/Shuffle-SOAR-purple)
![Threat Intelligence](https://img.shields.io/badge/Threat-Intelligence-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

</div>

---

# Overview

This project demonstrates the implementation of a Security Operations Center (SOC) environment using Wazuh SIEM, XDR detection capabilities, Shuffle SOAR automation, Active Response, and Threat Intelligence integrations.

The environment was configured to collect and analyze security events from Windows Server 2022, Bodhi Linux, and pfSense Firewall systems. Security incidents were detected using custom Wazuh rules, automatically responded to using Active Response and Shuffle playbooks, and enriched using external Threat Intelligence platforms.

The project simulates real-world SOC operations including threat detection, incident investigation, containment, automated response, and threat intelligence enrichment.

---

# Table of Contents

- Overview
- Lab Environment
- Technologies Used
- SOC Architecture
- Security Operations Workflow
- Task 1 – Wazuh Configuration & Event Validation
- Task 2 – XDR Detection & Automated Response
- Task 3 – SOAR Automation with Shuffle
- Task 4 – Threat Intelligence Integration
- Threat Intelligence Sources
- Key Results
- Skills Demonstrated
- Screenshots
- Author

---

# Lab Environment

## Systems

| System | Purpose |
|----------|----------|
| Wazuh Server | SIEM Platform |
| Windows Server 2022 | Endpoint Monitoring |
| Bodhi Linux | Linux Endpoint |
| Kali Linux | Attack Simulation |
| pfSense Firewall | Firewall & Syslog Source |
| Shuffle | SOAR Platform |

---

# Technologies Used

## Security Monitoring

- Wazuh SIEM
- Custom Wazuh Rules
- Active Response

## Operating Systems

- Windows Server 2022
- Bodhi Linux
- Kali Linux

## Network Security

- pfSense Firewall
- Syslog Monitoring

## SOAR

- Shuffle
- Python Automation

## Threat Intelligence

- VirusTotal
- AbuseIPDB
- AlienVault OTX

## Scripting & Automation

- PowerShell
- Bash
- Python

---

# SOC Architecture

```text
┌─────────────────────────────────────────┐
│               Endpoints                 │
│  Windows Server 2022 • Bodhi Linux      │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│          Network Security Layer         │
│            pfSense Firewall             │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│            Log Collection               │
│     Windows • Linux • Firewall Logs     │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│              Wazuh SIEM                 │
│  Correlation • Detection • Monitoring   │
└─────────────────────────────────────────┘
                    │
     ┌──────────────┼──────────────┐
     ▼              ▼              ▼
┌─────────┐  ┌─────────────┐  ┌───────────┐
│   XDR   │  │Threat Intel │  │Active Resp│
└─────────┘  └─────────────┘  └───────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│             Shuffle SOAR                │
│ Account Disable • Notifications         │
│ Automated Incident Response             │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│ Detection → Analysis → Response         │
│ Continuous Security Monitoring          │
└─────────────────────────────────────────┘
```

---

# Security Operations Workflow

```text
Data Collection
      │
      ▼
Detection
      │
      ▼
Analysis
      │
      ▼
Response
      │
      ▼
Continuous Monitoring
```

---

# Task 1 – Wazuh Configuration & Event Validation

## Objective

Deploy and configure Wazuh SIEM for centralized log collection and monitoring.

---

## Integrated Systems

### Windows Server 2022

- Wazuh Agent Installed
- Security Events Monitored
- Microsoft Defender Events Collected

### Bodhi Linux

- Wazuh Agent Installed
- Authentication Logs Collected
- System Activity Monitored

### pfSense Firewall

- Syslog Forwarding Enabled
- Firewall Logs Collected
- Network Events Forwarded to Wazuh

---

## Validation Results

| Validation Item | Status |
|----------------|---------|
| Windows Logs Collection | ✅ |
| Linux Logs Collection | ✅ |
| pfSense Log Collection | ✅ |
| Event Correlation | ✅ |
| Centralized Monitoring | ✅ |

---

# Task 2 – XDR Detection & Automated Response

## Objective

Develop custom detection rules and automated responses to identify and contain suspicious activities.

---

## Detection Engineering

### Brute Force Detection

Custom rules were created to detect repeated authentication failures.

### Privilege Escalation Detection

Custom rules monitored changes to privileged groups and administrative accounts.

### Malware Detection

Microsoft Defender and Wazuh generated alerts for suspicious files and malicious activity.

---

## Active Response

Automated actions included:

- Blocking malicious IP addresses
- Disabling suspicious user accounts
- Removing detected threats
- Generating high-priority alerts

---

# Task 3 – SOAR Automation with Shuffle

## Objective

Integrate Wazuh with Shuffle SOAR to automate incident response workflows.

---

## Detection Rule

```text
Rule ID: 100601
```

Description:

```text
Privilege Escalation – Administrators Group Modified
```

---

## Playbook Workflow

```text
Wazuh Alert
      │
      ▼
Shuffle Webhook
      │
      ▼
Condition Check
      │
      ▼
Python Response Action
      │
      ▼
Disable Suspicious Account
      │
      ▼
Email Notification
```

---

## Automated Response

The playbook automatically:

- Receives Wazuh alerts
- Evaluates alert conditions
- Executes a Python response script
- Disables suspicious user accounts
- Sends email notifications
- Logs response actions

---

## Validation

A test account was added to the Windows Administrators group.

The alert triggered:

```text
Rule ID 100601
```

Shuffle successfully:

- Detected the event
- Executed the response workflow
- Disabled the suspicious account
- Sent notification alerts

---

# Task 4 – Threat Intelligence Integration

## Objective

Enhance detection capabilities using external Threat Intelligence feeds.

---

## VirusTotal Integration

### Purpose

File reputation analysis and malware validation.

### Rule IDs

```text
87105
100092
100093
```

### Test Scenario

- EICAR Test File Downloaded
- Wazuh FIM Detected File Creation
- VirusTotal Query Executed

### Result

- File Identified as Malicious
- Threat Detected
- Active Response Triggered
- File Removed Automatically

---

## AbuseIPDB Integration

### Purpose

IP Reputation Enrichment

### Rule IDs

```text
100002
100003
100004
```

### Test Scenario

Failed SSH authentication events were generated using a public IP address.

### Result

- Suspicious IP Detected
- AbuseIPDB Lookup Executed
- Reputation Data Returned
- Alert Enriched with Confidence Score

---

## AlienVault OTX Integration

### Purpose

IOC and Domain Reputation Analysis

### Rule IDs

```text
100220
100300
100301
```

### Test Scenario

A suspicious domain indicator was generated.

```text
shmrwqwmrn.biz
```

### Result

- Domain Detection Triggered
- OTX Lookup Executed
- Threat Intelligence Match Returned
- High Severity Alert Generated

---

# Threat Intelligence Sources

| Source | Purpose |
|----------|----------|
| VirusTotal | File Reputation Analysis |
| AbuseIPDB | IP Reputation Analysis |
| AlienVault OTX | IOC and Domain Intelligence |

---

# SOC Roles

| Role | Responsibility |
|---------|---------|
| SOC Analyst L1 | Alert Monitoring and Initial Triage |
| SOC Analyst L2 | Incident Investigation and Correlation |
| SOC Analyst L3 | Advanced Threat Hunting and Detection Engineering |
| Threat Hunter | Proactive Threat Hunting and IOC Analysis |
| Incident Responder | Containment and Remediation |
| Threat Intelligence Analyst | Threat Intelligence Management |
| SOC Manager | SOC Oversight and Reporting |

---

# Key Results

| Capability | Status |
|------------|---------|
| Wazuh Deployment | ✅ |
| Windows Integration | ✅ |
| Linux Integration | ✅ |
| pfSense Integration | ✅ |
| Custom Detection Rules | ✅ |
| XDR Detection | ✅ |
| Active Response | ✅ |
| Shuffle SOAR Automation | ✅ |
| VirusTotal Integration | ✅ |
| AbuseIPDB Integration | ✅ |
| AlienVault OTX Integration | ✅ |
| Threat Intelligence Enrichment | ✅ |

---

# Skills Demonstrated

## SIEM

- Wazuh Deployment
- Log Analysis
- Event Correlation
- Detection Engineering
- Alert Triage

## XDR

- Endpoint Monitoring
- Threat Detection
- Active Response
- Incident Investigation

## SOAR

- Shuffle Automation
- Webhook Integration
- Automated Response Playbooks
- Incident Workflow Automation

## Threat Intelligence

- VirusTotal Integration
- AbuseIPDB Integration
- AlienVault OTX Integration
- IOC Analysis
- Threat Enrichment

## Security Operations

- Threat Hunting
- Incident Response
- Security Monitoring
- Detection Engineering
- SOC Operations

---

# Screenshots

```text
screenshots/
│
├── soc-architecture.png
├── wazuh-dashboard.png
├── windows-agent.png
├── bodhi-agent.png
├── pfsense-syslog.png
├── event-validation.png
├── privilege-escalation-alert.png
├── shuffle-playbook.png
├── shuffle-response.png
├── account-disabled.png
├── virustotal-detection.png
├── abuseipdb-enrichment.png
├── otx-match.png
└── threat-intelligence-dashboard.png
```

---

# Author

Threat Intelligence & Threat Hunting Project

Implemented using Wazuh SIEM, XDR Detection, Active Response, Shuffle SOAR, VirusTotal, AbuseIPDB, AlienVault OTX, Windows Server 2022, Bodhi Linux, Kali Linux, and pfSense Firewall.
