## Purpose
Processes are programs that are running on your system. Being able to view, manage, and control processes is critical for system administration, performance monitoring, and in CTFs where you may need to identify suspicious processes or kill something that’s blocking you. Hackers and sysadmins alike need to know how to find and manage processes effectively.

## Core Commands
```bash
$ ps
  PID TTY          TIME CMD
 2342 pts/0    00:00:00 bash
 2451 pts/0    00:00:00 ps
#Lists currently running processes for the current shell

$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1 106240  8380 ?        Ss   08:00   0:03 systemd
#Shows all running processes with detailed info

$ top
#Opens interactive real-time process monitor (press q to quit)

$ htop
#Similar to top but more user-friendly and interactive (may need to be installed)

$ kill 2451
#Kills the process with PID 2451

$ jobs
[1]+  Running                 ping google.com &
#Lists background jobs in the current shell

$ command &
#Runs "command" in the background

$ fg %1
#Brings job 1 back to the foreground

$ bg %1
#Resumes job 1 in the background
```

!!! tip "Tips for Process Management"  
	- Use `ps aux | grep <process>` to search for a specific process.  
	- `kill -9 <PID>` force-kills a stubborn process.  
	- `top` and `htop` are great for monitoring CPU/memory usage in real time.  
	- Backgrounding with `&` is useful when running long commands so your shell stays usable.

### [[Linux Basics#08 - Processes|Processes Commands]]