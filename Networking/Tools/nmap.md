# Steps of Scanning:
Host Discovery> Port Scan> Service and Version Scaning> OS Scan> Script Scan

Nmap:
Nmap (Network Mapper) is a network scanning tool used to discover hosts, identify open ports, detect running services, and gather information about devices on a network.By default nmap scans top 1000 ports.

-sn (Host Discovery) -Pn (Port Discovery for ip address in the network, skips the ping assuming host is alive) -sV (Service Version Scan) -O (OS Scan)
