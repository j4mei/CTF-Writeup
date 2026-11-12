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

We used Gobuster on port 80 to find hidden directories and files on the web server

![gobuster](screenshots/02-gobuster.png)

