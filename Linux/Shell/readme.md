
# Shell Operators & Wildcards Cheat Sheet (Bash/Linux)

## Command Chaining / Control Operators

| Operator | Meaning                                                 | Example                                  | Result                                 |
| -------- | ------------------------------------------------------- | ---------------------------------------- | -------------------------------------- |
| `&`      | Run command in background                               | `python app.py &`                        | Starts process in background           |
| `&&`     | Run command2 only if command1 exits with status 0 (success). | `mkdir test && cd test`             | `cd` runs only if `mkdir` worked       |
| `|`      | pass output to next command                             | `ls | grep txt`                          | `ls`'s output is piped into grep txt, grep txt filters and shows only lines containing txt |
| `||`     | Run command2 only if command1 exits with non-zero status (failure). | `mkdir myfolder || echo "Failed to create folder"` |   If `mkdir` fails to create the directory then the message is shown |
| `;`      | Run commands sequentially regardless of success/failure | `pwd; ls`                                | Both run                               |
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
| `>/dev/null`  | Discard output                   | `cmd >/dev/null` Normal output is hidden, Error messages (stderr) still appear on screen  |
| `2>/dev/null` | Hide errors                      | `find / 2>/dev/null` Normal output is shown, Error messages (stderr) still hidden |

---

## Wildcards / Globbing

| Pattern  | Meaning                              | Example          |
| -------- | ------------------------------------ | ---------------- |
| `*`      | Alias Matches any string (0 or more chars), all files and folders in the current directory)| `ls *.txt`, `--exclude="*.txt"` (means excluding .txt files)       |
| `?`      | wildcard Matches exactly one character | `ls f?le.txt`    |
| `[abc]`  | Match one of listed chars            | `file[123].txt`  |
| `[a-z]`  | Match range                          | `file[a-z].txt`  |
| `[^a-z]` | Not in range (some shells use `!`)   | `file[^0-9].txt` |
| `*.txt`  | All `.txt` files                     | `cat *.txt`      |
| `file*`  | Starts with `file`                   | `rm file*`       |
| `*log*`  | Contains `log`                       | `ls *log*`       |

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

---

## Process Control

| Command    | Meaning                            |
| ---------- | ---------------------------------- |
| `jobs`     | Show background jobs               |
| `fg`       | Bring background job to foreground |
| `bg`       | Resume in background               |
| `kill PID` | Kill process                       |

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
* `&` = **Background**

---

