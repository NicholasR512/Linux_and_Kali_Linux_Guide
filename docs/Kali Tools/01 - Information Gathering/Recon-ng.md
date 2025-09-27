#### Official Documentation: [https://github.com/lanmaster53/recon-ng/wiki/Getting-Started](https://github.com/lanmaster53/recon-ng/wiki/Getting-Started)
#### Cheat Sheet: [[Kali Tools#Recon-ng|Recon-ng Commands]]
## Purpose
Recon-ng is a web reconnaissance framework that organizes the recon workflow into modules, similar to Metasploit for recon. It automates harvesting of data, storing results, and chaining modules.

## Scenarios
- CTF: Automate collection of subdomains, contacts, and web assets using multiple modules in a structured way.  
- Real world: Run multi-source passive recon (APIs, search engines, social footprints) and export structured results for reporting.

## Required info to run
- Python environment and `recon-ng` installed (often available in Kali).  
- API keys for certain modules (e.g., Shodan, VirusTotal, Twitter) to increase capability.  
- Basic workflow:
  1. `workspaces create <name>` (optional)  
  2. `modules load <module>`  
  3. `options set SOURCE <target>` and other module options  
  4. `run`  
  5. `show hosts` / `show domains` / `export`  
- Key commands:
  - `marketplace search` → search available modules  
  - `modules search <term>` → find module by name  
  - `modules load <recon/hosts-hosts>` → load module  
  - `options` → list/set module options  
  - `run` → execute module
- Examples of useful modules: `recon/domains-hosts/bing`, `recon/domains-contacts/whois_pocs`, `recon/hosts-hosts/brute_hosts`.

## Example commands & outputs
```bash
# Start recon-ng
$ recon-ng
recon-ng > workspaces create target_workspace
recon-ng > modules load recon/domains-hosts/bing
recon-ng > options set SOURCE example.com
recon-ng > run
# Output snippet:
# [!] Module finished. Hosts saved to the workspace.
recon-ng > show hosts
# id  host
# 1   www.example.com
# 2   dev.example.com

# Export hosts to CSV
recon-ng > export csv /path/to/output.csv hosts
```

!!! note "Recon-ng Basics"  
	- Use API keys for higher-volume sources (set via `keys add <service> <key>`).  
	- Workspaces keep recon organized — use them per target.  
	- Recon-ng is passive by default but some modules may be noisier; review module docs.  
	- Export results for ingestion into other tools (Burp, Dradis).

### [[Kali Tools#Recon-ng|Recon-ng Commands]]
