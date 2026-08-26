HTTP Tunnelling Using Chisel (Kali → Windows)
Lab Environment: Kali Linux → Windows
Chisel Version: v1.11.8 (AMD64)
Purpose: Create a reverse tunnel from Windows to Kali and access Windows RDP through the tunnel.
1. Kali Linux – Install Chisel
Method 1: Clone and Build
git clone https://github.com/jpillora/chisel.git
cd chisel
sudo apt install golang-go -y
go build
Method 2: Download Chisel
Download the appropriate Chisel v1.11.8 AMD64 ZIP/release file, extract it, and keep the chisel executable in Kali.
Verify:
./chisel version

2. Windows – Install Chisel
Download Chisel v1.11.8 AMD64 for Windows.
Extract the ZIP file and keep:
chisel.exe
For example:
C:\Tools\chisel.exe

3. Kali – Start Chisel Server
Start the Chisel server:
./chisel server --port 8080 --reverse
Keep this terminal running.

4. Windows – Create Reverse Tunnel
Open PowerShell and go to the folder containing chisel.exe:
cd C:\Tools
Then run:
.\chisel.exe client 192.168.1.10:8080 R:3389:127.0.0.1:3389
Replace 192.168.1.10 with the actual IP address of the Kali machine.
This creates a reverse tunnel from Kali’s local port 3389 to the Windows RDP service on port 3389.

5. Kali – Check the Tunnel
Open another Kali terminal and run:
ss -ltnp | grep 3389
If port 3389 is listening, the reverse tunnel has been created successfully.

6. Windows – Check RDP Status
Check whether Windows Remote Desktop is enabled:
Get-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Terminal Server" -Name fDenyTSConnections
Result:
0 = RDP Enabled
1 = RDP Disabled

7. Windows – Enable RDP if Disabled
If the result is 1, open PowerShell as Administrator and run:
Set-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Terminal Server" -Name fDenyTSConnections -Value 0
Then verify again:
Get-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Terminal Server" -Name fDenyTSConnections
It should show:
0

8. Kali – Install Remmina
If Remmina is not already installed, install it using the available package/source method.
After installation, verify:
Remmina
“sudo apt install remmina remmina-plugin-rdp remmina-plugin-vnc remmina-
plugin-secret”
If Remmina opens successfully, continue to the next step.
Remmina is used as the RDP client. It is not responsible for creating the Chisel tunnel. The Chisel tunnel must already be active.

9. Kali – Open Remmina
Open Remmina:
remmina
Click the + (New Connection Profile) icon.
Set:
Protocol : RDP
Server   : 127.0.0.1:3389
Username : Windows Username
Password : Windows Password
Then click Connect.

10. Expected Flow
             Reverse Chisel Tunnel
Windows ──────────────────────────────> Kali
   │                                      │
   │ RDP :3389                            │ :8080
   │                                      │
   └────────────── Chisel Client ─────────┘
                                          │
                                          ▼
                                   127.0.0.1:3389
                                          │
                                          ▼
                                      Remmina
                                          │
                                          ▼
                                    Windows RDP
Important Verification
Before connecting with Remmina, verify:
Windows:
Test-NetConnection localhost -Port 3389
Expected:
TcpTestSucceeded : True
Kali:
ss -ltnp | grep 3389
Port 3389 should be listening.
This verification flow is consistent with the troubleshooting steps in the original lab document.
