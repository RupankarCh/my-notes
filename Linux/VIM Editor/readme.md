# VIM EDITOR
VI Visual display editor
VIM Visual display editor improved

This is command mode editor for files. It has 3 modes:
- Command Mode ( :w to save the file, :q to exit from the file, :q! exit forcefully, ':se nu' to set line numbers on the file for viewing current time only)
- Insert mode (edit mode) (Press 'i' or 'o' to enter in the insert mode, Esc to get back to command mode)
- extended command mode ( : to enter extended mode)

```
$ <pkgmgr> install vim (To to install VIM)
# vim <filename.extension> (To create a file using VIM)
```
## Command Mode
Shift+G (To go to the end of the file)

| Key / Command | Action                                          |
| ------------- | ----------------------------------------------- |
| `gg`          | Go to the beginning of the page/file            |
| `G`           | Go to the end of the page/file                  |
| `w`           | Move the cursor forward word by word            |
| `b`           | Move the cursor backward word by word           |
| `nw`          | Move the cursor forward by *n* words            |
| `nb`          | Move the cursor backward by *n* words           |
| `u`           | Undo last change                                |
| `U`           | Undo all previous changes on the current line   |
| `Ctrl + R`    | Redo changes                                    |
| `yy`          | Copy (yank) current line                        |
| `nyy`         | Copy (yank) *n* lines                           |
| `p`           | Paste below the cursor position                 |
| `P`           | Paste above the cursor position                 |
| `dw`          | Delete a word from cursor forward               |
| `x`           | Delete character under cursor (like Delete key) |
| `dd`          | Delete entire line                              |
| `ndd`         | Delete *n* lines from cursor position           |
| `/word`       | Search for a word in the file                   |

## Extended Command Mode
| Command               | Action                                          |
| --------------------- | ----------------------------------------------- |
| `:w`                  | Save the file                                   |
| `:q`                  | Quit Vim                                        |
| `:wq`                 | Save and quit                                   |
| `:x`                  | Save and quit (if changes made)                 |
| `:q!`                 | Quit without saving                             |
| `:w!`                 | Force save                                      |
| `:e filename`         | Open/Edit another file                          |
| `:n`                  | Go to next file                                 |
| `:prev`               | Go to previous file                             |
| `:r filename`         | Read contents of another file into current file |
| `:saveas filename`    | Save current file with a new name               |
| `:set nu`             | Show line numbers                               |
| `:set nonu`           | Hide line numbers                               |
| `:set relativenumber` | Show relative line numbers                      |
| `:set ignorecase`     | Ignore case in search                           |
| `:set hlsearch`       | Highlight search results                        |
| `:set nowrap`         | Disable line wrapping                           |
| `:set wrap`           | Enable line wrapping                            |
| `:syntax on`          | Enable syntax highlighting                      |
| `:syntax off`         | Disable syntax highlighting                     |
| `:noh`                | Remove search highlight                         |
| `:1`                  | Go to line 1                                    |
| `:n`                  | Go to line *n*                                  |
| `:$`                  | Go to last line                                 |
| `:10,20d`             | Delete lines 10 to 20                           |
| `:10,20y`             | Copy (yank) lines 10 to 20                      |
| `:10,20p`             | Paste after line 20                             |
| `:%s/old/new/g`       | Replace all `old` with `new` in file            |
| `:10,20s/old/new/g`   | Replace `old` with `new` in lines 10–20         |
| `:g/word/d`           | Delete all lines containing `word`              |
| `:!command`           | Run shell command                               |
| `:help`               | Open help                                       |
| `:help command`       | Help for specific command                       |
| `:vs filename`        | Open file in vertical split                     |
| `:sp filename`        | Open file in horizontal split                   |
| `:tabnew`             | Open new tab                                    |
| `:tabn`               | Go to next tab                                  |
| `:tabp`               | Go to previous tab                              |
