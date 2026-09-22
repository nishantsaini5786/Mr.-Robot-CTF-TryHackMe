# Mr.-Robot-CTF-TryHackMe
Here's the Mr. Robot CTF (TryHackMe) machine intro

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│   ███╗   ███╗██████╗     ██████╗  ██████╗ ██████╗  ██████╗ ████████╗
│   ████╗ ████║██╔══██╗    ██╔══██╗██╔═══██╗██╔══██╗██╔═══██╗╚══██╔══╝
│   ██╔████╔██║██████╔╝    ██████╔╝██║   ██║██████╔╝██║   ██║   ██║
│   ██║╚██╔╝██║██╔══██╗    ██╔══██╗██║   ██║██╔══██╗██║   ██║   ██║
│   ██║ ╚═╝ ██║██║  ██║    ██║  ██║╚██████╔╝██║  ██║╚██████╔╝   ██║
│   ╚═╝     ╚═╝╚═╝  ╚═╝    ╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═╝ ╚═════╝    ╚═╝
│                                                                  │
│              TryHackMe  ·  Boot2Root  ·  Easy/Medium              │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

# Mr. Robot CTF — TryHackMe

> *"Hello, friend."* — A boot2root challenge inspired by the TV series **Mr. Robot**.

---

## Machine Info

| Field            | Value                          |
|------------------|--------------------------------|
| **Platform**     | TryHackMe                      |
| **Difficulty**   | Easy / Medium                  |
| **OS**           | Linux                          |
| **Category**     | Web Exploitation + PrivEsc     |
| **Objective**    | Find 3 hidden keys → root      |

---

## Overview

Mr. Robot is a Linux-based CTF machine that combines **web exploitation**
with **classic Linux privilege escalation**. The target runs a **WordPress**
site along with a custom web terminal interface.

You must chain together:

- Information gathering
- WordPress vulnerability exploitation
- SUID misconfiguration abuse

…to fully compromise the box and capture all three keys.

---

## Skills Required

| Area                  | Techniques                                              |
|-----------------------|---------------------------------------------------------|
| **Web Enumeration**   | `robots.txt` discovery · directory brute-force (gobuster / ffuf) |
| **Password Attacks**  | Custom wordlist dedup · Hydra brute-force on WP login   |
| **RCE Exploitation**  | PHP reverse shell via WordPress theme editor            |
| **Hash Cracking**     | MD5 identification & cracking (John / CrackStation)     |
| **Privilege Escalation** | Abusing SUID `nmap` interactive mode → root          |

---

## Path to the 3 Keys

```
[Key 1]  robots.txt  →  /key-1-of-3.txt
[Key 2]  shell → /home/robot/ MD5 hash → crack → su robot → key-2-of-3.txt
[Key 3]  SUID nmap --interactive → !sh → root → /root/key-3-of-3.txt
```

- **Key 1** — Discovered via `robots.txt`, accessed at `/key-1-of-3.txt`
- **Key 2** — After shell, find MD5 hash in `/home/robot/`, crack it, then `su robot`
- **Key 3** — Use SUID `nmap --interactive` → `!sh` → root → read root key

---

## Tools Used

```
nmap  ·  gobuster / ffuf  ·  hydra  ·  john  ·  nc  ·  python pty
```

---

## One-Line Summary

> A classic beginner-friendly CTF that chains the full pentest
> methodology: **Web Enum → Cred Brute-Force → WP RCE → Hash Crack
> → SUID PrivEsc.**

---

## Screenshots
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_27_15" src="https://github.com/user-attachments/assets/90838ccd-8ecb-45d4-9eae-f4b2875492bb" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_28_36" src="https://github.com/user-attachments/assets/84ae637a-b8ae-405a-a288-ee0c43172179" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_29_24" src="https://github.com/user-attachments/assets/99b394ed-9f8f-4667-87b5-74c67ce76b18" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_29_42" src="https://github.com/user-attachments/assets/35a94a36-0c52-4d51-99aa-2c69189c5a25" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_30_52" src="https://github.com/user-attachments/assets/034c34be-8a54-4f5c-b7f7-596c2e89795f" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_44_12" src="https://github.com/user-attachments/assets/90992647-17d2-44f5-8769-e66f8daec9ab" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_45_51" src="https://github.com/user-attachments/assets/09c0333d-a48a-4a74-88dd-4ec937d8a774" />


---

## Disclaimer

> This writeup is for **educational purposes only**.
> All testing was performed in a controlled lab environment
> (TryHackMe) with explicit permission.
