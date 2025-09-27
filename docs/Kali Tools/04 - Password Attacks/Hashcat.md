#### Official Documentation: [https://hashcat.net/hashcat/](https://hashcat.net/hashcat/)
#### Cheat Sheet: [[Kali Tools#Hashcat|Hashcat Commands]]
## Purpose
Hashcat is a high-performance password recovery tool that uses GPU acceleration to crack password hashes using many attack modes (dictionary, brute-force, rule-based, hybrid).

## Scenarios
- CTF: Crack dumped password hashes (MD5, bcrypt, NTLM) to get credentials or flags.  
- Real world: Authorized password recovery or offline credential audits using hash dumps from your environment.

## All needed info to run
- Hash type (e.g., MD5, NTLM, bcrypt). Hashcat uses mode numbers (see `hashcat --help` or online cheat-sheets).  
- Wordlists (e.g., `rockyou.txt`) or rules files.  
- GPU drivers installed (NVIDIA/CUDA or AMD/OpenCL) for best performance; CPU-only mode is possible but slow.  
- Common flags:
  - `-m <hash-type>` → hash mode (e.g., `0` for MD5, `1000` for NTLM)  
  - `-a <attack-mode>` → attack mode (`0` dict, `3` brute-force, `6` hybrid wordlist+mask, `7` mask+wordlist)  
  - `-o <outfile>` → save cracked results  
  - `--rules-file <rulefile>` → use rules  
  - `-w` → workload profile (1..4)
- Hash input formats: one hash per line, optional `salt` handling depending on algorithm.

## Example commands & outputs
```bash
# Basic dictionary attack (MD5 hashes)
$ hashcat -m 0 -a 0 hashes.txt /usr/share/wordlists/rockyou.txt -o cracked.txt
# Output snippet:
# Session..........: hashcat
# Status...........: Cracked
# Hash.Target......: hashes.txt
# Cracked          : 3/3 (100.00%)

# Brute-force with mask (lowercase letters, 6 chars)
$ hashcat -m 1000 -a 3 ntlm_hashes.txt ?l?l?l?l?l?l
# Output: tries combinations and reports cracked passwords

# Hybrid: wordlist + mask (append 2 digits)
$ hashcat -m 0 -a 6 hashes.txt rockyou.txt ?d?d
```

!!! note "Hashcat Basics"
	- Know the correct `-m` mode for the hash type; wrong mode fails.
	- GPU drivers must be installed correctly for high performance; use `hashcat -I` to list devices.
	- Start with targeted wordlists and rules before brute-forcing; brute-force is slow for long passwords.
	- Respect laws and only crack hashes you are authorized to test.

### [[Kali Tools#Hashcat|Hashcat Commands]]