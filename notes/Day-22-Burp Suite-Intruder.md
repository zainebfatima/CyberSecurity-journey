# Day 22: Burp Suite Intruder

## What is Intruder?
The work which we do manually in Repeater is done
automatically by Intruder.
Intruder sends hundreds of requests automatically
with different values — perfect for brute forcing!

## Intruder vs Repeater
| Feature | Repeater | Intruder |
|---------|----------|----------|
| Requests | Manual — one by one | Automatic — hundreds |
| Speed | Slow | Fast |
| Use case | Modify & test | Brute force & fuzz |

## 4 Attack Types

| Type | How it works |
|------|-------------|
| Sniper | One field targeted, one value fixed |
| Battering Ram | Same value in all fields |
| Pitchfork | Different lists, paired together |
| Cluster Bomb | Every possible combination tried |

## Practical Steps
1. Open Burp Suite → Proxy → Open Browser
2. Visit PortSwigger lab — username enumeration
3. Access lab → My account → Login page
4. Type anything in username & password → Submit
5. Proxy → HTTP History → POST request
6. Right click → Send to Intruder
7. Scroll down — highlight username value
8. Click "Add $" — payload position set!
9. Payloads tab → Add usernames manually
10. Click "Start Attack"
11. Results window opens — check status codes!

## Reading Results
| Status Code | Meaning |
|-------------|---------|
| 200 | Wrong credentials |
| 302 | Redirect = Login successful! 🎯 |
| 400 | Bad request / invalid username |

## Key Concept
Intruder is like having 1000 keys and a machine
that tries every key automatically — the one
that opens the lock = vulnerability found! 🎯
<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/58efc9a8-6589-4889-80fd-51a6b5ca474e" />
<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/95af8627-bf81-40ac-9c69-358b2aad068f" />
<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/3cfd8314-e06f-4149-8d4b-dc2402202840" />


