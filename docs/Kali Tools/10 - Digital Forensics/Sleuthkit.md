#### Official Documentation: [https://www.sleuthkit.org/](https://www.sleuthkit.org/)
#### Cheat Sheet: [[Kali Tools#Sleuthkit|Sleuthkit Commands]]
## Purpose
The Sleuth Kit (TSK) is a collection of command-line tools for filesystem and disk image forensics: listing files, carving, extracting file metadata, and examining partition layouts.

## Scenarios
- CTF: Use TSK to list deleted files, carve data from images, or recover specific inode contents containing flags.  
- Real world: Analyze disk images to reconstruct user activity, recover deleted evidence, and parse file system metadata.

## All needed info to run
- Tools included: `mmls` (partition layout), `fls` (list files and deleted entries), `icat` (extract file by inode), `fsstat` (filesystem info), `tsk_recover` (recover files).  
- Basic workflow:
  1. `mmls image.dd` → view partition table and offsets.  
  2. `fls -r -m / image.dd` → list files recursively with metadata and deleted markers.  
  3. `icat image.dd <inode> > file_recovered` → extract file content by inode.  
  4. `tsk_recover image.dd output_dir/` → recover many files.  
- Most commands require specifying the offset for embedded filesystems (`-o <offset>`), where offset is usually from `mmls` output (in sectors).

## Example commands & outputs
```bash
# Show partition layout
$ mmls image.dd
# Output snippet:
# DOS Partition Table
# Offset Sector: 0
# Slot  Start      End        Length      Description
# 0:    2048        209919     207872      Linux

# List files including deleted (-r recursive)
$ fls -r -m / image.dd
# Output snippet:
# r/r  1234:  file.txt
# d/d  1235:  deleted.txt

# Extract a file by inode
$ icat image.dd 1234 > recovered_file.txt
# recovered_file.txt now contains the file content

# Recover all files
$ tsk_recover image.dd recovered_files/
# Recovered X files to recovered_files/
```

!!! note "Sleuthkit Basics"
	- Use `mmls` first to get partition offsets; pass `-o <offset>` to tools when necessary.
	- `fls` shows deleted entries (prefixed with `r`/`d` markers).
	- `icat` extracts file contents by inode; useful when filenames are gone.
	- Work on copies of images — never write back to original evidence files.

### [[Kali Tools#Sleuthkit|Sleuthkit Commands]]
