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

Adding /development text to the URL IP address of the web app.
![image alt](https://github.com/adin991/Penetration-testing/blob/dd7622170b935c5d20aecce142294b80a648a57d/Web%20app%20testing%20and%20privilage%20escalation/src/2.2.png) </br>

Through the new directory, we don't really have any info to continue, and I tried NMAP to see what protocols are open with additional versions. SMB protocol is open.
![image alt](https://github.com/adin991/Penetration-testing/blob/dd7622170b935c5d20aecce142294b80a648a57d/Web%20app%20testing%20and%20privilage%20escalation/src/3.png)

