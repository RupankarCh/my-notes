# 1. **IP Address Configuration, Hostname Change:**
<img width="612" height="248" alt="WhatsApp Image 2026-06-11 at 8 27 41 AM" src="https://github.com/user-attachments/assets/dd6ea055-e689-4665-bc29-c4db9c685fe7" />

```
#nmtui (To configure IP address)
```
Edit a connection> Select the interface> IPv4 Address Show> Enter the Content and OK> Back> Activate a connection> deactive and activate and Back> Quit
If connection is not getting active
```
#nmcli connection up
#ifconfig (To check)
#hostnamectl set-hostname newhostname (To change hostname)
```
# 2.**Configure an YUM repository**

<img width="736" height="283" alt="WhatsApp Image 2026-06-11 at 8 28 09 AM" src="https://github.com/user-attachments/assets/1bf3685b-22e5-4035-a827-a8138643501c" />

```
#df -Th (To check if /dev/s0 exists on your system means the hardware device (the virtual CD/DVD drive) exists and has a disc inserted/attached inside it, If you see sr0 then start from Part 2, otherwise only disks like sda, vda, nvme0n1, etc., then there is no attached ISO so proceed)
```
Depending on your environment:

VMware Workstation
Power off the VM (or edit settings while powered on if supported).
Go to VM → Settings → CD/DVD.
Select Use ISO image file.
Browse to your RHEL 10 ISO.
Check Connected and Connect at power on.
Start the VM.

VirtualBox
Open Settings → Storage.
Select the empty optical drive.
Choose the RHEL 10 ISO.
Start the VM.
After attaching the ISO

Part 2:
```
lsblk
```
You should see something like:
sr0    11:0    1 10G 0 rom
If not then proceed If yes then start from Part 3

Then mount it:
```
mkdir -p /mnt/cdrom
mount /dev/sr0 /mnt/cdrom
```
Verify:
```
ls /mnt/cdrom
```
You should see directories such as:
AppStream
BaseOS
media.repo

Part 3: Configure Local YUM Repository
Check the mount point
```
ls /run/media/rupankar/RHEL-10-2-BaseOS-x86_64
```
You should see: AppStream, BaseOS, EFI, images, media.repo
#mkdir /root/foldername (To keep the main "RHEL installation DVD/ISO" untouched, it contains **operating system installation files, boot loaders, and the entire catalog of software packages**.) 

#cp -rvf /run/media/rupankar/RHEL-10-2-BaseOS-x86_64 /root/foldername 

Create a repository file:
```
#vim /etc/yum.repos.d/filename.repo
```
Add:
```
[BaseOS]
name=This is RHEL 10 BaseOS
baseurl=file:///root/foldername/RHEL-10-2-BaseOS-x86_64/BaseOS 
gpgcheck=0
enabled=1

[AppStream]
name=This RHEL 10 AppStream
baseurl=file:///root/foldername/RHEL-10-2-BaseOS-x86_64/AppStream
gpgcheck=0
enabled=1
```
Save and exit. Esc :wq if you get any error while creating the file E212/E303
rum with root previledge
rm -f /etc/yum.repos.d/.filename.repo.sw* (To cleanup)

```
#yum clean all (To Clean existing metadata)
#yum repolist (The command scans all the configuration files inside /etc/yum.repos.d/)
```
Test package installation
For example:
```
sudo dnf install httpd*
```

# 3.Create users and groups as per the following requirements
```
#groupadd sysadmin
#useradd -G natasha
#useradd -G jerry
#useradd -s /sbin/nologin sarah
#passwd natasha
#passwd jerry
#passwd sarah
(Checking)
#cat /etc/passwd
#cat /etc/group
#su <sarah> (user won't be able to login)
```

# 4. Setup collaborative directory
```
#mkdir /home/newfolder
#groupadd sysadmin
#chgrp sysadmin /home/newfolder
#chmod 770 sysadmin /home/newfolder
#chmod g+s /home/newfolder
(Checking)
#ls -ld /home/newfolder
```

# 5. Configure NTP Client
Your system should be configured as an NTP client of classromm example.com

```
#timedatectl set-ntp true
#vim /etc/chrony.conf
```
Comment out the third line and write "<domain.com> iburst" and save

# 6.create a user called system with ID number 2026
```
#sudo useradd -u 2026 system <username>
```

# 7.Create a tar archive
Create an archive called archive.tar.bz2 which contains the contents of /usr/local directory using bzip2 compression to perform this task
using bzip2
```
#yum install bzip*
#tar -Jcvf archive.tar.bz2 /usr/local/
```
using gzip
```
#yum install gzip*
#tar -zcvf archive.tar.gz2 /usr/local/
```

Decompress Not needed
# Using gzip
gzip -d file.txt.gz   # or gunzip file.txt.gz

# Using bzip2
bzip2 -d file.txt.bz2 # or bunzip2 file.txt.bz2

