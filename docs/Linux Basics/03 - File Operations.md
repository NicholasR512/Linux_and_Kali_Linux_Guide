## Purpose
File operations are critical when working in the command line. File operations allow you to make, copy, and remove files and directories just from the command line. Being able to add, remove, and move files to create and clean workspaces is crucial for jobs like a system admin all the way up to a professional pen tester. These skills will stick with you no matter what you do.

## Core Commands
```bash
$ mkdir testDir
#Creates The Directory/Folder "testDir" In Whatever Your Current Directory Is

$ touch test.txt 
#Creates The File "test.txt" In Whatever Directory You Are In

$ mv test.txt /home/nick/Desktop
#Moves "test.txt" From Its Current Directory To "/home/nick/Desktop"

$ mv test.txt rename.txt
#Renames "test.txt" to "rename.txt"

$ cp test.txt copy.txt
#Copies The File "test.txt" and Its Contents Into "copy.txt" So Now There Is "test.txt" and "copy.txt" With The Same Contents

$ cp -r testDir copyDir/
#Copies The Directory "testDir" and Its Contents Into "copyDir" So Now There Is "testDir" and "copyDir" With The Same Contents

$ rm test.txt
#Removes/Deletes "test.txt"

$ rm -r testDir
#Removes/Deletes "testDir" and Its Contents

$ rmdir testDir
#Removes/Delets "testDir" ONLY WORKS FOR EMPTY DIRECTORIES
```


!!! tip "Good Practice"
	- When working with important files that you don't want to mess up, making a copy and working on the copy is always a good idea
	- Be careful when deleting files because it can be difficult or even impossible to get them back
	- rmdir is to delete empty directories while rm -r is to delete directories with contents


### [[Linux Basics#03 - File Operations|File Operations Commands]]
