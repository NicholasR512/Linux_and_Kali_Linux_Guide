#### Official Documentation: [https://github.com/ReFirmLabs/binwalk](https://github.com/ReFirmLabs/binwalk)
#### Cheat Sheet: [[Kali Tools#Binwalk|Binwalk Commands]]
## Purpose
Binwalk is a firmware analysis tool that scans binary blobs to find embedded file systems, compressed archives, and firmware components. It extracts and lists embedded data for analysis.

## Scenarios
- CTF: Analyze a firmware blob / binary dump to extract embedded files that contain flags or credentials.  
- Real world: Reverse engineer router or IoT firmware to find configuration files, keys, or backdoors.

## All needed info to run
- Install via package manager (`apt install binwalk`) or pip for latest. `binwalk` often uses `dd`, `strings`, `tar`, and `unsquashfs` for extraction.  
- Common flags:
  - `-e` → automatic extraction of found files  
  - `-D <fmt>:<cmd>` → custom extraction commands for specific signatures  
  - `-B` → raw signature scan (fast)  
  - `--dd` → extract by file type with explicit mapping  
- Output: directory `_<filename>.extracted/` containing extracted files and extracted offsets listing.

## Example commands & outputs
```bash
# Scan for signatures
$ binwalk firmware.bin
# Output snippet:
# DECIMAL       HEXADECIMAL     DESCRIPTION
# --------------------------------------------------------------------------------
# 64            0x40            gzip compressed data, max compression, from Unix
# 4096          0x1000          Squashfs filesystem, little endian, version 4.0, size: 1234567 bytes

# Extract automatically
$ binwalk -e firmware.bin
# Output:
# Creating directory: _firmware.bin.extracted
# Extracted gzip: _firmware.bin.extracted/64.gz
# Extracted squashfs filesystem: _firmware.bin.extracted/1000.squashfs

# Inspect extracted filesystem
$ ls _firmware.bin.extracted/1000.squashfs-root/
bin  etc  usr  www
# Search for strings/flags
$ grep -R "flag{" _firmware.bin.extracted || true
# _firmware.bin.extracted/1000.squashfs-root/www/index.html: <!-- flag{example_flag} -->
```

!!! note "Binwalk Basics"
	- Use `binwalk -e` to auto-extract embedded files; check `_filename.extracted/` for results.
	- For SquashFS or other FS images, use `unsquashfs` or mount loopback to inspect files.
	- `--dd` and `-D` allow custom extraction rules for tricky signatures.
	- Always inspect extracted content with strings/grep and check for credentials or flags.


### [[Kali Tools#Binwalk|Binwalk Commands]]
