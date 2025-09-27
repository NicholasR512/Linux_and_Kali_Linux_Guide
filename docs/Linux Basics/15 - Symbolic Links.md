## Purpose
Symbolic links (symlinks) are pointers to other files or directories. They are commonly used to reference files in different locations without duplicating them. In CTFs, symlinks can help redirect processes or uncover hidden file paths. In the real world, they are useful for organizing files, managing configs, and maintaining compatibility.

## Core Commands
```bash
$ ln -s /home/nick/test.txt link.txt
#Creates a Symbolic Link "link.txt" That Points to "test.txt"

$ ls -l
lrwxrwxrwx 1 nick nick    8 Sep 21 17:30 link.txt -> test.txt
#Shows "link.txt" as a Symlink to "test.txt"

$ cat link.txt
hello world
#Accessing "link.txt" Shows the Contents of "test.txt"
```

!!! note "Symbolic Links Basics"  
	- `ln -s` creates a **soft link** (pointer) instead of copying.  
	- Deleting the symlink doesn’t remove the original file.  
	- If the original file is deleted, the symlink becomes broken.  
	- Useful for config files, version control, and redirecting paths.

### [[Linux Basics#15 - Symbolic Links|Symbolic Links Commands]]
