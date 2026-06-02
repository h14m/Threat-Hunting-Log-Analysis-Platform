# Username Enumeration Detection

source="/var/log/auth.log" "Invalid user"

# SSH Brute Force Detection

source="/var/log/auth.log" "Failed password"

# Top Attacker IP Analysis

source="/var/log/auth.log"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| sort -count

# Authentication Timeline

source="/var/log/auth.log"
("Invalid user" OR "Accepted publickey" OR "Failed password")
| timechart count
