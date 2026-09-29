# Bandit Over The Wire Game Notes

## Game progress 19 / 34

### Lvl 0
Login using ssh to a specified port

``` ssh -p PORT_NUMBER USER_NAME@HOST_IP ```

### Lvl 0 - 1 

`ls -a ` command to display all folder / files in main directory.

`cat` (concatenate) command to display the value of the specified file.

### Lvl 1 - 2
One of the ways to display value of a dashed filename is to use it's absolute path  

`cat ABSOLUTE_PATH`

### Lvl 2 - 3
Relative path + `TAB` or escape spaces with `\` character

`cat ./RELATIVE_PATH `

### Lvl 3 - 4
`ls -a` to display all files (even starting with `.` or `-`.

`cat` with relative path

### Lvl 4 - 5
`file` command 

`file DIRECTORY_NAME/*` - display file type of all files in this (DIRECTORY_NAME) directory 

### Lvl 5 - 6
`find` command 

Find files inside directory by specified file size 

`find . -size FILE_SIZE_WITH_UNIT_SUFFIX`

`.` - look for the files inside current directory 

`-size` - look for files with specified file size

`FILE_SIZE_WITH_UNIT_SUFFIX` - specified file size with unit suffix for e.x. 1033c (1033 bytes)

### Lvl 6 - 7
`find` command 

How to ignore errors like permission denied while looking for a file - `2>/dev/null`


### Lvl 7 - 8
`grep` command - to look for a specified phrase in a file 

```grep "PHRASE" FILE_TO_SEARCH```


### Lvl 8 - 9
`uniq -u` command Use the -u option to show lines that appear only once.

Remember that `uniq` need input data to be sorted beforehand.

Combination of `sort` & `uniq` commands


### Lvl 9 - 10

`strings` command to extract all strings from a file.

`-a` flag to cover all sections including metadata.

In combination with `grep` for specified characters.

### Lvl 10 - 11

`base64` command to decode encoded data.

`-d` - decode 

### Lvl 11 - 12

`tr` (translate) command - to switch position of each character by 13 (ROT 13 cipher) 

### Lvl 12 - 13

Work on temporary directory. Assign the value of `mktemp -d` to a variable and reuse it with `$VAR_NAME`

Copy origin data to a file and work on that copy `cp data.txt data_copy.txt`

Use standard output `stdout` redirection between files  

### Lvl 13 - 14

Copy a file with key using `scp` command - secure file copy between hosts on the same network. 

`scp -P PORT_NUMBER USER_NAME@HOST_IP:PATH_TO_FILE_WITH_KEY .` 

Log in to next lvl using key 

`ssh -i KEY_FILE USER_NAME@HOST_IP -p PORT_NUMBER`

### Lvl 14 - 15

Use `openssl s_client` to submit password.

### Lvl 15 - 16

`openssl s_client -connect HOST -port PORT_NUMBER ` 

### Lvl 16 - 17

Perform network scan on specified host and ports with `nmap`

```nmap -sV HOST -p PORT_RANGE```

Then submit the password again using 

```openssl s_client -connect HOST -port PORT_NUMBER -quiet```

Get the PRIVATE KEY password.

Create file on your local machine and copy key inside. Add permissions `chmod 600`.

Then use created file as a key to log in via ssh.

```ssh -i KEY_FILE USER@HOST -p PORT_NUMBER```

### Lvl 17 - 18

Use `diff` command to compare two files.

### Lvl 18 - 19

You can add commands at the end of ssh log in syntax. Given command will be executed on the remote host instead of a login shell.

### Lvl 19 - 20
Use of `nc` (netcat) and `sreen` commands
