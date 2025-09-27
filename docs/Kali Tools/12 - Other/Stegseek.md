#### Official Documentation: [https://github.com/RickdeJager/stegseek](https://github.com/RickdeJager/stegseek)
#### Cheat Sheet: [[Kali Tools#Stegseek|Stegseek Commands]]
## Purpose
Stegseek is a tool to brute-force passphrases for files hidden with certain stego tools (notably steghide). It tries a wordlist to find the passphrase and extract embedded content.

## Scenarios
- CTF: When `steghide info` shows embedded data but you don’t know the passphrase, use Stegseek with a wordlist to try common passwords.  
- Real world: Recover hidden data when passphrase is weak and known-list attack is permitted.

## All needed info to run
- Install: `apt install stegseek` (or get from repo). Some versions are Python wrappers — check `--help`.  
- Syntax: `stegseek <stego-file> <wordlist> <output-file>` (varies slightly by install).  
- Wordlists: use `rockyou.txt`, Cewl-generated lists, or targeted wordlists.  
- Speed depends on wordlist size and stego algorithm; stegseek targets specific formats (e.g., steghide).

## Example commands & outputs
```bash
# Run stegseek with rockyou to try and extract data from image
$ stegseek suspicious.jpg /usr/share/wordlists/rockyou.txt extracted_output
# Output snippet:
# Trying password: 123456
# Trying password: password
# Password found: letmein
# Extracted to extracted_output

# If not found, stegseek will finish scanning the list and report no match
```

!!! note "Stegseek Basics"
	- Stegseek automates a wordlist attack against stego passphrases — choose wordlists wisely (targeted > huge).
	- If stegseek fails, try custom lists from Cewl or context-specific words.
	- Brute-forcing large lists is slow; prefer targeted lists first.
	- Verify extracted output (file magic/type) after extraction to confirm success.

### [[Kali Tools#Stegseek|Stegseek Commands]]