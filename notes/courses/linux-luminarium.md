# PWN Linux Luminarium 

## Current course status 🗓️

11 / 17 modules done ✅

## Modules

1. Hello Hackers            ✅
2. Pondering Paths          ✅
3. Comprehending Commands   ✅
4. Digesting Documentation  ✅
5. File Globing             ✅
6. Practicing Piping        🟡 in progress 14/15
7. Shell Variables          ✅
8. Data Manipulation        🟡 in progress 5/6
9. Processes and Jobs       ✅
10. Untangling Users        ✅
11. [Perceiving Permissions](#perceiving-permissions)  ✅
12. [Chaining Commands](#chaining-commands)       ✅
13. Terminal Multiplexing   🟡 in progress 5/6
14. Pondering PATH          🟡 in progress 3/5
15. Silly Shenanigans
16. Daring Destruction
17. Further Learning

## Notes 

### Perceiving Permissions

### How to read file permisions

`ls -l`  to display list of files with permissions 

```
-rw-r--r-- 1 hacker hacker    0 May 22 13:42 college_file
drwxr-xr-x 2 hacker hacker 4096 May 22 13:42 pwn_directory
```

First char is a file type `-` is a normal file , `d` means directory and so on .

Next 9 chars are the permissions grouped by 3 characters 

`rw-r--r--`

- first 3 - rights of a owner of a file
- second 3 - rights of a group
- last 3 - rights of other users & group


Permisions:

- `r` - read
- `w` - write
- `x` - execute 
- `a` - append
- `o` - own

Then user name & group name that owns a file

`hacker hacker `


### How to change permissions 

`chmod [OPTIONS] MODE [FILE]` - change mode command  
[OPTIONS] - `WHO/WHAT` where `WHO` is user/group/others and `WHAT` is read/write/execute

`WHO`
- `u` - user
- `g` - group
- `o` - other (groups & users)
- `a` - all

`WHAT`
- `r` - user/group/other can read the file (or list the directory)
- `w` - user/group/other can modify the files (or create/delete files in the directory)
- `x` - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
- `-` - nothing / no peermissions at all

`MODE` - you can modify existing permisions or overwrite with new ones 
- `+` add permissions
- `-` remove rermissions
- `=` overwrite previous permission

`chmod u+rw /my_file` - adds to user read & write permissions for /my_file


### How to change file ownership 

`chown [username] [file]` - change ownership command 
`chown hacker /my_file`


### Chaining Commands

The easiest way to chain commands is to separates them with `;` semicolon 

`echo COLLEGE > pwn; cat pwn`

`&&` and `||` operators.

You can use `&&` to run commands on success. Meaning - run second command only when the first one ends with success

`touch /my_file && echo "file /my_file created successfully"`.

In the same manner, you can run commands on failure - run command2 if command1 fails to succeed.

` touch my_file || echo "You cannot touch this file so you see this error message"`

### Writing bash scripts

To write s bash script we need to create a file for e.g. `script.sh` but the `.sh` extension is not necessary - it can be a Python script as well (`.py`) or other.

When a program is invoked, Linux kernel inspects first few bytes of the file to determine how it should be run.
Shell script must start with characters `#!/bin/bash` as the very first line in a file and then the rest of the code.

For e.g.:

```
  #!/bin/bash
  echo "Hello Hackers!"
```

Then we can run our bash script with 

`bash [SCRIPT_NAME]` like so `bash script.sh`

or just by path of the script - `./script.sh`
