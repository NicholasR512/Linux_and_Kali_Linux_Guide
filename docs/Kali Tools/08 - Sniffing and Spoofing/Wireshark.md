#### Official Documentation: [https://www.wireshark.org/](https://www.wireshark.org/)
#### Cheat Sheet: [[Kali Tools#Wireshark|Wireshark Commands]]
## Purpose
Wireshark is a GUI packet analyzer. It captures traffic live or reads pcaps, with advanced filters and protocol decoding.

## Scenarios
- CTF: Open a provided `.pcap` to search for flags in cleartext HTTP, FTP, or DNS queries.  
- Real world: Diagnose network problems, analyze suspicious traffic, or validate protocol behavior.

## All needed info to run
- GUI: `wireshark` (requires X11/GUI).  
- CLI alternative: `tshark`.  
- Common features:
  - Capture on interface (requires root or group privileges).  
  - Display filters: `http`, `ip.addr == 192.168.56.101`, `tcp.port == 21`.  
  - Follow streams: right-click packet → Follow → TCP Stream.  
  - Export objects: HTTP, SMB, etc.  
- File formats: `.pcap`, `.pcapng`.  
- Use with `tcpdump` for headless capture.

## Example commands & outputs
```bash
# Launch GUI
$ wireshark &
# GUI opens, select interface, start capture

# Display filter examples:
http
ip.addr == 192.168.56.101
tcp.port == 21

# Follow TCP stream:
Right-click packet -> Follow -> TCP Stream
# Output shows plaintext conversation or HTTP request/response

# Export objects:
File -> Export Objects -> HTTP -> Save files
```

!!! note "Wireshark Basics"
	- Use display filters (`http`, `ip.addr == X`) to quickly find relevant packets.
	- Follow TCP Stream to reconstruct conversations.
	- Use Export Objects to recover files from captures.
	- Run `tshark` if only CLI access is available.


### [[Kali Tools#Wireshark|Wireshark Commands]]