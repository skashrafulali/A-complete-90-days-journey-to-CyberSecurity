# Day 14 — Cronjobs, Log Analysis & Regular Expressions

## 🎯 Objectives

Today's focus:

* Continue progressing through OverTheWire Bandit
* Build a Python web server log parser
* Learn Regular Expressions (Regex)
* Continue the PortSwigger XSS learning path

---

# ⚔️ Hour 1 — OverTheWire Bandit

## Goal

Progress from Level 22 to Level 23

---

## Level 21 → 22

### Objective

Investigate a scheduled cron job and discover where it stores the next password.

### View the Cron Job

```bash
cat /etc/cron.d/cronjob_bandit22
```

Identify the script executed by the cron job, then inspect it:

```bash
cat /path/to/the/script
```

Follow the script's logic to determine where it writes the password in `/tmp`, then read the file.

---

## Level 22 → 23

### Objective

Analyze another cron job that generates a filename using an MD5 hash.

### View the Cron Job

```bash
cat /etc/cron.d/cronjob_bandit23
```

Inspect the script:

```bash
cat /path/to/the/script
```

Reproduce the filename generation manually:

```bash
echo "I am user bandit23" | md5sum | cut -d ' ' -f1
```

Use the resulting hash as the filename inside `/tmp` to retrieve the password.

---

## What is a Cron Job?

A **cron job** is a scheduled task that runs automatically at predefined times on Linux systems.

### Why Cron Jobs Matter in Penetration Testing

Misconfigured cron jobs can become powerful privilege escalation vectors when they:

* Execute scripts with elevated privileges
* Write sensitive files to predictable locations
* Run writable scripts or binaries
* Trust insecure file permissions

Understanding how scheduled tasks work is an essential Linux privilege escalation skill.

---

## Checklist

* [ ] Level 22 solved
* [ ] Level 23 attempted
* [ ] Can explain cron jobs in your own words
* [ ] Understand why cron jobs are common privilege escalation targets

---

# 🐍 Hour 2 — Python Mini Project #8

## Project — Web Server Log Parser

### Files

```text
day16_log_parser.py
server.log
```

---

## Step 1 — Create a Sample Log File

Create `server.log` with the following contents:

```text
192.168.1.1 - GET /index.html 200
192.168.1.2 - GET /admin 404
10.0.0.5 - POST /login 200
192.168.1.1 - GET /secret 403
10.0.0.5 - GET /admin 404
192.168.1.2 - POST /login 200
```

---

## Step 2 — Build the Parser

```python
from collections import Counter

ip_counter = Counter()
error_ips = []

with open("server.log", "r") as f:
    for line in f:
        parts = line.strip().split()
        ip = parts[0]
        status = parts[-1]

        ip_counter[ip] += 1

        if status in ("403", "404"):
            error_ips.append(ip)

print("=== Request Count per IP ===")

for ip, count in ip_counter.items():
    print(f"{ip}: {count} requests")

print("\n=== IPs with Errors ===")

for ip in set(error_ips):
    print(ip)
```

---

## New Concepts

| Concept   | Purpose                              |
| --------- | ------------------------------------ |
| `Counter` | Count repeated values efficiently    |
| `open()`  | Read files                           |
| `strip()` | Remove extra whitespace              |
| `split()` | Separate text into individual fields |

---

## Real-World Application

A SOC analyst or penetration tester can use log parsers to:

* Identify suspicious IP addresses
* Detect repeated login attempts
* Find error responses such as **403** or **404**
* Spot reconnaissance activity
* Analyze web server traffic

---

## Checklist

* [ ] `server.log` created
* [ ] Log parser built
* [ ] Request counts are correct
* [ ] Error IPs displayed correctly

---

# 📚 Hour 3 — CS50P Lecture 7

## Resource

**CS50P — Lecture 7: Regular Expressions (Regex)**

### Topics Covered

* Pattern matching
* Searching text
* Replacing text
* Extracting information

---

## Common Regex Functions

| Function       | Purpose               |
| -------------- | --------------------- |
| `re.search()`  | Find the first match  |
| `re.findall()` | Find every match      |
| `re.sub()`     | Replace matching text |

---

## Practice Exercise

Display only log entries with a **404** status code.

```python
import re

with open("server.log", "r") as f:
    for line in f:
        if re.search(r"\b404\b", line):
            print(line.strip())
```

---

## Why Regex Matters in Cybersecurity

Regular expressions are widely used for:

* Log analysis
* Input validation
* IOC hunting
* Parsing security reports
* Searching large datasets
* Detecting attack patterns

---

## Checklist

* [ ] Lecture 7 completed
* [ ] Notes written
* [ ] Regex filter added to the log parser
* [ ] Successfully filtered only 404 responses

---

# 🌐 Hour 4 — PortSwigger Web Security Academy

## Goal

Continue the **Cross-Site Scripting (XSS)** learning path.

---

## Tasks

Complete:

* Lab 4
* Lab 5
* Lab 6

---

## Concept Focus — DOM-Based XSS

### DOM-Based XSS

Occurs when JavaScript running in the browser takes untrusted data from the page (such as the URL, fragment, or other client-side sources) and inserts it into the DOM in an unsafe way.

### Comparison

| Type          | Payload Stored? | Executes Where?                                 |
| ------------- | --------------- | ----------------------------------------------- |
| Reflected XSS | No              | Server response after user request              |
| Stored XSS    | Yes             | Server/database, affecting future visitors      |
| DOM-Based XSS | No              | Entirely in the client's browser via JavaScript |

---

## Checklist

* [ ] Lab 4 completed
* [ ] Lab 5 attempted
* [ ] Lab 6 attempted
* [ ] Can explain DOM-based XSS without external references

---

# ✅ End of Day Checklist

* [ ] Bandit Level 22 solved
* [ ] Bandit Level 23 attempted
* [ ] Web Server Log Parser built
* [ ] Regex filter added
* [ ] CS50P Lecture 7 completed
* [ ] PortSwigger XSS Labs 4–6 attempted

---

## 📝 Daily Reflection

### What I Learned

*
*
*

### Challenges Faced

*
*
*

### Tomorrow's Goal

*
