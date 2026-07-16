1.Password Chaning
- Set line Console Password
- Set Aux Console Passord
- Set Enable Password
- Set Enable Secret Password
```
line console 0
password abc
login
exit
line aux 0
password abc
login
exit
enable password abc
enable secret password
```
While Booting
press Ctrl+c (To enter in rommon mode)
```
rommon> confreg 0x2142
reset
copy startup-config running-config
enable password abc
wr
```
```
conf t
config-register 0x2102
```
restart
