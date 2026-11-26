# Passive Interface
Disable routing updates.

# RSPAN (Remote Switched Port Analyzer) 
A Cisco networking technology that allows to monitor network traffic from remote switches. It copies traffic from a source switch and sends it to a monitoring device through an RSPAN VLAN.
**Source Switch> Traffic Copying> RSPAN VLAN> Destination Switch> Monitoring Device**

# NAT Limitations
- NAT hides private IP addresses behind a public IP address.
- It makes direct communication between two devices difficult.
- Incoming connections may be blocked by NAT.
- **P2P applications require additional techniques such as UDP hole punching and NAT traversal**.
- It can increase connection complexity and cause communication problems.

# Anycast Routing in IPv6
An **IPv6 communication method** where same IP address is assigned to multiple devices located in different geographical locations. Routers deliver packets to the nearest available device according to routing metrics.

# Dual Stack in IPv6
A network transition technique which allows a device use IPv4 and IPv6 simultaneously.

# Token Ring Technology
A LAN technology in which computers are connected in a logical ring topology. It uses a special frame called token to control data transmission. Only the device holding the token can transmit data.

# EtherChannel
A networking technology that combines multiple physical Ethernet links into one logical connection.

# DHCP Snooping
**monitor and filter DHCP messages to prevent rogue DHCP servers**. It's an L2 security feature used in networking switches to protect against unauthorized DHCP servers. It divides switch ports into two categories: trusted and untrusted. DHCP server messages received on untrusted ports are blocked.
It maintains a DHCP snooping binding table containing IP address, MAC address, VLAN and switch port information.

# STP 
A L2 network protocol to prevent switching loops
Working:
1. Switches exchange special messages called BPDUs.
2. They elect one switch as the Root Bridge based on the lowest Bridge ID.
3. Each non-root switch selects its best path towards the Root Bridge.
4. STP blocks redundant paths to prevent switching loops.
5. If an active link fails, STP can activate an alternative path.

# BPDU Guard 
A Security feature used with STP to protect a network against unauthorized switches and switching loops.

# Secure Neighbor Discovery (SEND) in IPv6
security extension of IPv6 Neighbor Discovery Protocol(NDP). It protects communication between neighboring IPv6 devices from spoofing and other attacks.
functions:
1. Cryptographic Authentication
2. Digital Signatures
3. Replay Protection
4. Spoofing Prevention
5. Secure Communication

# IPv6 Security Policy Components
- IPsec: Provides data encryption, authentication and integrity to secure communication.
- Firewall: Monitors and filters incoming and outgoing network traffic.
- Access Control Lists (ACLs): Allow or deny network traffic based on predefined rules.
- Authentication: Verifies the identity of users and devices before allowing access.
- Secure Neighbor Discovery (SEND): Protects IPv6 Neighbor Discovery from spoofing attacks.

# SLAAC (Stateless Address Autoconfiguration) 
An IPv6 feature that allows devices to automatically configure their own IPv6 addresses without requiring a DHCPv6 server for address assignment.
Working:
1. A device connects to an IPv6 network.
2. It sends a Router Solicitation (RS) message to discover available routers.
3. The router responds with a Router Advertisement (RA) message containing network prefix information.
4. The device combines the network prefix with an interface identifier to generate its IPv6 address.
5. The device performs Duplicate Address Detection (DAD) to check whether the address is already in use.

# Network Prefix (/24): 
Represents the **fixed portion of an IP address**. For example, in 192.168.1.0/24, the first 24 bits are the network address, and the remaining 8 bits are available for host devices (IPs from 192.168.1.1 to 192.168.1.254).

# Prefix List (Router Tool): 
A firewall-like or routing filter rule set used by network administrators. It tells a router: "Allow or deny traffic/routing updates coming from these specific network prefixes.

# Distribute list 
An **access control tool used in routing protocols** (like OSPF, EIGRP, or BGP) **to filter routing updates**. It functions like a firewall rule for routes, it prevents a router from advertising certain prefixes to its neighbors, or from accepting certain prefixes into its routing table.

# Route map 
A tool used in enterprise networking (commonly on Cisco platforms) to filter and manipulate traffic or routing information. **Think of it as a smart, programmable script (similar to an if/then/else statement) that combines Access Control Lists (ACLs) and actions.**

# Dynamic ARP Inspection (DAI) 
A Layer 2 security feature that prevents ARP spoofing (ARP poisoning) by intercepting, logging, and validating all ARP packets on a network.



---
# Network Security:

## Accessing
**Fixed-time password-based authentication**:
controls access to network devices using passwords with specific time restrictions. features Password Expiry, Login Timeout, Account Lockout.


---
# Configuration
**Backup and restore process of an IOS:**
Backup:
```
show flash: (Check the IOS image)
# copy flash: tftp: (Copy the IOS image from flash memory to a TFTP server)
```
Restore:
```
# copy tftp: flash: (Copy the IOS image from the TFTP server to flash memory)
```
Configure the boot system command and save the configuration.


**Router privilege levels:**
Cisco IOS provides 16 privilege levels (0–15).
1. Level 0: Provides minimum access to basic commands.
2. Level 1: Provides normal user EXEC mode for basic monitoring.
3. Level 15: Provides full administrative access to configure and manage the router.
Levels 2–14 can be customized according to user roles.

**Telnet Configuration:**
```
Router(config)# line vty 0 4 (Configure the VTY lines)
Router(config-line)# password cisco123 (Set password)
Router(config-line)# login (Enable login authentication)
Router(config-line)# transport input telnet (Allow Telnet access)
```

## Common Cisco router password recovery techniques include:

- ROMMON Mode: Interrupt the router's boot process using a console connection.
  - Connect a PC to the router's console port using a rollover console cable and a terminal emulator (such as PuTTY etc.
  - Power cycle or reload the router and send a Break sequence (for example, Ctrl+Break on Windows terminals or Ctrl+] followed by send break in Telnet)
  - Enter ROMMON
  - 
- Configuration Register: Change the configuration register to 0x2142 so the router ignores the saved startup configuration.
- Reset Password: Load the original configuration into RAM, configure a new password, restore the register to 0x2102 and save the configuration.

## Commands
show cdp neighbors (To display CDP information on a cisco router)
cdp run (Enables CDP)
no cdp enable (disable CDP on a specific interface)

ntp server x.x.x.x (Enable NTP on a router)

passive-interface <Interface_name> (command to prevent RIP update from being sent out on a specific interface)

privilege exec level (set a router's privilege level)
privilege level X (change the privilege level of a Cisco router user)

copy tftp running-config (command to restore configuration from a TFTP server)
copy flash tftp (backup IOS to TFTP)

service password-encryption (To encrypt all passwords in the running configuration)
enable secret (setting an encrypted privileged EXEC mode password)

copy running-config startup-config (Saves config permanently)




