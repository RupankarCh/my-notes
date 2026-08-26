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
# How nmap works by default
If you didn't specify -sT or -sS, Nmap normally uses a TCP SYN scan (-sS) when run with sufficient privileges.

Conceptually, it does this for each TCP port:
```
Nmap                         Metasploitable 2
 │                                  │
 │──── TCP SYN → port 21 ──────────>│
 │<─── SYN/ACK ─────────────────────│
 │                                  │
 │──── TCP SYN → port 22 ──────────>│
 │<─── SYN/ACK ─────────────────────│
 │                                  │
 │──── TCP SYN → port 23 ──────────>│
 │<─── SYN/ACK ─────────────────────│
```
