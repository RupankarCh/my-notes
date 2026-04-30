~ means home
Any file name start with ‘.’ is considered a hidden file

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
| `file <filename>`  | To know what kind of file it is                                                |


# ls <directory_path(Optional)> 
(To see directories and files list-wise in the current directory or in other directories)

| Option | Description                                                |
| ------ | ---------------------------------------------------------- |
| `-l`   | Long **listing format of files** and directories, one per line, with **permissions, size, owner etc.** |
| `-a`   | List all **hidden files** and directories starting with `.`    |
| `-F`   | Add a file type classification at the end of each entry    |
| `-g`   | List all files and directories with the group name         |
| `-i`   | Print **index number (inode)** of each file and directory      |
| `-m`   | List all files and directories separated by commas         |
| `-n`   | List numeric UID and GID of owners and groups              |
| `-r`   | List all files and directories in reverse order            |
| `-R`   | Recursively list all subdirectories                        |
| `-t`   | Sort by **modified time**, starting with the newest file   |
| `-h`   | Human-readable format with file sizes in KB, MB, etc.      |
| `-d <directory_path>`   | view permissions of a directory/file      |     


# cd 
Change Directory

| Command            | What It Does                          | Easy Way to Remember          |
| ------------------ | ------------------------------------- | ----------------------------- |
| `cd`               | Goes to **current user’s home directory** | Plain `cd` = Home         |
| `cd -`             | Goes to the previous directory        | `-` = Back to the **previous working directory**   |
| `cd /`             | Goes to the root of the filesystem    | `/` = **Root/Top of system**  |
| `cd ..`            | Moves up one directory                | `..` = **One step back**      |
| `cd ../..`         | Moves up two directories              | Two `..` = Two steps back     |
| `cd ../../..`      | Moves up three directories            | Three `..` = Three steps back |
| `cd directoryname` | Enters a specific folder              | Use folder name               |
| `cd ../../var`     | Move up two levels, then enter `var`  | Back 2 → Go to `var`          |

# cp
Copy

| Command                       | What It Does                                            | Easy Way to Remember     |
| ----------------------------- | ------------------------------------------------------- | ------------------------ |
| `cp file1 file2`              | **Copy `file1` and name it as `file2`** in same folder, file1 exists | Copy + rename |
| `cp file /path/`              | Copy file to another folder                             | **Copy to location**     |
| `cp data* /path/`             | Copy all files starting with `data`                     | **`*` = wildcard**       |
| `cp *.txt /path/`             | **Copy all `.txt` files**                               | `*` = all matching files |
| `cp -r dir1 /path/`           | **Copy folder recursively**                             | `-r` = copy folders      |
| `cp -i file1 file2`           | Ask before overwriting                                  | `i` = interactive        |
| `cp -f file1 file2`           | Force overwrite existing file                           | `f` = force              |
| `cp -u file1 file2`           | Copy only if newer                                      | `u` = update             |
| `cp -v file1 file2`           | Show what is being copied                               | `v` = verbose            |
| `cp -n file1 file2`           | Do not overwrite existing file                          | `n` = **no overwrite**   |
| `cp -a dir1 backup/`          | Archive copy (preserves permissions, timestamps, links) | `a` = **copies all attributes** |
| `cp file1 file2 file3 /path/` | **Copy multiple files to folder**                       | Many files at once       |


#mv
move/rename

| Task                            | Command                        |
| ------------------------------- | ------------------------------ |
| **Rename** file/folder          | `mv old.txt new.txt`           |
| **Move folder** into another folder | `mv project backup/`       |
| Move one file                   | `mv file.txt /home/user/docs/` |
| **Move multiple files**         | `mv file1.txt file2.txt docs/` |
| **Move all `.txt` files**       | `mv *.txt docs/`               |
| Creates **backup before overwriting** | mv -b file.txt docs/     |
| **Ask before overwrite**        | `mv -i file.txt docs/`         |


#rm 
remove

| Command                   | What It Does                                          | Easy Way to Remember                |
| ------------------------- | ----------------------------------------------------- | ----------------------------------- |
| `rm file.txt`             | Deletes a single file                                 | **rm = remove file**                |
| `rm file1.txt file2.txt`  | **Deletes multiple files**                            | Remove many files together          |
| `rm *`                    | Deletes **all files in current folder** (not directories) | `*` = everything                |
| `rm -f file.txt`          | Force delete without asking                           | `f = force`                         |
| `rm -r folder/`           | Deletes folder and all contents                       | `r = recursive`                     |
| `rm -rf folder/`          | **Force delete folder + contents**                    | Dangerous combo: remove all fast    |
| `rm -d folder/`           | Deletes **empty folder only**                         | `d = directory`                     |
| `rm -v file.txt`          | Shows what is being deleted                           | `v = verbose / visible`             |
| `rm -I *`                 | Prompts once before deleting many files               | Capital `I` = one Important warning |
| `rmdir folder/`           | Removes empty directory                               | `rmdir = remove dir`                |

#echo
| Command                        | What It Does                      | Easy Way to Remember              |
| ------------------------------ | --------------------------------- | --------------------------------- |
| `echo Hello`                   | **Displays** `Hello` on screen    | Echo repeats what you say         |
| echo "Hello World"             | Displays text with spaces         | Quotes **keep words together**    |
| `echo $HOME`                   | Shows **value of variable**       | `$` = variable value              |
| `echo > file.txt`              | Creates blank file                | Empty echo + `>` makes file       |
| `echo "Text" > file.txt`       | **Writes text to file** (overwrite)| `>` = send into file             |
| `echo "More text" >> file.txt` | Adds text to end of file (**Append**) | `>>` = append more            |
| `echo -n "Hello"`              | Prints without new line           | `n = no new line`                 |
| `echo -e "Line1\nLine2"`       | Enables escapes like new lines    | `e = enable escapes`              |
| `echo -e "A\tB"`               | Inserts tab space                 | `\t` = tab                        |
| `echo -e "Path:\\home"`        | Prints backslash                  | `\\` = one backslash              |
| `echo *`                       | Shows all files in current folder | `*` = everything                  |
| `echo .*`                      | Shows hidden files too            | `.` = hidden files start with dot |
Escape Sequences
| Escape | Meaning        | Easy Way      |
| ------ | -------------- | ------------- |
| `\n`   | New line       | **next line** |
| `\t`   | Horizontal tab | tab space     |
| `\\`   | Backslash      | escaped slash |
| `\a`   | Alert bell     | alarm         |
| `\b`   | Backspace      | move back     |

#

