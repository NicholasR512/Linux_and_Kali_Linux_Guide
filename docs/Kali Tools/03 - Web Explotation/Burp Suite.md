#### Official Documentation: [https://portswigger.net/burp/documentation](https://portswigger.net/burp/documentation)
#### Cheat Sheet: [[Kali Tools#Burp Suite|Burp Suite Commands]]
## Purpose
Burp Suite is a web-proxy and testing platform used to intercept, inspect, and modify HTTP(S) traffic between your browser and a web app. It also includes scanners, intruders, and many tools for manual and automated testing.

## Scenarios
- CTF: Intercept requests to change parameters, replay requests, or fuzz inputs to find flags.  
- Real world: Perform full web app testing — proxy traffic, find injection points, scan for common vulnerabilities, and automate repetitive attacks.

## All needed info to run
- GUI tool (Community or Professional). On Kali you can run `burpsuite` or the bundled launcher.  
- Configure your browser to use Burp as a proxy (default: 127.0.0.1:8080). Install Burp's CA certificate in your browser to intercept HTTPS.  
- Key modules:
  - **Proxy** — intercept and modify requests/responses.  
  - **Repeater** — resend and tweak individual requests manually.  
  - **Intruder** — automate payloads (wordlists, fuzzing).  
  - **Scanner** (Pro only) — automated vulnerability scanning.  
  - **Sequencer**, **Decoder**, **Comparer** — helpers for tokens, encodings, diffs.  
- Useful file locations:
  - Project files saved via GUI.  
  - Use Burp extensions (BApp Store) for extra functionality.

## Example commands & outputs
```bash
# Launch Burp Suite from terminal (Kali)
$ burpsuite
# GUI opens. Configure browser proxy to 127.0.0.1:8080 and install Burp CA.

# Intercept a request in Proxy -> HTTP history, send to Repeater, modify and resend.
# Repeater output snippet (after sending modified POST):
# HTTP/1.1 200 OK
# Content-Type: application/json
# {"status":"success","flag":"CTF{example_flag_1234}"}

# Use Intruder to fuzz a parameter with a wordlist (GUI-driven).
# Intruder result table shows payload, status, length, matches — use length and status to spot interesting responses.
```

!!! note "Burp Suite Basics"
	- Configure your browser to use Burp's proxy (127.0.0.1:8080) and install the Burp CA cert to intercept HTTPS safely.
	- Community edition lacks the automated scanner and some Intruder features — Pro is faster for large tests.
	- Use Repeater for manual testing and Intruder for automated payloads.
	- Save projects and use Burp extensions (BApp store) to add functionality.

### [[Kali Tools#Burp Suite|Burp Suite Commands]]
