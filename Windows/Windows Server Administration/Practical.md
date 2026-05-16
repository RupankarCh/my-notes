# Windows Server Installation
1. Download the Windows Server ISO from Microsoft website
2. Create a bootable USB using tools like Rufus
3. Insert USB and restart your system
4. Enter BIOS/UEFI and set USB as first boot device
5. Boot from the USB drive
6. Select language, time, and keyboard → click Next
7. Click Install Now
8. Enter product key (or skip if needed)
9. Select Windows Server edition (Standard/Datacenter)
10. Choose installation type → Custom (Advanced)
11. Select disk/partition → click Next
12. Wait while Windows copies and installs files
13. System will restart automatically
14. Set Administrator password after installation
15. Log in and complete initial configuration (Server Manager)

# Installation of DNS Server
1. Set Static IP (DNS servers should never change IP)
2. Set Preferred DNS → 127.0.0.1 (or its own IP basically same, After installation, the DNS service runs locally)
3. Open Server Manager
4. Click Add Roles and Features
5. Select Role-based or feature-based installation
6. Choose your server from the server pool
7. In Roles list, select DNS Server
8. Click Add Features when prompted
9. Click Next through features section
10. Click Install
11. Wait for installation to complete
12. Click Close

# Configuration of DNS Server
13. Open DNS Manager from Server Manager
14. Right-click server → select New Zone
15. Choose Primary Zone
16. Enter domain name (e.g., example.com)
17. Allow dynamic updates (optional)
18. Finish the wizard
19. Add A record (name → IP mapping)
20. Test using nslookup

# Configure Forwarders
1. Open DNS Manager
2. Right-click server → Properties
3. Go to Forwarders tab
4. Add public DNS like:
- 8.8.8.8 (Google)
- 1.1.1.1 (Cloudflare)
5. Apply settings
