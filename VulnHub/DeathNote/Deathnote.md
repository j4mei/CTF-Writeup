![Death Note Banner](screenshots/int.png)

Machine: Deathnote: 1
Platform: VulnHub
Difficulty: Easy
Author: HWKDS
OS: Linux

**1. Reconnaissance**

I started with an Nmap scan to identify open ports and running services on the target machine.

![nmap](screenshots/nmap01.png)

The scan revealed two open ports:
- Port 80/tcp HTTP
- Port 22/tcp SSH

Port 80 indicated that a web server was running, while port 22 indicated that SSH was available for remote access.

**2. Web Enumeration**

![http](screenshots/http02.png)

I visited the website running on port 80 to inspect its content. After checking the website, I used Gobuster to perform directory enumeration and discover hidden directories and files.

![gobuster](screenshots/gobuster03.png)

The Gobuster scan did not reveal anything useful. While checking the robots.txt file, I found a reference to important.jpeg, but the image did not contain any useful information.

After that, I decided to inspect the website more carefully to look for any hidden clues or interesting details.

![kira hint](screenshots/hint04.png)

While inspecting the website, I found a hint left by Kira. The hint suggested looking for a file named note.txt on the server.

After spending quite some time exploring the website, I decided to inspect its source code to look for hidden information or clues

![source code](sourceCode05.png)

While inspecting the page source, I found an endpoint pointing to the WordPress uploads directory. I discovered an image named cropped-kiralogo.jpeg and visited the URL to investigate it further.

![url endpoint](screenshots/url06.png)
