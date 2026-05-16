# Cisco Proprietary Protocols Exclusive networking protocols designed by Cisco: 

✔ EIGRP – Efficient routing for enterprise networks  
✔ HSRP – Ensures high availability for routers  
✔ CDP – Helps Cisco devices share network information  
✔ VTP – Simplifies VLAN management across Cisco switches  
✔ PVST – Optimizes network traffic per VLAN 

# STP (Spanning Tree Protocol):
**Prevents network loops in switched networks** by dynamically selecting the best data transmission path while blocking redundant links. 

✔ Prevents broadcast storms & data duplication  
✔ Elects a Root Bridge to optimize traffic flow  
✔ Variants like RSTP provide faster convergence 


# TLS (Transport Layer Security):
A cryptographic **protocol securing communication over the internet.** Successor to SSL, TLS ensures **data encryption, integrity, and authentication** in web browsing, email, and secure transactions. 

✔ Used for HTTPS (port 443), secure emails (IMAPS, SMTPS)
✔ Enhances security over older SSL versions
✔ Latest versions (TLS 1.2 & TLS 1.3) offer stronger encryption 


# SSH
It allows to connect to a remote machine all using the CLI.

## There's a connection timeout
This is a security group issue. Any timeout (not just for SSH) is related to security groups or a firewall. Ensure your security group looks like this and correctly assigned to your EC2 instance.
<img width="1298" height="332" alt="image" src="https://github.com/user-attachments/assets/ff5a7cb8-012c-462a-b3a3-fa4270da9c77" />

## 2) There's still a connection timeout issue
If your security group is properly configured as above, and you still have connection timeout issues, then that means a corporate firewall or a personal firewall is blocking the connection. Please use EC2 Instance Connect as described in the next lecture.

## SSH does not work on Windows
If it says: ssh command not found, that means you have to use Putty

## There's a connection refused
This means the instance is reachable, but no SSH utility is running on the instance
Try to restart the instance
If it doesn't work, terminate the instance and create a new one. Make sure you're using Amazon Linux 2

## Permission denied (publickey,gssapi-keyex,gssapi-with-mic)
This means either two things:
You are using the wrong security key or not using a security key. Please look at your EC2 instance configuration to make sure you have assigned the correct key to it.
You are using the wrong user. Make sure you have started an Amazon Linux 2 EC2 instance, and make sure you're using the user ec2-user. This is something you specify when doing ec2-user@<public-ip> (ex: ec2-user@35.180.242.162) in your SSH command or your Putty configuration
