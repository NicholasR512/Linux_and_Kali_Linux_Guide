#### Official Documentation: [https://man.openbsd.org/ssh](https://man.openbsd.org/ssh)
#### Cheat Sheet: [[Kali Tools#SSH|SSH Commands]]
## Purpose
SSH (Secure Shell) is the standard tool for secure remote login and tunneling. It encrypts traffic and allows shell access, file transfer, and port forwarding.

## Scenarios
- CTF: Log in with leaked credentials/keys to pivot further.  
- Real world: Administer remote systems securely, use tunneling for access to internal services.

## All needed info to run
- Syntax: `ssh [user@]host [options]`.  
- Common options:
  - `-i <keyfile>` → specify private key  
  - `-p <port>` → custom port  
  - `-L <lport>:<rhost>:<rport>` → local port forward  
  - `-R <rport>:<lhost>:<lport>` → remote port forward  
  - `-D <port>` → dynamic (SOCKS) proxy  
- Config file: `~/.ssh/config` for shortcuts.  
- Keys: generated with `ssh-keygen`.

## Example commands & outputs
```bash
# Basic login
$ ssh user@192.168.56.101
# Output: user shell prompt on remote system

# Login with private key
$ ssh -i id_rsa user@192.168.56.101

# Local port forward (access internal service)
$ ssh -L 8080:localhost:3306 user@192.168.56.101
# Localhost:8080 forwards to remote MySQL port

# Dynamic SOCKS proxy
$ ssh -D 1080 user@192.168.56.101
# Configure browser to use SOCKS5 proxy localhost:1080
```

!!! note "SSH Basics"
	- Use key-based auth for better security; manage with `ssh-keygen` and `~/.ssh/config`.
	- Port forwarding (`-L`, `-R`, `-D`) enables powerful tunneling and pivoting.
	- Check permissions on private keys (chmod 600 id_rsa).
	- Always verify host authenticity with fingerprints to prevent MITM.

### [[Kali Tools#SSH|SSH Commands]]