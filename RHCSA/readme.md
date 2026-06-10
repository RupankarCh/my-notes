1. IP Address Configuration, Hostname Change:
Set IP Address, Subnet Mask, Gateway Address, DNS Address
```
#nmtui (To configure IP address)
Edit a connection> Select the interface> IPv4 Address Show> Enter the Content and OK> Back> Activate a connection> deactive and activate and Back> Quit
#ifconfig (To check)
#hostnamectl set-hostname newhostname (To change hostname)
```
2.Configure an YUM repository
```
#df -Th (To check If you see s0 then start from Part 3, otherwise only disks like sda, vda, nvme0n1, etc., then there is no mounted ISO so proceed)
```
Check:
```
lsblk
```
You should see something like:
sr0    11:0    1 10G 0 rom
If not then proceed If yes then start from part 2
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

Check:
```
lsblk
```
You should see something like:
sr0    11:0    1 10G 0 rom

**Part 2**
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

Part 3


