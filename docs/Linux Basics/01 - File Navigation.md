## Purpose
One of the most important skills to know inside the linux command line is how to navigate through the filesystem. This can be useful to show where you are, move to different directories to see whats inside, and more.

## Core Commands
```bash
$ pwd 
/home/nick
#Prints Directory You Are Currently In

$ ls
Desktop  Documents  Downloads  full_scan.txt  Music  Pictures  Public  Templates  Videos
#Lists Non-Hidden Directory Contents

$ ls -l
total 36
drwxr-xr-x 2 nick nick 4096 Aug 25 15:04 Desktop
drwxr-xr-x 2 nick nick 4096 Aug 28 21:09 Documents
drwxr-xr-x 2 nick nick 4096 Aug 25 15:04 Downloads
-rw-rw-r-- 1 nick nick  494 Aug 26 17:23 full_scan.txt
drwxr-xr-x 2 nick nick 4096 Aug 25 15:04 Music
drwxr-xr-x 2 nick nick 4096 Aug 25 15:04 Pictures
drwxr-xr-x 2 nick nick 4096 Aug 25 15:04 Public
drwxr-xr-x 2 nick nick 4096 Aug 25 15:04 Templates
drwxr-xr-x 2 nick nick 4096 Aug 25 15:04 Videos
#Lists Non-Hidden Directory Contents With More Info

$ cd <directory name>
#Changes Your Current Directory To <directory name>

$ cd ..
#Changes Your Current Directory To The Directory Your Current Directory Is In (Moves Up A Level)

$ cd ~
#Changes Your Current Directory Back To Your Home Directory
```


!!! tip "Absolute vs Relative Paths"
	- Absolute Path disregards the current directory you are in, and you move to any specific path | `$ cd /home/nick/Downloads`
		- must start with */*
	- Relative Path takes into account what your current directory so you don't have to type the full path out. Lets say I'm in */home/nick* and I want to get to *Downloads* | `$ cd Downloads` 

### [[Linux Basics#01 - File Navigation|File Navigation Commands]]


