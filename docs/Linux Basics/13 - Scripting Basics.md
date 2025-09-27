## Purpose
Shell scripting is a core Linux skill. Scripts let you automate tasks, chain commands, and create repeatable tools. In CTFs, scripts can speed up repetitive exploitation. In the real world, sysadmins and penetration testers use them to manage systems and automate workflows.

## Core Commands
```bash
$ nano script.sh
#Creates/Edit a Script File "script.sh"

#!/bin/bash
echo "Hello World"
#Basic Script With Shebang and Command

$ chmod +x script.sh
#Gives Execution Permissions to "script.sh"

$ ./script.sh
Hello World
#Executes "script.sh"
```

!!! note "Scripting Basics"  
	- Always start scripts with a **shebang** (`#!/bin/bash`) to specify interpreter.  
	- `chmod +x` makes scripts executable.  
	- Useful for automating repetitive commands in CTFs or sysadmin tasks.

### [[Linux Basics#13 - Scripting Basics|Scripting Basics Commands]]
