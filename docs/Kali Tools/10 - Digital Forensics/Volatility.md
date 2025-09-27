#### Official Documentation: [https://volatilityfoundation.org/](https://volatilityfoundation.org/)
#### Cheat Sheet: [[Kali Tools#Volatility|Volatility Commands]]
## Purpose
Volatility is a memory forensics framework used to analyze RAM captures for processes, network connections, loaded DLLs, command history, and other volatile artifacts.

## Scenarios
- CTF: Analyze a memory dump from a challenge VM to find strings, hidden processes, or credentials in memory.  
- Real world: Investigate live incidents by analyzing memory captures for malware processes, injected code, or active network sessions.

## All needed info to run
- Use either Volatility 2 (classic, many plugins) or Volatility 3 (actively developed). Install via package manager or pip in a virtualenv.  
- Input: memory image (raw `memory.dmp`, `lime`, `aff4`, etc.). Determine profile/OS (Volatility 2) or use auto-detection (Vol3).  
- Common Volatility 2 commands:
  - `vol.py -f mem.img --profile=LinuxUbuntu_... pslist` → list processes  
  - `vol.py -f mem.img --profile=... netscan` → show network connections (plugins vary by OS)  
  - `vol.py -f mem.img --profile=... strings` → search strings  
  - `vol.py -f mem.img --profile=... dumpfiles -D out/ -Q <offset>` → dump file-like objects
- Common Volatility 3 usage:
  - `vol -f mem.img windows.pslist` or `vol -f mem.img linux.pslist` (plugin names differ)  
  - `vol -f mem.img windows.dlllist` → list loaded DLLs  
  - `vol -f mem.img linux.lsof` → list open files/sockets
- Some plugins need debug symbols or extra requirements; check plugin docs.

## Example commands & outputs
```bash
# Volatility 2 example (Windows-like)
$ vol.py -f memory.dmp --profile=Win7SP1x64 pslist
# Output:
# Offset(P)          Name                    PID   PPID   Thds   Hnds   Time
# 0x1a2b3c4d0        explorer.exe            1234  1000   35     800    2025-09-01 12:00:00

# Volatility 3 example
$ vol -f memory.raw linux.pslist
# Output:
# PID   PPID   NAME
# 1     0      systemd
# 1234  1      bash

# Search for strings containing "password"
$ strings memory.raw | grep -i password || true
# output: "db_password=secret123"

# Dump a process memory region (Vol3 example)
$ vol -f memory.raw linux.dumpfiles --output-directory=out --pids=1234
# Output: files dumped to out/
```

!!! note "Volatility Basics"
	- Choose Volatility 2 or 3 based on plugin support for the OS/image; Vol3 is actively developed but plugin names differ.
	- Use `file` and `strings` as quick checks, then run `pslist`/`psscan` and `netscan`/`lsof` to find suspicious processes and connections.
	- Memory analysis can reveal credentials, injected shells, and in-memory-only artifacts not on disk.
	- Work on copies of memory captures and document each step for reproducibility.

### [[Kali Tools#Volatility|Volatility Commands]]
