## Purpose
Cron jobs allow you to schedule commands or scripts to run automatically at specific times. In CTFs, cron jobs can sometimes be exploited for persistence or privilege escalation. In the real world, they are essential for automating backups, maintenance, and monitoring tasks.

## Core Commands
```bash
$ crontab -l
#Lists Current User's Cron Jobs

$ crontab -e
#Edits the Current User's Cron Jobs

# Example Entry in crontab (runs script every day at midnight)
0 0 * * * /home/nick/backup.sh

$ systemctl status cron
#Checks Status of Cron Service
```

!!! note "Cron Jobs Basics"  
	- Cron jobs are defined in **crontab** files.  
	- Format: `minute hour day month weekday command`.  
	- `crontab -e` opens the editor to add new jobs.  
	- Useful for automation, but also a common target in privilege escalation.

### [[Linux Basics#20 - Cron Jobs|Cron Jobs Commands]]
