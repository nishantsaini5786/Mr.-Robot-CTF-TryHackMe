# Mr.Robot CTF TryHackMe
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
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_47_51" src="https://github.com/user-attachments/assets/dff9fba5-6bc4-4bf3-8e38-2784e5320dbb" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_48_43" src="https://github.com/user-attachments/assets/94a99c1b-b864-486a-9e59-79e5e7472d7d" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_49_06" src="https://github.com/user-attachments/assets/fd3b8792-29d2-4ad5-9d42-bdc506cf47ef" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_51_32" src="https://github.com/user-attachments/assets/036984a0-f67f-4014-840f-9be143a33bde" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_51_55" src="https://github.com/user-attachments/assets/11a61e51-e4eb-45f3-898f-bcd9c2148cd6" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_52_33" src="https://github.com/user-attachments/assets/b1dcacca-520d-4fcf-aed0-fead35fbdefd" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_55_40" src="https://github.com/user-attachments/assets/5597e72e-43e0-4bfa-936a-2c5a10aa2655" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_55_43" src="https://github.com/user-attachments/assets/746b2ae5-2508-407f-94a3-51a73c05517f" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_58_25" src="https://github.com/user-attachments/assets/220b895b-a01c-43a7-91b0-a4315b737781" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_58_58" src="https://github.com/user-attachments/assets/446949ef-2f07-480c-9f11-56b9c09dc867" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_22_59_50" src="https://github.com/user-attachments/assets/51707009-2e64-4888-9395-1295502cc30d" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_00_54" src="https://github.com/user-attachments/assets/ecc90097-316b-4595-8032-123dec1801ff" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_01_23" src="https://github.com/user-attachments/assets/e49c8ed1-5acd-4d29-a51e-f2edbacd847b" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_08_01" src="https://github.com/user-attachments/assets/95a20f7b-a73a-4c1c-9be2-30cd9e842bba" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_09_28" src="https://github.com/user-attachments/assets/238e3689-927d-49ca-9db9-bfedcb08696a" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_10_14" src="https://github.com/user-attachments/assets/a6d2fe3c-2c9c-45cc-aac5-1b2822dc7aee" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_11_04" src="https://github.com/user-attachments/assets/f6b7875a-8597-4746-afb9-209eed0a3ffc" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_11_20" src="https://github.com/user-attachments/assets/743b1312-47d8-4dfe-aebb-38e97883d9e2" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_21_46" src="https://github.com/user-attachments/assets/b05cfd68-54d5-487c-bf46-432aca31debb" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_26_27" src="https://github.com/user-attachments/assets/d7328a24-f774-412e-a254-4a30d27b7112" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_27_26" src="https://github.com/user-attachments/assets/9b06001a-4c80-454a-9926-2cac9c30c61d" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_29_39" src="https://github.com/user-attachments/assets/82d7497b-15a1-4123-9f1d-cdd65ccfadfd" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_29_53" src="https://github.com/user-attachments/assets/985a4f73-9fbd-4e76-af17-d6f89d77f080" />
<img width="1920" height="1080" alt="Screenshot_2026-09-22_23_30_12" src="https://github.com/user-attachments/assets/9d3ccbf9-44db-4adc-b9a9-86e15c3a1510" />


---

## Disclaimer

> This writeup is for **educational purposes only**.
> All testing was performed in a controlled lab environment
> (TryHackMe) with explicit permission.
