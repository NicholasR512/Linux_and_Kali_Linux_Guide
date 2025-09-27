## Purpose
Redirection and pipes let you control input and output between commands. They are extremely powerful in both CTFs and real-world environments. You can save output to files, append results, or chain multiple commands together to process data efficiently.

## Core Commands
```bash
$ echo "hello" > file.txt
#Writes "hello" Into file.txt (Overwrites if Exists)

$ echo "world" >> file.txt
#Appends "world" to file.txt

$ cat < file.txt
#Reads file.txt Using Input Redirection

$ cat file.txt | grep hello
hello
#Pipes the Output of cat Into grep to Search for "hello"

$ ps aux | grep bash
nick      1234  0.0  0.1  12345  2345 ?        S    12:34   0:00 bash
#Finds Processes Containing "bash" by Piping ps Output Into grep
```

!!! note "Redirection & Pipes Basics"  
	- `>` overwrites, while `>>` appends.  
	- `<` redirects a file as input to a command.  
	- `|` pipes the output of one command into another.  
	- Common CTF trick: pipe command outputs into `grep` or `strings` to quickly extract info.

### [[Linux Basics#18 - Redirection & Pipes|Redirection & Pipes Commands]]
