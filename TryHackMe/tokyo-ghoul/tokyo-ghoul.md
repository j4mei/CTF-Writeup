![tokyo intro](image/into.png)
**Tokyo Ghoul TryHackMe**

**Machine Information**

Platform: TryHackMe

Machine: Tokyo Ghoul

Difficulty:medium

Category: Boot2Root

**Network Scanning**

![nmap](image/nmap.png)

There are 3 open ports: 21, 22, and 80.
Port 21 allows anonymous login.

I opened the website running on port 80

![http source page](image/http.png)

**The source code mentioned anonymous FTP login, so I decided to connect to the FTP server.**

![ftp login anonymous](image/ftp.png)

**After logging into the FTP server, I found three files:**

- aogiri_tree.txt
- rize_and_kaneki.jpg
- need_to_talk


- 
