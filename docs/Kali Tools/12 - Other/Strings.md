#### Official Documentation: [https://man7.org/linux/man-pages/man1/strings.1.html](https://man7.org/linux/man-pages/man1/strings.1.html)
#### Cheat Sheet: [[Kali Tools#Strings|Strings Commands]]
## Purpose
`strings` extracts printable character sequences from binary files. It's a fast first-pass tool to find hidden text, URLs, passwords, or flags inside executables, images, or memory dumps.

## Scenarios
- CTF: Quickly scan a binary, firmware image, or memory dump for obvious flags or credentials (`flag{...}`, URLs, API keys).  
- Real world: Triage binaries or memory captures to find plaintext secrets, hardcoded strings, or artifacts.

## All needed info to run
- `strings` is part of `binutils` (installed by default on Kali).  
- Basic flags:
  - `strings <file>` → print printable strings (default min length 4)  
  - `strings -n <length> <file>` → set minimum string length (e.g., `-n 6`)  
  - `strings -a <file>` → scan the entire file (disabled by default for some builds)  
  - `strings -t x <file>` → show offset in hex before each string  
- Combine with `grep` to focus on patterns: `strings file | grep -i flag`.

## Example commands & outputs
```bash
# Basic strings scan
$ strings firmware.bin | head -n 40
# Output snippet:
# /bin/sh
# admin:password123
# http://example.com/login
# flag{example_flag_here}

# Show offsets for strings (hex)
$ strings -t x memory.raw | grep -i password
# 1a2b3c password123

# Increase min length to 6 to reduce noise
$ strings -n 6 sample.bin | grep -i flag
# flag{hidden_flag}
```

!!! note "strings Basics"
	- `strings` is a quick triage tool — it prints anything printable, so expect noise.
	- Use `-n` to increase min-length and reduce false positives.
	- Pipe into `grep` for targeted searches (`flag`, `password`, `http`).
	- Great for scanning firmware, binaries, and memory dumps for quick leads.

### [[Kali Tools#Strings|Strings Commands]]