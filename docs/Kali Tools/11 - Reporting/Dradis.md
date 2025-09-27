#### Official Documentation: [https://dradis.com/](https://dradis.com/)
#### Cheat Sheet: [[Kali Tools#Dradis|Dradis Commands]]
## Purpose
Dradis is a collaboration and reporting platform for security assessments. It centralizes findings from scans and manual testing, lets teams share notes, and generates consistent reports (HTML/PDF).

## Scenarios
- CTF: Keep track of discovered vulnerabilities, PoCs, and flags when working in a team.  
- Real world: Consolidate outputs from Nmap, Burp, Nikto, etc., assign issues to teammates, and produce professional reports for clients.

## All needed info to run
- Installation: available as package/docker or via source (`apt`, Docker image `dradis/dradis-ce`).  
- Basic workflow:
  1. Start server (e.g., `docker run -p 3000:3000 dradis/dradis-ce`) or system service.  
  2. Login via web UI (default port 3000).  
  3. Create a project/case, import findings (CSV, XML, JSON, Nessus, Nmap), or add manual notes.  
  4. Organize issues, set severity, add remediation text, and assign owners.  
  5. Export templates: HTML, PDF, Markdown.  
- Integrations: many scanners (Nessus, Burp, Nikto), plugins for automation.  
- Permissions: set user roles (admin, contributor, viewer).

## Example commands & outputs
```bash
# Quick Docker run (community edition)
$ docker run --rm -p 3000:3000 dradis/dradis-ce
# Output:
# Listening on http://0.0.0.0:3000
# Visit http://localhost:3000 to login and create a project

# Import an Nmap XML from the UI: Project -> Import -> Nmap (upload file)
# Add manual note in the web UI: Findings -> Add Finding -> set severity/notes
# Export: Project -> Export -> choose template (HTML/PDF)
```

!!! note "Dradis Basics"
	- Dradis is web/UI-first — run the server (Docker or package) and use the browser to manage projects.
	- Import scanner outputs (Nmap, Nessus, Burp) to avoid manual re-entry.
	- Use report templates to standardize client deliverables.
	- Set user roles and backups for team work; never run production data without access controls.


### [[Kali Tools#Dradis|Dradis Commands]]