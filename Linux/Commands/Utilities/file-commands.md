file <filename> (To know what kind of file it is)

| Option | Description                                                |
| ------ | ---------------------------------------------------------- |
| `-l`   | Long listing format of files and directories, one per line |
| `-a`   | List all hidden files and directories starting with `.`    |
| `-F`   | Add a file type classification at the end of each entry    |
| `-g`   | List all files and directories with the group name         |
| `-i`   | Print index number (inode) of each file and directory      |
| `-m`   | List all files and directories separated by commas         |
| `-n`   | List numeric UID and GID of owners and groups              |
| `-r`   | List all files and directories in reverse order            |
| `-R`   | Recursively list all subdirectories                        |
| `-t`   | Sort by modified time, starting with the newest file       |




| File Type              | First Character in File Listing | Description                                                                                                |
| ---------------------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Regular file           | `-`                             | Normal files such as text, data, executable files                                                          |
| Directory              | `d`                             | Files that are lists of other files                                                                        |
| Symbolic link          | `l`                             | A shortcut that points to the location of the actual file                                                  |
| Character special file | `c`                             | Mechanism used for input and output, such as files in `/dev`                                               |
| Socket                 | `s`                             | A special file that provides inter-process networking protected by file system access control              |
| Pipe (FIFO)            | `p`                             | A special file that allows processes to communicate with each other without using network socket semantics |
| Block special file     | `b`                             | Special file used for block devices such as disks and storage devices                                      |
