#### Official Documentation: [https://github.com/skylot/jadx](https://github.com/skylot/jadx)
#### Cheat Sheet: [[Kali Tools#Jadx|Jadx Commands]]
## Purpose
Jadx is an Android decompiler that converts APK bytecode (DEX) into readable Java-like source. It’s useful for analyzing Android apps, finding strings, API usage, and logic without running the app.

## Scenarios
- CTF: Inspect an APK to find hardcoded keys, flags, or logic that reveals vulnerabilities.  
- Real world: Audit Android apps for insecure code, sensitive keys in resources, or suspicious behavior.

## All needed info to run
- Jadx has a GUI (`jadx-gui`) and CLI (`jadx`). On Kali you can install jadx or download the binary from repo.  
- Typical commands:
  - GUI: `jadx-gui app.apk` → interactive browse of decompiled source.  
  - CLI: `jadx -d out/ app.apk` → decompile and save Java-like sources to `out/`.  
  - `jadx -r` → no-resources option; `-j <threads>` → parallel threads.  
- Inspect resources: `apktool` can decode resources if needed, but Jadx shows `strings` and Java code.  
- Have Java installed for GUI.

## Example commands & outputs
```bash
# Launch GUI for interactive browsing
$ jadx-gui app.apk
# GUI shows package tree, decompiled Java files, and search box for strings/classes.

# CLI decompile to folder
$ jadx -d out app.apk
# Output:
# Processing classes...
# Decompilation completed. Sources saved to out/

# Search for suspicious strings (e.g., API key)
$ grep -R "API_KEY" out/
# out/smali/... : String API_KEY = "abcd1234"
```

!!! note "Jadx Basics"
	- Use `jadx-gui` for quick browsing and string/class search; CLI for batch decompiles.
	- Decompiled code is Java-like and may not compile; logic is usually readable though.
	- For resource translation or manifest details combine with `apktool` for full decoding.
	- Respect app licenses and only analyze APKs you are allowed to inspect.


### [[Kali Tools#Jadx|Jadx Commands]]