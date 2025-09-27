#### Official Documentation: [https://github.com/eteran/edb-debugger](https://github.com/eteran/edb-debugger)
#### Cheat Sheet: [[Kali Tools#Edb-debugger|Edb-debugger Commands]]
## Purpose
Edb (Evan's Debugger) is a graphical x86/x86_64 debugger with a user-friendly GUI for stepping, setting breakpoints, viewing memory, registers, and disassembly. It’s great for beginners who want a visual debugger.

## Scenarios
- CTF: Step through a crackme or vulnerable binary to find how a check works and extract a flag.  
- Real world: Debug a native program to inspect registers and memory when reproducing a crash or analyzing malware in a controlled lab.

## All needed info to run
- Edb is GUI-based (`edb` or `edb -p <pid>`). On Kali it can be installed via package manager or downloaded.  
- Run as the user that can access the binary/process (root only if necessary).  
- Key UI areas: register pane, stack/memory view, disassembly, breakpoints, hex dump, gadget search.  
- Useful actions:
  - Open binary: `File -> Open` or `edb <binary>`  
  - Attach to running process: `edb -p <pid>` or use GUI attach.  
  - Set breakpoint: click an instruction or right-click -> Breakpoint.  
  - Step/Continue: Step Into (F7), Step Over (F8), Continue (F9).  
  - Memory dump / save memory regions via context menu.

## Example commands & outputs
```bash
# Launch Edb and open a binary (graphical)
$ edb ./vuln_binary
# GUI opens. Use the disassembly pane to set a breakpoint at main and press F9 to run.
# Example observed register output in GUI after breakpoint:
# EAX: 0x0  EBX: 0x7ffff7dd18c0  ECX: 0x1  EIP: 0x0040056d

# Attach to running PID 1234
$ edb -p 1234
# GUI shows current threads, registers, and stack for PID 1234

# Save memory region from GUI (hex dump) -> exported to file for offline analysis
```

!!! note "Edb Basics"
	- Edb is GUI-first — good for beginners who want visual register/memory/disasm views.
	- Use `edb -p <pid>` to attach to a running process and inspect live state.
	- When debugging set breakpoints at `main` or known functions to avoid stepping through startup code.
	- Save memory/dump files from the GUI to analyze with strings or other tools offline.

### [[Kali Tools#Edb-debugger|Edb-debugger Commands]]