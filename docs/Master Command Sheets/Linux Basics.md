#### [[01 - File Navigation]]
- `$ pwd` -> prints current path
- `$ ls` -> prints non-hidden directory contents
- `$ ls -l` -> prints non-hidden directory contents + more info
- `$ cd <dir name>` -> changes current directory to `<dir name>`
- `$ cd ..` -> changes current directory to one directory higher
- `$ cd ~` -> changes current directory to home directory
#### [[02 - Hidden Files]]
- `$ ls -a` -> prints non-hidden and hidden directory contents
- `$ ls -la` -> prints non-hidden and hidden directory contents + more info
#### [[03 - File Operations]]
- `$ mkdir <dir name>` -> creates directory `<dir name>`
- `$ touch <file name>` -> creates file `<file name>`
- `$ mv <file name> <new path>` -> moves file `<file name>` into `<new path>`
- `$ mv <file name> <new file name>` -> renames file `<file name>` to `<new file name>`
- `$ cp <file name> <copy name>` -> copies `<file name>` into `<copy name>` (same contents, 2 files now)
- `$ cp -r <dir name> <copy name>` -> copies directory `<dir name>` and its contents into `<copy name>`
- `$ rm <file name>` -> deletes `<file name>`
- `$ rm -r <dir name>` -> deletes directory `<dir name>` and its contents
- `$ rmdir <dir name>` -> deletes empty directory `<dir name>`
#### [[04 - Viewing Files]]
- `$ cat <file>` -> prints entire contents of `<file>`
- `$ less <file>` -> opens `<file>` in scrollable pager (arrow keys, `q` to quit)
- `$ head <file>` -> prints first 10 lines of `<file>`
- `$ head -n <num> <file>` -> prints first `<num>` lines of `<file>`
- `$ tail <file>` -> prints last 10 lines of `<file>`
- `$ tail -n <num> <file>` -> prints last `<num>` lines of `<file>`
- `$ tail -f <file>` -> prints and follows changes in `<file>` in real time
#### [[05 - Searching Files]]
- `$ find <path> -name <pattern>` -> searches `<path>` for files matching `<pattern>`
- `$ find <path> -type f` -> lists all files in `<path>`
- `$ find <path> -type d` -> lists all directories in `<path>`
- `$ locate <filename>` -> quickly finds paths containing `<filename>`
- `$ grep <pattern> <file>` -> prints lines in `<file>` containing `<pattern>`
- `$ grep -r <pattern> <dir>` -> searches all files in `<dir>` for `<pattern>`
- `$ grep -i <pattern> <file>` -> searches `<file>` ignoring case
- `$ which <command>` -> shows path of `<command>` if installed
- `$ whereis <command>` -> shows all locations of `<command>` (binary, source, man page)
#### [[06 - File Permissions]]
- `$ ls -l` -> shows permissions, owner, group, and file info
- `$ chmod <mode> <file>` -> changes file permissions (e.g., `755` or `+x`)
- `$ chown <user>:<group> <file>` -> changes ownership of file
- `$ groups` -> shows groups the current user belongs to
- `$ umask` -> shows default permission mask for new files
#### [[07 - Users and Groups]]
- `$ whoami` -> prints current logged-in user
- `$ id` -> shows user ID, group ID, and memberships
- `$ su <user>` -> switch to another user account
- `$ sudo <command>` -> run command with root privileges
- `$ adduser <username>` -> create new user
- `$ cat /etc/passwd` -> shows user account info
#### [[08 - Processes]]
- `$ ps` -> shows running processes for current shell
- `$ ps aux` -> shows all running processes with details
- `$ top` -> real-time interactive process monitor
- `$ htop` -> user-friendly interactive process monitor
- `$ kill <PID>` -> kills process with given PID
- `$ jobs` -> lists background jobs in shell
- `<command> &` -> runs command in background
- `$ fg %<job>` -> brings background job to foreground
- `$ bg %<job>` -> resumes job in background
#### [[09 - System Info]]
- `$ uname -a` -> prints kernel name, version, machine, and system info
- `$ hostname` -> prints the system’s hostname
- `$ uptime` -> shows system uptime, logged-in users, and load averages
- `$ df -h` -> shows disk space usage (human-readable)
- `$ free -m` -> shows memory usage in MB
#### [[10 - Networking Basics]]
- `$ ifconfig` -> shows network interfaces and IP addresses (legacy)
- `$ ip a` -> shows network interfaces and IP addresses (modern)
- `$ ping <host>` -> tests connectivity to `<host>`
- `$ netstat -tuln` -> shows active connections and listening ports (deprecated)
- `$ ss -tuln` -> shows active connections and listening ports (modern)
- `$ curl <url>` -> fetches and displays contents from `<url>`
- `$ wget <url>` -> downloads file(s) from `<url>`
#### [[11 - Archives and Compression]]
- `$ tar -cvf <archive.tar> <files>` -> create tar archive
- `$ tar -xvf <archive.tar>` -> extract tar archive
- `$ tar -czvf <archive.tar.gz> <files>` -> create compressed tar.gz archive
- `$ tar -xzvf <archive.tar.gz>` -> extract tar.gz archive
- `$ gzip <file>` -> compress file into .gz
- `$ gunzip <file.gz>` -> decompress .gz file
- `$ zip <archive.zip> <files>` -> create zip archive
- `$ unzip <archive.zip>` -> extract zip archive
#### [[12 - Editors]]
- `$ nano <file>` -> open file in nano editor
- `$ vim <file>` -> open file in vim editor
- `$ gedit <file>` -> open file in gedit GUI editor
#### [[13 - Scripting Basics]]
- `#!/bin/bash` -> shebang to define shell for script
- `$ nano <script.sh>` -> create/edit script file
- `$ chmod +x <script.sh>` -> make script executable
- `$ ./<script.sh>` -> run script
#### [[14 - Environment Variables]]
- `$ echo $PATH` -> prints PATH variable
- `$ export <VAR>=<value>` -> sets environment variable for session
- `$ echo $VAR` -> prints value of variable
- `$ nano ~/.bashrc` -> edit bashrc to make variables permanent
#### [[15 - Symbolic Links]]
- `$ ln -s <target> <link>` -> create symbolic link to target
- `$ ls -l` -> shows symlinks and their targets
- `$ cat <symlink>` -> follows symlink and prints target contents
#### [[16 - Package Management]]
- `$ sudo apt update` -> update package list
- `$ sudo apt upgrade` -> upgrade installed packages
- `$ sudo apt install <pkg>` -> install package
- `$ sudo apt remove <pkg>` -> remove package
- `$ dpkg -i <file.deb>` -> install from local .deb file
- `$ apt-cache search <term>` -> search package repositories
#### [[17 - Logging]]
- `/var/log/` -> main system log directory
- `$ cat /var/log/auth.log` -> view authentication logs
- `$ tail -f /var/log/syslog` -> follow system log in real time
- `$ dmesg` -> view kernel messages
#### [[18 - Redirection & Pipes]]
- `> <file>` -> overwrite file with command output
- `>> <file>` -> append command output to file
- `< <file>` -> use file as input to command
- `<cmd1> | <cmd2>` -> pipe output of cmd1 into cmd2
#### [[19 - Wildcards & Globbing]]
- `*` -> matches zero or more characters
- `?` -> matches exactly one character
- `[abc]` -> matches one character in set
#### [[20 - Cron Jobs]]
- `$ crontab -l` -> list cron jobs
- `$ crontab -e` -> edit cron jobs
- `0 0 * * * <cmd>` -> run command every day at midnight
- `$ systemctl status cron` -> check cron service
#### [[21 - SSH Basics]]
- `$ ssh user@host` -> connect to host as user
- `$ ssh -p <port> user@host` -> connect with custom port
- `$ ssh -i <key> user@host` -> connect with SSH key
- `$ scp <file> user@host:/path>` -> copy file to remote host
#### [[22 - Services]]
- `$ systemctl status <service>` -> check service status
- `$ systemctl start <service>` -> start service
- `$ systemctl stop <service>` -> stop service
- `$ systemctl enable <service>` -> enable service at boot
- `$ service <service> restart` -> restart service (legacy)