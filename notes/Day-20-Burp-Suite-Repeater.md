# Day 20: Burp Suite Repeater

## What is Repeater?
Repeater lets you send the same request repeatedly,
modify parameters each time, and see how the server responds.
Unlike Intercept (which captures once), Repeater gives you
full control to test again and again.

## Intercept vs Repeater
| Feature | Intercept | Repeater |
|---------|-----------|----------|
| Captures request | Once | Already captured |
| Modify request | Yes | Yes |
| Send again | No | Yes, unlimited times |
| Use case | See live request | Test/manipulate |

## How to Use Repeater
1. Proxy → Intercept ON
2. Visit any website in Burp browser
3. Request appears → Right click → Send to Repeater
4. Go to Repeater tab
5. Modify request → Click Send
6. Response appears on right side!

## What I Practiced
- Intercepted request from http://example.com
- Sent to Repeater
- Changed GET / to GET /test
- Got 404 response — proves modification works!

## Real World Usage
- Change parameters to test for vulnerabilities
- Test SQLi, XSS, IDOR all through Repeater
- Modify headers, cookies, body — see server reaction

## Important Concept
Burp Suite only captures YOUR OWN browser traffic.
Cannot capture other people's traffic — that would be illegal!

<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/0b79854a-2b0b-42d2-bcbb-8d2fdcba9c48" />
<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/4c91f2ca-09b9-4492-9601-3d99cecc9cd1" />

