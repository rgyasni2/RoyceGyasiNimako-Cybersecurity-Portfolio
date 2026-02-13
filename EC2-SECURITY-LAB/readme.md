E2 Security Lab

Overview: For this lab I am going to incorrectly configure a EC2 instance. I am going to intentionally misconfigure the traffic that is allowed. Then I am going to find the vulnerabilites using GuardDuty, then logging future actions using CloudTrail, and then hardening the instance as much as possible. 

Setting up the EC2 Instance: As I was setting up the EC2 instance I intentionally left everything default except switching traffic from anywhere to just my IP and leaving SSH on. 
<img width="1209" height="644" alt="image" src="https://github.com/user-attachments/assets/b217fb78-af6c-421c-8ce5-e8e744b2b204" />

Attaching an IAM Role to EC2: After launching the instance I  went to IAM Roles to create a role for this EC2 instance that has AmazonSSMManagedInstanceCore attached to it to ensure a secure connection when in use. 
<img width="1518" height="759" alt="image" src="https://github.com/user-attachments/assets/4ea5b961-ee77-47b2-a9a6-623c1c29f91f" />
<img width="1919" height="416" alt="image" src="https://github.com/user-attachments/assets/a174c74a-41b5-418c-b4ed-e8152e462e75" />

Setting up CloudTrail: After I went to Cloud Trail to capture any AWS API traffic that might happen. I kept management events, read, write permissions active. 
<img width="1847" height="291" alt="image" src="https://github.com/user-attachments/assets/536598c6-df19-42fe-9593-7425568f7c22" />
<img width="992" height="294" alt="image" src="https://github.com/user-attachments/assets/d562bb6a-af63-4978-b744-1c9f75a0ab2e" />
