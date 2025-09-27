## Purpose
Linux is a multi-user system, meaning multiple people can use the same machine with different permissions. Users and groups control access to files, processes, and commands. Understanding how to manage users and groups is key for system administration, privilege escalation in CTFs, and maintaining security in the real world.

## Core Commands
```bash
$ whoami
nick
#Prints the current logged-in user

$ id
uid=1000(nick) gid=1000(nick) groups=1000(nick),27(sudo)
#Shows user ID, group ID, and group memberships

$ su root
Password:
#Switches current user to "root" (requires root password)

$ sudo ls /root
#Runs "ls /root" as root using sudo (requires user to be in sudo group)

$ adduser testuser
#Creates a new user "testuser"

$ cat /etc/passwd
nick:x:1000:1000:nick:/home/nick:/bin/bash
#Shows all user accounts, their IDs, home directories, and default shells
```

!!! note "User & Group Basics"  
	- Every file and process belongs to a **user** and a **group**.  
	- `sudo` allows temporary root privileges if the user is in the sudoers file.  
	- `/etc/passwd` stores user account details (but not passwords — those are in `/etc/shadow`).  
	- Groups allow permissions to be shared among multiple users.

### [[Linux Basics#07 - Users and Groups|Users and Groups Commands]]