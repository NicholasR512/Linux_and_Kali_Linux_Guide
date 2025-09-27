## Purpose
Services are background processes that start at boot and provide functionality like web servers, databases, or SSH. In CTFs, understanding services is key to finding attack vectors. In the real world, sysadmins and penetration testers manage services to keep systems secure and running properly.

## Core Commands
```bash
$ systemctl status ssh
#Checks Status of "ssh" Service

$ systemctl start apache2
#Starts "apache2" Web Server Service

$ systemctl stop apache2
#Stops "apache2" Web Server Service

$ systemctl enable apache2
#Enables "apache2" to Start at Boot

$ service apache2 restart
#Restarts "apache2" Service (Older Syntax)
```

!!! note "Services Basics"  
	- `systemctl` is the modern command for managing services (systemd).  
	- `service` is legacy but still works on many systems.  
	- Services are critical attack points in CTFs (e.g., misconfigured Apache, MySQL).  
	- Always check what services are running on a target system.

### [[Linux Basics#22 - Services|Services Commands]]
