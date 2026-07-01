# Day 13 — Cronjobs, Cryptography & Cross-Site Scripting (XSS)

## 🎯 Objectives

Today's focus:

* Continue progressing through OverTheWire Bandit
* Build a Caesar Cipher in Python
* Learn file handling with Python
* Begin the Cross-Site Scripting (XSS) learning path on PortSwigger

---

# ⚔️ Hour 1 — OverTheWire Bandit

## Goal

Progress from Level 20 to Level 22

---

## Level 20 → 21

### Objective

Use the `suconnect` SUID binary to communicate with a local port and retrieve the next password.

### Terminal 1 — Start a Netcat Listener

```bash
echo "your_bandit20_password" | nc -l -p 1234
```

### Terminal 2 — Execute the Binary

```bash
./suconnect 1234
```

### Concepts Learned

* Local network communication
* Netcat listeners
* SUID binaries
* Multiple SSH sessions

---

## Level 21 → 22

### Objective

Inspect the system's scheduled cron jobs and locate where the next password is written.

### List Cron Jobs

```bash
ls /etc/cron.d/
```

### View the Bandit Cron Job

```bash
cat /etc/cron.d/cronjob_bandit22
```

Follow the script referenced by the cron job to discover where it stores the password.

---

## What is a Cron Job?

A **cron job** is a scheduled task that runs automatically at specified intervals on Linux systems.

### Why Attackers Care

Misconfigured cron jobs can:

* Execute scripts with elevated privileges
* Leak sensitive files
* Enable privilege escalation
* Execute attacker-controlled code

---

## Checklist

* [ ] Level 20 solved
* [ ] Level 21 attempted
* [ ] Understood what cron jobs are
* [ ] Learned why cron jobs matter in penetration testing

---

# 🐍 Hour 2 — Python Mini Project #7

## Project — Caesar Cipher

### File

```text
day15_caesar_cipher.py
```

### Goal

Build a simple Caesar Cipher to understand basic cryptography concepts.

---

## Source Code

```python
def encrypt(text, shift):
    result = ""
    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            result += char
    return result

def decrypt(text, shift):
    return encrypt(text, -shift)

message = input("Enter message: ")
shift = int(input("Enter shift (1-25): "))

encrypted = encrypt(message, shift)
decrypted = decrypt(encrypted, shift)

print(f"\nOriginal:  {message}")
print(f"Encrypted: {encrypted}")
print(f"Decrypted: {decrypted}")
```

---

## New Concepts

| Function | Purpose                                            |
| -------- | -------------------------------------------------- |
| `ord()`  | Convert a character to its ASCII/Unicode value     |
| `chr()`  | Convert an ASCII/Unicode value back to a character |
| `% 26`   | Wrap alphabet letters from Z back to A             |

---

## Example

### Input

```text
Message: Hello
Shift: 3
```

### Output

```text
Original:   Hello
Encrypted:  Khoor
Decrypted:  Hello
```

---

## Why `% 26`?

The English alphabet contains **26 letters**.

Using modulo (`% 26`) ensures that when shifting beyond **Z**, the cipher wraps back to **A**.

Example:

```text
Z + 1 → A
```

---

## Why Is Caesar Cipher Weak?

* Only **25 possible keys**
* Easily brute-forced
* No protection against modern attacks

It is useful for learning cryptography fundamentals but is **not secure** for real-world encryption.

---

## Checklist

* [ ] File created successfully
* [ ] Tested with **Hello** and shift **3**
* [ ] Understood `% 26`
* [ ] Understood why Caesar Cipher is insecure

---

# 📂 Hour 3 — CS50P Lecture 6

## Resource

**CS50P — Lecture 6: File I/O**

### Topics Covered

* Opening files
* Reading files
* Writing files
* Context managers (`with`)

---

## Key Functions

| Function  | Purpose                           |
| --------- | --------------------------------- |
| `open()`  | Open a file                       |
| `read()`  | Read file contents                |
| `write()` | Write data to a file              |
| `with`    | Automatically closes files safely |

---

## Practice Exercise

Save the encrypted Caesar Cipher output to a file.

```python
with open("output.txt", "w") as file:
    file.write(encrypted)
```

---

## Checklist

* [ ] Lecture 6 completed
* [ ] Notes written
* [ ] Caesar Cipher output saved to `output.txt`

---

# 🌐 Hour 4 — PortSwigger Web Security Academy

## Goal

Begin the **Cross-Site Scripting (XSS)** learning path.

---

## Tasks

Read:

* XSS Introduction

Complete:

* Lab 1
* Lab 2
* Lab 3

---

## What is XSS?

Cross-Site Scripting (XSS) is a web vulnerability that allows attackers to inject malicious JavaScript into web pages viewed by other users.

---

## Stored vs Reflected XSS

| Stored XSS                                   | Reflected XSS                                           |
| -------------------------------------------- | ------------------------------------------------------- |
| Payload is permanently stored on the server  | Payload is reflected immediately in the server response |
| Affects every visitor to the vulnerable page | Usually requires the victim to click a crafted link     |
| More persistent and often more dangerous     | Often used in phishing and social engineering attacks   |

---

## Checklist

* [ ] XSS introduction completed
* [ ] Lab 1 completed
* [ ] Lab 2 attempted
* [ ] Lab 3 attempted
* [ ] Understood the difference between Stored and Reflected XSS

---

# ✅ End of Day Checklist

* [ ] Bandit Level 20 solved
* [ ] Bandit Level 21 attempted
* [ ] Caesar Cipher built
* [ ] Caesar Cipher tested
* [ ] CS50P Lecture 6 completed
* [ ] Caesar Cipher output saved to a file
* [ ] XSS introduction completed
* [ ] PortSwigger XSS Labs 1–3 attempted

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
