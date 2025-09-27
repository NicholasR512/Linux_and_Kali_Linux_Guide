#### Official Documentation: [https://www.kismetwireless.net/](https://www.kismetwireless.net/)
#### Cheat Sheet: [[Kali Tools#Kismet|Kismet Commands]]
## Purpose
Kismet is a wireless network detector, sniffer, and IDS. It passively collects wireless traffic, detects hidden networks, logs captures, and supports many plugins and sources.

## Scenarios
- CTF: Passively discover hidden SSIDs, probe requests, and devices without active probing.  
- Real world: Monitor wireless environment for rogue APs, sniff traffic for analysis (authorized), and log historical wireless activity.

## All needed info to run
- Kismet works with many adapters and supports monitor mode; check adapter compatibility.  
- Typical start: `kismet` or `kismet -c <source>`; web UI available (default `localhost:2501`).  
- Can read from a variety of sources (local radio, remote sensors).  
- Output: pcap/ng (kismet.db, pcap files), GPS logs, and web UI alerts.  
- Run as root or with proper permissions to access wireless device.

## Example commands & outputs
```bash
# Launch Kismet using default devices
$ sudo kismet
# Output: Kismet server starting, web UI accessible at http://127.0.0.1:2501

# Launch Kismet with a specific source (example for wlan0)
$ sudo kismet -c wifi:mon0:name=mon0
# Output: Kismet capturing; shows discovered networks and clients in UI

# Save pcap output (configured in kismet.conf or via UI)
# The web UI shows networks, clients, vendor info, and probe requests (useful to find hidden SSIDs)
```

!!! note "Kismet Basics"
	- Kismet is passive by default — safer for stealthy discovery than active tools.
	- Use the web UI ([http://127.0.0.1:2501](http://127.0.0.1:2501)) to inspect networks, clients, and logs visually.
	- Kismet stores data in its own DB and can export pcaps for later analysis with Wireshark.
	- If you need active attacks (deauth, handshake capture), use `airodump-ng`/`aireplay-ng` instead.

### [[Kali Tools#Kismet|Kismet Commands]]