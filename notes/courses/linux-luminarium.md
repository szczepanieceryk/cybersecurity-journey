# PWN Linux Luminarium 

## Current course status 🗓️

7 / 17 modules done ✅

## Modules

1. Hello Hackers            ✅
2. Pondering Paths          ✅
3. Comprehending Commands   ✅
4. Digesting Documentation  ✅
5. File Globing             🟡 in progress 8/10
6. Practicing Piping        🟡 in progress 14/15
7. Shell Variables          ✅
8. Data Manipulation        🟡 in progress 5/6
9. Processes and Jobs       ✅
10. Untangling Users        ✅
11. [Perceiving Permissions](#perceiving-permissions)  ✅
12. Chaining Commands
13. Terminal Multiplexing    
14. Pondering PATH
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

