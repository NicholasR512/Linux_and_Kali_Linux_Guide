#### Official Documentation: [https://radare.org/n/radare2.html](https://radare.org/n/radare2.html)
#### Cheat Sheet: [[Kali Tools#Radare2|Radare2 Commands]]
## Purpose
Radare2 (r2) is a powerful command-line reverse engineering framework supporting disassembly, analysis, binary patching, scripting, and more. It’s very scriptable and used for deep binary analysis.

## Scenarios
- CTF: Perform static analysis of a challenge binary to find functions, decode obfuscated code, and patch binaries.  
- Real world: Advanced reversing, automating analysis pipelines, and creating reproducible analysis scripts.

## All needed info to run
- r2 installed (`radare2` / `r2`). Use `r2 -v` to check version.  
- Basic workflow:
  - `r2 -A <binary>` → open and run auto-analysis (`-A` runs `aa`/`af` etc.).  
  - Inside r2 shell:
    - `aa` → analyze all  
    - `afl` → list functions  
    - `pdf @ main` → print disassembly of function `main`  
    - `s main` → seek to `main` address  
    - `px` / `pxj` → hexdump (json)  
    - `iz` → list strings  
    - `VV` → visual mode (press `V` twice) for interactive disassembly UI  
    - `e asm.arch=x86` → set architecture option if needed  
  - Use `rizin` fork or `radare2` depending on your preference (radare2 remains standard in Kali).  
- Save changes / patch with `wt` or use `wx` to write bytes.

## Example commands & outputs
```bash
# Run r2 with auto analysis
$ r2 -A ./vuln_binary
[0x00400520]> aa
[0x00400520]> afl
0x00400540  24   1  sym.main
[0x00400520]> pdf @ sym.main
# prints disassembly of sym.main

# Visual mode
[0x00400520]> VV
# Opens curses-based visual disasm UI (navigate with keyboard)

# Print strings
[0x00400520]> iz
# 0x00400600  12  "flag{example_flag}"

# Seek and hexdump
[0x00400520]> s 0x00400600
[0x00400600]> px 32
# hex bytes printed
```

!!! note "Radare2 Basics"
	- `r2 -A` runs quick auto-analysis but you can run `aa`/`af` step-by-step for control.
	- Use `VV` visual mode for a more interactive disassembly experience.
	- `afl` lists functions and `pdf @ <func>` prints disassembly for a function.
	- Radare2 has a steep learning curve but is extremely powerful and scriptable; keep a cheat sheet for common commands.


### [[Kali Tools#Radare2|Radare2 Commands]]