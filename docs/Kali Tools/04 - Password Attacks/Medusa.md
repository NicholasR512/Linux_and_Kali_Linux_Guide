#### Official Documentation: [https://www.kali.org/tools/medusa/](https://www.kali.org/tools/medusa/)
#### Cheat Sheet: [[Kali Tools#Medusa|Medusa Commands]]
## Purpose
Medusa is a parallel, modular login brute-forcer similar to Hydra, designed for speed and flexibility across many protocols.

## Scenarios
- CTF: Rapidly test credentials against services in lab environments.  
- Real world: Use in authorized penetration tests for credential stuffing or multi-service testing.

## All needed info to run
- Target service and module (e.g., `ssh`, `ftp`, `http`).  
- Username/password lists.  
- Common flags:
  - `-h <host>` → target host  
  - `-U <userlist>` → usernames file  
  - `-P <passlist>` → passwords file  
  - `-M <module>` → module/service name (e.g., `ssh`)  
  - `-t <threads>` → concurrent threads  
  - `-f` → stop on first found login  
- Check `medusa -H` for module list and syntax details.

## Example commands & outputs
```bash
# SSH brute-force with medusa
$ medusa -h 192.168.56.101 -U users.txt -P passwords.txt -M ssh -t 8 -f
# Output snippet:
# SUCCESS: 192.168.56.101:22 ssh - login: root password: toor123

# FTP example
$ medusa -h 192.168.56.101 -U users.txt -P passwords.txt -M ftp
```

!!! note "Medusa Basics"
	- Medusa is fast and parallel — set `-t` carefully to avoid overwhelming targets.
	- Use `-f` to stop after a success and save time.
	- Modules differ in argument requirements; check medusa module docs.
	- Only use Medusa on authorized targets and be mindful of lockouts.

### [[Kali Tools#Medusa|Medusa Commands]]