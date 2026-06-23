# Day 11 — SSH Keys, Port Scanning & Python Libraries

## 🎯 Objectives

Today's focus:

* Continue progressing through OverTheWire Bandit
* Build your first real Python port scanner
* Learn Python libraries and modules
* Continue the PortSwigger SQL Injection path

---

# ⚔️ Hour 1 — OverTheWire Bandit

## Goal

Progress from Level 17 to Level 18

---

## Level 16 → 17

### Objective

Use the private SSH key obtained in Level 16 to log in as `bandit17`.

### Setup

Create a secure directory for your private key:

```bash
mkdir /tmp/bandit17
chmod 700 /tmp/bandit17
```

Create the key file:

```bash
nano /tmp/bandit17/key.private
```

Paste the private key, then secure it:

```bash
chmod 600 /tmp/bandit17/key.private
```

---

### Login Command

```bash
ssh -i /tmp/bandit17/key.private bandit17@bandit.labs.overthewire.org -p 2220
```

### Concepts Learned

* SSH private key authentication
* File permissions (`700` vs `600`)
* Secure key storage

---

## Level 17 → 18

### Objective

Find the only changed line between two files.

### Command

```bash
diff passwords.new passwords.old
```

### What `diff` Does

The `diff` command compares two files and highlights differences between them.

### Example

```bash
diff file1.txt file2.txt
```

Useful for:

* Comparing configuration files
* Finding changed passwords
* Tracking modifications

---

## Checklist

* [ ] Level 17 solved
* [ ] Level 18 attempted
* [ ] `diff` command documented

---

# 🐍 Hour 2 — Python Mini Project #5

## Project — Real Port Scanner

### File

```text
day13_port_scanner.py
```

### Goal

Transform your earlier port scanner concept into a functional TCP port scanner.

---

## Source Code

```python
import socket

target = input("Enter target IP: ")
start_port = int(input("Start port: "))
end_port = int(input("End port: "))

print(f"\nScanning {target} from port {start_port} to {end_port}...\n")

for port in range(start_port, end_port + 1):
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.settimeout(0.5)

    result = sock.connect_ex((target, port))

    if result == 0:
        print(f"[OPEN] Port {port}")

    sock.close()

print("\nScan complete!")
```

---

## New Concepts

### Importing Modules

```python
import socket
```

Provides access to networking functionality.

---

### Creating a Socket

```python
socket.socket(socket.AF_INET, socket.SOCK_STREAM)
```

| Component   | Meaning |
| ----------- | ------- |
| AF_INET     | IPv4    |
| SOCK_STREAM | TCP     |

---

### Connection Testing

```python
result = sock.connect_ex((target, port))
```

Return Values:

| Result   | Meaning                   |
| -------- | ------------------------- |
| 0        | Port Open                 |
| Non-Zero | Port Closed / Unreachable |

---

### Timeout Handling

```python
sock.settimeout(0.5)
```

Prevents the program from hanging too long while waiting for responses.

---

## Safe Testing Target

```text
scanme.nmap.org
```

Recommended Port Range:

```text
1-100
```

---

## Checklist

* [ ] File created successfully
* [ ] Scanner runs without errors
* [ ] Tested against scanme.nmap.org
* [ ] Open ports detected
* [ ] Understood `connect_ex()` return values

---

# 📚 Hour 3 — CS50P Lecture 4

## Resource

**CS50P — Lecture 4: Libraries**

### Topics Covered

* Importing modules
* Standard libraries
* Third-party libraries
* Code reuse

---

## Standard Library vs Third-Party Library

| Standard Library | Third-Party Library |
| ---------------- | ------------------- |
| socket           | requests            |
| os               | nmap                |
| random           | flask               |
| datetime         | pandas              |

---

## Practice Exercise

### Generate a Random Number

```python
import random

number = random.randint(1, 100)

print(number)
```

### Concepts Learned

* Module importing
* Function usage
* Random number generation

---

## Checklist

* [ ] Lecture 4 completed
* [ ] Notes written
* [ ] `import random` tested
* [ ] Random number generated successfully

---

# 🌐 Hour 4 — PortSwigger SQL Injection

## Goal

Continue progressing through SQL Injection labs.

---

## Labs

Attempt:

* Lab 5
* Lab 6
* Lab 7

---

## Concept Focus

### Normal SQL Injection

The application's response changes immediately after injecting SQL payloads.

Example:

```sql
' OR 1=1--
```

---

### Blind SQL Injection

The application does not directly reveal database output.

Instead, attackers infer information through:

* Boolean responses
* Different page behavior
* Response timing

---

## Notes

### Blind SQLi vs Normal SQLi

| Normal SQLi            | Blind SQLi             |
| ---------------------- | ---------------------- |
| Results visible        | Results hidden         |
| Easier to exploit      | Requires inference     |
| Faster data extraction | Slower data extraction |

---

## Checklist

* [ ] Lab 5 attempted
* [ ] Lab 6 attempted
* [ ] Lab 7 attempted
* [ ] Blind SQLi explained in your own words

---

# ✅ End of Day Checklist

* [ ] Bandit Level 17 solved
* [ ] Bandit Level 18 attempted
* [ ] Real Port Scanner built
* [ ] Port Scanner tested successfully
* [ ] CS50P Lecture 4 completed
* [ ] Random number generator tested
* [ ] PortSwigger Labs 5–7 attempted
* [ ] Blind SQLi notes written

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
