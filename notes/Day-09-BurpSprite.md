# Day 9 — Burp Suite

## 📌 What I Learned
Burp Suite is a cybersecurity tool used
to intercept, read, and modify web traffic.
It works as a proxy — sitting between
your browser and the website.

---

## 🔄 What is a Proxy?


Your PC → Proxy → Website
Website → Proxy → Your PC


A proxy receives your internet request
first, then forwards it to the website
and brings the response back to you.

A proxy is not a single software —
it is a middle man system/service
that intercepts traffic.
Sometimes it appears as a software
interface where requests can be
viewed and modified.

### What a Proxy Can Do:
- See which website you are visiting
- See what pages you open
- Read data being sent
- Read headers and cookies
- Read login requests
- Modify requests before forwarding
- Some people use proxy to hide real IP

### Popular Proxy Tools:
- *Burp Suite* — most widely used
- *OWASP ZAP* — free and open source

---

## 🛠️ What is Burp Suite?

Burp Suite is a cybersecurity tool used by:
- Ethical Hackers
- Penetration Testers
- Security Researchers

### What Burp Suite Does:
- Intercept web traffic
- Read requests and responses
- Modify requests
- Test website security

---

## 🔧 Burp Suite Tools Breakdown

---

### 1. Proxy

Your Browser → Burp Proxy → Website

Intercept means the proxy catches
or stops requests in the middle
before they reach the website.

The middle man that:
- Catches requests
- Lets you read them
- Lets you modify them
- Lets you forward them

---

### 2. Repeater
Sends the same request again
and again manually.

You can edit, modify and manually
resend the request again and again.

*Useful for:*
- Testing APIs
- Changing parameters
- Learning how website responds
- Testing IDOR (changing IDs)
- Testing SQL injection payloads

---

### 3. Intruder
Instead of manually editing and
sending requests one by one —
Intruder sends many modified
requests to the target automatically.

*Payloads* = the values to try

*Common Uses:*
- Password brute forcing
- Testing IDs
- Finding hidden parameters
- Fuzzing inputs for vulnerabilities
- Testing rate limiting
- Sending and changing data

---

### 4. Decoder
Encode, decode and transform
data into different formats.

*What Decoder can do:*

| Function | Purpose |
|----------|---------|
| Base64 encode/decode | Most common encoding |
| URL encode/decode | For URL parameters |
| HTML encode/decode | For web content |
| Hex conversion | Raw data viewing |
| Hashing | MD5, SHA1, SHA256 |
| Gzip decompression | Compressed data |

---

### 5. Comparer
Used to compare two pieces of data
and highlight the differences between them.

*Useful for:*
- Comparing responses when testing IDOR
- Seeing what changed between requests
- Finding hidden differences in responses
- Identifying successful vs failed attempts

---

### 6. Target
Stores and displays discovered
website pages.

Organized view of the website
you are testing.

*Shows:*
- All pages discovered
- All endpoints found
- Site map of target
- Organized structure

---

## 🔗 How Everything Connects


FoxyProxy (Firefox Extension)
         ↓
Routes browser traffic to Burp
         ↓
Burp Proxy intercepts request
         ↓
You read the request:
POST /login HTTP/1.1
Host: 10.49.173.81
username=molly&password=test123
         ↓
Options:
→ Forward (let it through)
→ Drop (block it)
→ Send to Repeater (test manually)
→ Send to Intruder (automate attack)


---

## 💡 Real Usage Examples

*Testing IDOR with Repeater:*

Original: GET /profile?id=1234
Modified: GET /profile?id=1235
Send → See if other user data appears!


*Brute forcing with Intruder:*

POST /login
username=molly&password=§test123§

§ § marks the payload position
Intruder replaces with wordlist
Finds correct password automatically!


*Decoding with Decoder:*

Cookie value looks weird?
Paste in Decoder
Try Base64 decode
See the real value inside!


---

## ⚠️ Important Note
Burp Suite used only on
TryHackMe authorized labs.
Never intercept traffic on
systems without permission.
