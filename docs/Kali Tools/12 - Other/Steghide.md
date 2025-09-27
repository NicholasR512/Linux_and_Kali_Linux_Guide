#### Official Documentation: [https://steghide.sourceforge.net/](https://steghide.sourceforge.net/)
#### Cheat Sheet: [[Kali Tools#Steghide|Steghide Commands]]
## Purpose
Steghide hides and extracts data in image (JPEG, BMP) and audio (WAV) files using passphrase-based steganography. Use it to hide a small file inside an image or reveal hidden content if you know (or brute-force) the passphrase.

## Scenarios
- CTF: Extract a hidden file from an image when the challenge says "stego" or provides a suspicious image.  
- Real world: Demonstrate risks of hidden content in media during an assessment or extract hidden artifacts in incident response.

## All needed info to run
- Install: `apt install steghide`.  
- Basic commands:
  - `steghide embed -cf cover.jpg -ef secret.txt -sf out.jpg` → embed `secret.txt` into `out.jpg` (prompts for passphrase)  
  - `steghide extract -sf out.jpg -xf secret.txt` → extract `secret.txt` from `out.jpg` (prompts for passphrase)  
  - `steghide info <file>` → show if file contains embedded data (gives capacity info)  
- Passphrase required to extract; if unknown, use wordlists to brute-force (external wrappers/scripts help).

## Example commands & outputs
```bash
# Check if an image has steghide data
$ steghide info suspicious.jpg
# Output snippet:
# steghide v0.5.1
# "suspicious.jpg":
#  embedded file "secret.txt", size: 1234 bytes, 
#  method: aes-256, compressed: yes

# Extract embedded file (will prompt for passphrase)
$ steghide extract -sf suspicious.jpg -xf secret.txt
Enter passphrase: ********
# Output: wrote extracted data to "secret.txt"

# Embed a file (will prompt for passphrase)
$ steghide embed -cf cover.jpg -ef secret.txt -sf out.jpg
Enter passphrase: ********
# Output: embedding successful
```

!!! note "Steghide Basics"
	- `steghide info <file>` is your first check to see if data is embedded.
	- Extraction requires the correct passphrase; if unknown, try context-derived wordlists from Cewl or common lists.
	- Steghide supports compression + AES encryption — check method in `steghide info`.
	- Don’t overwrite originals when embedding; work on copies.

### [[Kali Tools#Steghide|Steghide Commands]]