# Splunk Detection Queries

## Failed SSH Login Detection

```spl
source="/var/log/auth.log"
"Failed password"
```

## Invalid Username Detection

```spl
source="/var/log/auth.log"
"Invalid user"
```

## SSH Brute Force Detection

```spl
source="/var/log/auth.log"
"Failed password"
| stats count by src_ip
| where count > 5
```

## Top Attacker IP Addresses

```spl
source="/var/log/auth.log"
"Failed password"
| top limit=10 src_ip
```

## Authentication Activity Timeline

```spl
source="/var/log/auth.log"
| timechart count
```
