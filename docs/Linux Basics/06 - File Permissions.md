## Purpose
File permissions are one of the most important parts of Linux because they control who can read, write, or execute files and directories. Understanding permissions is crucial for security, whether you are managing a system, working in a team environment, or doing a CTF challenge where permissions may block or allow access to important files. Hackers, sysadmins, and pen testers all need to know how to view and modify permissions to keep systems secure or to escalate privileges.

## Core Commands
```bash
$ ls -l
-rw-r--r--  1 nick nick   220 Aug 25 14:57 example.txt
#Shows permissions, owner, group, size, and date of each file

$ chmod 755 script.sh
#Changes permissions of "script.sh" to rwxr-xr-x (owner can read/write/execute, group and others can read/execute)

$ chmod +x script.sh
#Adds execute permission to "script.sh" for everyone

$ chown root:root example.txt
#Changes ownership of "example.txt" to user "root" and group "root"

$ groups
nick : nick sudo
#Shows which groups the current user belongs to

$ umask
0022
#Shows the default permission mask for newly created files/directories
```

!!! tip "Tips for Permissions"  

	- The 3 permission types are **read (r)**, **write (w)**, and **execute (x)**.  
	- The 3 permission levels are **owner**, **group**, and **others**.  
	- `chmod` can use either **numbers (e.g., 755)** or **symbols (e.g., +x, -w)**.  
	- `umask` controls the default permissions when new files or folders are created.

### [[Linux Basics#06 - File Permissions|File Permissions Commands]]