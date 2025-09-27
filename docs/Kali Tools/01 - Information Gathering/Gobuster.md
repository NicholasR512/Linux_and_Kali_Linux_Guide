#### Official Documentation: [https://github.com/OJ/gobuster](https://github.com/OJ/gobuster)
#### Cheat Sheet: [[Kali Tools#Gobuster|Gobuster Commands]]
## Purpose
Gobuster is a fast directory and DNS brute-forcing tool written in Go. It discovers hidden directories, files, and subdomains by using wordlists. It’s optimized for speed and concurrency.

## Scenarios
- CTF: Find hidden web directories (`/admin`, `/backup/secret.txt`) or virtual host subdomains used to host challenges.  
- Real world: Discover forgotten admin panels, backup files, or exposed endpoints before deeper web testing.

## Required info to run
- Target URL (e.g., `http://example.com`) or domain for vhost/subdomain bruteforce.  
- Wordlist path (e.g., `/usr/share/wordlists/dirb/common.txt`).  
- Choose mode:
  - `dir` → directory/file bruteforce  
  - `dns` → subdomain bruteforce (requires `--wildcard` awareness)  
  - `vhost` → virtual host bruteforce  
- Useful flags:
  - `-w <wordlist>` → wordlist file  
  - `-u <url>` → target URL  
  - `-t <threads>` → concurrency (default 10)  
  - `-x <extensions>` → append extensions (e.g., `.php, .html`)  
  - `-o <file>` → output file  
  - `-s <codes>` → show only specific HTTP codes (e.g., `200,301,302`)

## Example commands & outputs
```bash
# Basic directory brute-force
$ gobuster dir -u http://192.168.56.101 -w /usr/share/wordlists/dirb/common.txt -t 50 -o gobuster-dir.txt
# Output snippet:
# /admin (Status: 301)
# /images (Status: 200)
# /backup.zip (Status: 200)

# Bruteforce with extensions
$ gobuster dir -u https://example.com -w /usr/share/wordlists/raft-large-directories.txt -x .php,.txt -t 40

# DNS subdomain bruteforce
$ gobuster dns -d example.com -w /usr/share/wordlists/dns/subdomains-top1million-5000.txt -t 50 -o gobuster-dns.txt
# Output snippet:
# dev.example.com
# test.example.com
```

!!! note "Gobuster Basics"  
	- Respect `robots.txt` and scope in real engagements. Gobuster is noisy.  
	- Use `-s` to filter only interesting HTTP codes and reduce noise.  
	- Watch for wildcard DNS (false positives); use `--wildcard` detection or cross-check with `dig`.  
	- Increase `-t` for speed but monitor stability and target rate limits.

### [[Kali Tools#Gobuster|Gobuster Commands]]