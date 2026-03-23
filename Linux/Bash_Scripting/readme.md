# Definition
Bash scripting is the **process of writing a series of commands in a file (called a script) using the Bash shell** so they can be executed automatically instead of typing them one by one.

Description:
Bourne Shell was used in Unix it was propriatory so **Brian Fox created Bourne Again Shell for the GNU project**, It was built for open source replacement of the propriatory Bourne Shell with many improments.
- **/bin/bash** shell:When a user is assigned /bin/bash, they get an interactive shell. This allows them to run commands, use Bash syntax, and execute shell scripts from the terminal.
- **/bin/false** and **/usr/sbin/nologin** shells:
  - These are used for system or service accounts (daemons). They prevent login access:
  - **/bin/false** immediately exits (no shell access at all).
- **/usr/sbin/nologin** blocks login and may show a message.These accounts are not meant for human use, only for running background processes.

Bash script file extension:
Bash scripts often use **.sh**, but this is just a convention. What really matters is the **shebang line (e.g., #!/bin/bash)** at the top, It calls the interpreter to interpret the code, in other words the code will be passed to the interpreter via the path /bin/bash

# Commands

```text
vim <file_name.sh>   #To start creating a script using vim editor
bash </file.sh>      #To run the script
$(command)           #It print the output of the command
```


#Variables: 
$ symbol is used as a variable for reading, variable don't require parenthesis to access them.
$0 holds the name of the current shell
$SHELL contains the path to our current interpreter.
$USER will output current username ($USER is an environment variable which holds current user’s username)
$HOME will show the home directory of the current user


