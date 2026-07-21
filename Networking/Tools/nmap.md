# Steps of Scanning:
Host Discovery> Port Scan> Service and Version Scaning> OS Scan> Script Scan

Nmap:
Nmap (Network Mapper) is a network scanning tool used to discover hosts, identify open ports, detect running services, and gather information about devices on a network.By default nmap scans top 1000 ports. /usr/share/nmap/scripts is the location to find nmap scripts. It is stored with .nse extension.


-sn (Host Discovery) -Pn (Port Discovery for ip address in the network, skips the ping assuming host is alive) -sV (Service Version Scan) -O (OS Scan)

-sF (FIN Scan) only the FIN flag
-sN (Null Scan) zero flag set
-sX (Xmas Scan) 3 flags FIN, PSH, URG

Nmap Script Scan
```
nmap --script=ftp-anon.nse <Target_IP>
```
