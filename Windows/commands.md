# Networking
| Command                                            | What it does (one-liner)                                                                            |
| -------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `ipconfig`                                         | Displays the basic IP configuration of network adapters.                                            |
| `ipconfig /all`                                    | Displays detailed network information, including IP address, MAC address, DNS, DHCP and gateway.    |
| `ncpa.cpl`                                         | Opens Network Connections to view and manage network adapters.                                      |
| `devmgmt.msc`                                      | Opens Device Manager to view and manage hardware devices and network drivers.                       |
| `getmac`                                           | Displays the MAC addresses of network adapters.                                                     |
| `getmac /v /fo list`                               | Displays detailed MAC address information in list format.                                           |
| `netsh wlan show interfaces`                       | Displays Wi-Fi interface details, including SSID, signal strength, connection state and radio type. |
| `wmic NIC where "NetEnabled=True" get Name, Speed` | Displays the names and link speeds of enabled network adapters.                                     |
