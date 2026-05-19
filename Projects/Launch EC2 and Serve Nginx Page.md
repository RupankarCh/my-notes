# Goal: Launch an EC2 instance and host a webpage using Nginx. 

**Step 1: Launch and Connect** 
1. Launch a t2.micro instance (Amazon Linux/Ubuntu). 
2. Allow HTTP (80) and SSH (22) in the Security Group. 
3. Connect via SSH: ssh -i your-key.pem ec2-user@your-public-ip. 

**Step 2: Install and Start Nginx** 
● For Ubuntu: sudo apt update && sudo apt install nginx -y 
● Start Service: sudo systemctl start nginx 

**Step 3: Modify Web Page** 
1. Run: sudo nano /usr/share/nginx/html/index.html 
2. Replace content with: <h1>Hello from EC2 Nginx</h1>
