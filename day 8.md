# Day 08 — Python Functions, Conditionals, Bandit & Google Dorking

## 🎯 Objectives

Today's focus:

* Continue Python fundamentals with CS50P
* Build a simple port scanner concept project
* Learn Python conditionals
* Progress further through OverTheWire Bandit
* Begin OSINT and Google Dorking fundamentals

---

# 🐍 Hour 1 — Python Continues

## Resource

**CS50P (Harvard)**

### Lecture

* Finish any remaining content from Lecture 0 — Functions & Variables

---

## Mini Project #2 — Simple Port Scanner Concept

### Goal

Build the logical foundation of a port scanner using functions and loops.

### Source Code

```python
def scan_port(ip, port):
    print(f"Scanning {ip} on port {port}...")
    # We'll add real socket logic later

target = input("Enter target IP: ")
start_port = int(input("Enter start port: "))
end_port = int(input("Enter end port: "))

for port in range(start_port, end_port + 1):
    scan_port(target, port)

print("Scan complete!")
```

### Concepts Practiced

* Functions (`def`)
* Parameters
* `for` loops
* `range()`
* `int()` type conversion
* f-strings

### Test Case

```text
Target IP: 127.0.0.1
Start Port: 1
End Port: 10
```

### Checklist

* [ ] CS50P Lecture 0 fully completed
* [ ] Project typed manually
* [ ] Program tested successfully
* [ ] Every line understood before moving on

---

# 🧠 Hour 2 — Python Conditionals

## Resource

**CS50P Lecture 1 — Conditionals**

### Topics Covered

* `if`
* `elif`
* `else`
* Comparison operators
* Logical decision making

---

## Notes

### Python vs C++

| C++           | Python         |
| ------------- | -------------- |
| `{}` Braces   | Indentation    |
| `else if`     | `elif`         |
| Semicolons    | Not required   |
| Static typing | Dynamic typing |

---

## Practice Exercise

Create a simple program:

```python
port = int(input("Enter a port number: "))

if port < 1024:
    print("Well-known Port")
else:
    print("Dynamic Port")
```

### Checklist

* [ ] Lecture 1 completed
* [ ] Differences from C++ noted
* [ ] Conditional practice program tested

---

# ⚔️ Hour 3 — OverTheWire Bandit

## Goal

Reach Level 13

---

## Level 12 → 13

### Challenge

The password is hidden inside a file that has been repeatedly compressed and encoded.

### Recommended Workflow

```bash
mkdir /tmp/ashraful
cp data.txt /tmp/ashraful
cd /tmp/ashraful

xxd -r data.txt > data.bin
```

---

## Useful Commands

### Check File Type

```bash
file filename
```

### Rename File Extension

```bash
mv filename filename.gz
```

### Decompress Gzip

```bash
gzip -d filename.gz
```

### Decompress Bzip2

```bash
bzip2 -d filename.bz2
```

### Extract Tar Archive

```bash
tar -xf filename.tar
```

### Reverse Hexdump

```bash
xxd -r data.txt > data.bin
```

---

## Key Takeaway

Keep using the `file` command after each extraction step to identify the next file format.

### Checklist

* [ ] Bandit Level 12 → 13 attempted
* [ ] Compression types identified
* [ ] Commands documented
* [ ] Reached Level 13 (or made significant progress)

---

# 🔎 Hour 4 — Google Dorking & OSINT Basics

## Resource

**TryHackMe Room**

Room Name:

```text
Google Dorking
```

---

## What You'll Learn

* Open Source Intelligence (OSINT)
* Search engine reconnaissance
* Finding exposed resources
* Advanced Google operators

---

## Useful Google Dorks

### Search Within a Website

```text
site:github.com
```

### Search for Specific File Types

```text
filetype:pdf cybersecurity
```

### Search Page Titles

```text
intitle:"login"
```

### Search URLs

```text
inurl:admin
```

### Search Environment Files

```text
site:github.com filetype:env
```

---

## Important Note

Use Google Dorking responsibly and ethically. The purpose is learning reconnaissance techniques, not accessing systems without permission.

### Checklist

* [ ] Google Dorking room opened
* [ ] All room tasks completed
* [ ] Five useful dorks documented
* [ ] One safe dork tested

---

# ✅ End of Day Checklist

* [ ] CS50P Lecture 0 completed
* [ ] Python Project #2 completed
* [ ] CS50P Lecture 1 completed
* [ ] Conditional program tested
* [ ] Bandit Level 12 → 13 attempted
* [ ] Google Dorking room completed

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
