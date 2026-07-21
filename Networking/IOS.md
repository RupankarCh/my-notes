# Theory
## Types of Password
- Console Password: Connectiing with port
- AUX Password: Connecting with port
- Enable Password: Priviledge Escalation
- Enable Secret Password: Encrypted Priviledge Escalation
- Line VTY Password: Connecting remotely
**VTY: A VTY (Virtual Teletype) line is a virtual login port that allows users to remotely access the router using Telnet or SSH over the network.**

| Mode                                   | Prompt                   | Purpose                                                     | How to Enter                        |
| -------------------------------------- | ------------------------ | ----------------------------------------------------------- | ----------------------------------- |
| **User EXEC**                          | `Router>`                | Basic monitoring commands; limited access                   | Default after login                 |
| **Privileged EXEC**                    | `Router#`                | Full administrative commands, access to configuration modes | `enable`                            |
| **Global Configuration**               | `Router(config)#`        | Configure the device as a whole                             | `configure terminal`                |
| **Interface Configuration**            | `Router(config-if)#`     | Configure a specific interface                              | `interface <type> <number>`         |
| **Line Configuration**                 | `Router(config-line)#`   | Configure console, AUX, or VTY lines                        | `line console 0` or `line vty 0 4`  |
| **Router Configuration**               | `Router(config-router)#` | Configure routing protocols (OSPF, EIGRP, RIP, etc.)        | `router ospf 1`, `router rip`, etc. |
| **Subinterface Configuration**         | `Router(config-subif)#`  | Configure logical subinterfaces                             | `interface GigabitEthernet0/0.10`   |
| **VLAN Configuration** *(on switches)* | `Switch(config-vlan)#`   | Configure VLANs                                             | `vlan <vlan-id>`                    |

There are three most common ways to access the Cisco IOS:
1. Console
2. Telnet
3. SSH

# Practicals
## Password Implementation
```
show running-config (Displays the current active configuration stored in the router's RAM)
```
**Set line Console Password**
```
(config)#line console 0 (Enters console line configuration mode to configure the physical console port)
password abc (Sets the console login password to abc)
login (Enables password authentication on the console line. Without this command, the configured password is ignored)
exit
wr (Saves the running configuration to the startup configuration)
```
**Set Aux Console Passord**
```
(config)#line aux 0 (Enters AUX (auxiliary) line configuration mode)
password abc
login
exit
wr
```
**Set Enable Password (Useless)**
```
enable password abc (Sets the enable password to abc for accessing Privileged EXEC mode. It is Stored in plain text (or weakly encrypted if password encryption is enabled), so it is less secure.)
```
**Set Enable Secret Password**
```
enable secret password (Sets the enable secret password to password for accessing Privileged EXEC mode. It is Stored as a hashed (encrypted) password and is more secure than enable password. You can configure only enable secret without configuring enable password)
```
**Encrypt all Passwords**
```
(config)#service password-encryption (Encrypts all plain-text passwords in the running configuration using Cisco's Type 7 encryption.)
```
**Password Policy Configuration**
```
(config)#show login   (Displays the router's login security settings, such as delays, blocking status, and failed login statistics)
security passwords min-length 8   (Requires all newly created passwords to be at least 8 characters long)
security passwords lifetime 30   (Sets passwords to expire after 30 days (supported on some IOS versions/features))
security passwords history 5   (Prevents users from reusing any of their last 5 passwords (supported on some IOS versions/features))
login delay 5   (Waits 5 seconds after a failed login attempt before allowing another attempt)
login on-failure log   (Logs every failed login attempt in the system log)
login on-success log   (Logs every successful login attempt in the system log)
security authentication failure rate 3 log   (Logs an event if there are 3 authentication failures within the configured monitoring period (platform/IOS support varies))
login block-for 120 attempts 3 within 30   (Blocks all login attempts for 120 seconds if there are 3 failed attempts within 30 seconds)
```
**Bypassing Password(Startup Configuration)**
While Booting
press Ctrl+c (To enter in rommon mode)
```
rommon> confreg 0x2142 (To configure a Cisco router to bypass the startup configuration during its next boot)
rommon> reset (To reboots the Cisco device directly from the ROM Monitor (ROMMON) mode.)
copy startup-config running-config
enable password abc
wr
conf t
(config)#config-register 0x2102 (To boot securely which was not possible after doing confreg 0x2142, and prevent no authentication from next time onwards)
```

# 
Connect a router and Linux machine in GNS3
```
(config)#enable password <password>
(config)#line vty 0 4 (opens configuration mode for Virtual Teletype lines 0 through 4, allowing up to 5 simultaneous remote connections (via SSH or Telnet) to manage the device.)
(config-line)#password abc@123
(config-line)#login
(config-line)#exit
(config)#username <name> password <pass>
(config)#line vty 0 4
(config-line)#login local 
exit
exit
wr
(config)#interface fastEthernet 0/0
(config)#ip address 192.168.10.10 255.255.255.0
```

Kali Linux:
Edit connections>Wired Connections,IPv4>Add 192.168.10.11, 255.255.255.0, save
```
ping 192.168.10.10 (To check)
telnet 192.168.10.10
Username <name>
```
