## Purpose
Logs provide critical information about what is happening on a system. In CTFs, checking logs can reveal misconfigurations, failed logins, or hidden activity. In the real world, sysadmins and penetration testers rely on logs for troubleshooting, monitoring, and forensic analysis.

## Core Commands
```bash
$ cd /var/log
#Default Directory That Contains System and Application Logs

$ ls /var/log/
auth.log  syslog  dmesg  kern.log
#Lists Common Logs (Authentication, System, Kernel)

$ cat /var/log/auth.log
#View Authentication Log Entries

$ tail -f /var/log/syslog
#Follow the System Log in Real Time

$ dmesg | less
#Displays Kernel Ring Buffer Messages (Hardware/Driver Info)
```

!!! note "Logging Basics"  
	- `/var/log/` is the main directory for logs.  
	- `auth.log` → authentication attempts; `syslog` → general system events; `dmesg` → kernel info.  
	- `tail -f` is great for live monitoring logs during attacks or troubleshooting.  
	- Logs are key in incident response and digital forensics.

### [[Linux Basics#17 - Logging|Logging Commands]]
