**Simple CTF**

**Q. How many services are running under port 1000?**

![nmapscan](https://github.com/Anirudh-Saxena/Simple-CTF-THM/assets/73027020/b5bdcb11-ebca-49c7-a058-211ee488244d)

So we can see in total there are 2 ports running in open state under 1000

**Q. What is running on the higher port?**

`ssh` services are running on openport

**Q. What's the CVE you're using against the application?**

Before answering this lets check the website and see if we can go anything on it...

![image](https://github.com/Anirudh-Saxena/Simple-CTF-THM/assets/73027020/a7f863a8-7e73-4eb3-a83c-2d3c1c7fb78b)

hmm okie we can see that the webiste is running on apache server well this was informed to us by nmap also so nothing new ..



Lets use gobuster and see the dir that we can visit on the website..

![gobires](https://github.com/Anirudh-Saxena/Simple-CTF-THM/assets/73027020/69389b70-3ee1-4052-8500-da01b5a7ab15)

Lets visit the /simple dir and see if we can find anything on the website ..

Hmm intresteing after looking in the site for a little long i found out something intresting, which is:


![228](https://github.com/Anirudh-Saxena/Simple-CTF-THM/assets/73027020/57269c6d-6ff4-4997-8dea-690d06d890ec)

Simply searching this we can find the exploit for it which is sqli... 

https://www.exploit-db.com/exploits/46635

lets use this exploit and connect with the website..

This can be done by this command..

      python3 46635.py -u http://<ip>/simple

as we can see the script is in python2 so we will be changing it to python3 using the tool `2to3`, the command is simple


        2to3 46635.py -w

Now execute the script and wait for the result..

![res](https://github.com/Anirudh-Saxena/Simple-CTF-THM/assets/73027020/f1e421e6-b332-4ac5-a99f-5f73c783f4af)

Noice now we have the password as well as the name lets decrypt this and see what the password is 

https://www.dcode.fr/md5-hash visit this wesbite and enter the salt as well as the password you will find the pass now lets conennect 

Now we have the pass lets move forward with the `ssh` connection

**Q. What's the password?**
Try to crack this its fun!!

**Q. Where can you login with the details obtained?**

`ssh`

**Q. What's the user flag?**

        G00d j0b, keep up!

**Q. Is there any other user in the home directory? What's its name?**

Lets find out yes there is another one..

![ssh](https://github.com/Anirudh-Saxena/Simple-CTF-THM/assets/73027020/2e88b639-e22c-4e21-81ae-7a7ae3d3ef40)


Now lets seee the version and see if we can find any vuln in it..

After searching the version found the vuln  for more infor read this : https://steflan-security.com/linux-privilege-escalation-vulnerable-sudo-version/

So we can simply use the `vim` editor and execute the command in it and we are good to goo..

![congo](https://github.com/Anirudh-Saxena/Simple-CTF-THM/assets/73027020/da6ec6c2-8637-4ba0-aeb5-622ccbf9f2fa)


Letss goo...
