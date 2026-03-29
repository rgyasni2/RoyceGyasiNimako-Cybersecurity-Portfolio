This is a Security Engineer Home Lab. This lab is a beginner level project that is a blue-team hardening and monitoring lab with basic attacker validation from Kali. I set up an Ubuntu Server Virtual machine and a Kali Linux Virtual machine. On the Ubuntu server I will first harden the server and enable logging. Then test that the hardening worked on the Kali VM and verify that everything worked. 

I first got a baseline of the ubuntu server so I confirm the IP as well as the user. 

I then moved onto creating a non root admin user so that I can practice the principle of least privilege. 

The next step would be hardening the SSH so first I made a copy so that just incase anything happens I can safely go back. I then blocked direct root logins, disabled password logins over SSH, and finally allowed SSH key logins so that I can login through my Kali VM. 

I then created the key on Kali and sent it thorugh to my Ubuntu server. 

Next I wanted to check the UFW status and saw that it was off so my next steps were to first turn it on and ensure that its purpose is to deny incoming, allow outgoing unless I intentionally changed both.

I wanted to make sure that I got Fail2ban so that it monitors authentication logs and can trigger bans after repeated failed attempts. I created a local jali config (after copying the original) that has SSH protection, blocks you after 3 failed attempts that are counted over 10 minutes, and the ban is for 1 hour. 

I now want to set up logs for the related logs for the SSH, fail2ban, and live logs in a journal for later. 

Now that the logs are set up I am going to go to my Kali VM and run a basic nmap scan which shows that ssh is still open. I then wanted to run a -sv run to see the versions that the ports were running on for possible explotation. Finally I ran an advanced nmap scan just to see what more would be shown to me as Im not sure. I learned that it showed me which ports where closed 

Since I had the nmap scan finished and "confirmed" that SSH was open I first logged into through ssh and then tried logging into a fake user so that the logs could pick it up. I then repeadtly tried logging in with SSH using the wrong password to test the detection and automatic banning.

Now that I confirmed that the firewall works and correctly bans users when they do not comply. The final step that I wanted to complete was adding monitoring on the SSH config file to make sure that it would not be altered in any case and if it was it would be logged accordingly. The config that I had on the file was: sudo auditctl -w /etc/ssh/sshd_config -p wa -k ssh_config_watch which seemed good enough. 


What I learned:

The thing that I feel 100% more confident is setting up VMs. I ran into a lot of problems trying to figure out how to send the key from the Kali VM to the Ubuntu sever as I didn't enable internet access to the ubuntu server for some reason, I didn't know that I had to set up IP's for each servers, I didn't know about having mulitple adapters, etc. etc. After I smoothed all of that out I had a basic understanding of linux before but now I feel a lot more comfortable with at least a rough frame work how I should defend an ubuntu server. This was my first cyber project so I learned good practices such as copying important files incase you mess up and what nmap actually does. I learned about hardening a server, the importance of keys, detection & response, etc. Overall it was a really fun project.  

