# 1.Disk Quota
**Instance Creation:**
EC2> Launch Instance> Name it> Select RHEL 10 as AMI> Create key pair with .ppk extension> Enable auto-assign public IP> Launch Instance.

**Connecting to Instance:**
Open PuTTy paste the public IP of the instance> THen SSH, Auth, Credentials and Browse the key and press open, enter ec2-user> sudo -i

**Adding the Volume:**
EBS> Volumes> Create volume> Select Size, Availability zone will be same as instance> Create volume.

Select the instance, Actions> Storage> Attach volume> Select Volume> Attach Volume.
**Configuration of Disk Quota:**
```
fdisk /dev/nvme1n1
mkfs.ext4 /dev/nvme1n1p1
mkdir /data
mount /dev/nvme1n1p1 /data
vi /etc/mtab
```
Go to last line enter Esc yy
Esc:n /etc/fstab
Esc p 
Esc: wq
```
yum install quota
yum list installed quota
useradd a
useradd b
useradd c
useradd d
groupadd quota
usermod -g quota b
vi /etc/fstab
```
Write realtime, usrquota, grpquota
Esc: wq
```
systemctl daemon-reload
mount -o remount /data
mount | grep /data
passwd root
passwd a
chmod 777 /data
quotacheck -cug /data
edquota a
```
blocks soft 100000, hard 200000
inodes soft 100000, hard 200000
```
quotaon /data
su - a
touch a.user{1..21}.txt
```
