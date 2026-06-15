# Day 13 — Authentication Bypass

## 📌 What I Learned
Authentication Bypass is a security
vulnerability where an attacker gains
access to a system, account or protected
resource without providing valid credentials
(username, password, token etc).

---

## 🔑 Key Definitions


Authentication:
Proving who you are + providing proof
"I am Sara and here is my password"

Bypass:
Getting around that proof

Authentication Bypass:
The application incorrectly trusts
a user even though they have not
properly authenticated!


---

## ❓ What is Authentication Bypass?


Normal process:
User provides credentials
         ↓
System verifies them
         ↓
Access granted only if correct

Authentication Bypass:
Attacker skips or tricks
the verification step
         ↓
Access granted WITHOUT
valid credentials!


---

## 🔴 Common Causes

Authentication bypass usually happens
because developers make mistakes in:
- Login logic
- Access control logic
- Session handling

---

### 1. SQL Injection in Login Forms

If the application builds SQL queries
insecurely an attacker can alter the
query to always return true!

*Normal query:*
sql
SELECT * FROM users
WHERE username='admin'
AND password='test123'


*Attacker enters:*

Username: admin'--
Password: anything


*Query becomes:*
sql
SELECT * FROM users
WHERE username='admin'--'
AND password='anything'



-- comments out the rest!
Password check is ignored!
Logged in as admin
without knowing password! 🎯


---

### 2. Weak or Predictable Session Tokens


If session IDs are:
- Predictable
- Not validated properly
- Sequential (1001, 1002, 1003...)

Attacker can:
- Guess valid session tokens
- Reuse old tokens
- Login as another user
  without their password!


---

### 3. Improper Access Control


Example:
Visiting /dashboard directly
without logging in
still loads the dashboard!

Application never checked:
"Is this user logged in?"

Attacker just types the URL
and gets full access! 😱


---

### 4. Login Logic Flaws


Mistakes in how login
process is coded.

Example:
App checks username correctly
but forgets to check password!

Or:
App says "wrong password"
before checking if user exists
Reveals which usernames are valid!
(Username enumeration)


---

### 5. Broken Multi-Factor Authentication (MFA)


MFA = Two factor authentication
Something you know (password)
+ Something you have (OTP code)

Broken MFA happens when:
- App allows skipping second factor
- OTP codes don't expire
- OTP validated improperly
- Same OTP works multiple times

Attacker bypasses MFA and
logs in with only password!


---

## 🔍 How is it Detected?

Testers look for:
- Login forms vulnerable to SQLi
- Broken MFA flows
- Authentication logic flaws
- Weak session management
- Insecure password reset mechanisms

---

## 🧪 Typical Testing Steps


Step 1:
Try accessing protected URLs
without logging in
/dashboard
/admin
/profile
/settings

Step 2:
Modify cookies or session tokens
Change values in Burp Suite
See if access granted!

Step 3:
Test login forms for SQL injection
Try: admin'--
Try: ' OR 1=1--

Step 4:
Check whether tokens expire properly
Logout then reuse old session cookie
Still works? = Vulnerability!

Step 5:
Test MFA implementation
Try skipping second factor
Try reusing OTP codes
Try expired OTP codes


---

## 🔗 Connection to What We Already Know


Day 10 — SQLi:
' OR 1=1-- bypasses login ✅
admin'-- comments out password ✅
Both are authentication bypass methods!

Day 12 — IDOR:
IDOR = broken AUTHORIZATION
Auth Bypass = broken AUTHENTICATION

Two different things:
Authentication = proving who you are
Authorization = what you can access

Both are access control failures
but at different stages!


---

## 📊 Authentication vs Authorization vs IDOR

| Concept | Question | Example |
|---------|----------|---------|
| Authentication | Who are you? | Login with username/password |
| Authorization | What can you do? | Can you access admin panel? |
| IDOR | Is this YOUR data? | Can you see order #1234? |


Auth Bypass = skipping authentication
IDOR = bypassing authorization
Both = unauthorized access!


---

## 💰 Bug Bounty Value


Authentication bypass bugs are
some of the HIGHEST paid!

Why?
Full account takeover =
Critical severity!

Payouts:
MFA bypass:          $1000 — $10,000
Login SQLi:          $500  — $5,000
Session token flaw:  $500  — $3,000
Improper access:     $200  — $2,000

These are dream finds
for bug bounty hunters! 🎯


---

## ⚠️ Important Note
All authentication bypass practice
on TryHackMe authorized labs only.
Never test on systems without
written permission.
