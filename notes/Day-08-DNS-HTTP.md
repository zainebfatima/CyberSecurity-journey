# Day 8 — DNS + HTTP/HTTPS

## 📌 What I Learned
DNS converts website names into IP addresses.
HTTP is the language browsers and servers
use to communicate.
HTTPS is the secured version of HTTP
protected by TLS.

---

## 🌐 DNS — Domain Name System

### What is DNS?
DNS is like an internet notebook.
It contains records that convert
website names into IP addresses.
Without DNS we would have to memorize
the IP address of every website!

### DNS Record Types

| Record | Purpose |
|--------|---------|
| A | Maps domain to IPv4 address |
| AAAA | Maps domain to IPv6 address |
| CNAME | Maps domain to another domain |
| MX | Mail server records |
| TXT | Text information records |
| NS | Nameserver records |

### Domain Hierarchy
Using tryhackme.com as example:


admin.tryhackme.com
  ↑        ↑    ↑
Subdomain  SLD  TLD


*TLD — Top Level Domain (.com)*
Specifies the purpose of the website.

Two types of TLD:
- *gTLD* (Generic TLD) — shows purpose:
  - .com = commercial
  - .org = organization
  - .gov = government
  - .edu = education
- *ccTLD* (Country Code TLD) — shows country:
  - .pk = Pakistan
  - .uk = United Kingdom
  - .us = United States

*SLD — Second Level Domain (tryhackme)*
The actual name of the website.

Rules for SLD:
- Maximum 63 characters
- Can use a to z, 0 to 9, hyphens
- ✅ Correct: my-site.com
- ❌ Wrong: -site.com
- ❌ Wrong: site-.com
- ❌ Wrong: si-te-.com

*Subdomain (admin.tryhackme.com)*
Tells which specific section or
page of the website we are visiting.
admin.tryhackme.com = admin page of tryhackme

---

### How DNS Works — Step by Step


You search: tryhackme.com
        ↓
1. Computer checks its own memory (cache)
        ↓
2. Not found → Asks Router
        ↓
3. Not found → Asks ISP DNS Server
        ↓
4. Not found → Asks Root DNS Server
        ↓
5. Root DNS → Authoritative DNS Server
   (holds all records for that domain)
        ↓
6. IP address returned to browser
        ↓
7. Website loads on screen! ✅

All this happens in milliseconds!


*Authoritative DNS Server:*
Holds all the records for a specific domain.
Final source of truth for DNS information.

### TTL — Time To Live
Specifies how long a DNS record
should be cached (stored in memory).
After TTL expires the record is
fetched fresh from DNS server.

---

## 🌍 HTTP + HTTPS

### Restaurant Analogy 🍽️

URL     = Restaurant address
Browser = Customer
HTTP    = Language used to talk
          to the restaurant
GET     = "I want to order this"
Response = Food delivered!


### What is HTTP?
HTTP = HyperText Transfer Protocol
The language browsers and servers
use to communicate with each other.

### What is HTTPS?
HTTPS = HyperText Transfer Protocol Secure
More secured version of HTTP.
Protected by TLS encryption.

### HTTP Request Example

GET / HTTP/1.1

GET      = I want something
/        = Homepage
HTTP/1.1 = Version of the protocol


### HTTP Response Example

HTTP/1.1 200 OK

HTTP/1.1 = Same protocol version
200      = Status code
OK       = Everything successful


---

## 📋 HTTP Request Methods

| Method | Purpose |
|--------|---------|
| GET | Retrieve/get information |
| POST | Submit data, create new records |
| PUT | Update existing information |
| DELETE | Remove information |

---

## 📊 HTTP Status Codes
Status codes tell whether a request
was successful or something went wrong.

| Range | Category | Example |
|-------|----------|---------|
| 100-199 | Informational | 100 Continue |
| 200-299 | Success | 200 OK |
| 300-399 | Redirection | 301 Moved |
| 400-499 | Client Errors | 404 Not Found |
| 500-599 | Server Errors | 500 Server Error |

### Most Important Status Codes

| Code | Meaning | Hacker Relevance |
|------|---------|-----------------|
| 200 | Success | Page exists — investigate! |
| 301 | Permanent redirect | Follow the redirect |
| 302 | Temporary redirect | Login success! |
| 403 | Forbidden | Exists but blocked — try bypass! |
| 404 | Not found | Skip it |
| 500 | Server error | Might be vulnerable! |

---

## 🔒 TLS — Transport Layer Security
TLS is a protocol used to protect
and secure communication over a network.
It is what makes HTTPS secure.


HTTP  = Postcard (everyone can read)
HTTPS = Sealed letter (encrypted)
TLS   = The seal that protects the letter


---

## 🔗 Connection to Hacking


HTTP knowledge helps because:

1. Burp Suite intercepts HTTP requests
   Now you understand every line!

2. Status codes reveal information:
   403 = page exists but blocked
   500 = server error = investigate

3. HTTP methods matter:
   POST requests carry login data
   GET parameters visible in URL
   Both can be manipulated!

4. HTTPS doesn't mean safe!
   SQLi, XSS, IDOR all work on HTTPS
   Encryption protects transit only
   Not application vulnerabilities!


---

## ⚠️ Important Note
All practice on TryHackMe authorized
labs only. Never test on systems
without written permission.
