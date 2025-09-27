#### Official Documentation: [https://www.autopsy.com/](https://www.autopsy.com/)
#### Cheat Sheet: [[Kali Tools#Autopsy|Autopsy Commands]]
## Purpose
Autopsy is a web-based digital forensics platform (GUI) that helps analyze disk images, recover files, examine timelines, and generate reports. It's a beginner-friendly frontend for The Sleuth Kit.

## Scenarios
- CTF: Load a disk image from a challenge to recover deleted files or find timestamps that point to flags.  
- Real world: Triage a disk image from an incident to find suspicious files, timeline activity, and produce an evidence report.

## All needed info to run
- Autopsy provides a GUI (runs on http://127.0.0.1:9999 by default). Install via package manager (`apt install autopsy`) or use the upstream installer.  
- Input: disk images (E01, raw `.dd`, `.img`) or local drives (read-only). Preferred workflow: create case → add image → run ingest modules.  
- Key ingest modules: File type identification, keyword search, timeline, hash lookup, EXIF parser, email parser.  
- Reports: export HTML/PDF with findings.  
- Permissions: run as a user that can read image files; the server runs as a service and the browser is used to interact.

## Example commands & outputs
```bash
# Start Autopsy (service or CLI launcher)
$ autopsy
# Output:
# Launching Autopsy server on http://127.0.0.1:9999
# Open browser and navigate to the URL, create a new case and add an image

# Typical GUI flow (no long CLI output):
# 1. Create Case -> Add Data Source -> Choose disk image (image.dd)
# 2. Select ingest modules (Timeline, File Type, Keyword Search)
# 3. Run ingest. Progress shown in GUI. Results: recovered files, hits, and timeline entries.

# Example result in GUI:
# Recovered Files: 124
# Keyword hits: 3 (strings: "flag{example}")
# Timeline: file created 2025-06-01 12:34:56
```

!!! note "Autopsy Basics"
	- Autopsy is GUI-first — run `autopsy` and use the browser to interact with cases and ingest modules.
	- Always work on copies of images (read-only ingest) to avoid changing evidence.
	- Use hash lookups (MD5/SHA1) to flag known-good/known-bad files quickly.
	- Export reports (HTML/PDF) for documentation and sharing with stakeholders.

### [[Kali Tools#Autopsy|Autopsy Commands]]
