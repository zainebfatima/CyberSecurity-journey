# Day 21: Burp Suite — Target Tab & Scope

## What is the Target Tab?
Target tab in Burp Suite shows you every website 
you have visited and their complete structure —
pages, parameters, files — everything mapped automatically.

## What is Scope?
Scope defines your boundary in bug bounty hunting.
In Scope = Websites you are allowed to test ✅
Out of Scope = Websites you must NOT touch ❌
[3:16 pm, 21/07/2026] ...: ## Why Scope is Important?
Scope tells us our boundaries — where we can work,
what we can access and test, and where our limits end.
Without scope we could accidentally test unauthorized
targets which is illegal! ⚠️

## Real Bug Bounty Example
IN SCOPE:
✅ https://portswigger.net/

EXCLUDE FROM SCOPE:
❌ Third party services
❌ Out of scope subdomains
## Practical Steps — How to Set Scope in Burp Suite
1. Open Burp Suite → Proxy → Open Browser
2. Visit target website
3. Go to Target → Site map
4. Website structure visible automatically
5. Right click on target → "Add to scope"
6. Go to Scope tab — target visible there!
7. Include in scope ✅ / Exclude from scope ❌

## Key Concepts
| Term | Meaning |
|------|---------|
| Site map | Auto-generated map of visited websites |
| Include in scope | Websites allowed to test |
| Exclude from scope | Websites NOT to touch |
| Add to scope | Right click → Add to scope |

## Golden Rules of Scope
- Always read scope BEFORE starting bug bounty
- Never go out of scope even if you find a bug
- Out of scope testing = illegal ⚠️
- <img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/062e7a8e-3839-4d95-a742-7791ba5c4df4" />
<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/5678e444-882b-4d1d-8602-b4b77c57efac" />

