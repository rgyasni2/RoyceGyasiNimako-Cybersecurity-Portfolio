E2 Security Lab

Overview: For this lab I am going to incorrectly configure a EC2 instance. This instance will only allow traffic from my IP and SSH. I will first walk through the first iteration of the instance. Realize that the security controls are not enough then attaching an IAM role to the Instance and setting up a necessary cloud trail. After I am going to simulate an attack and then detect the attack with Cloud Trail. Finally I will remove SSH using SSM and go over what I learned. 

Setting up the EC2 Instance: As I was setting up the EC2 instance I intentionally left everything default except switching traffic from anywhere to just my IP and leaving SSH on. 
<img width="1209" height="644" alt="image" src="https://github.com/user-attachments/assets/b217fb78-af6c-421c-8ce5-e8e744b2b204" />

Attaching an IAM Role to EC2: After launching the instance I  went to IAM Roles to create a role for this EC2 instance that has AmazonSSMManagedInstanceCore attached to it to ensure a secure connection when in use. 
<img width="1518" height="759" alt="image" src="https://github.com/user-attachments/assets/4ea5b961-ee77-47b2-a9a6-623c1c29f91f" />
<img width="1919" height="416" alt="image" src="https://github.com/user-attachments/assets/a174c74a-41b5-418c-b4ed-e8152e462e75" />

Setting up CloudTrail: After I went to Cloud Trail to capture any AWS API traffic that might happen. I kept management events, read, write permissions active. 
<img width="1847" height="291" alt="image" src="https://github.com/user-attachments/assets/536598c6-df19-42fe-9593-7425568f7c22" />
<img width="992" height="294" alt="image" src="https://github.com/user-attachments/assets/d562bb6a-af63-4978-b744-1c9f75a0ab2e" />

Checking if things are working as intended: I checked the resources inside of the instance to see if the Cloud Trail would catch it and it did.
<img width="1585" height="620" alt="image" src="https://github.com/user-attachments/assets/34dc1932-a036-4321-a85c-55748a09a32b" />

SSM Session Manager: Now that I know that traffic is being captured I decided to remove SSH entirely. I first launched a session using Systems Manager, then went back to my instance removed SSH from the inbound rules. Then I went to networking to ensure that there were no elastic IPs being published. 
<img width="1911" height="295" alt="image" src="https://github.com/user-attachments/assets/82ddaf51-a089-4ef0-b8db-8aa20729e66b" />
<img width="1587" height="242" alt="image" src="https://github.com/user-attachments/assets/bb28cd12-1082-4d34-99be-1ef40d7b2790" />

Future Improvements: For my first lab I made an IAM user with AdministratorAccess but for the future I will practice the principles of least privilege.

What I learned: 
1. A big take away that I learned was that the principle of least privilege does matter a lot. I accidentally made and deleted a lot of instances (because I am new) but if everyone in the company was able to mess around with every tool available it would be so dangerous because they could either not know what they are doing and mess something up or accidentally give information away on accident.
2. Another big thing is reducing attack surface, the simple task of making sure that you are not attaching your Elastic IP is super imortant because if an attacker attacks that instance its important that they cannot open ports, attach IAM permissions, etc. 
3. Cloud Trail is a cool tool that I can imagine that is utilized a great deal as it can watch for any type of traffic that you configure it to make monitoring your servers even easier. 


Future Improvements: Instead using an IAM accounnt with AdministratorAccess, try to practice principle of least privilege at all levels. 
