# SSH Brute Force Investigation Report

## Executive Summary

A brute-force attack was detected against the SSH service running on the AWS Ubuntu server. Multiple failed authentication attempts were observed originating from a single external IP address. The activity was identified through Splunk log analysis of Linux authentication logs.

## Incident Details

**Incident Type:** SSH Brute Force Attempt

**Detection Source:** /var/log/auth.log

**SIEM Platform:** Splunk Enterprise

**Target Service:** SSH (Port 22)

**Target Host:** Ubuntu EC2 Instance

## Indicators of Compromise (IOCs)

### Source IP

1.39.174.44

### Attack Behavior

* Repeated failed SSH authentication attempts
* Multiple login attempts within a short period
* Password guessing activity

## Detection Query

```spl
source="/var/log/auth.log" "Failed password"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| where count > 3
```

## Investigation Findings

Analysis of authentication logs revealed repeated login failures against the Ubuntu account. The activity originated from a single external IP address and matched common brute-force attack patterns.

No successful unauthorized authentication was observed during the investigation period.

## MITRE ATT&CK Mapping

Technique: T1110 - Brute Force

Tactic: Credential Access

## Impact Assessment

Current Impact: Low

No evidence of successful compromise was identified.

Potential Impact: Medium

If successful, the attacker could obtain shell access to the Linux server and perform privilege escalation or persistence activities.

## Recommendations

1. Disable password authentication when testing is complete.
2. Enforce SSH key-based authentication.
3. Implement fail2ban.
4. Restrict SSH access using AWS Security Groups.
5. Create Splunk alerts for excessive authentication failures.

## Conclusion

The detected activity was classified as an SSH brute-force attempt. The attack was unsuccessful, and no unauthorized access was observed. Continuous monitoring and alerting are recommended to detect future credential-based attacks.
