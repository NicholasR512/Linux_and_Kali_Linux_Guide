#### Official Documentation: [https://github.com/urbanadventurer/WhatWeb](https://github.com/urbanadventurer/WhatWeb)
#### Cheat Sheet: [[Kali Tools#WhatWeb|WhatWeb Commands]]
## Purpose
WhatWeb identifies what technologies a website is running (web server, CMS, frameworks, JavaScript libs, analytics). It fingerprints web targets using plugins and signatures.

## Scenarios
- CTF: Quickly identify CMS versions (e.g., WordPress) or server types that suggest certain exploit paths.  
- Real world: Inventory web technologies to plan targeted web tests and detect out-of-date platforms.

## Required info to run
- Target URL (http/https).  
- Common flags:
  - `-v` / `-V` → verbose/version info  
  - `--plugins` → list or control plugins used  
  - `-a <level>` → detection aggressiveness (0-3)  
  - `-U` → custom user-agent  
  - `-t <num>` → number of threads (parallel scans)  
  - `-p` → specify plugins  
  - `-o` → output file
- No special privileges required. Network access to the target required.

## Example commands & outputs
```bash
# Basic fingerprint
$ whatweb http://example.com
# Output snippet:
# http://example.com [200] Apache[Linux], PHP, X-Powered-By, WordPress[5.6.1], jQuery

# Aggressive scan with verbose output
$ whatweb -a 3 -v https://example.com -o whatweb.txt
# Output saved to whatweb.txt
```

!!! note "WhatWeb Basics"  
	- `-a 3` increases detection but may be noisier.  
	- Use custom plugins or update signatures frequently for best results.  
	- Combine WhatWeb data with `wpscan` or manual checks for CMS-specific vulnerabilities.  
	- False positives are possible — verify findings manually.

### [[Kali Tools#WhatWeb|WhatWeb Commands]]