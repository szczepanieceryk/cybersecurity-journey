# Bandit Over The Wire Game Notes

## Game progress 5 / 34

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
