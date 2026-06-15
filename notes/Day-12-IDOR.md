# Day 12 — IDOR (Insecure Direct Object Reference)

## 📌 What I Learned
IDOR is an authorization vulnerability
where a website lets a user access
someone else's data just by changing
an ID in a URL or parameter —
without properly checking permissions.

---

## ❓ What is IDOR?


IDOR = Insecure Direct Object Reference

Simple example:
Your profile:    website.com/user?id=1547
Change ID to:    website.com/user?id=1548
You see someone else's private data!

That's IDOR — no complex payload needed!
Just change a number!


---

## ⚠️ Why is IDOR Dangerous?

An attacker may gain access to:
- Banking and financial data
- Personal information
- Medical records
- Financial records
- Customer databases
- Internal company documents

### Consequences:

→ Data breaches
→ Financial loss
→ Privacy violations
→ Regulatory penalties


---

## 🌍 Where IDOR Exists

IDOR vulnerabilities are common in:
- Web applications
- Mobile applications
- REST APIs
- Cloud applications
- Internal business portals
- E-commerce websites

---

## 🔍 Where to Look for IDOR

### In URLs:

?id=
?user_id=
?order=
?file=
?invoice=
?account=


### In Request Body (POST):
json
{"user_id": 1234}
{"order_id": 5678}


### In Cookies:

user=1234



Simple rule:
Anywhere you see a number
that references YOUR data
= potential IDOR!


---

## 🔑 Authentication vs Authorization

This is the most important
distinction in security!

### Authentication:

Verifies YOUR IDENTITY
"Who are you?"

Example:
Supplying username and password
Proving you are who you claim to be


### Authorization:

Determines what you CAN ACCESS
"What are you allowed to do?"

Example:
Are you allowed to visit admin page?
Are you allowed to make a payment?
Are you allowed to see this file?


### Why IDOR Happens:

Authentication EXISTS ✅
but
Authorization is MISSING ❌

Website checks: "Are you logged in?"
But doesn't check: "Is this YOUR data?"

That gap = IDOR vulnerability!


---

## 📈 Privilege Escalation

Privilege escalation is a technique
used to gain higher access rights
than initially granted.

### Two Types:

*Vertical Privilege Escalation:*

Normal user acts like an admin
More power than you should have!

Example:
Regular user accesses admin panel
Regular user deletes other accounts


*Horizontal Privilege Escalation:*

User accesses ANOTHER user's data
Same power level — different account!

Example:
You access someone else's profile
You view someone else's orders



IDOR is usually a form of
HORIZONTAL privilege escalation!


---

## 🛡️ How Developers Prevent IDOR


1. Always perform authorization checks
   Check: "Does this user OWN this data?"

2. Use indirect references
   Instead of real database ID
   use random unpredictable tokens

3. Apply principle of least privilege
   Users only access what they need
   Nothing more!

4. Test access controls regularly
   Regular security testing


---

## 🔗 IDOR vs Other Vulnerabilities

| Vulnerability | What it attacks | Complexity |
|--------------|----------------|------------|
| SQLi | Database | High — needs SQL knowledge |
| XSS | Users/browsers | Medium — needs JS knowledge |
| IDOR | Authorization | Low — just change a number! |


IDOR is the most beginner friendly
vulnerability to find because:
→ No special payload needed
→ No programming language needed
→ Just logic and observation!


---

## 💰 Bug Bounty Value


IDOR payouts on HackerOne:
Low severity:      $200 - $500
Medium severity:   $500 - $2000
High severity:     $2000 - $10000

Most common first bug
found by beginners!


---

## 📝 Step by Step — Finding IDOR


Step 1:
Create two test accounts
Account A and Account B

Step 2:
Login as Account A
Perform an action that generates ID
(view profile, place order etc)

Step 3:
Open Burp Suite
Intercept the request
Find the ID parameter

Step 4:
Send to Repeater
Change ID to Account B's ID

Step 5:
If you see Account B's data =
IDOR found! 🎯

Step 6:
Document everything
Write your bug report!


---

## ⚠️ Important Note
All IDOR practice on TryHackMe
authorized labs only.
Never test on systems
without written permission.
