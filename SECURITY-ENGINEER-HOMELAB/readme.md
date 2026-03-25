This is a Security Engineer Home Lab. This lab is a beginner level project that teaches the basics of what a security engineer might do with a purple team project. I set up an Ubuntu Server Virtual machine and a Kali Linux Virtual machine. On the Ubuntu server I will first harden the server and enable logging. Then test that the hardening worked on the Kali VM and verify that everything worked. 

I first got a baseline of the ubuntu server so I confirm the IP as well as the user. 

I then moved onto creating a non root admin user so that I can practice the principle of least privilege. 

The next step would be hardening the SSH so first I made a copy so that just incase anything happens I can safely go back. I then blocked direct root logins, disabled password logins over SSH, and finally allowed SSH key logins so that I can login through my Kali VM. 

I then created the key on Kali and sent it thorugh to my Ubuuntu server. 
