# SOC-Analyst-Home-Lab
Hands-On SIEM, Threat Hunting, Detection, and Incident Response Project using Wazuh, Sysmon, & AWS
## Overview
In this project I did my best to simulate an encompassing SOC Analyst workflow. Highlighted by common SOC level tasks including, SIEM deployment, log ingestion, MITRE ATT&CK detection mapping, threat hunting, simulated attacks, and incident response playbooks. The goal of this lab was to replicate real world training and demonstrate hands on and technical skills.  

## Lab Architecture 
- Ubuntu 22.04, AWS EC2 - Acted as Wazuh server, hosting Wazuh Indexer, Manager, and Dashboard
- Windows Endpoint, AWS EC2 - Wazuh agent, connected to server, Sysmon installed
- Linux (Ubuntu) Endpoint, AWS EC2 - Wazuh agent, connected to server,
- Linux (Kali) Endpoint, Local VM - Used to help simulate attacks
- Wazuh SIEM - Collected, parsed, analyzed logs, and generated reports
- Log Sources - Sysmon, Windows Event Logs, Linux auth logs, Wazuh agent events

## What was Implemented
### 1. Wazuh SIEM Deployment
- Deployed Wazuh Manger, Indexer, and Dashboard within AWS EC2 Instance
- Configured inbound rules, security groups, certificates, and cluster readiness
- Verified successful dashboard operation and indexing

### 2. Endpoint Integration 
Windows Endpoint
- AWS EC2 Instance
- Used RDP to manipulate and use endpoint throughout lab
- Installed Wazuh Agent
- Installed Sysmon for more detailed and intricate logs
- Enabled crucial logs
  - Process creation
  - Network connections
  - Registry modifications
  - File events

Ubuntu Linux Endpoint
- Installed Wazuh Agent
- Enabled:
  - Authentication logs
  - sudo activity logs
  - Syslog forwarding

Kali Linux Endpoint
- Local VM
- Used it's tools like NMap and others to simulate scans and attacks

### 3. Simulated Cyber Attacks
Conducted controlled, safe attacks from Kali and endpoints themselves, some of the attacks conducted include:
- Failed login brute force attempts
- File modification / creation events
- PowerShell execution tests
- Suspicious network activity
- Persistence technique tests

Captured logs, alerts, and dashbaord for each, more details can be seen in the screenshots section. 

### 4. MITRE ATT&CK Detection & Reporting
- Triggered alerts and validated MITRE technique mappings
- Filtered alerts by:
  - rule.mitre.id
  - Specific ATT&CK techniques, ex: T1059 - Command and Scriping Interpreter, T1105 - Ingress Tool Transfer
  - Generated a number of reports from dashboard:
    - MITRE Heat Map
    - ATT&CK Matrix Report
    - Alert distribution dashbaord
   
### 5. Threat Hunting Investigation
Investigated what manual threat hunting looks like using Sysmon and Wazuh telemtry
- Built search queries to identify specific events
- Identified suspicious PowerShell execution
- Correlatated multiple logs to try and understand how to locate and find a root cause

### 6. SOC Playbook
Created an incident response playbook specifically for suspicious PowerShell execution. Can be seen more in the playbook section of this repository. 

### 7. Documentation / Reporting
Created a collection of reports in varying areas
- SIEM Configuration Documentation
- Threat Hunting Report
- Incident Response Playbook
- MITRE ATT&CK Heat Map
- Screenshots of dashbaords, alerts, searches and queries
- Full lab write up (this README)

## Skills Demonstrated
- This lab demonstrates real SOC analyst capabilities:
- SIEM Deployment & Administration
- Log Ingestion & Parsing
- Sysmon + Windows Event Analysis
- MITRE ATT&CK Detection Engineering
- Threat Hunting
- Incident Response
- Playbook Creation
- Documentation & Reporting
- Cloud (AWS) Architecture
- Linux + Windows endpoint security

## Future Improvements
This goal of this lab was to get introductory and begginer level experience and understanding of working with a SIEM. But future improvements and growth can be seen in...
- Adding custom Wazuh rules
- Adding automated responses via Python or bash
- Sigma Rules
