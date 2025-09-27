#### Official Documentation: [https://faradaysec.com/penetration-testing-reporting/](https://faradaysec.com/penetration-testing-reporting/)
#### Cheat Sheet: [[Kali Tools#Faraday|Faraday Commands]]
## Purpose
Faraday is a collaborative penetration testing IDE that centralizes results, provides issue tracking, and integrates many security tools for team workflows.

## Scenarios
- CTF: Share discoveries and scan outputs with teammates in real time to divide tasks and avoid duplication.  
- Real world: Centralize scan results (Nmap, Nikto, SQLmap), annotate findings, track remediation status, and generate reports.

## All needed info to run
- Deployment: Faraday Server + Client (Docker images available) or package installs. Typical ports: 5985 (API/UI) depending on version.  
- Basic workflow:
  1. Start Faraday server and web UI (or use docker-compose).  
  2. Create workspace and invite team members.  
  3. Import scan outputs (Nmap, Nessus, Burp, OpenVAS) via UI or CLI importer.  
  4. Tag findings, add notes, and link evidence (screenshots, pcap).  
  5. Export reports (CSV, HTML) or integrate with issue trackers (Jira).  
- CLI import examples: `faraday_importer -i nmap.xml -w workspace_name` (actual CLI depends on installed package/version).  
- Integrations: many scanners, issue trackers, and CI pipelines.

## Example commands & outputs
```bash
# Example docker-compose quickstart (depends on version)
$ docker-compose up -d
# Output: starts faraday-server, faraday-client containers, UI accessible at configured port

# Import an Nmap XML from server CLI (example helper)
$ faraday-import nmap -f nmap.xml -w myworkspace
# Output:
# Imported 12 hosts and 34 services into workspace "myworkspace"

# Use web UI: open server URL, select workspace, view hosts/services, add issues and notes
# Export CSV/HTML from the Export menu
```

!!! note "Faraday Basics"
	- Faraday centralizes many tool outputs — import scanner XMLs to build a single source of truth.
	- Use workspaces per engagement and control user permissions for collaboration.
	- Integrates with trackers (Jira) and CI for automated workflows.
	- CLI import helper names may vary by version — check `faraday --help` or package docs.

### [[Kali Tools#Faraday|Faraday Commands]]