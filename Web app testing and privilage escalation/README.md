In this set of tasks, the following:

brute forcing </br>
hash cracking </br>
service enumeration </br>
Linux Enumeration </br>
</br>
Web app testing and privilege escalation </br>                                
This is a documented log of a step-by-step process of an Act. </br>
</br>
Connected to a server through a VPN service. Testing connectivity on private server through </br>
command ping. </br>
Nmap scanning reports protocols and services on the web app. </br>

![image alt](https://github.com/adin991/Penetration-testing/blob/59c1bdbc6cb1948c89bf1a38781eca85aa7e9915/Web%20App%20Testing%20and%20Privilage%20Escalation/src/1.png)</br>
</br>

Web app can be accessed through an IP address given, on web browser can be searched up on the URL lba search link. Given that it doesn’t have info on the web page, I sought on “Inspect </br> element” to see hidden messages or additional information.  </br>
NOTE: The site is using the HTTP protocol, which isn't encrypting data and has an HTML comment on the web page. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/8082a74f48782448992c16fa44a052a0325b51aa/Web%20App%20Testing%20and%20Privilage%20Escalation/src/a%2B3.png)</br>

Using the gobuster command explained in the command.txt file, trying to brute force hidden directories. It gets with the result of a /development hidden directory. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/dd7622170b935c5d20aecce142294b80a648a57d/Web%20app%20testing%20and%20privilage%20escalation/src/2.1.png) </br>

Adding /development text to the URL IP address of the web app. </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/dd7622170b935c5d20aecce142294b80a648a57d/Web%20app%20testing%20and%20privilage%20escalation/src/2.2.png) </br>

Through the new directory, I don't really have any info to continue, and I tried NMAP to see what protocols are open with additional versions. SMB protocol is open. Trying to find information on the SMB protocol. SMB protocol is a shared resource inside of the network (Files, printers, password policy, folders, Information of the system). Using the command enum4linux to gather information on Linux (or Windows). </br>

![image alt](https://github.com/adin991/Penetration-testing/blob/dd7622170b935c5d20aecce142294b80a648a57d/Web%20app%20testing%20and%20privilage%20escalation/src/3.png) </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/eca896785d1d11b8000762f4f28d4666384782f2/Web%20app%20testing%20and%20privilage%20escalation/src/4.png) </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/eca896785d1d11b8000762f4f28d4666384782f2/Web%20app%20testing%20and%20privilage%20escalation/src/5.png) </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/eca896785d1d11b8000762f4f28d4666384782f2/Web%20app%20testing%20and%20privilage%20escalation/src/6.png) </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/eca896785d1d11b8000762f4f28d4666384782f2/Web%20app%20testing%20and%20privilage%20escalation/src/7.png) </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/eca896785d1d11b8000762f4f28d4666384782f2/Web%20app%20testing%20and%20privilage%20escalation/src/8.png) </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/eca896785d1d11b8000762f4f28d4666384782f2/Web%20app%20testing%20and%20privilage%20escalation/src/9.png) </br>
![image alt](https://github.com/adin991/Penetration-testing/blob/eca896785d1d11b8000762f4f28d4666384782f2/Web%20app%20testing%20and%20privilage%20escalation/src/10.png) </br>

So here I found an enumeration of the users, kay and jan. Ubuntu is the default user. </br>

![image alt](https://github.com/adin991/Penetration-testing/blob/eca896785d1d11b8000762f4f28d4666384782f2/Web%20app%20testing%20and%20privilage%20escalation/src/11.png)</br>

So now I know on the machine it has 2 users, and now I was trying to see how to crack some of those 2 users, so basically I found a rockyou.txt.gz to unzip with a command gunzip. Rockyou.txt is a text document that has common passwords. </br>

![image alt](https://github.com/adin991/Penetration-testing/blob/0a1b0b29ab3abfb07fa42e46673de6e2ccded934/Web%20app%20testing%20and%20privilage%20escalation/src/12.png)</br>

I first tried jan user through the SSH protocol, and I found the password on blue marked text. </br> 

![image alt](https://github.com/adin991/Penetration-testing/blob/0a1b0b29ab3abfb07fa42e46673de6e2ccded934/Web%20app%20testing%20and%20privilage%20escalation/src/13.png)</br>

So I enter the jan user with ssh [name]@[IP address], enter the password, and access the user jan. Additional research through a hierarchy of the machine I access as jan tried to see what files are available and etc. </br>

![image alt](https://github.com/adin991/Penetration-testing/blob/0a1b0b29ab3abfb07fa42e46673de6e2ccded934/Web%20app%20testing%20and%20privilage%20escalation/src/14.png)</br>

I started a script [linpeas.sh](https://github.com/peass-ng/PEASS-ng/releases) downloaded on the link. I used 2 windows of the terminal with the command scp to transfer a script from my machine to a machine I am attacking. </br>

![image alt](https://github.com/adin991/Penetration-testing/blob/7177c02be9764d85dd772cdf0d2be9c2dac2f851/Web%20app%20testing%20and%20privilage%20escalation/src/17.1.png)</br>

In the next images, you will see the result of the script. </br>

![image alt](https://github.com/adin991/Penetration-testing/blob/339fef39b841275f7e0851d47fcffa9233120aa7/Web%20app%20testing%20and%20privilage%20escalation/src/18.png)</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/339fef39b841275f7e0851d47fcffa9233120aa7/Web%20app%20testing%20and%20privilage%20escalation/src/19.png)</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/339fef39b841275f7e0851d47fcffa9233120aa7/Web%20app%20testing%20and%20privilage%20escalation/src/20.png)</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/339fef39b841275f7e0851d47fcffa9233120aa7/Web%20app%20testing%20and%20privilage%20escalation/src/21.png)</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/339fef39b841275f7e0851d47fcffa9233120aa7/Web%20app%20testing%20and%20privilage%20escalation/src/22.png)</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/339fef39b841275f7e0851d47fcffa9233120aa7/Web%20app%20testing%20and%20privilage%20escalation/src/23.png)</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/339fef39b841275f7e0851d47fcffa9233120aa7/Web%20app%20testing%20and%20privilage%20escalation/src/24.png)</br>

Script found private SSH keys. The route of the file is seen. 

![image alt](https://github.com/adin991/Penetration-testing/blob/339fef39b841275f7e0851d47fcffa9233120aa7/Web%20app%20testing%20and%20privilage%20escalation/src/25.png)</br>

On the first terminal that I accessed, I found the route and opened it the file is encrypted. RSA is a private key used as SSH authentication instead of a password. </br> 

![image alt](https://github.com/adin991/Penetration-testing/blob/fa71307c8efb7fa5071a1a556b56793eb4fed912/Web%20app%20testing%20and%20privilage%20escalation/src/27.png)</br>
![image alt](https://github.com/adin991/Penetration-testing/blob/fa71307c8efb7fa5071a1a556b56793eb4fed912/Web%20app%20testing%20and%20privilage%20escalation/src/28.png)</br>



![image alt]()</br>
![image alt]()</br>
![image alt]()</br>
