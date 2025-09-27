## Purpose
Knowing basic system information is important when working on Linux machines. In CTFs you may need to learn about the environment you are working in to figure out what you can and cannot do. In the real world, system admins and penetration testers use these commands to check kernel versions, uptime, resource usage, and available space. These commands give you a quick way to learn about the system without needing a GUI.

## Core Commands
```bash
$ uname -a
Linux kali 6.6.9-kali9-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.6.9-1kali1 (2024-01-10) x86_64 GNU/Linux
#Prints Kernel Name, Version, Machine, and Other System Info

$ hostname
kali
#Prints The Name of The System

$ uptime
 16:40:17 up  1:23,  2 users,  load average: 0.10, 0.21, 0.18
#Shows How Long The System Has Been Running, How Many Users Logged In, and System Load Averages

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2.0G     0  2.0G   0% /dev
tmpfs           394M  1.6M  392M   1% /run
/dev/sda1        50G   20G   28G  42% /
#Shows Disk Space Usage of All File Systems in Human-Readable Format (-h)

$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3940        1486         912         156        1541        2112
Swap:          2047           0        2047
#Shows Memory Usage in Megabytes (-m)
```


!!! note "System Info Basics"  
	- `uname -a` is helpful in CTFs for finding kernel version → may hint at kernel exploits.  
	- `hostname` is often used to identify machines when pivoting across networks.  
	- `uptime` can help detect if a system was recently rebooted (useful in attacks/log clearing).  
	- `df -h` and `free -m` are great for spotting low disk/memory, which can cause instability during attacks or scans.

### [[Linux Basics#09 - System Info|System Info Commands]]