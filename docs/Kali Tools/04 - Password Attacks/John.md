#### Official Documentation: [https://www.openwall.com/john/](https://www.openwall.com/john/)
#### Cheat Sheet: [[Kali Tools#John|John Commands]]
## Purpose
John the Ripper is a versatile password cracker for hashes and password files; it supports many formats and has builtin rules for smart guessing.

## Scenarios
- CTF: Crack password hashes from a captured file to retrieve credentials or flags.  
- Real world: Offline password audits of hashed credentials (shadow files, dumps) with wordlists and rules.

## All needed info to run
- Input file format: `john` auto-detects many formats; use `--format` if needed.  
- Wordlists (e.g., `rockyou.txt`) and `john` rules (in `john.conf`).  
- Common commands:
  - `john <hashfile>` → run with default wordlist/rules  
  - `john --wordlist=<file> --rules <hashfile>` → wordlist + rules  
  - `john --incremental` → brute-force with incremental mode  
  - `john --show <hashfile>` → show cracked passwords  
  - `unshadow /etc/passwd /etc/shadow > mypasswd` → combine files for cracking (local lab only)
- Use `john --list=formats` to see supported hash types.

## Example commands & outputs
```bash
# Basic run with rockyou
$ john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
# Output snippet:
# Loaded 5 password hashes with 5 different salts (md5crypt)
# Proceeding with Wordlist-based attack, rules: Single

# Show cracked results
$ john --show hashes.txt
# user:password

# Incremental brute-force (slow)
$ john --incremental hashes.txt
```

!!! note "John Basics"
	- John is great for format auto-detection; use `--format` if auto-detect fails.
	- Use `unshadow` to combine passwd+shadow for local system password auditing (only on boxes you control).
	- Try `--wordlist` + `--rules` before `--incremental` to save time.
	- Respect authorization and laws — only crack hashes you own or are permitted to test.

### [[Kali Tools#John|John Commands]]