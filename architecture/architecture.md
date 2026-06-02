# Threat Hunting & Log Analysis Platform Architecture

## Overview

The platform simulates a SOC environment where security logs are collected, analyzed, and investigated using Splunk Enterprise.

## Architecture Flow

```text
Attacker Machine
(Kali Linux)
        │
        ▼
AWS EC2 Ubuntu Server
(SSH Service)
        │
        ▼
Linux Authentication Logs
(/var/log/auth.log)
        │
        ▼
Splunk Universal Forwarder
        │
        ▼
Splunk Enterprise SIEM
        │
 ┌──────┼────────┬─────────┐
 ▼      ▼        ▼         ▼
Dashboards Alerts Detection Threat Hunting
        │
        ▼
Incident Investigation
```

## Components

### Kali Linux

* Simulates attacker activity
* Performs SSH reconnaissance
* Generates failed login attempts

### AWS Ubuntu Server

* Acts as monitored target system
* Generates authentication logs
* Hosts SSH service

### Splunk Universal Forwarder

* Collects log data
* Sends logs securely to Splunk Enterprise

### Splunk Enterprise

* Centralized log collection
* Threat detection
* Dashboard visualization
* Alert generation
* Investigation platform

## Security Use Cases

* Failed SSH Login Detection
* Username Enumeration Detection
* Brute Force Detection
* Authentication Monitoring
* Attacker IP Analysis
* Threat Hunting
