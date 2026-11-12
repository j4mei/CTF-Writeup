# Vegeta - VulnHub CTF

## Machine Information

- **Platform:** VulnHub
- **Machine:** Vegeta
- **Difficulty:** Beginner
- **Type:** Boot2Root
- **Goal:** Capture the user and root flags.

## Introduction

This writeup covers my walkthrough of the Vegeta machine from VulnHub.I will document the enumeration, exploitation, and privilege escalation steps taken during the assessment.

**Reconnaissance**

Started with Nmap to identify open ports and running services.

![nmap](screenshots/01-nmap.png)

Used Nmap and found two open ports: 22 (SSH) and 80 (HTTP)

**Web Enumeration**

We used Gobuster on port 80 to find hidden directories and files on the web server

![gobuster](screenshots/02-gobuster.png)

After finding directories with Gobuster, I opened the target website on port 80 to investigate further

![web](screenshots/03-web.png)

We first checked the `robots.txt` file to look for any hidden paths or directories.

![robots.txt](screenshots/04-robots.png)

The robots.txt file revealed a directory named `/find_me`.

![find me](screenshots/05-find.png)

Inside `/find_me`, we found a file named `find_me_html`.

![base64](screenshots/06-cypto.png)

We found a Base64-encoded string in the page source code.

Decoded the Base64 string using CyberChef.

![cyberchef](screenshots/07-qr.png)

Decoded the Base64 string twice in CyberChef, then changed the output format to Raw. This generated a QR code.

![qr scan](screenshots/08-qr-decode.png)

After scanning the QR code, we found a password: `topshellv`.

Next, we checked another directory on the web server named `/bulme`.

![bulme](screenshots/09-bulme.png)

Inside `/blume`, we found `hahahah.wav`. It was an MP3 audio file containing Morse code sounds.

I searched for an online Morse code decoder and used it to decode the Morse code sounds.

![morse decoder](screenshots/10morse.png)

After decoding, we found a text containing a username and password.

We used the username and password to try logging in through SSH.

![ssh](screenshots/11-ssh.png)

Successfully logged in via SSH using:

- **Username:** `trunks`
- **Password:** `u$3r`

