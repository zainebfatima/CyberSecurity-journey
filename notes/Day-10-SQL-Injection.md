# Day 10 — SQL Injection

## 📌 What I Learned
SQL Injection is a vulnerability that allows
attackers to interfere with database queries.
It is consistently ranked #1 in OWASP Top 10.

---

## 🔑 How It Works

Normal login query:
sql
SELECT * FROM users 
WHERE username='molly' AND password='test123'


SQLi attack input:
Username: admin'--

Password: anything
Query becomes:
sql
SELECT * FROM users 
WHERE username='admin'--' AND password='anything'


The -- comments out password check.
Result: logged in without knowing password!

---

## 💉 Basic Payloads

sql
' OR 1=1--          # Always true — bypass login
admin'--            # Comment out password check
' OR '1'='1         # Another always true payload
1; DROP TABLE users-- # Destructive (never use!)


---

## 🔍 Payload Breakdown

| Part | What it does |
|------|-------------|
| ' | Breaks out of the string |
| OR 1=1 | Always returns true |
| -- | Comments out everything after |

---

## ⚠️ Important Note
Only practiced on TryHackMe authorized labs.
Never test on systems without permission.
