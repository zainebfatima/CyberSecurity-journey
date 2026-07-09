# Day 19: Burp Suite Basics — Intercepting Requests

## What is Burp Suite?
Burp Suite is a tool used to inspect, modify and test the
communication between a web browser and a website.
It acts as a proxy, allowing you to see every HTTP/HTTPS
request and response.

## How It Works
Browser → Burp Suite → Website
Burp sits in the middle — like an ethical postman who reads
and can modify letters before delivering them.

## Main Components
| Component | Purpose |
|-----------|---------|
| Proxy | Captures requests from browser, lets you see and edit them |
| HTTP History | Stores every request and response made |
| Repeater | Send same request repeatedly, modify parameters |
| Intruder | Automates sending many requests with different input |
| Decoder | Encodes and decodes data |

## Proxy Setup — Built-in Browser Method
No configuration needed!
Proxy → Open Browser → Already connected to Burp ✅

## How to Intercept a Request
1. Proxy → Intercept tab
2. Click "Intercept off" → becomes "Intercept on"
3. Visit any website in Burp browser
4. Request pauses — visible in Intercept tab
5. Read/modify → click "Forward" to send

## What a Raw Request Looks Like
GET / HTTP/1.1
Host: testphp.vulnweb.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept-Language: en-US, en; q=0.9
## Key Fields in a Request
| Field | Meaning |
|-------|---------|
| GET | Method — requesting data |
| / | URL path — home page |
| Host | Which server request is going to |
| User-Agent | Which browser is sending |

## Important Fix Discovered
HTTP History was not showing before because regular Firefox
proxy was not configured. Solution: Always use Burp's
built-in browser — zero setup required! ✅

## Lab Practiced On
- Target: http://testphp.vulnweb.com
- Successfully intercepted GET request
- Forwarded request and page loaded
- HTTP History populated correctly
