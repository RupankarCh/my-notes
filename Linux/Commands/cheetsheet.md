# 🥇 Level 1 — Daily Commands (Use Every Day)

## 📂 Navigation

```
pwd      # Where am I?
ls       # What's here?
cd       # Go somewhere
cd ..    # Up one folder
cd ~      # Home
man -k <keyword> # Searches the short descriptions of all manual pages for the specified keyword and returns a list of matching commands
```

---

## 📄 File Operations

```
touch file.txt
mkdir folder
cp source dest
mv old new
rm file
rm -r folder
```

---

## 🔍 Viewing Files

```
file <filename> (see file type)
cat file
head file
tail file
less file
```

## I/O redirection:
```
> overwrite
>> Append
2>> Error Append
&>> Error and Output Append
grep <word> takes the line containing the word.
```

## Text Editor (Vim)
```
:se nu (turns on line numbers in the editor buffer)
/<word> (To search for the word's next occurrence in the file)
yy (Copy current line)
p (Paste)
```

## Archive:
```
tar -czvf <filename>.tar.gz <directory> (c-create, z-compress, f-file, to archive a directory)
tar -xzvf <filename>.tar.gz <directory> (x-extract, )
zip -r <filename>.zip <directory> 
unzip <filename>.zip 
```

---

# 🥈 Level 2 — Permissions & Users

## Permissions

```
ls -l
chmod +x script.sh
chmod g+w <directory/rup> (To change permissions)
chmod 644 file
chmod 755 script.sh
chown user:user file
chown -R <username> <groupname> <directory/rup> (To change user owner and group owner) 
```

## User Info
<img width="994" height="235" alt="Screenshot 2026-08-17 204537" src="https://github.com/user-attachments/assets/bd546f8e-a9a0-48a3-ba42-876c554bc612" />

**System Users**: The **users created by the softwares or applications** for example if we install Apache it will create a user apache. These kind of users are known as system users.

Whenever a user is created in Linux things created by default:
- A home directory is created (/home/username/)
- A mail box is created (/var/spool/mail)
- unique UID & GID are given to user


```
whoami
id
groups
passwd
```

### Memory:

> **Who am I? → What can I do?**

## User Modification
```
usermod -aG <username> <groupname> (To add an already existing user to another existing group)
userdel -r <username> (To delete the user with it's home directory also)
---

# 🥉 Level 3 — Processes

## Running Programs

```
ps aux
top
htop
pgrep nginx
pidof sshd
```

## Killing Programs

```
kill PID
kill -9 PID
pkill firefox
```

### Memory:

> **Find → Monitor → Kill**

---

# 🏅 Level 4 — System Information and Processes

```
hostnamectl
uname -a
lsb_release -a
uptime
free -h
lscpu
date
timedatectl
top (To System Information processes)
free -m (To see RAM details)
ps -aux (To sort processes by PID)
kill <PPID> (To stop all the process and then the parent process itself is stopped, It may happen that systemctl stop <ps> command won't be available)
kill -9 <PID> <PID> <PID> (stop process forcefully)
```

### Memory:

> **System → CPU → Memory → Time**

---

# 🌐 Level 5 — Networking

## Addresses

```
ip a
ip route
```

## Connectivity

```bash
ping google.com
traceroute google.com
```

## Ports

```
ss -tulnp
```

## DNS

```
dig google.com
nslookup google.com
resolvectl status
```

## Downloading

```
curl URL
wget URL
```

### Memory:

> **IP → Ping → Ports → DNS → Download**

---

# ⚙️ Level 6 — Services

```
systemctl status nginx
systemctl start nginx
systemctl stop nginx
systemctl restart nginx
systemctl enable nginx
systemctl disable nginx
```

### Memory:

> **Status → Start → Stop → Restart → Enable**

---

# 📜 Level 7 — Logs & Troubleshooting

## Journal

```
journalctl -b
journalctl -f
journalctl -u nginx
```

## Kernel

```
dmesg -T
```

## Syslog

```
tail -f /var/log/syslog
grep error /var/log
```

### Memory:

> **Journal → Kernel → Syslog**

---

# 💾 Level 8 — Disk & Storage

## Space

```
df -h
du -sh .
lsblk
blkid
```

## Mounting

```
mount
findmnt
umount
```

## Files

```bash
stat file
file unknown.bin
```

### Memory:

> **Space → Disks → Mounts → Files**

---

# 📦 Level 9 — Packages 
/etc/yum.repos.d
/etc/apt/sources.list (this file contains the repositories)

On Fedora based systems like RHEL/CentOS: 
```
yum update (checks for the latest indices and upgrades all installed packages at once also while removing the obsolete packages)
yum install <package_name> (updates the index for every package on your system, and installs the latest version of the package_name mentioned)
```

On Debian based systems Kali/Ubuntu: (The default editor is nano here)
```
adduser <username>
export EDITOR=vim (To change default editor to vim)
dpkg -i <downloaded_package> 
dpkg -l (To list all the Debian package on the system)
dpkg -r <package_name> (To remove a package)
apt update (downloads the latest package information from configured repositories so your system knows which software updates and new packages are available) 
apt upgrade (installs the newest versions of all currently installed packages on your system using the package list fetched by apt update)
apt search <package_name> 
apt install <package_name> (To install and start a service)
apt remove <package_name>
apt purge <package_name> (To remove all the configuration, data and the package itself from the system)
systemctl status <apache2>
systemctl is-enabled <service_name> 
sudo apt autoremove
```

### Memory:

> **Update → Upgrade → Install → Remove**

---

# 🔐 Level 10 — SSH & Firewall

## SSH

```
ssh user@host
ssh -v user@host
ssh-copy-id user@host
ssh-keygen -R host
```

## Firewall

```
sudo ufw status
sudo ufw allow 22/tcp
sudo ufw deny 22/tcp
sudo ufw reload
```

### Memory:

> **Connect → Keys → Firewall**

---

# 📝 Level 11 — Text Processing

```
grep
sed
awk
cut
sort
uniq
wc
```

### Memory:

Think of a pipeline:

```
Find → Modify → Extract → Sort → Count
grep → sed → awk → sort → uniq → wc
```

---

# 💾 Level 12 — Backup

```
rsync
tar
zip
sha256sum
diff
```

### Memory:

```
Copy → Compress → Verify → Compare
```

---

# 🖥️ Level 13 — Hardware

```
lspci
lsusb
lsmod
modprobe
sensors
rfkill
```

### Memory:

> **Devices → Drivers → Temperature**

---


This order follows how Linux administrators usually troubleshoot:

> **Where am I → What files are there → Who owns them → What's running → Is the system healthy → Is the network working → Are services running → What do the logs say → Is disk space okay → Are packages broken → Can I SSH → Need to edit text → Backup → Check hardware.**
