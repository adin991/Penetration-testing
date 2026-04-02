Investigating a Windows machine that has been previously compromised.

When I started the Windows machine, I saw that Windows is connecting to an IP adress following below.</br>

![image_alt](https://github.com/adin991/Penetration-testing-CTF/blob/a1cdb6f68529b910a808ddf183beb3283839a188/03%20Investigating%20Windows/src/1-additional.png) </br>

Also, when I exited the connection terminal first, what I did was find who I am. </br>

![image_alt](https://github.com/adin991/Penetration-testing-CTF/blob/a1cdb6f68529b910a808ddf183beb3283839a188/03%20Investigating%20Windows/src/2.png) </br>

First, when investigating the OS, I needed to know which version of Windows it is. Here it says Windows Server 2016. </br> 

![image_alt](https://github.com/adin991/Penetration-testing-CTF/blob/d335215b1db61ff0f40e1d60a92e49946a6a276d/03%20Investigating%20Windows/src/3.png) </br>

Here I saw that only 2 accounts have logged on, and the last one that was logged on is the Administrator (It was me) and I also see that John was last logged on in 2019 (suspicious). </br>

![image_alt](https://github.com/adin991/Penetration-testing-CTF/blob/d335215b1db61ff0f40e1d60a92e49946a6a276d/03%20Investigating%20Windows/src/4.png) </br>
![image_alt](https://github.com/adin991/Penetration-testing-CTF/blob/d335215b1db61ff0f40e1d60a92e49946a6a276d/03%20Investigating%20Windows/src/5.png) </br>

Also, here we see the users who have administrator privileges. Those are Jenny and the guest beside the user Administrator. </br>

![image_alt](https://github.com/adin991/Penetration-testing-CTF/blob/d335215b1db61ff0f40e1d60a92e49946a6a276d/03%20Investigating%20Windows/src/6.png) </br>

Now, name of the scheduled tasks that are malicious, here I get the Idea which is the Windows OS to see the scheduled tasks that are not in the Microsoft route. Many of them are malicious. One of them is "Clean system info", also flashupdate22 is where additional 22 is customised because he has an original file called "flashupdate" and "falshupdate" where there is a typo. </br>

![image_alt](https://github.com/adin991/Penetration-testing-CTF/blob/d335215b1db61ff0f40e1d60a92e49946a6a276d/03%20Investigating%20Windows/src/7.png) </br>

For falshupdate I see -WindowStyle hidden, also "update windows" in Internet Explorer is very obvious because WindowsUpdate is in Windows\temp\...  

![image_alt](https://github.com/adin991/Penetration-testing-CTF/blob/43a88a3f033e40a2fd313de917637340354fe3aa/03%20Investigating%20Windows/src/ad-1.png) </br>
![image_alt](https://github.com/adin991/Penetration-testing-CTF/blob/43a88a3f033e40a2fd313de917637340354fe3aa/03%20Investigating%20Windows/src/ad-1.png) </br>




![image_alt]() </br>
![image_alt]() </br>
![image_alt]() </br>
![image_alt]() </br>
![image_alt]() </br>

![image_alt]() </br>
![image_alt]() </br>
![image_alt]() </br>

![image_alt]() </br>
![image_alt]() </br>
![image_alt]() </br>


