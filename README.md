# Threat-Hunting-Log-Analysis-Platform
SOC-focused Threat Hunting and Log Analysis Platform using Splunk Enterprise, AWS EC2 Ubuntu, and Kali Linux for attack simulation, IOC analysis, incident investigation, and security monitoring.

## Overview

This project simulates a Security Operations Center (SOC) environment for threat hunting and log analysis.

The platform monitors Linux authentication logs collected from an AWS EC2 Ubuntu server and analyzes them using Splunk Enterprise. Attack activity is generated from Kali Linux to simulate real-world adversarial behavior.

The objective is to detect unauthorized access attempts, identify Indicators of Compromise (IOCs), investigate suspicious activity, and create actionable security alerts and dashboards.

## Architecture

Kali Linux (Attacker)
        ↓
AWS EC2 Ubuntu Server
        ↓
/var/log/auth.log
        ↓
Splunk Enterprise
        ↓
Threat Detection & Investigation
        ↓
Dashboards & Alerts
----
## Technologies Used

- Splunk Enterprise
- AWS EC2 Ubuntu Server
- Kali Linux
- Linux Authentication Logs
- SSH
- SPL (Search Processing Language)
- Git & GitHub
----
## Screenshots

### SOC Monitoring Dashboard
![SOC Dashboard](screenshots/dashboard_1.png)

### Threat Hunting Dashboard
![Threat Hunting Dashboard](screenshots/dashboard_2.png)

### Security Analytics Dashboard
![Security Analytics Dashboard](screenshots/dashboard_3.png)

### Top Attacker IP Addresses
![Top Attacker IPs](screenshots/top-attacker-ips.png)

### Failed Login Trend Analysis
![Failed Login Trend](screenshots/failed-login-trend.png)

### Invalid Username Attempts
![Invalid Username Attempts](screenshots/invalid-username-attempts.png)

### Username Enumeration Evidence
![Username Enumeration](screenshots/username-enumeration-evidence.png)

### SSH Brute Force Detection
![SSH Brute Force Detection](screenshots/ssh-brute-force-detection.png)

### Brute Force Investigation Evidence
![Brute Force Evidence](screenshots/brute-force-evidence.png)

### Authentication Activity Timeline
![Authentication Activity Timeline](screenshots/authentication-activity-timeline.png)
