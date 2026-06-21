# Day 10 — VS Code, Loops & Web Security

## 🎯 Objectives

Today's focus:

* Continue progressing through OverTheWire Bandit
* Practice Python development in VS Code
* Learn loops with CS50P
* Begin Web Application Security with PortSwigger Academy

---

# ⚔️ Hour 1 — OverTheWire Bandit

## Goal

Progress from Level 14 to Level 16

---

## Level 13 → 14

### Objective

Use the SSH private key obtained in Level 13 to log in as `bandit14`.

### Command

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

### Retrieve the Password

```bash
cat /etc/bandit_pass/bandit14 | nc localhost 30000
```

### Concepts Learned

* SSH private key authentication
* Local service communication
* Using Netcat (`nc`) to interact with network services

---

## Level 14 → 15

### Objective

Connect to an SSL-encrypted service and submit the password.

### Command

```bash
cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -quiet
```

### Concepts Learned

* SSL/TLS encrypted communication
* Using OpenSSL as a client
* Secure service interaction

---

## Notes

### Netcat vs OpenSSL

| Tool               | Purpose                         |
| ------------------ | ------------------------------- |
| `nc` (Netcat)      | Plain TCP communication         |
| `openssl s_client` | SSL/TLS encrypted communication |

---

## Checklist

* [ ] Level 14 solved
* [ ] Level 15 attempted
* [ ] Difference between Netcat and OpenSSL documented

---

# 🐍 Hour 2 — Python in VS Code

## Project #3 — Subnet Class Checker

### Goal

Determine the IP address class based on the first octet.

### File

```text
day10_subnet_checker.py
```

---

## Source Code

```python
ip = input("Enter an IP address (e.g. 192.168.1.1): ")

first_octet = int(ip.split(".")[0])

if first_octet >= 1 and first_octet <= 126:
    print("Class A")
elif first_octet >= 128 and first_octet <= 191:
    print("Class B")
elif first_octet >= 192 and first_octet <= 223:
    print("Class C")
else:
    print("Other/Reserved range")
```

---

## New Concepts

### String Splitting

```python
ip.split(".")
```

Example:

```python
'192.168.1.1'.split(".")
```

Output:

```python
['192', '168', '1', '1']
```

---

### List Indexing

```python
ip.split(".")[0]
```

Returns:

```text
192
```

---

## Test Cases

| IP Address  | Expected Class |
| ----------- | -------------- |
| 10.0.0.1    | Class A        |
| 172.16.0.1  | Class B        |
| 192.168.1.1 | Class C        |

---

## Checklist

* [ ] File created and executed in VS Code
* [ ] Tested all sample IPs
* [ ] Understood `.split(".")`
* [ ] Understood list indexing

---

# 🔄 Hour 3 — CS50P Lecture 2

## Resource

**CS50P — Lecture 2: Loops**

### Topics Covered

* `while` loops
* `for` loops
* Iteration
* Repetition

---

## Python vs C++ Loops

### C++

```cpp
for(int i = 1; i <= 10; i++)
{
    cout << i << endl;
}
```

### Python

```python
for i in range(1, 11):
    print(i)
```

---

## Practice Exercise

Print numbers from 1 to 10.

```python
for i in range(1, 11):
    print(i)
```

---

## Checklist

* [ ] Lecture 2 watched
* [ ] Loop notes written
* [ ] Practice exercise completed

---

# 🌐 Hour 4 — PortSwigger Web Security Academy

## Setup

Create a free account:

```text
https://portswigger.net/web-security
```

---

## Topic

### SQL Injection (SQLi)

Study:

* What is SQL Injection?
* SQL Injection Basics
* First Lab
* Second Lab

---

## Why It Matters

SQL Injection is one of the most important web vulnerabilities and a core skill in web penetration testing.

---

## Skills Introduced

* Databases
* SQL Queries
* User Input Validation
* Injection Vulnerabilities

---

## Checklist

* [ ] PortSwigger account created
* [ ] SQL Injection introduction completed
* [ ] First lab attempted

---

# ✅ End of Day Checklist

* [ ] Bandit Level 14 solved
* [ ] Bandit Level 15 attempted
* [ ] Subnet Class Checker built
* [ ] Subnet Class Checker tested
* [ ] CS50P Lecture 2 completed
* [ ] Loop exercise completed
* [ ] PortSwigger account created
* [ ] First SQL Injection lab attempted

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
