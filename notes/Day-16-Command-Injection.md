# Day 16: Command Injection

## What is Command Injection?
Instructions given to a computer are called commands.
Some websites need the OS to do work on their behalf.
Command Injection is when an attacker tricks the server into executing
their own malicious OS commands through the website.

It is more dangerous than most web vulnerabilities because it runs
commands directly on the server.

## How It Works
User Input → Website → Operating System → Result comes back

system() is a function that executes commands on the OS.

*Vulnerable Code:*
python
system("ping" + userInput)


*Malicious Input:*
8.8.8.8; whoami
*What actually executes:*
ping 8.8.8.8; whoami
## Real Life Analogy
Normal: You ask assistant → "Buy milk"
Attack: Attacker says → "Buy milk; also empty the safe"
If the assistant follows all instructions without checking = Command Injection

## Common Injection Characters
| Character | Meaning |
|-----------|---------|
| ; | Run second command after first |
| && | Run second only if first succeeds |
| \|\| | Run second only if first fails |
| \| | Pipe output to next command |
| $() | Execute command inside |

## What Attackers Run
| Command | Purpose |
|---------|---------|
| whoami | Who is running the server |
| id | User permissions |
| hostname | Server name |
| cat /etc/passwd | User list |
| ls /var/www | List website files |
| cat config.php | Database passwords |
| nc -e /bin/sh | Reverse shell = Full server control |
