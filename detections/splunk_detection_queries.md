# Splunk Detection Queries

## 1. Failed SSH Login Detection
### Purpose
Detects failed SSH password authentication attempts on the AWS Ubuntu server.
```spl
source="/var/log/auth.log"
"Failed password"
```
This query searches Linux authentication logs for failed SSH login events. These events may indicate password guessing, brute-force attempts, or unauthorized access attempts.

## 2. Invalid Username Detection
### Purpose
Detects login attempts using usernames that do not exist on the server.
```spl
source="/var/log/auth.log"
"Invalid user"
```
Attackers often try common usernames such as admin, test, oracle, root, or user. Multiple invalid username attempts may indicate username enumeration.

## 3. SSH Brute Force Detection
### Purpose
Detects source IP addresses generating repeated failed SSH login attempts.
```spl
source="/var/log/auth.log"
"Failed password"
| stats count by src_ip
| where count > 5
```
This query extracts the source IP address from SSH failure logs and counts failed login attempts per IP. If one IP generates more than 5 failed attempts, it is treated as suspicious brute-force behavior.

## 4. Top Attacker IP Addresses
### Purpose
Identifies the most active source IP addresses involved in failed SSH activity.
```spl
source="/var/log/auth.log"
"Failed password"
| top limit=10 src_ip
```
This query identifies the top source IP addresses responsible for suspicious SSH authentication activity. It helps analysts prioritize which IPs to investigate first.
## 5. Username Enumeration Detection
### Purpose
Identifies usernames attempted by attackers during SSH login attempts.
```spl
source="/var/log/auth.log" "Invalid user"
| rex "Invalid user (?<username>\S+)"
| stats count by username
| sort -count
```
This query extracts usernames from invalid login attempts. A high number of different usernames may indicate username enumeration before a brute-force attack.
