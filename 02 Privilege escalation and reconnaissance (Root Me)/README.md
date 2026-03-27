Here we are having another system to privilege escalation. </br>
First of all, I connected to a VPN and started pinging the machine to check the connection between the two machines. </br>

![image alt](https://github.com/adin991/Penetration-testing/blob/3502d3712d9ce87264ce8a94776d9d7f55910fa9/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/1.png)</br>

I nmap the IP address that was given to me, and saw two port open, such as SSH and HTTP, which HTTP is an unencrypted protocol. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/2.png) </br>


First, we see that the site is not secure (using exactly the HTTP protocol that I mentioned earlier) </br>
![image_alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/3.png)</br>

With the gobuster command, I see the hidden web application directories. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/4.png)</br>
![imge alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/5.png)</br>

So, first on the list of hidden directories was /panel directory, which was leading me on this UI of the web. Here we have an upload option, so I figured out that it is an option for communicating through this web. If you remember from previous pictures, we also have a directory called /uploads.</br>
![imge alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/6.png)</br>

On suggestion, I downloaded the script called "Reverse shell script" which is used to establish a reverse communication starting on the other machine trying to communicate to my machine.</br>
![imge alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/7.png)</br>

First of all, i didnt quite establish my .ovpn using on CTF platform, so I didn't have tun0 (a virtual VPN interface used by 3rd authories). Here I activated it so I can move on to this penetration testing. </br>
![imge alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/8.png)</br>

So when I downloaded the script and established the VPN network, I used the nano command to change the IP to my tun0 interface and a custom port "4444" that I know isn't in use. Trying to have a connection to my IP address from the IP I am trying to take advantage of.</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/9.png)</br>

Using nc -lvp, I am listening on port 4444, which is also typed in the script.</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/10.png)</br>

The script I uploaded didn't quite work. I didn't understand what this meant, so i translated it, and it's saying that "PHP is not allowed". So i knew what it meant exetention .php cannot be uploaded. So I need a different extension.</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/11.png)</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/12.png)</br>

I also saw that I can rename it just to .php5, which is a significant version of PHP. And it worked.</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/13.png)</br>

So when I go to /uploads (hidden directory in previous pictures), I saw that it is listed on the uploaded files on the web app. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/14.png)</br>

So I used the curl command, which is used to download content on the site through some of the protocols.
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/14-a.png)</br>

So the script is executed, I went back to the previous terminal where I was listening on port "4444". And it caught basically unauthorized access, which I can use the terminal on the web app. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/15.png)</br>

So here I was trying to find user.txt that has secret information inside of the file and found it on the end of the terminal. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/16.png)</br>

I was trying to find SUID files that looks "weird". In SUID (Set User ID), executing programs that have the original owner, in most cases, that is the root user. Here i didn't go furher because I found Python that looks wierd. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/17.png)</br>

This is the most important part, here I am using privilege escalation using python script i am starting it. Executing a script that won't create .py on the machine. Importing operation system and replacing the shell with a new one, and most importantly, not rejecting the effective user ID (EUID). With the command whoami, we got the root access. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/18.png)</br>

So basically I can know see what is on the root.txt file because it's owned by root, and in this situation I am the root, so I can see the file THM{...}.
![image alt](https://github.com/adin991/Penetration-testing/blob/af781a5cb96443f6774198f9f00079415c38f550/02%20Privilege%20escalation%20and%20reconnaissance%20(Root%20Me)/src/19.png)</br>
