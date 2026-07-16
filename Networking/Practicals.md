# 1.Password Chaning
- Set line Console Password
- Set Aux Console Passord
- Set Enable Password
- Set Enable Secret Password
```
line console 0
password abc
login
exit
line aux 0
password abc
login
exit
enable password abc
enable secret password
```
While Booting
press Ctrl+c (To enter in rommon mode)
```
rommon> confreg 0x2142 (To configures a Cisco router to bypass the startup configuration during its next boot)
rommon> reset (To reboots the Cisco device directly from the ROM Monitor (ROMMON) mode.)
copy startup-config running-config
enable password abc
wr
conf t
config-register 0x2102 (To boot securely which was not possible after doing confreg 0x2142, and prevent no authentication from next time onwards)
```
# 2.
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
