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

![SOC Architecture](screenshots/soc-architecture.png)

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

## Windows Server 2022 Integration

- Wazuh Agent Installed
- Security Events Monitored
- Microsoft Defender Events Collected

![Windows Agent](screenshots/windows-agent.png)

---

## Bodhi Linux Integration

- Wazuh Agent Installed
- Authentication Logs Collected
- System Activity Monitored

![Bodhi Agent](screenshots/bodhi-agent.png)

---

## pfSense Firewall Integration

- Syslog Forwarding Enabled
- Firewall Logs Collected
- Network Events Forwarded to Wazuh

![pfSense Integration](screenshots/pfsense-syslog.png)

---

## Wazuh Dashboard

![Wazuh Dashboard](screenshots/wazuh-dashboard.png)

---

# Task 2 – XDR Detection & Automated Response

## Privilege Escalation Detection

Custom Wazuh rule detected modifications to the Windows Administrators group.

**Rule ID:** `100601`

![Privilege Escalation Alert](screenshots/privilege-escalation-alert.png)

---

## Active Response Validation

The suspicious account was automatically disabled after detection.

![Account Disabled](screenshots/account-disabled.png)

---

# Task 3 – SOAR Automation with Shuffle

## Shuffle Playbook

The SOAR workflow receives alerts from Wazuh and performs automated response actions.

![Shuffle Playbook](screenshots/shuffle-playbook.png)

---

## Workflow Execution

Successful execution of the automated response workflow.

![Shuffle Execution](screenshots/shuffle-run-history.png)

---

# Task 4 – Threat Intelligence Integration

## VirusTotal Integration

### Purpose

File reputation analysis and malware validation.

### Rule IDs

- 87105
- 100092

### Validation

- EICAR test file detected
- VirusTotal lookup performed
- Threat removed automatically

![VirusTotal Detection](screenshots/virustotal-detection.png)

---

## AbuseIPDB Integration

### Purpose

IP reputation enrichment.

### Rule ID

- 100004

### Validation

- Suspicious IP detected
- Reputation lookup completed
- Confidence score returned

![AbuseIPDB Enrichment](screenshots/abuseipdb-enrichment.png)

---

## AlienVault OTX Integration

### Purpose

IOC and domain reputation analysis.

### Rule IDs

- 100220
- 100300
- 100301

### Validation

- Suspicious domain detected
- OTX lookup completed
- Threat intelligence match identified

![OTX Match](screenshots/otx-match.png)

---

# Threat Intelligence Sources

| Source | Purpose |
|----------|----------|
| VirusTotal | File Reputation Analysis |
| AbuseIPDB | IP Reputation Analysis |
| AlienVault OTX | IOC & Domain Intelligence |

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

---

# Skills Demonstrated

## SIEM

- Wazuh Deployment
- Log Analysis
- Event Correlation
- Detection Engineering

## XDR

- Threat Detection
- Endpoint Monitoring
- Active Response

## SOAR

- Shuffle Automation
- Webhook Integration
- Automated Incident Response

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
- Alert Triage

---

# Screenshots

```text
screenshots/
├── soc-architecture.png
├── wazuh-dashboard.png
├── windows-agent.png
├── bodhi-agent.png
├── pfsense-syslog.png
├── privilege-escalation-alert.png
├── account-disabled.png
├── shuffle-playbook.png
├── shuffle-run-history.png
├── virustotal-detection.png
├── abuseipdb-enrichment.png
├── otx-match.png
└── project-summary.png
```

---

# Author

Threat Intelligence & Threat Hunting Project using:

- Wazuh SIEM
- Active Response
- Shuffle SOAR
- VirusTotal
- AbuseIPDB
- AlienVault OTX
- Windows Server 2022
- Bodhi Linux
- Kali Linux
- pfSense Firewall
