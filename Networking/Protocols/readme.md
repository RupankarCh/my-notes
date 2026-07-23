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

**Errors**
- There's a connection timeout: This is a security group issue. Any timeout (not just for SSH) is related to security groups or a firewall. Ensure your security group looks like this and correctly assigned to your EC2 instance.
<img width="1298" height="332" alt="image" src="https://github.com/user-attachments/assets/ff5a7cb8-012c-462a-b3a3-fa4270da9c77" />
- There's still a connection timeout issue: If your security group is properly configured as above, and you still have connection timeout issues, then that means a corporate firewall or a personal firewall is blocking the connection. Please use EC2 Instance Connect as described in the next lecture.
- SSH does not work on Windows: If it says: ssh command not found, that means you have to use Putty
- There's a connection refused: This means the instance is reachable, but no SSH utility is running on the instance Try to restart the instance If it doesn't work, terminate the instance and create a new one. Make sure you're using Amazon Linux 2.
- Permission denied (publickey,gssapi-keyex,gssapi-with-mic) This means either two things: You are using the wrong security key or not using a security key. Please look at your EC2 instance configuration to make sure you have assigned the correct key to it. or You are using the wrong user. Make sure you have started an Amazon Linux 2 EC2 instance, and make sure you're using the user ec2-user. This is something you specify when doing ec2-user@<public-ip> (ex: ec2-user@35.180.242.162) in your SSH command or your Putty configuration


**SSH Configuration**:

On Router:
```
R1(config)# hostname <hostname>
<hostname>(config)# ip domain-name <ssh.domain.lab>
(config)# username <user_name> privilege 15 secret <ssh_password>
(config)# crypto key generate rsa
1024
(config)#line vty 0 4
(config-line)# transport input ssh
(config-line)# login local
(config-line)# ip ssh version 2
(config-line)# end
#wr
#show ip ssh
```
Connect with Linux:
```
#ssh <username>@<IP>
```
Connect with Router:
```
#ssh -l <user_name> <IP>
```

# Telnet
Port 23 – Telnet is a **terminal emulation program that enables you to access IOS through the network and configure the device remotely**. The device that is being configured needs to have a Telnet server installed and an IP address configured.
Telnet was used before SSH and offers the same functionality, One of the biggest disadvantages of this protocol is that it **sends all data as clear text**, which includes the passwords! This is the reason why this type of access is usually not used anymore. Instead, SSH is usually used.

you don’t need to run a Telnet service or have any special port open on your side.
Your computer: runs the Telnet client program.

**Configuration:**
To configure basic Telnet between two Cisco routers, you need:

IP connectivity between the routers. ping must work

**Topology:**
Router1 ---------------- Router2
192.168.1.1/24      192.168.1.2/24

**Option 1:** A username/password (or line password) on the router being accessed.

Router 2
```
R2(config)# username admin secret cisco123
R2(config)# line vty 0 4 (Configure remote virtual terminal lines, Here 0-4 means a total of 5 simultaneous remote login sessions)
R2(config-line)# login local (Authenticate using the local username database)
R2(config-line)# transport input telnet (Allow Telnet connections)
R2(config-line)# exit
R2(config)# enable secret class123
R2(config)# end
R2# copy running-config startup-config
```
Router 1
```
#telnet 192.168.1.2
username: admin
password: cisco123
Router2> enable
Password: class123
```


**Option 2:** use a VTY password
**VTY: A VTY (Virtual Teletype) line is a virtual login port that allows users to remotely access the router using Telnet or SSH over the network.**
```
Router2(config)# line vty 0 4 
Router2(config-line)# password telnet123
Router2(config-line)# login
Router2(config-line)# transport input telnet 
```
Then connect:
```
Router1# telnet 192.168.1.2
Password: telnet123
Router2> enable
Password: class123
Router2#
```

# RIP V2 Configuration
```
Router> enable
Router# configure terminal

Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# no auto-summary
Router(config-router)# network 192.168.1.0
Router(config-router)# network 10.0.0.0
Router(config-router)# exit

Router(config)# end
Router# write memory
```
**Configuration of CISCO routing protocol authentication:** (Do same for all Routers)
```
(config)#key chain RIP
key 1
key-string 0 rip@123
exit
exit
interface s 1/0
ip rip authentication mode text
ip rip authentication key-chain RIP
shutdown
no shutdown
exit
#show ip protocols
#show key chain
#show ip route
```
If one wants to communicate with a machine they must know the password
