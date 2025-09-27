## Purpose
SSH (Secure Shell) is used to securely connect to remote systems. In CTFs, SSH is often a way to pivot or gain shell access once credentials are discovered. In the real world, sysadmins and penetration testers use SSH daily for remote management and file transfers.

## Core Commands
```bash
$ ssh user@192.168.1.10
#Connects to Remote Host at 192.168.1.10 as "user"

$ ssh -p 2222 user@192.168.1.10
#Connects Using Port 2222 Instead of Default Port 22

$ ssh -i id_rsa user@192.168.1.10
#Connects Using SSH Key "id_rsa" for Authentication

$ scp file.txt user@192.168.1.10:/home/user/
#Copies "file.txt" to Remote Host's /home/user/ Directory Using SSH
```

!!! note "SSH Basics"  
	- Default SSH port is **22**, but admins may change it.  
	- Keys (`id_rsa`, `id_ed25519`) are more secure than passwords.  
	- `scp` (secure copy) uses SSH to transfer files.  
	- Misconfigured SSH can be a major security risk in CTFs and real life.

### [[Linux Basics#21 - SSH Basics|SSH Basics Commands]]
