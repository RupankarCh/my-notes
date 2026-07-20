# Terms:
- Attack Surface: The total sum of all possible entry points, paths, and vulnerabilities that a hacker can use to access a system or steal data.

# Steps of Scanning:
Host Discovery> Port Scan> Service and Version Scaning> OS Scan> Script Scan

# Tools
## Nmap:
**Nmap (Network Mapper)** is a network scanning tool used to discover hosts, identify open ports, detect running services, and gather information about devices on a network.By default nmap scans top 1000 ports.

-sn <Network Address> (Host Discovery)
-Pn <Network Address> (Port Discovery for ip address in the network, skips the ping assuming host is alive)
-Pn <IP Address> (Port Discovery for a single ip address)
-sV <IP Address> (Service Version Scan)
-O <IP Address> (OS Scan)
