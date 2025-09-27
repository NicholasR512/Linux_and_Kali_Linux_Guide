#### Official Documentation: [https://www.kali.org/tools/gdb/](https://www.kali.org/tools/gdb/)
#### Cheat Sheet: [[Kali Tools#Gdb|Gdb Commands]]
## Purpose
GDB is the GNU Debugger — a powerful command-line debugger for binaries. It supports breakpoints, stepping, inspecting memory/registers, core dump analysis, and scripting. It’s the core tool for low-level reverse engineering.

## Scenarios
- CTF: Attach to a challenge binary, set breakpoints, inspect arguments and memory to bypass checks or extract flags.  
- Real world: Analyze crashes, examine core dumps (`core`) to find root cause, and debug native code.

## All needed info to run
- GDB installed by default on Kali (`gdb`). For exploit dev use `gef` or `pwndbg` plugins for nicer UX.  
- Run with binary: `gdb ./binary` or attach to PID: `gdb -p <pid>`.  
- Useful commands:
  - `break <func|addr>` / `b main` → set breakpoint  
  - `run <args>` → start program with arguments  
  - `continue` / `c` → resume execution  
  - `step` / `s` → step into  
  - `next` / `n` → step over  
  - `info registers` → show registers  
  - `x/<fmt> <addr>` → examine memory (e.g., `x/32xb $rsp`)  
  - `disassemble <func>` → show disassembly  
  - `set follow-fork-mode child` → follow child after fork  
  - `core <corefile>` → analyze core dump: `gdb ./binary core.1234`
- For remote debugging use `target remote <host>:<port>` with `gdbserver`.

## Example commands & outputs
```bash
# Start gdb with a binary
$ gdb ./vuln_binary
(gdb) break main
Breakpoint 1 at 0x4005d6
(gdb) run arg1 arg2
# Program stops at breakpoint:
# Breakpoint 1, main () at vuln.c:10
(gdb) info registers
# rax 0x0 rbx 0x7fffffffe0c0 rcx ...
(gdb) x/32xb $rsp
# 0x7fffffffe0b0: 0x41 0x42 0x43 ...
(gdb) disassemble main
# Dump of assembler code for function main: ...

# Attach to running PID
$ gdb -p 4321
# Attaching to process 4321
```

!!! note "GDB Basics"
	- Use `gdb -q` to suppress startup messages.
	- Plugins like `pwndbg` or `gef` improve output (register display, heap info, one-liner commands).
	- Use `x/` to examine memory in different formats (b = byte, w = word, g = giant/8 bytes, s = string).
	- When analyzing crashes, load the core file with `gdb ./binary core` to inspect stack and registers at crash time.


### [[Kali Tools#Gdb|Gdb Commands]]