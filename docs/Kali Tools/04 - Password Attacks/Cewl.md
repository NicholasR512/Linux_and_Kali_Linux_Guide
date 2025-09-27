#### Official Documentation: [https://github.com/digininja/CeWL](https://github.com/digininja/CeWL)
#### Cheat Sheet: [[Kali Tools#Cewl|Cewl Commands]]
## Purpose
Cewl (Custom Word List generator) spider a website to collect words and build a wordlist. It helps create targeted wordlists for password cracking based on site content.

## Scenarios
- CTF: Generate a wordlist from a target’s web pages (about pages, team bios) to crack weak passwords that use site-specific words.  
- Real world: Create custom dictionaries for targeted password audits instead of using huge generic lists.

## All needed info to run
- Target URL (e.g., `http://example.com`).  
- Flags:
  - `-m <minlen>` → minimum word length (default 3)  
  - `-w <file>` → write output to file  
  - `-d <depth>` → crawl depth (how many link levels)  
  - `-u <url>` → start URL (alias)  
  - `-c` → count words and sort  
- Network access to the target. Use `--ua` to set a custom user-agent if needed.

## Example commands & outputs
```bash
# Basic crawl and save wordlist
$ cewl http://example.com -w example-words.txt
# Output snippet:
# [*] Crawling: http://example.com
# [*] 234 words collected and saved in example-words.txt

# Crawl with min length 5 and depth 2, count & sort
$ cewl -d 2 -m 5 -c http://example.com -w example-words-deep.txt
# Output:
# [*] 132 words (>=5 chars) saved to example-words-deep.txt
```

!!! note "Cewl Basics"
	- Cewl builds targeted wordlists from page content; it won't find passwords but it creates better dictionaries.
	- Use `-d` conservatively — higher depth crawls more pages and takes longer.
	- Combine Cewl output with `cewl` + `john`/`hashcat` or append to rockyou for hybrid attacks.
	- Respect robots.txt and get permission before crawling production sites.

### [[Kali Tools#Cewl|Cewl Commands]]