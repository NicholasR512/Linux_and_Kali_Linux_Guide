## Purpose
Environment variables store configuration values that control how processes run. In CTFs, they can reveal hidden paths or misconfigurations. In real-world scenarios, sysadmins and penetration testers check variables like `$PATH` to debug issues or configure tools.

## Core Commands
```bash
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
#Prints The Current PATH Variable

$ export TEST=hello
#Creates a Temporary Environment Variable "TEST" with Value "hello"

$ echo $TEST
hello
#Prints Value of TEST Variable

$ nano ~/.bashrc
#Opens Bash Configuration File Where You Can Add Permanent Variables
```

!!! note "Environment Variables Basics"  
	- `$PATH` defines where the system looks for executables.  
	- `export` sets variables for the current session.  
	- Adding variables to `~/.bashrc` makes them permanent across sessions.  
	- Misconfigured environment variables can break tools or create exploits.

### [[Linux Basics#14 - Environment Variables|Environment Variables Commands]]
