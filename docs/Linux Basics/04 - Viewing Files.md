## Purpose
The ability to view and navigate file contents within the terminal is a key skill to have in CTFs and in the real world. Some servers don't have a graphical user interface to view file contents, so the terminal in the most convenient method to view the contents. These commands allow you to either see the full file or just a sneak peak so you can see if you are looking at the right file. System admins and pen testers use some of these commands to view the live actions of files. A LOT of CTFs involve you going through a secret file in order to find a hidden password.

## Core Commands
```bash
$ cat test.txt
hello world1 
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world11
#Prints The Contents of "test.txt" Into The Terminal

$ less test.txt
#Opens The File "test.txt" In a Scrollable Pager Where You Can Use Arrow Keys To Navigate | Type "q" To Quit

$ head test.txt
hello world1
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world
#Prints The First 10 Lines of "test.txt" Into The Terminal

$ head -n 3 test.txt
hello world1
hello world
hello world
#Prints The First 3 Lines of "test.txt"

$ tail test.txt
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world11
#Prints The Last 10 Lines of "test.txt" Into The Terminal

$ tail -n 3 test.txt
hello world
hello world
hello world11
#Prints The Last 3 Lines of "test.txt"

$ tail -f test.txt
hello world1 
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world
hello world11
#Prints The Contents of "test.txt" and Follows and Prints Changes in Real Time
```


!!! tip "Tips"
	- `$ tail -f` is useful when watching logs update | not used too much in CTFs
	- `$ cat` is good for smaller files, but it can be overwhelming for larger ones | use `$ less` for larger files


### [[Linux Basics#04 - Viewing Files|Viewing Files Commands]]