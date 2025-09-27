#### Official Documentation: [https://nmap.org/docs.html](https://nmap.org/docs.html)
#### Cheat Sheet: [[Kali Tools#Nmap|Nmap Commands]]
## Purpose
Nmap (Network Mapper) discovers hosts, open ports, running services and versions, and can perform OS detection and script-based checks. It’s the foundational tool for network reconnaissance.

## Scenarios
- CTF: Map a target VM to find open services (SSH, web, SMB) and versions to guide exploitation.  
- Real world: Conduct host discovery and service inventory for vulnerability assessment or asset management.

## Required info to run
- Target IP(s) or hostnames (single, range, CIDR).  
- Privileges: certain scans (SYN, OS detection) require root (`sudo`).  
- Common flags:
  - `-sS` → SYN scan (stealth)  
  - `-sV` → service/version detection  
  - `-O`  → OS detection  
  - `-A`  → aggressive (scripts, versions, traceroute)  
  - `-p-` → scan all ports  
  - `-Pn` → skip host discovery (treat host as up)  
  - `-sU` → UDP scan  
  - `-oN/-oX/-oG/-oA` → save outputs  
  - `-T0..5` → timing template (higher is faster/noisier)
- Output parsing: use `grepable` (.gnmap) or XML for automated workflows.

## Example commands & outputs
```bash
# Quick scan of common ports
$ nmap -T4 -F 192.168.56.101
# PORT    STATE SERVICE
# 22/tcp  open  ssh
# 80/tcp  open  http

# Full SYN scan + service/version detection + default scripts + OS detection, save all outputs
$ sudo nmap -sS -sV -sC -O -p- -T4 -oA scans/target_full 192.168.56.101
# Output snippet:
# 22/tcp   open     ssh     OpenSSH 7.9p1 Debian 10 (protocol 2.0)
# 80/tcp   open     http    Apache httpd 2.4.29
# MAC Address: 08:00:27:1A:2B:3C

# UDP scan example (slow)
$ sudo nmap -sU -p 53,67,123 192.168.56.101
```

!!! note "Nmap Basics"  
	- Use `sudo` for privileged scans. `-sS` + `-O` require root.  
	- `-p-` scans 65535 ports — use only when necessary. Combine `-F` or common port lists for speed.  
	- NSE scripts (`-sC` or `--script`) can surface useful vuln hints.  
	- Save outputs with `-oA` for later parsing and reporting.

### [[Kali Tools#Nmap|Nmap Commands]]