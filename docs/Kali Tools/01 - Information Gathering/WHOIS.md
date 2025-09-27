#### Official Documentation: [https://www.kali.org/tools/whois/](https://www.kali.org/tools/whois/)
#### Cheat Sheet: [[Kali Tools#WHOIS|WHOIS Commands]]
## Purpose
whois retrieves domain and IP registration information: registrant, registrar, registration/expiry dates, name servers, and contact info (where available).

## Scenarios
- CTF: Find ownership hints or related domains via registration details or contact emails.  
- Real world: Verify domain ownership, check for impending expiry (possible takeover risk), or gather points of contact for disclosure.

## Required info to run
- A domain name or IP address.  
- The `whois` client installed (included in Kali).  
- Understand that WHOIS data can be privacy-protected; use historical WHOIS or WHOIS APIs if needed.
- Command options:
  - `whois <domain>` → basic lookup  
  - `whois -h <server> <query>` → query a specific WHOIS server (advanced)  
  - For bulk lookups, use APIs (paid) to avoid rate limiting.

## Example commands & outputs
```bash
# Domain whois
$ whois example.com
# Output snippet:
# Domain Name: EXAMPLE.COM
# Registrar: RESERVED-Internet Assigned Numbers Authority
# Creation Date: 1995-08-04T04:00:00Z
# Name Server: A.IANA-SERVERS.NET

# IP whois (shows allocation/owner)
$ whois 8.8.8.8
# Output snippet:
# NetRange:       8.0.0.0 - 8.127.255.255
# Organization:   Google LLC
```

!!! note "whois Basics"  
	- WHOIS can be rate-limited; space queries. For many domains, contact details are redacted.  
	- For historical records, use services like SecurityTrails, DomainTools, or whoisxmlapi (API keys may be required).  
	- Combine WHOIS with DNS enumeration and `theHarvester` for fuller recon.

### [[Kali Tools#WHOIS|WHOIS Commands]]
