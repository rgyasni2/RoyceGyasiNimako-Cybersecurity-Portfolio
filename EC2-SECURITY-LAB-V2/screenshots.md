

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

SSM Session Manager: Now that I know that traffic is being captured I decided to remove SSH entirely. I first launched a session using Systems Manager, then went back to my instance and removed SSH from the inbound rules. Then I went to networking to ensure that there were no elastic IPs being published. 
<img width="1911" height="295" alt="image" src="https://github.com/user-attachments/assets/82ddaf51-a089-4ef0-b8db-8aa20729e66b" />
<img width="1587" height="242" alt="image" src="https://github.com/user-attachments/assets/bb28cd12-1082-4d34-99be-1ef40d7b2790" />


