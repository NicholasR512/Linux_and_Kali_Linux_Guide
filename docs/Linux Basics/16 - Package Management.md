## Purpose
Package management allows you to install, remove, and update software on Linux. In CTFs, you may need to quickly install missing tools. In real-world environments, sysadmins and penetration testers rely on package managers to maintain systems securely and efficiently.

## Core Commands
```bash
$ sudo apt update
#Updates the List of Available Packages

$ sudo apt upgrade
#Upgrades All Installed Packages to Latest Versions

$ sudo apt install nmap
#Installs "nmap" Package

$ sudo apt remove nmap
#Removes "nmap" Package

$ dpkg -i package.deb
#Installs a Package From a Local .deb File

$ apt-cache search nmap
nmap - The Network Mapper
#Searches For "nmap" in the Package Repository
```

!!! note "Package Management Basics"  
	- `apt` is the higher-level tool used in Debian/Ubuntu systems.  
	- `dpkg` handles `.deb` files directly.  
	- Always run `apt update` before installing new packages.  
	- Be cautious with upgrades on production systems — they may break dependencies.

### [[Linux Basics#16 - Package Management|Package Management Commands]]
