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



Command which can be used without options
| Command            | Description                                                                    |
| ------------------ | ------------------------------------------------------------------------------ |
| `visudo`           | Edit the `sudoers` file safely                                                 |
| `updatedb`         | Update the file index database used by `locate`                                |
| `pwd`              | Print the current/working directory                                            |
| `whereis bash`     | Show location of the `bash` interpreter and related files                      |
| `which pwd`        | Show the path of the `pwd` command                                             |
| `cmp file1 file2`  | Compare two files byte by byte and show first difference                       |
| `diff file1 file2` | Compare two files line by line and show differences                            |
| `comm file1 file2` | Compare two sorted files line by line and display differences in three columns |
