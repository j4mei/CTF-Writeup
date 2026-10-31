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


I found three files on the FTP server: aogiri_tree.txt, rize_and_kaneki.jpg, and need_to_talk.

I used the get command to download all three files to my machine. Now I will check these files.

-**need_to_talk**

Now, I will try to run these files.

![run file](image/need-to-talk.png)

Now, I will use the strings command to check what is inside the need_to_talk file.

![strings ntt](image/stringsntk.png)

I ran the file again and entered Kamishiro as the keyword. It gave me the text You_found_1t. This might be a password to extract hidden data from the image.

![kamishiro](image/kamishiro.png)


-**rize_and_kaneki.jpg**

I found a password and used it with steghide on the rize_and_kaneki.jpg image. It successfully extracted a file named yougotme.txt.

![steghide](image/steghide.png)

Now, I will use the cat command to check the contents of yougotme.txt.

![yougotme](image/cat-yougotme.png)

I found some Morse code. Let's decode it using the CyberChef website.

![cyberchef](image/cyberchef.png)

In CyberChef, I used the following steps to decode the message:

1. From Morse Code
2. From Hex
3. To Base64
4. From Base64
5. From Base64

**Now, we will use this message as an HTTP website directory.**

![scan me](image/httpscanme.png)

**Now, I will use DIRB to find hidden directories on the website.**

![dirb](image/dirb.png)

**After running DIRB, I found an endpoint in the claim directory.**

![claim](image/httphide.png)

It redirected me to another page. I thought there might be a vulnerability, so I checked the available options on the page.

![flow entpoint](image/flower.png)

I couldn't see anything on the page, but I noticed something strange in the URL. It looked like LFI, so I decided to test it.

![LFI try](image/tryetc.png)

**It looks like we found an LFI vulnerability, but it is not showing any results. So, I will try URL encoding.**

Now, I will try URL encoding the LFI payload.

%2E%2E%2F%2E%2E%2F%2E%2E%2F%2E%2E%2F%2E%2E%2F%2E%2E%2F%2E%2E%2F%2E%2E%2F%2E%2E%2F%2E%2E%2F%2E%2E%2F%2E%2E%2F%2Fetc%2Fpasswd

![encoding url](image/lfl.png)

**we’ve found something. we can see username and password hash.**

Now, I will use John the Ripper to crack the hash.

![john ](image/john.png)

**I found the username:kamishiro & password:password123. Now, I will use these credentials to connect via SSH.**

![ssh connect](image/ssh.png)

**I successfully connected via SSH. Now, I will look for the user flag.**

![user flag](image/user.png)
