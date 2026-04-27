# 🐚 Basic Shell Knowledge (Linux)

## 🧑‍💻 Prompt Symbols

```text
#  → Superuser (root) prompt, means you are running commands as **root (administrator)** → full system access ⚠️
$  → Normal user prompt, means you are a **regular user** → limited permissions
~  → Refers to the current user's home directory
```

---

## ▶️ Running Executables

```bash
./program_name   You need to use ./program_name to run an program existing on the same directory as you, If you downloaded that program in your current folder but didn’t move it to a PATH directory, typing `beef` alone will NOT work.
```
---

## 🏃‍♂️ Directory Traversal
Absolute Path:
ls /usr/sbin/

Relative Path:
ls sbin/

## 📦 to run without ./ (Why `./` is needed)

```text
move the program to PATH, the list of directories where the system looks for executable files "echo $PATH" to see the paths or move to the following directories
python
ls
nano
```

### Common PATH directories:

```text
/usr/bin
/bin
/usr/local/bin
```

## 📁 File & Directory Basics

```bash
pwd        # Show current directory
ls         # List files
cd         # return to the home directory of the current user)
cd /       # go to the root directory of the OS)
cd ..      # return to the upper directory
cd folder  # Change directory
```

---

## 🔐 Permissions (Very Important)

```bash
ls -l
```

Example output:

```text
-rwxr-xr-x  1 user user  1234 file.sh
```

### Meaning:

```text
r = read
w = write
x = execute
```

### Make a file executable:

```bash
chmod +x file.sh
```

---

## ⚡ Useful Tips

```bash
./script.sh     # Run script in current folder
bash script.sh  # Run using bash interpreter
```

---

# 🐧 Universal Terminal Manipulation Guide

## 📌 Basic Commands (Work on almost all Linux systems)

```bash
clear      # Clear the terminal screen
reset      # Reset terminal (fix broken display)
exit       # Close the terminal session
```

---

## ⌨️ Cursor Movement (Shell-level — works in most shells like Bash)

```text
Ctrl + A   → Move cursor to beginning of line
Ctrl + E   → Move cursor to end of line
Alt + B    → Move backward one word
Alt + F    → Move forward one word
```

---

## ✂️ Text Editing

```text
Ctrl + U   → Delete from cursor to beginning of line
Ctrl + K   → Delete from cursor to end of line
Ctrl + W   → Delete previous word
Ctrl + Y   → Paste (yank) last deleted text
```

---

## 🔄 Screen Control

```text
Ctrl + L   → Clear screen (same as `clear`)
Ctrl + C   → Cancel running command
Ctrl + Z   → Suspend current process
```

---

## 📜 History Navigation

```text
Ctrl + P   → Previous command
Ctrl + N   → Next command
↑ / ↓      → Scroll through command history
Ctrl + R   → Reverse search in history
```

---

## 🧵 Process & Session Control

```text
jobs       # List background jobs
bg         # Resume job in background
fg         # Bring job to foreground
kill %1    # Kill job number 1
```

---

## 📂 Tab & Autocomplete

```text
Tab        → Auto-complete commands/files
Tab (x2)   → Show all possible completions
```

---

## 🔍 Useful Terminal Tricks

```bash
history            # Show command history
!!                 # Run last command again
!n                 # Run command number n
```

---

## File Usage Tips:

1. If a filename is '-' then 'cat ./-' can open it meaning you are telling cat to search for a file name '-' in the current directory './'
2. To exit from ssh shell "exit"
3. file ./-* (This command can be used for finding human readable text in a bunch of files where which file contains text is not specified because, ./-* means all files whose names start with -, The file command tells you the type of each file, e.g., ASCII text (human-readable), binary data.)
4. find . -type f -size 1033c ! -executable -exec file {} + | grep "text" (find . (searches in the current directory and all subdirectories), -type f (looks for regular files only), -size 1033c (looks for files that are exactly 1033 bytes (c = bytes)), ! -executable (keep non executables files), -exec (lets you run a command on each file that found), file (determines file type), {} (is a placeholder that gets replaced with the current file's path/name for each match), + (passes multiple files at once), | grep "text" (filters the output to only show lines containing "text" i.e., human-readable files.)


sudo -i (To switch from a vagrant user to a root user)
mkdir folder1 folder2 folder3 (To make multiple directories at a time)
touch file{1..5}.txt (To make multiple files at a time)
cd /tmp/ (To move to temp directory from anywhre)
cp <coping_file_path> <destination_directory> (To copy, paste a file from one directory to another while not being present to the coping file directory)
cp -r <coping_directory_name> <destination_directory_name> (To copy a directory recursively)
mv <moving_directory_name> <destination_directory_name> (To move a directory from one place to another)
mv <file_name.txt> <file_new_name.txt> (To rename a file)
rm <file_name.txt> (To remove a file)
rm -r <directory_name> (To remove a directory)

# Shell Operators & Wildcards Cheat Sheet (Bash/Linux)

## Command Chaining / Control Operators

| Operator | Meaning                                                 | Example                                  | Result                                 |
| -------- | ------------------------------------------------------- | ---------------------------------------- | -------------------------------------- |
| `&`      | Run command in background                               | `python app.py &`                        | Starts process in background           |
| `&&`     | Run second command only if first succeeds               | `mkdir test && cd test`                  | `cd` runs only if `mkdir` worked       |
| `        |                                                         | `                                        | Run second command only if first fails |
| `;`      | Run commands sequentially regardless of success/failure | `pwd; ls`                                | Both run                               |
| `        | `                                                       | Pipe output of first command into second | `ls                                    |
| `()`     | Run commands in subshell                                | `(cd dir && ls)`                         | Runs inside temporary shell            |
| `{}`     | Group commands in current shell                         | `{ echo hi; echo bye; }`                 | Runs grouped commands                  |

---

## Redirection Operators

| Operator      | Meaning                          | Example                   |
| ------------- | -------------------------------- | ------------------------- |
| `>`           | Redirect output (overwrite file) | `ls > files.txt`          |
| `>>`          | Redirect output (append)         | `date >> log.txt`         |
| `<`           | Use file as input                | `sort < names.txt`        |
| `2>`          | Redirect errors only             | `ls badfile 2> error.txt` |
| `2>>`         | Append errors only               | `cmd 2>> err.log`         |
| `&>`          | Redirect stdout + stderr         | `cmd &> all.log`          |
| `>/dev/null`  | Discard output                   | `cmd >/dev/null`          |
| `2>/dev/null` | Hide errors                      | `find / 2>/dev/null`      |

---

## Wildcards / Globbing

| Pattern  | Meaning                              | Example          |
| -------- | ------------------------------------ | ---------------- |
| `*`      | Matches any string (0 or more chars) | `ls *.txt`       |
| `?`      | Matches exactly one character        | `ls f?le.txt`    |
| `[abc]`  | Match one of listed chars            | `file[123].txt`  |
| `[a-z]`  | Match range                          | `file[a-z].txt`  |
| `[^a-z]` | Not in range (some shells use `!`)   | `file[^0-9].txt` |
| `*.txt`  | All `.txt` files                     | `cat *.txt`      |
| `file*`  | Starts with `file`                   | `rm file*`       |
| `*log*`  | Contains `log`                       | `ls *log*`       |

> Note: `*` is a wildcard, **not alias**.

---

## Common Filters / Search with Wildcards

| Command                   | Meaning                       |
| ------------------------- | ----------------------------- |
| `rm *.tmp`                | Remove all `.tmp` files       |
| `cp file* backup/`        | Copy files starting with file |
| `ls *report*`             | Show names containing report  |
| `rsync --exclude="*.txt"` | Exclude `.txt` files          |

---

## Useful Shell Expansions

| Syntax      | Meaning                  | Example          |
| ----------- | ------------------------ | ---------------- |
| `~`         | Home directory           | `cd ~`           |
| `$VAR`      | Variable value           | `echo $HOME`     |
| `$(cmd)`    | Command substitution     | `echo $(date)`   |
| `` `cmd` `` | Old command substitution | ``echo `date` `` |

---

## Exit Status Logic

| Code     | Meaning |
| -------- | ------- |
| `0`      | Success |
| Non-zero | Failure |

Example:

```bash
mkdir test && echo "Created"
mkdir bad || echo "Failed"
```

---

## Process Control

| Command    | Meaning                            |
| ---------- | ---------------------------------- |
| `jobs`     | Show background jobs               |
| `fg`       | Bring background job to foreground |
| `bg`       | Resume in background               |
| `kill PID` | Kill process                       |

---

## Best Practical Examples

```bash
ls *.txt > files.txt
grep error log.txt | less
mkdir project && cd project
cd docs || echo "No docs folder"
python server.py &
find / -name "*.conf" 2>/dev/null
```

---

## Important Notes

* Use quotes if filenames contain spaces:

```bash
rm "my file.txt"
```

* Use `--` before filenames starting with dash:

```bash
rm -- -file.txt
```

---

## Quick Memory Trick

* `&&` = **If success then next**
* `||` = **If fail then next**
* `|` = **Send output onward**
* `>` = **Write fresh**
* `>>` = **Append**
* `&` = **Background**

---

