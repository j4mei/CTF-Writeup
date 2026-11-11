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

![kira hint](screenshots/Hint04.png)

While inspecting the website, I found a hint left by Kira. The hint suggested looking for a file named note.txt on the server.

After spending quite some time exploring the website, I decided to inspect its source code to look for hidden information or clues

![source code](screenshots/sourceCode05.png)

While inspecting the page source, I found an endpoint pointing to the WordPress uploads directory. I discovered an image named cropped-kiralogo.jpeg and visited the URL to investigate it further.

![url endpoint](screenshots/url06.png)

After that, I removed the unnecessary directory path from the URL and accessed the uploads directory directly to check its contents

![uploads](screenshots/uploads-07.png)

Inside the uploads directory, I found a folder named 2021. I explored its contents and found a directory named 07 containing some files. However, the 08 and 09 directories did not contain anything useful.

![07 note](screenshots/notes09.png)

Inside the 07 directory, I found two text files: note.txt and user.txt The note.txt file matched the hint I had discovered earlier on the website, while user.txt was an additional file I found during enumeration.

![note txt](screenshots/note10.png)

After checking note.txt I suspected that its contents might be a password list.

![user txt](screenshots/user11.png)

After inspecting user.txt, I confirmed that it contained a list of usernames, while note.txt contained a list of possible passwords.

**Now that I had both username and password lists, I decided to use Hydra to test for valid SSH credentials.**

![hydra](screenshots/hydra12.png)

