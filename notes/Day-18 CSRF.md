# Day 18: CSRF (Cross-Site Request Forgery)

## What is CSRF?
CSRF is a web security vulnerability where an attacker tries to trick
a logged-in user into performing an unwanted action on a website
without their knowledge.

## Real Life Example
- You are logged into your banking account
- You don't logout and session is still active
- You then visit a malicious website
- That malicious website secretly sends a request:
- POST /transfer
Amount = 10000
To = Attacker
Because your browser is already logged in, it automatically attaches
your session cookie to the request.

The attacker cannot steal your password or cookie,
but they abuse your existing login session.

## How CSRF Works
User logs into Website A
↓
Website sends a session cookie
↓
User stays logged in
↓
User visits a malicious website
↓
Malicious website sends a hidden request to Website A
↓
Browser automatically includes session cookie
↓
Website A thinks the request came from legitimate user
↓
Action is performed
It happens because browser automatically sends
session and authentication cookies.

## Common Targets
- Changing password
- Changing email
- Money transfer
- Account deletion
- Purchasing items
- Adding administration
- Updating info

## Lab — TryHackMe CSRF Introduction
*Flag 1:* THM{Got_The_Evil_Email001}
*Flag 2:* Captured via special@evilmail.thm

*What I did:*
- Created malicious HTML page with hidden form
- Used auto-submit JavaScript
- Victim's email changed without their knowledge
- CSRF attack successful!

## Prevention
- CSRF Tokens — unique secret value attacker cannot guess
- Server verifies token with every request
