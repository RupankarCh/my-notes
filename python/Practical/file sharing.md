# Share Files Locally using Python(Both Devices must be on the same local network)
Using Python HTTP Server
(Python must be installed in both systems)

TO **START THE HTTP SERVER**:(Navigate to the path the particular file/folder is located at)
```
python -m http.server 8080((To host the current directory’s files over HTTP )(port 8080 can be changed)
```

**ON RECEIVER DEVICE GO TO BROWSER**:
```
http://<IP_address_of_sharer_machine>:8080/File_name.txt  
Or if the file contains spaces in it’s name then type
http://<Ethernet Adapter Ethernet IPv4>:8080/EH%Couses.txt
```

**For Android Install Termux** from playstore
```
pkg install python (To install python, not needed if already installed)
Termux-setup-storage (And provide storage permission)
cd /storage/emulated/0/Ebook (To go to the Directory)
python3 -m http.server 8080 (To host the current directory’s files over HTTP )(port 8080 can be changed)
```
