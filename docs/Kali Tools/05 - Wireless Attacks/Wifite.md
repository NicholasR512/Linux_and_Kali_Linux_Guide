#### Official Documentation: [https://www.kali.org/tools/wifite/](https://www.kali.org/tools/wifite/)
#### Cheat Sheet: [[Kali Tools#Wifite|Wifite Commands]]
## Purpose
Wifite is an automated tool to audit multiple wireless networks quickly. It wraps aircrack-ng tools and automates scanning, handshake capture, WPS attacks, and cracking.

## Scenarios
- CTF: Quickly run through nearby APs to capture handshakes and attempt common attacks with minimal typing.  
- Real world: Fast auditing of nearby networks in a controlled environment to find weak PSKs or WPS vulnerabilities.

## All needed info to run
- Requires a monitor-mode capable wireless adapter.  
- Wifite automates using `airodump-ng`, `aireplay-ng`, `aircrack-ng`, and `reaver` where applicable.  
- Common runtime options:
  - `--kill` → kill interfering services (NetworkManager)  
  - `--wps` → enable WPS attacks (Reaver)  
  - `--crack` → try cracking captured handshakes automatically with a wordlist  
  - `-i <iface>` → specify interface  
  - `-p <path>` → path to wordlist for cracking  
- Wifite prompts to select targets or can run fully non-interactive with flags.

## Example commands & outputs
```bash
# Launch interactive Wifite (select APs via text UI)
$ sudo wifite
# Output: scans and lists APs; choose targets by number; attempts handshake/WPS

# Non-interactive: enable WPS attacks and automatic cracking with rockyou
$ sudo wifite --kill --wps --crack --dict /usr/share/wordlists/rockyou.txt -i mon0
# Output: tries WPS PINs or captures handshakes, then runs aircrack-ng with provided dict

# Example success output
# Handshake captured from 00:11:22:33:44:55
# Cracked with wordlist: password123
```

!!! note "Wifite Basics"
	- Wifite automates many steps — great for speed but understand what it runs under the hood.
	- `--kill` will stop network services; re-enable them after testing.
	- Be careful running WPS attacks (`--wps`) — they can be intrusive and slow.
	- Always test only on networks you own or have written permission to audit.

### [[Kali Tools#Wifite|Wifite Commands]]