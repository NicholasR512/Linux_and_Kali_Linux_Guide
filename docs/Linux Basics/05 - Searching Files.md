## Purpose
Searching files has many time saving benefits. When doing a CTF and you encounter a massive file which has thousands or lines, or you encounter a folder with a bunch of different files an folders, you can easily search and and filter through them using all of these search commands. Another extremely useful case is your about to run a large command with a lot of typing, but your not even sure if you have that command installed on your device. You run a quick "which" command and your problem is solved.

## Core Commands
```bash
$ find ~ -name "test.txt"
/home/nick/Desktop/testDir/test.txt
/home/nick/Documents/test.txt
#Prints All the Paths of "test.txt" in my "home" Directory | "~" Can be Replaced With a Specific Path or a "." to Search Your Current Directory

$ find /home/nick/Documents -type f
/home/nick/Documents/bandit.txt
/home/nick/Documents/test2.txt
/home/nick/Documents/test.txt
#Prints All the Paths of Any Files in "/home/nick/Documents" | "/home/nick/Documents" can be replaced with "~" for "home" directory and "." for current directory

$ find /home/nick/Desktop -type d
/home/nick/Desktop
/home/nick/Desktop/testDir
#Prints All the Paths of Any Directories Located in "/home/nick/Desktop" | "/home/nick/Desktop" can be replaced with "~" for "home" directory and "." for current directory

$ locate bandit.txt
/home/nick/Documents/bandit.txt
#Prints All the Paths Containing "bandit.txt" 

$ grep hello test.txt
hello world
#Searches Through "test.txt" for Instances of "hello" -> Prints All Lines Containing "hello" 

$ grep -r this testDir
testDir/test2.txt:this a movie 
testDir/test.txt:this is a test 
#Searches Through All Files in "testDir" for Instances of "this" -> Prints All Files That Contain "this" Along With the Specific Lines 

$ which nmap
/usr/bin/nmap
#Prints the Loaction of "nmap" if "nmap" is Installed | If "nmap" isn't Installed "nmap not found" Would be Printed

$ whereis nmap
nmap: /usr/bin/nmap /usr/lib/nmap /usr/share/nmap /usr/share/man/man1/nmap.1.gz
#Prints All Locations of "nmap" if "nmap" is Installed | If "nmap" isn't Installed "nmap not found" Would be Printed
```


!!! tip "Difference"
	- `$ find` is used for finding specific files or file types
	- `$ locate` is used for a more general search of a file name
	- `$ grep` is used for finding specific words, chars, or numbers in the contents of files
	- `$ which` and `$ whereis` is used for finding if specific commands are installed | ex) You are going to run a nmap scan, but you aren't sure if nmap is installed on your device `$ which nmap` will show you


### [[Linux Basics#05 - Searching Files|Searching Files Commands]]
