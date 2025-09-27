## Purpose
Networking commands are critical when working on remote machines or during CTF challenges. They allow you to see IP addresses, test connectivity, view open ports, and transfer data. In the real world, sysadmins and penetration testers use these commands daily to troubleshoot network issues, verify configurations, and check connectivity between systems.

## Core Commands
```bash
$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.10  netmask 255.255.255.0  broadcast 192.168.1.255
        ether 08:00:27:1a:2b:3c  txqueuelen 1000  (Ethernet)
#Displays Network Interfaces, IP Addresses, and MAC Addresses | Legacy command

$ ip a
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet 192.168.1.10/24 brd 192.168.1.255 scope global dynamic eth0
       valid_lft 86375sec preferred_lft 86375sec
#Displays All Network Interfaces and Their Details | Preferred over ifconfig

$ ping -c 4 google.com
PING google.com (142.250.190.14) 56(84) bytes of data.
64 bytes from lga25s60-in-f14.1e100.net (142.250.190.14): icmp_seq=1 ttl=114 time=23.5 ms
#Sends 4 ICMP Echo Requests to Test Connectivity to "google.com"

$ netstat -tuln
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
#Displays Active Connections and Listening Ports | Deprecated but still used

$ ss -tuln
Netid State  Recv-Q Send-Q Local Address:Port   Peer Address:Port Process
tcp   LISTEN 0      128    0.0.0.0:22           0.0.0.0:*
#Displays Active Connections and Listening Ports | Replacement for netstat

$ curl http://example.com
<!doctype html><html><head><title>Example Domain</title></head>...</html>
#Fetches and Displays Contents of a Web Page (HTTP Request)

$ wget http://example.com/file.txt
--2025-09-21 17:41:19--  http://example.com/file.txt
Saving to: ‘file.txt’
#Downloads a File from a Web Server to Your System
```

!!! note "Networking Basics"  
	- `ip a` is preferred over `ifconfig` on modern systems, but both show interface and IP info.  
	- `ping` is great for checking connectivity, but blocked ICMP doesn’t always mean the host is down.  
	- `netstat` is deprecated → `ss` is its modern replacement for socket and port info.  
	- `curl` is better for API requests, while `wget` is better for bulk/simple downloads.

### [[Linux Basics#10 - Networking Basics|Networking Basics Commands]]