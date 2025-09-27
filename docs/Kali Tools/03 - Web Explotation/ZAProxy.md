#### Official Documentation: [https://www.zaproxy.org/docs/](https://www.zaproxy.org/docs/)
#### Cheat Sheet: [[Kali Tools#ZAProxy|ZAProxy Commands]]
## Purpose
ZAProxy (OWASP Zed Attack Proxy, ZAP) is an open-source web application proxy for finding vulnerabilities. It provides automated scanners, a proxy for manual inspection, and many plugins.

## Scenarios
- CTF: Intercept requests, replay them, use the active scanner for quick checks, and find injection points or misconfigurations.  
- Real world: Use as a free alternative to Burp for automated scanning and manual testing workflows.

## All needed info to run
- GUI or headless mode. On Kali, launch `owasp-zap` or `zap.sh`.  
- Configure your browser proxy to ZAP (default 127.0.0.1:8080) and install ZAP CA cert for HTTPS.  
- Key features:
  - **Spider** — discover URLs.  
  - **Active Scanner** — send attacks to find vulnerabilities.  
  - **Passive scanner** — analyzes traffic without attacking.  
  - **Fuzzer**, **Breakpoints**, **Scripting** plugins.  
- Headless mode uses `zap.sh -daemon -port 8080 -config ...` and the REST API for automation.

## Example commands & outputs
```bash
# Launch ZAP GUI
$ owasp-zap
# GUI opens; set browser proxy to 127.0.0.1:8080 and import ZAP CA cert.

# Launch ZAP in daemon (headless) mode
$ zap.sh -daemon -port 8080 -host 127.0.0.1
# Output snippet:
# ZAP Daemon started and listening on 127.0.0.1:8080

# Use the API or UI to run a quick active scan on a target
# Active scanner output (UI): alerts list with risk (High/Medium/Low), URL, parameter, and description.
```

!!! note "ZAProxy Basics"
	- Install and import ZAP's CA cert into your browser to intercept HTTPS safely.
	- ZAP has a powerful API — use headless mode + API for automation and CI pipelines.
	- Active scanning can be intrusive; run only on authorized targets.
	- ZAP is a great free alternative to Burp for many workflows.


### [[Kali Tools#ZAProxy|ZAProxy Commands]]