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
It's an L2 security feature used in networking switches to protect against unauthorized DHCP servers. It divides switch ports into two categories: trusted and untrusted. DHCP server messages received on untrusted ports are blocked.
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


