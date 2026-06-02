# Incident Response Report

## Project
Threat Hunting & Log Analysis Platform

## Incident Summary
Multiple suspicious SSH authentication attempts were detected against an AWS-hosted Ubuntu server. The activity included failed login attempts, invalid username attempts, and brute-force indicators from external IP addresses.

## Affected Asset
- AWS EC2 Ubuntu Server
- Service: SSH
- Log Source: `/var/log/auth.log`
- SIEM Tool: Splunk Enterprise

## Detection Method
The incident was detected using Splunk SPL queries analyzing Linux authentication logs.

## Key Findings
- Multiple failed SSH login attempts were observed.
- Invalid usernames were used, indicating possible username enumeration.
- Repeated attempts from attacker IP addresses suggested brute-force activity.
- Authentication events were visualized using Splunk dashboards.

## Evidence
- Failed Login Trend Analysis
- Top Attacker IP Addresses
- SSH Brute Force Detection
- Username Enumeration Evidence
- Authentication Activity Timeline

## MITRE ATT&CK Mapping
- T1110 - Brute Force
- T1087 - Account Discovery
- T1078 - Valid Accounts

## Impact
No confirmed successful unauthorized access was identified. However, the activity indicates active reconnaissance and credential attack attempts against the SSH service.

## Response Actions
- Investigated authentication logs in Splunk.
- Identified source IPs involved in repeated failed login attempts.
- Documented evidence using dashboard screenshots.
- Recommended restricting SSH access to trusted IP addresses.
- Recommended disabling password authentication and using SSH key-based login.

## Recommendations
- Restrict inbound SSH access in AWS Security Groups.
- Disable password-based SSH authentication.
- Use key-based authentication only.
- Enable MFA where applicable.
- Monitor failed login thresholds continuously.
- Create scheduled alerts for brute-force behavior.
- Review logs regularly for unusual authentication activity.

## Conclusion
The investigation confirmed suspicious SSH activity consistent with brute-force attempts and username enumeration. Splunk dashboards and detection queries helped identify attacker behavior, affected services, and recommended remediation steps.
