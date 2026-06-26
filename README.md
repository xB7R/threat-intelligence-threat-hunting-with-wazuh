<div align="center">

# 🛡️ Wazuh XDR, SOAR & Threat Intelligence Lab

### Threat Intelligence and Threat Hunting Project

Wazuh SIEM • XDR Detection • Shuffle SOAR • Threat Intelligence Integration

![Wazuh](https://img.shields.io/badge/Wazuh-SIEM-blue)
![XDR](https://img.shields.io/badge/XDR-Detection-red)
![SOAR](https://img.shields.io/badge/Shuffle-SOAR-purple)
![Threat Intelligence](https://img.shields.io/badge/Threat-Intelligence-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

</div>

---

# Overview

This project demonstrates the implementation of a Security Operations Center (SOC) environment using Wazuh SIEM, XDR detection capabilities, Shuffle SOAR automation, and Threat Intelligence integrations.

The environment was configured to collect logs from Windows Server 2022, Bodhi Linux, and IDS/Firewall systems. Security events were detected using custom Wazuh rules, automatically responded to using Active Response and Shuffle playbooks, and enriched using external Threat Intelligence sources.

---

# Lab Environment

## Systems

| System | Purpose |
|----------|----------|
| Wazuh Server | SIEM Platform |
| Windows Server 2022 | Endpoint Monitoring |
| Bodhi Linux | Linux Endpoint |
| Kali Linux | Attack Simulation |
| Shuffle | SOAR Platform |
| Suricata IDS | Network Detection |

---

## Technologies Used

- Wazuh SIEM
- OpenSearch
- Filebeat
- Windows Server 2022
- Bodhi Linux
- Kali Linux
- Suricata IDS
- Shuffle SOAR
- VirusTotal
- AbuseIPDB
- AlienVault OTX
- Active Response
- PowerShell
- Bash Scripting

---

# Architecture

```text
Kali Linux
     │
     ▼
Windows Server / Bodhi Linux
     │
     ▼
Suricata IDS
     │
     ▼
Wazuh Manager
     │
 ┌───┼───────────────┐
 ▼   ▼               ▼
XDR Threat Intel   Active Response
     │
     ▼
Shuffle SOAR
     │
     ▼
Automated Containment
```

---

# Task 1 – Wazuh Configuration & Event Validation

## Objectives

- Deploy Wazuh SIEM
- Integrate Windows Server 2022
- Integrate Bodhi Linux
- Integrate Suricata IDS
- Validate centralized log collection

---

## Integrated Log Sources

### Windows Server 2022

- Wazuh Agent Installed
- Security Events Collected
- Event Logs Forwarded

### Bodhi Linux

- Wazuh Agent Installed
- Syslog Collection Enabled
- Authentication Events Monitored

### Suricata IDS

- Syslog Forwarding Enabled
- Alerts Collected by Wazuh

---

## Validation Results

| Validation | Status |
|------------|---------|
| Windows Logs | ✅ |
| Linux Logs | ✅ |
| Suricata Alerts | ✅ |
| Event Collection | ✅ |
| Kali Attack Visibility | ✅ |

---

# Task 2 – XDR Detection & Automated Response

## Attack 1 – SMB Brute Force

### Detection Rule

Rule ID:

```text
100100
```

Description:

```text
Custom: SMB Brute Force Detected
```

### Attack Simulation

Kali Linux generated multiple failed SMB login attempts against Windows Server 2022.

### Automated Response

```text
block-ip.sh
```

### Result

- Attacker IP detected
- IP automatically blocked
- Active Response executed successfully

---

## Attack 2 – Linux Privilege Escalation

### Detection Rules

```text
100101
100102
```

### Attack Simulation

A new Linux user was created and added to the sudo group.

### Automated Response

```text
disable-account
```

### Result

- User creation detected
- Privilege escalation detected
- Account automatically locked

---

## Attack 3 – Malware Detection

### Detection Rule

```text
100150
```

Description:

```text
XDR: Malware detected on Windows endpoint by Microsoft Defender
```

### Attack Simulation

EICAR malware test file executed on Windows Server.

### Automated Response

Microsoft Defender remediation.

### Result

- Malware detected
- Alert generated
- File quarantined automatically

---

# Task 3 – SOAR Automation Using Shuffle

## Objective

Implement Security Orchestration, Automation and Response (SOAR) using Shuffle.

---

## Detection Rule

Rule ID:

```text
100601
```

Description:

```text
Custom: Privilege Escalation - Administrators Group Modified
```

---

## Workflow

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

## Automated Actions

### User Account Disablement

Shuffle receives alerts from Wazuh and automatically disables suspicious user accounts through SSH.

### Email Notification

SOC analysts receive automatic incident notifications containing:

- Rule ID
- Severity
- Agent Name
- Username
- Action Taken

---

## Validation

### Attack Simulation

```powershell
net user SecOpsTest2026 P@ssw0rd123! /add

net localgroup Administrators SecOpsTest2026 /add
```

### Result

```powershell
Get-LocalUser -Name "SecOpsTest2026"
```

Account Status:

```text
Disabled = False
```

After SOAR Response:

```text
Disabled = True
```

✅ Automated containment successful

---

# Task 4 – Threat Intelligence Integration

## VirusTotal Integration

### Purpose

File reputation analysis.

### Integration

Wazuh FIM sends file hashes to VirusTotal.

### Rule IDs

```text
87105
100092
100093
```

### Test

EICAR Test File

### Result

- VirusTotal detected malicious file
- Wazuh generated alert
- remove-threat.exe executed
- File removed automatically

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

### Test

```text
136.228.161.66
```

### Result

- SSH Authentication Failure Detected
- AbuseIPDB Lookup Performed
- Confidence Score Returned
- Alert Enriched Successfully

---

## AlienVault OTX Integration

### Purpose

Threat Intelligence Domain Lookup

### Rule IDs

```text
100220
100300
100301
```

### Test Domain

```text
shmrwqwmrn.biz
```

### Result

- Domain Detected
- OTX Lookup Executed
- Threat Match Returned
- High Severity Alert Generated

---

# Threat Intelligence Sources

## VirusTotal

Provides:

- File Hash Reputation
- URL Analysis
- Domain Intelligence
- Malware Analysis
- MITRE ATT&CK Mapping

---

## AbuseIPDB

Provides:

- IP Reputation
- Abuse Confidence Scores
- Historical Reports
- Geolocation Data

---

## AlienVault OTX

Provides:

- Threat Indicators
- Malicious Domains
- Malicious IPs
- IOC Enrichment
- Threat Pulses

---

# Key Results

| Capability | Status |
|------------|---------|
| Wazuh Deployment | ✅ |
| Windows Integration | ✅ |
| Linux Integration | ✅ |
| Suricata Integration | ✅ |
| Event Validation | ✅ |
| XDR Detection | ✅ |
| Active Response | ✅ |
| Shuffle SOAR | ✅ |
| VirusTotal Integration | ✅ |
| AbuseIPDB Integration | ✅ |
| AlienVault OTX Integration | ✅ |

---

# Skills Demonstrated

## SIEM

- Wazuh Deployment
- Log Management
- Event Correlation
- Detection Engineering

## XDR

- Threat Detection
- Endpoint Monitoring
- Automated Response

## SOAR

- Shuffle Playbooks
- Webhooks
- Incident Automation

## Threat Intelligence

- VirusTotal
- AbuseIPDB
- AlienVault OTX
- IOC Analysis

## Security Operations

- Incident Detection
- Alert Triage
- Incident Response
- Threat Hunting

---

# Screenshots

Add screenshots for:

```text
screenshots/
│
├── wazuh-dashboard.png
├── windows-agent.png
├── bodhi-agent.png
├── suricata-integration.png
├── smb-bruteforce-alert.png
├── block-ip-response.png
├── privilege-escalation-alert.png
├── disable-account-response.png
├── malware-detection.png
├── defender-remediation.png
├── shuffle-playbook.png
├── shuffle-email-alert.png
├── virustotal-detection.png
├── abuseipdb-enrichment.png
└── otx-match.png
```

---

# Author

Cybersecurity Project – Threat Intelligence & Threat Hunting using Wazuh, XDR, SOAR and Threat Intelligence Integration.
