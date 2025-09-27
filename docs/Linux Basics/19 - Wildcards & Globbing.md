## Purpose
Wildcards and globbing allow you to select groups of files and directories without typing them all out. They are extremely useful in CTFs for quickly filtering file lists or searching through directories. In the real world, sysadmins and penetration testers use them to work with large sets of files efficiently.

## Core Commands
```bash
$ ls *.txt
#Lists All Files Ending in ".txt"

$ ls file?.txt
#Lists Files Like file1.txt, file2.txt, fileA.txt (Single Character Match)

$ ls [ab]*.txt
#Lists Files Starting With "a" or "b" That End in ".txt"

$ rm *.log
#Deletes All Files Ending in ".log"
```

!!! note "Wildcards & Globbing Basics"  
	- `*` → matches zero or more characters.  
	- `?` → matches exactly one character.  
	- `[ ]` → matches any character in the brackets.  
	- Great for bulk operations, but dangerous with commands like `rm`.

### [[Linux Basics#19 - Wildcards & Globbing|Wildcards & Globbing Commands]]