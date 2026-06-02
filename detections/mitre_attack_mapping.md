# MITRE ATT&CK Mapping

## Technique 1: Brute Force

**MITRE Technique:** T1110 - Brute Force  
**Tactic:** Credential Access  

### Description
Multiple failed SSH login attempts were detected from external IP addresses. This activity indicates possible brute-force attempts against the Ubuntu server.

### Splunk Query
## spl
source="/var/log/auth.log"
"Failed password"
| stats count by src_ip
| where count > 5

## Technique 2: Valid Account Attempt

**MITRE Technique:** T1078 - Valid Accounts
**Tactic:** Defense Evasion / Persistence / Privilege Escalation / Initial Access

### Description

Attackers may attempt to authenticate using guessed or stolen credentials over SSH.

### Splunk Query
``spl
source="/var/log/auth.log"
"Accepted password" OR "Accepted publickey"

## Technique 3: Account Discovery / Username Enumeration

MITRE Technique: T1087 - Account Discovery
Tactic: Discovery

### Description

Invalid username attempts indicate possible username enumeration activity against the SSH service.
