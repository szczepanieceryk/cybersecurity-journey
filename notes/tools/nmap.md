# nmap

CLI notes on using nmap for network discovery and security auditing.

## What it's for

Network scanner used to discover hosts, open ports, running services, and (with scripts) known vulnerabilities on a network. Used it hands-on during a home network audit to map devices (IoT cameras, router) and check for exposed services.

## Core commands

```bash
# Basic host discovery (ping scan, no port scan)
nmap -sn 192.168.1.0/24

# Scan a single host, default ports
nmap 192.168.1.1

# Scan all 65535 ports
nmap -p- 192.168.1.1

# Service/version detection
nmap -sV 192.168.1.1

# OS detection
nmap -O 192.168.1.1

# Aggressive scan (OS, version, script scan, traceroute)
nmap -A 192.168.1.1

# Scan with default NSE scripts (includes basic vuln checks)
nmap -sC 192.168.1.1

# Combine version detection + default scripts
nmap -sC -sV 192.168.1.1
```

## Vulnerability scanning (NSE scripts)

```bash
# Run vuln-category scripts against a target
nmap --script vuln 192.168.1.1

# Check a specific known CVE script
nmap --script <script-name> 192.168.1.1
```

> TODO: log specific CVEs found on home IoT devices (camera, router) and which script/flag surfaced them.

## Output formats

```bash
# Save results in normal, XML, and grepable format at once
nmap -oA scan_results 192.168.1.0/24
```

## Notes / gotchas

- `-sn` = no port scan, just discovery — good first pass on an unfamiliar network.
- Scanning networks you don't own/manage without permission is illegal — only scan your own devices/lab environments.
- `-T4` speeds up timing; useful on local networks, riskier/noisier on scans over the internet.

## Related

- [Home Network Security Audit](../../labs/home-network-audit) — practical write-up using these commands
