# Day 14 — SUID, Password Security & Unit Testing

## 🎯 Objectives

Today's focus:

* Continue progressing through OverTheWire Bandit
* Build a Password Strength Checker in Python
* Learn the basics of unit testing with CS50P
* Complete the SQL Injection learning path on PortSwigger

---

# ⚔️ Hour 1 — OverTheWire Bandit

## Goal

Progress from Level 18 to Level 20

---

## Level 18 → 19

### Objective

Bypass the logout script by executing a command directly during login.

### Command

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

### Concepts Learned

* Non-interactive SSH commands
* Executing commands during login
* Bypassing restricted shell environments

---

## Level 19 → 20

### Objective

Use the SUID binary to execute a command as another user.

### Command

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

---

## What is a SUID Binary?

**SUID (Set User ID)** is a special Linux file permission that allows a program to run with the permissions of the file owner instead of the user executing it.

### Why It Matters

SUID binaries are frequently encountered during Linux privilege escalation in penetration testing. Misconfigured SUID programs can allow attackers to gain elevated privileges.

### Identify SUID Files

```bash
find / -perm -4000 2>/dev/null
```

---

## Checklist

* [ ] Level 18 solved
* [ ] Level 19 attempted
* [ ] Understood what a SUID binary is
* [ ] Learned how SUID can be abused in privilege escalation

---

# 🐍 Hour 2 — Python Mini Project #6

## Project — Password Strength Checker

### File

```text
day14_password_strength.py
```

### Goal

Build a password strength checker using Python string methods and logical conditions.

---

## Source Code

```python
password = input("Enter a password to check: ")

length_ok = len(password) >= 8
has_upper = any(c.isupper() for c in password)
has_lower = any(c.islower() for c in password)
has_digit = any(c.isdigit() for c in password)

score = sum([length_ok, has_upper, has_lower, has_digit])

print(f"\nLength >= 8: {length_ok}")
print(f"Has uppercase: {has_upper}")
print(f"Has lowercase: {has_lower}")
print(f"Has digit: {has_digit}")

if score == 4:
    print("\nStrength: STRONG")
elif score >= 2:
    print("\nStrength: MEDIUM")
else:
    print("\nStrength: WEAK")
```

---

## New Concepts

| Function     | Purpose                                          |
| ------------ | ------------------------------------------------ |
| `len()`      | Count characters                                 |
| `.isupper()` | Check uppercase letters                          |
| `.islower()` | Check lowercase letters                          |
| `.isdigit()` | Check numeric characters                         |
| `any()`      | Returns `True` if at least one condition matches |
| `sum()`      | Adds Boolean values (`True = 1`, `False = 0`)    |

---

## Test Cases

| Password   | Expected Result |
| ---------- | --------------- |
| `abc`      | Weak            |
| `abc123`   | Medium          |
| `Abc12345` | Strong          |

---

## Key Concept

```python
any(c.isupper() for c in password)
```

This checks every character in the password and returns `True` if at least one uppercase letter is found.

---

## Checklist

* [ ] File created successfully
* [ ] Tested with weak, medium, and strong passwords
* [ ] Understood `any()` with generator expressions
* [ ] Understood how the strength score is calculated

---

# 🧪 Hour 3 — CS50P Lecture 5

## Resource

**CS50P — Lecture 5: Unit Tests**

### Topics Covered

* Unit Testing
* `assert`
* Introduction to `pytest`
* Why automated testing matters

---

## Why Testing Matters

Security tools should behave reliably. Unit tests help catch bugs early and ensure code works as expected before being used in real-world scenarios.

---

## Practice Exercise

### Simple Assertion

```python
assert len("Abc12345") >= 8
```

### Example Function Test

```python
def is_long(password):
    return len(password) >= 8

assert is_long("Abc12345") == True
```

---

## Checklist

* [ ] Lecture 5 completed
* [ ] Notes written
* [ ] At least one `assert` statement tested

---

# 🌐 Hour 4 — PortSwigger Web Security Academy

## Goal

Complete the SQL Injection learning path.

---

## Tasks

* Continue remaining SQL Injection labs
* Attempt Labs 8–10 (or the remaining labs in the track)
* Review completed exercises

---

## Summary Notes

### What is SQL Injection?

SQL Injection (SQLi) is a web vulnerability that occurs when untrusted user input is interpreted as part of a SQL query, allowing attackers to manipulate database operations.

### How to Test for SQLi

* Test user input fields with SQL payloads
* Observe application behavior and responses
* Look for database errors or unexpected results

### How to Prevent SQLi

* Use parameterized queries (prepared statements)
* Validate and sanitize user input
* Apply the principle of least privilege to database accounts

---

## Checklist

* [ ] Remaining SQLi labs attempted
* [ ] SQL Injection topic completed (or nearly completed)
* [ ] Wrote a summary of SQL Injection, testing methods, and prevention techniques

---

# ✅ End of Day Checklist

* [ ] Bandit Level 18 solved
* [ ] Bandit Level 19 attempted
* [ ] Password Strength Checker built
* [ ] Password Strength Checker tested
* [ ] CS50P Lecture 5 completed
* [ ] `assert` statement written
* [ ] Remaining SQL Injection labs attempted
* [ ] SQL Injection notes completed

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
