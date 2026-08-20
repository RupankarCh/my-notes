# Types of Password
- Console Password: Connectiing with port
- AUX Password: Connecting with port
- Enable Password: Priviledge Escalation
- Enable Secret Password: Encrypted Priviledge Escalation
- Line VTY Password: Connecting remotely

**VTY: A VTY (Virtual Teletype) line is a virtual login port that allows users to remotely access the router using Telnet or SSH over the network.**


# Navigation in IOS
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

# 4 Ways to access the Cisco IOS:
| Access method | IOS line         | Typical use                     |
| ------------- | ---------------- | ------------------------------- |
| **Console**   | `line console 0` | Local physical access           |
| **AUX**       | `line aux 0`     | Modem/out-of-band remote access |
| **Telnet**    | `line vty 0 4`   | Remote network access           |
| **SSH**       | `line vty 0 4`   | Secure remote network access    |

| Console                                | AUX                                                        |
| -------------------------------------- | ---------------------------------------------------------- |
| Mainly for local management            | Mainly for remote management                               |
| Direct connection to the device        | Can be connected through a modem                           |
| Commonly used during initial setup     | Useful for out-of-band remote access                       |
| Usually does not require an IP address | Also works independently of the device's normal IP network |

---

## i. Console Access
Means connecting your computer **directly to the Cisco device's console port**. You don't need an IP address, Telnet, or SSH for the initial connection.

Practical setup

```
PC
 │
 │ Console cable
 ▼
Cisco Router/Switch
```

In **Cisco Packet Tracer**:

1. Add a PC and router/switch.
2. Choose the **Console cable**.
3. Connect:

   * **PC → `RS232` Modern laptops do not come with built-in RS232 (DB9) serial ports use USB-to-RS232 Adapter**
   * Router/Switch → `Console`
4. Click the PC.
5. Go to **Desktop → Terminal**.
6. Accept the default settings and press Enter.
---
## ii. SSH Access

SSH encrypts the communication.

For practical setup the router needs:

* Hostname
* Domain name
* Username/password
* RSA keys
* VTY configuration
* SSH transport
---

Step 1: Configure an IP address '192.168.1.1/24'

Step 2: Set a hostname 'R1' **SSH requires a hostname/domain setup for RSA key generation**.

Step 3: Configure a domain name

```
R1(config)# ip domain-name lab.local
```

Step 4: Create a local username, **`secret` means IOS stores the password in a hashed/secured form** rather than as plain text.

```
R1(config)# username admin privilege 15 secret rup
```

Step 5: Generate RSA keys, On modern real devices, use a stronger key size appropriate to the platform and security policy.

```
R1(config)# crypto key generate rsa
How many bits in the modulus [512]: 1024
```

Step 6: Configure the VTY lines for SSH, **login local tells the router to Use the locally configured username/password.** **transport input ssh Allows SSH connections on the VTY lines.**


```
R1(config)# line vty 0 4
R1(config-line)# login local
R1(config-line)# transport input ssh
R1(config-line)# exit
```

Step 7: Connect using SSH From the PC and provide the local user's password:

```
ssh -l admin 192.168.1.1
```
## iii. AUX Access
The AUX port is mainly used for remote management, commonly through a modem or another serial connection. Unlike console access, **AUX access is designed for remote out-of-band management(Accessing devices via a completely separate physical connection that does not depend on the router's IP interfaces or WAN links)**

Step 1: Add a PC and a Cisco router.
Step 2: Choose the appropriate cable/connection for the AUX interface.
Connect:
PC → RS232
Router → AUX
Click the PC.
Go to Desktop → Terminal.
Accept the default terminal settings and press Enter.


## iv. Telnet Access

Telnet is different because you're accessing the Cisco device **over the network**. Telnet is **not encrypted**.For learning, labs, and understanding IOS, it's useful. In real networks, **SSH should normally be used instead**.


For example:

```text
PC ───────────── Network ───────────── Router
192.168.1.10                         192.168.1.1
```

The PC connects to the router's IP address using Telnet.

---

Step 1: Give the router an IP address 192.168.1.1/24

Step 2: Configure a PC

```text
IP address:      192.168.1.10/24
Default gateway: 192.168.1.1
```
Test connectivity from the PC using ping.

Step 3: Configure Telnet on the router and Set a password:

```text
Router(config)# line vty 0 4
Router(config-line)# password cisco
Router(config-line)# login
```

Step 4: Telnet from the PC
```text
telnet 192.168.1.1
```
---

# Password Implementation
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
Now when someone connects through the console, they'll be prompted for:
```
Password:
```

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

# Connect a router and Linux machine in GNS3
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


# Configure a console password

Go to Privileged EXEC:

```text
Router> enable
Router#
```

Enter Global Configuration:

```text
Router# configure terminal
Router(config)#
```

Enter the console line:

```text
Router(config)# line console 0
Router(config-line)#
```

Set a password:

```text
Router(config-line)# password cisco
```

Tell IOS to require that password:

```text
Router(config-line)# login
```

Exit:

```text
Router(config-line)# exit
Router(config)# exit
```

Now when someone connects through the console, they'll be prompted for:

```text
Password:
```

Complete configuration

```text
Router> enable
Router# configure terminal
Router(config)# line console 0
Router(config-line)# password cisco
Router(config-line)# login
Router(config-line)# end
Router#
```

---
**Set Aux Console Passord**
```
(config)#line aux 0 (Enters AUX (auxiliary) line configuration mode)
password abc
login
exit
wr
```

---
