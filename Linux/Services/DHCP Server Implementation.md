Prerequisites:
- Configure manual IP address <192.186.25.1>
- Yum repository configuration
DHCP Configuration
```
#yum install dhcp-server.x86_64 -y
#cd /etc/dhcp
#ls (To see if dhcp.conf is present)
#vim /etc/dhcp/dhcpd.conf (copy the path)
#cp -v <path> /etc/dhcp/dhcpd.conf
#vim dhcpd.conf
authoritative;
log-facility local6;

subnet 192.168.25.0 netmask 255.255.255.0 {
    range 192.168.25.10 192.168.25.20;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.25.255;
    # option routers 192.168.25.1;
    # option domain-name-servers 192.168.25.1;
}
#vim /etc/rsyslog.conf
local6.* /var/log/dhcpd.log
#systemctl restart dhcpd.log
#dhcpd -t -cf /etc/dhcp/dhcpd.conf (To validate the configuration)
#systemctl enable --now dhcpd
#systemctl status dhcp-server
#tail -f /var/log/dhcpd.log (To check DHCP logs)
#firewall -cmd --add-service=dhcp --permanent
#firewall-cmd --reload
```
Client Joining:
At first choose same network for each client machine as DHCP server.

RHEL Client:
#nmcli con mod ens160 ipv4.method auto
Restart the machine or interface

Windows 7 Client:
Go to run (Win+R) ncpa.cpl, Disable and Enable it.

dhcpd.conf Configuration Description:
| Configuration                        | Purpose                                                       |
| ------------------------------------ | ------------------------------------------------------------- |
| `authoritative;`                     | Declares this server authoritative for its configured subnet. |
| `log-facility local6;`               | Sends DHCP logs to the `local6` syslog facility.              |
| `subnet 192.168.25.0`                | Defines the network served by DHCP.                           |
| `netmask 255.255.255.0`              | Defines the subnet mask.                                      |
| `range 192.168.25.10 192.168.25.20;` | Specifies the IP addresses available for clients.             |
| `option subnet-mask`                 | Provides the subnet mask to clients.                          |
| `option broadcast-address`           | Provides the broadcast address to clients.                    |
| `option routers`                     | Provides the default gateway to clients when configured.      |
| `option domain-name-servers`         | Provides the DNS server address to clients when configured.   |
