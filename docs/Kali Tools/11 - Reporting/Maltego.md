#### Official Documentation: [https://docs.maltego.com/en/support/solutions/articles/15000059016-reports](https://docs.maltego.com/en/support/solutions/articles/15000059016-reports)
#### Cheat Sheet: [[Kali Tools#Maltego|Maltego Commands]]
## Purpose
Maltego is a visual link-analysis tool for OSINT and relationship mapping. It transforms data (domains, emails, IPs) into graphs showing connections and attributes.

## Scenarios
- CTF: Map entities (domains, subdomains, email addresses) to find relationships or pivot points for further recon.  
- Real world: Conduct OSINT investigations, map infrastructure, and visualize attacker infrastructure or social links.

## All needed info to run
- Maltego TRx (Community, Classic, XL) GUI available; install from Paterva.  
- Transforms: built-in and remote transforms (WHOIS, DNS, Shodan, social media) — many require API keys.  
- Basic workflow:
  1. Start Maltego GUI.  
  2. Create a graph and add seed entities (domain, email, IP).  
  3. Run transforms to expand nodes (DNS transforms, WHOIS, subdomain finders).  
  4. Use filters/visual styles to focus on high-signal nodes and export graphs (PNG, CSV).  
- Transform hubs: community transforms and paid transform servers increase capabilities.  
- API keys: register for keys (Shodan, VirusTotal, etc.) to unlock transforms.

## Example commands & outputs
```text
# GUI flow (no terminal output):
# 1. New Graph -> Add Entity: "example.com"
# 2. Right-click entity -> Run Transform -> DNS from Domain -> finds subdomains
# 3. Expand nodes: run WHOIS and DNS transforms to get registrar/name servers
# 4. Visual graph shows connections; export via File -> Export -> PNG/CSV

# Example transform result:
# example.com -> mail.example.com (MX) -> 192.0.2.1 (A record) -> AS12345 (owner)
```

!!! note "Maltego Basics"
	- Maltego is GUI/visual-first — use transforms to pivot from a seed entity into a graph.
	- Many useful transforms need API keys (Shodan, VirusTotal) — add keys in settings for full power.
	- Use filtering and grouping to manage large graphs and focus on high-value nodes.
	- Respect privacy and legal limits when performing OSINT — always follow terms of service.

### [[Kali Tools#Maltego|Maltego Commands]]