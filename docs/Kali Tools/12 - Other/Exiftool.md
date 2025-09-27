#### Official Documentation: [https://exiftool.org/exiftool_pod.html](https://exiftool.org/exiftool_pod.html)
#### Cheat Sheet: [[Kali Tools#Exiftool|Exiftool Commands]]
## Purpose
ExifTool reads and writes metadata from many file types (images, audio, documents). It's the go-to tool to find hidden metadata like camera model, timestamps, comments, and sometimes user-added strings.

## Scenarios
- CTF: Inspect an image submission for hidden metadata (comments, GPS, user fields) that may contain a flag.  
- Real world: Check files for leaked sensitive metadata (GPS coordinates in images, author names in documents) during investigations.

## All needed info to run
- Install: `apt install libimage-exiftool-perl` (package name) or `exiftool` binary.  
- Basic flags:
  - `exiftool <file>` → show all metadata  
  - `exiftool -a -u -g1 <file>` → show all tags, unknown tags, grouped by family 1  
  - `exiftool -list` → list supported tags  
  - `exiftool -TAG=<value> <file>` → write/edit tag (be careful; keep copies)  
  - `exiftool -csv -all <file>` → export metadata as CSV  
- Works on images (`.jpg/.png`), PDFs, Office docs, audio, etc.

## Example commands & outputs
```bash
# Show metadata for an image
$ exiftool photo.jpg
# Output snippet:
# File Name                       : photo.jpg
# Camera Model Name               : Canon EOS 80D
# Create Date                     : 2024:05:21 14:33:10
# GPS Longitude                   : -73.935242
# Artist                          : alice@example.com
# Comment                         : flag{example_flag_here}

# Show full tag groups and unknowns
$ exiftool -a -u -g1 photo.jpg
# Output shows tags grouped (EXIF, XMP, IPTC) including any weird custom fields

# Export metadata to CSV
$ exiftool -csv image.jpg > metadata.csv
```

!!! note "ExifTool Basics"
	- `exiftool <file>` shows most tags; use `-a -u -g1` to reveal all tags including unknown/custom ones.
	- Metadata may include sensitive info (GPS, emails, comments); check images, docs, and office files.
	- Avoid writing edits to originals; make a copy before using write flags.
	- Use `exiftool -csv` to export results for easy searching or reporting.

### [[Kali Tools#Exiftool|Exiftool Commands]]