#### Official Documentation: [https://www.kali.org/tools/dnsenum/](https://www.kali.org/tools/dnsenum/)
#### Cheat Sheet:  [[Kali Tools#DNSenum|DNSenum Commands]]

## Purpose
dnsenum automates DNS enumeration: it finds name servers, MX/SOA records, performs zone transfer checks, and brute-forces subdomains. It’s a fast way to map DNS information for a domain.

## Scenarios
- CTF: Discover hidden subdomains (e.g., `dev.target.local`) that host additional services or flags.  
- Real world: During reconnaissance for a pentest, map the DNS attack surface to find misconfigurations (e.g., open AXFR) or forgotten hosts.

## Required info to run
- Target domain (e.g., `example.com`).  
- Optional wordlist for brute-force (common locations: `/usr/share/wordlists/` or custom lists).  
- Optional DNS server override (`--dnsserver` or `--dns`) if you want to query a specific resolver.  
- Network/DNS access (internet access or access to target DNS).  
- Useful flags:
  - `-f <wordlist>` → use wordlist for subdomain bruteforce  
  - `-s <server>` → specify name server(s)  
  - `-o <file>` → output file prefix  
  - `--threads <n>` → set concurrency  
  - `--enum` / default checks include NS, MX, SOA, subdomains

## Example commands & outputs
```bash
# Basic enumeration (default checks NS, MX, SOA, subdomains)
$ dnsenum example.com
# Output snippet:
# [+] Servers: ns1.example.com, ns2.example.com
# [+] MX: mail.example.com
# [+] Hosts found: www.example.com, dev.example.com

# Bruteforce subdomains with a wordlist and save output
$ dnsenum -f /usr/share/wordlists/subdomains-top1million-5000.txt --dnsserver 8.8.8.8 -o dnsenum-example example.com
# Creates dnsenum-example.* with discovered hosts and records

# Check for zone transfer (AXFR) directly with dig (fallback)
$ dig @ns1.example.com example.com AXFR
# If allowed, returns full zone file (rare)
```

!!! note "DNSenum Basics"  
	- Zone transfers (AXFR) are rare but a jackpot if allowed; always check with `dig`.  
	- Keep wordlists updated; bigger lists increase coverage but take longer.  
	- Combine `dnsenum` output with `massdns`, `subfinder`, or `amass` for higher recall.  
	- Use `--dnsserver` to avoid rate-limiting by your default resolver.

### [[Kali Tools#DNSenum|DNSenum Commands]]

