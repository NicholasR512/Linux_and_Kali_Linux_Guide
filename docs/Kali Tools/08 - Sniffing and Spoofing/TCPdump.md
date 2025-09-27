#### Official Documentation: [https://www.tcpdump.org/](https://www.tcpdump.org/)
#### Cheat Sheet: [[Kali Tools#TCPdump|TCPdump Commands]]
## Purpose
Tcpdump is a command-line packet capture tool. It captures and filters packets for analysis, letting you see headers, protocols, and payloads directly in terminal or save to pcap.

## Scenarios
- CTF: Capture and filter traffic on a challenge interface to find flags (like FTP passwords or HTTP secrets).  
- Real world: Quickly diagnose network issues or gather packet traces for Wireshark.

## All needed info to run
- Run as root for most interfaces.  
- Syntax: `tcpdump [options] [filter]`.  
- Common flags:
  - `-i <iface>` → interface (default: first active)  
  - `-nn` → don’t resolve hostnames/ports  
  - `-v`, `-vv` → verbosity  
  - `-X` → print hex + ASCII  
  - `-A` → ASCII only  
  - `-c <count>` → stop after n packets  
  - `-w <file>` → write to pcap file  
  - `-r <file>` → read from pcap file  
- Filters use pcap syntax: `host`, `port`, `tcp`, `udp`, `and`, `or`.

## Example commands & outputs
```bash
# Capture 10 packets on eth0
$ sudo tcpdump -i eth0 -nn -c 10
# Output snippet:
# IP 192.168.56.101.22 > 192.168.56.1.51544: Flags [P], length 48

# Capture HTTP traffic
$ sudo tcpdump -i eth0 -nn port 80 -A
# Output: shows ASCII HTTP requests/responses

# Save capture to file
$ sudo tcpdump -i wlan0 -w capture.pcap
# Output: listening on wlan0, link-type EN10MB
```

!!! note "Tcpdump Basics"
	- Use `-nn` to avoid DNS/port lookups (faster, cleaner output).
	- Combine filters (`tcp and port 80`) for precision.
	- Use `-w` to capture and analyze later in Wireshark.
	- Tcpdump is powerful for quick filtering and is scriptable for automation.

### [[Kali Tools#TCPdump|TCPdump Commands]]