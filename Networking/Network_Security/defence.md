# Core Operational Pillars of Infrastructure Hardening
## Management Plane Security:
The part of a system responsible for **controlling, configuring, monitoring, and administering the infrastructure**.
- Use Secure Protocols: like SSH
- Privilege Level Separation: Apply Least Privilege principle
## Control Plane Security
The part of an infrastructure system that **makes decisions about how the system should operate**. 
- Protocol Authentication: prevent unintended participant know and modify the underlying infrastructure.
- Topology Safeguards: 
## Data Plane Security
The part of an infrastructure system that actually **handles and processes the workload or traffic**.
- Traffic Filtering: ACLs
- Edge Protections: Port Security


# Structure of Secure Enterprise Network:
network infrastructure is never flat. It is logically and physically partitioned into distinct security zones using Virtual Local Area Networks (VLANs) and firewalls to mitigate lateral threat movement. 
- **Perimeter Firewall**:  The initial line of defense that enforces explicit inbound traffic constraints using **stateful packet inspection and Application-Layer inspection**. 
- **The DMZ (Demilitarized Zone)**: A dedicated, **semi-isolated network segment hosting external facing corporate resources (e.g., public web servers, DNS servers, mail relays)**. If a server inside the 
DMZ is compromised, the primary internal firewall prevents the attacker from shifting laterally into the internal core. 
- **The Trusted Zone (Internal Corporate LAN)**: The highly restricted segment housing corporate **workstations, internal database arrays, active directory infrastructure, and core network management endpoints**. 

# Fixed-Time Password Based Authentication:
It refers to a security control where **access to a network device’s management plane (Console, VTY lines, or Aux port) is restricted using a static password** that is governed by explicit temporal and administrative constraints.  

**Advantages:**
- **Administrative Validity Lifespan**: A operational policy requiring **passwords to expire and be forcefully rotated after a fixed window of time** (e.g., 30, 60, or 90 days).
- **Login Session Timeouts (Exec-Timeout)**: Automatically **terminating an authenticated administrative session if no input is detected within a designated, fixed duration of time**. This prevents an open terminal from being hijacked if an administrator walks away from their desk.
- **Brute-Force Lockout Windows**: Temporarily disabling authentication attempts for a fixed period if a user enters an incorrect password multiple times within a short timeframe. 

**Disadvantages:**
- **Clear-Text Exposure by default**
- Lack of Accountability (If multiple junior engineers share a single, fixed local password to access a router's privilege mode, it becomes **impossible to determine who executed a specific command during an incident**.)
- **Credential Stuffing & Brute-Forcing**

**Common Cisco IOS Hashing Types**:
- Type 0 (Plain Text)
- Type 7 (Vigenère Cipher)
- Type 5 (MD5)
- Type 8 (SHA-256) & Type 9 (scrypt)

## Enabling Basic Password Obfuscation (Type 7) 
This obscures any existing clear-text line passwords in the configuration file. 
```
Router# configure terminal 
Router(config)# service password-encryption
```

## Configuring Strong Enable Passwords (Type 5/8/9) 
Always use enable secret rather than enable password, as the latter uses insecure Type 0 or Type 7 formatting. 
```
Router(config)# enable secret P@ssw0rd123!
```

## Implementing Fixed-Time Login Constraints (Brute-Force Block) 
To defend against automated dictionary attacks, we can configure the device to block authentication attempts for a fixed period if an engineer fails to log in successfully.
```
Router(config)# login block-for 180 attempts 3 within 60 (Block all login attempts for 180 seconds if 3 failed attempts are registered within a 60
second window.)
```

## Configuring Administrative Session Timeouts (Exec-Timeout) 
To prevent left-behind management sessions from remaining open indefinitely, apply a fixed-time execution limit on Console and VTY (remote access) lines. 

```
Router(config)# line console 0 
Router(config-line)# exec-timeout 5 0 (exec-timeout 5 0 means the session will automatically terminate after 5 minutes and 0 seconds of absolute inactivity)
Router(config-line)# exit 
Router(config)# line vty 0 4 
Router(config-line)# exec-timeout 10 0 
Router(config-line)# exit
```

# Password Policy:
A set of administrative and technical rules designed to ensure that access credentials used to manage corporate routers, switches, and firewalls are highly resilient against compromise.

```
Router(config)# security passwords min-length 10  (Configure password's minimum length 
Router(config)# username NetAdmin secret strong_P@ssw0rd!9 (Preventing Shared Access with Local Named Accounts) 
Router(config)# login block-for 120 attempts 4 within 60 (stop login interface  120 seconds if 4 incorrect entries occur 
within a 60-second window.
Router(config)# show running-config | include passwords (Verifies if the global minimum length restriction is currently active on the device)
Router(config)#show login (To Displays whether any brute-force tracking windows or administrative lockout parameters are in effect)
Router(config)#show running-config | include username (Enables checking of local user parameters. Ensure that the strings displayed following the username show safe hash identifier digits (like $5$, $8$, or $9$) rather than plain text)
```

# Password Recovery Techniques:
**Cisco Configuration Register** a 16-bit NVRAM value that dictates how a router behaves when it boots up. 
- **0x2102 (Default Factory Setting)**: Tells the router to boot normally. It **loads the Cisco IOS software from Flash memory and applies the saved configuration file (startup-config) from NVRAM into RAM.**
- **0x2142 (Password Recovery Setting)**: Tells the router to **ignore the startup-config** in NVRAM during bootup. The **router boots into a clean, default state** as if it has no passwords configured, while leaving your original configuration file untouched in NVRAM. 

# Router Privilege Levels and Their Configuration:
**Privilege levels control what commands a user can execute**. They are part of Cisco IOS’s basic access-control mechanism. **Level 2-14 can be customized to create role-based access control, while level 15 provides full administrative access**.

## 1.Configure passwords for privilege levels:
```
Router(config)# enable secret level 5 <password>
Router(config)# enable secret level 10 <password>
```
now 'Router> enable 5' and 'Router> enable 10' will ask for different passwords for different privileges 

## 2.Assign required commands to a lower privilege level
```
Router(config)# privilege exec level 5 configure terminal (Allows privilege level 5 users to enter global configuration mode using configure terminal)
Router(config)# privilege configure level 5 interface (Allows level 5 users to use the interface command from global configuration mode)
Router(config)# privilege interface level 5 shutdown (Allows level 5 users to use the shutdown command inside interface configuration mode)
Router(config)# privilege exec level 5 show running-config (Allows level 5 users to run show running-config from EXEC mode)
```

## 3.Create users and assign them a privilege level
```
Router(config)# username <user_name> privilege 5 secret <Password>
Router(config)# username <user_name> privilege 15 secret <password> (Creates a local user with privilege level 15, giving that user full administrative privileges)
```
After this when you login 'Router(config)# line console 0, Router(config-line)# login local' you will be prompted for username and password.
The privilege level of those users will be predefined

## Verification and Troubleshooting Commands
```
Router(config)# show privilege (Displays the exact numeric privilege level (0–15) of the current terminal session)
Router(config)# show running-config | include privilege (Lists all custom command-shifting maps and role definitions configured globally on the device) 
Router(config)# disconnect or logout (Allows students to exit their session to test the credential mappings of different administrative profiles)
```

# NTP (Network Time Protocol):
A networking protocol operating over **UDP port 123 at the Application Layer (Layer 7)** of the OSI model. Its primary objective is to **synchronize the internal clocks of network devices (routers, switches, firewalls, and servers)** to a precise, common time reference. 

**Stratum number indicates how many routing hops a device is away from an authoritative, atomic hardware clock.**  Most enterprise networks sync their edge routers with public Stratum 2 servers

```
Router# show clock 
Router# show calendar (check the hardware and software clock status of the device)
Router# clock set 12:00:00 16 June 2026 (manually configuring a rough baseline can help speed up initial NTP acquisition)
Router# configure terminal 
Router(config)# ntp server 192.168.10.100 (Point your infrastructure device to a secure, known Stratum 2 network address)
Router(config)# access-list 10 permit 192.168.10.100 
Router(config)# ntp access-group peer 10 ( the device will only accept time synchronization updates and peering packets from IP)
Router(config)# show ntp status (whether the clock is synchronized or unsynchronized)
Router(config)# show ntp associations ( list of all upstream NTP servers configured on the device, including metrics such as delay, offset, and jitter. An asterisk (*) next to a server indicates that the router has chosen that specific server as its primary master time source.)
```

# Access Control List:
**set of filter rules placed on routers, switches, or firewalls to permit or deny data packets.**

## Standard ACL (Close to destination)
**Filter traffic using only the source IP address, They block or allow an entire protocol suite, Numbered 1–99** and 1300–1999.
```
#access-list 10 deny host <src_IP>
access-list 10 permit any
int 
ip access_group 10 out
```

## Extended ACL (Close to Source)
**Filter traffic using source and destination IPs, specific protocols (TCP/UDP), and port numbers. They offer precise traffic control. (Numbered 100–199** and 2000–2699).
```
#access-list 100 deny icmp host <src_IP> host <dst_IP>
access-list 101 permit ip any any
int <Interface_name>
ip access-group 101 in
```

## Name Based ACL
**Use alphanumeric names** instead of numbers for easier identification and management.
```
#ip access-list extended <Name>
deny tcp host <src_IP> host <dst_IP> eq 80
permit tp any any
int <Interface_name>
ip access-group <Name> out
```


# AAA Authentication
**Authentication, Authorization and Accounting. A framework to control and monitor access to network devices.**

1. Authentication "Who are you": Verifies the identity of a user using credentials.
2. Authorization "What you can do": Determines the commands privileges and resources that an authenticated user is allowed to access.
3. Accounting "What did you do": It records and tracks user's activities.

