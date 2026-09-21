# PWN Linux Luminarium 

## Current course status 🗓️

14 / 16 modules done ✅

## Modules

1. Hello Hackers            ✅
2. Pondering Paths          ✅
3. [Comprehending Commands](#comprehending-commands)   ✅
4. Digesting Documentation  ✅
5. File Globing             ✅
6. [Practicing Piping](#practicing-piping)      ✅
7. [Shell Variables](#shell-variables)          ✅
8. Data Manipulation        ✅
9. Processes and Jobs       ✅
10. Untangling Users        ✅
11. [Perceiving Permissions](#perceiving-permissions)  ✅
12. [Chaining Commands](#chaining-commands)       ✅
13. Terminal Multiplexing   ✅
14. [Pondering PATH](#pondering-path)          ✅
15. Silly Shenanigans       🟡 in progress 1/6
16. Daring Destruction

## Notes 


### Comprehending Commands

`grep` command - It is used to search for specific words, phrases, or patterns inside text files, and shows the matching lines on your screen.

`hacker@dojo:~$ grep SEARCH_STRING /path_to_file`

for e.x.:

```
grep flag /challenge/data.txt
```

`SEARCH_STRING` - a phrase your searching for

`/path_to_file` - a file you want to search in


### Practicing Piping

Initial, standard channels of communication in Linux: `stdin`, `stdout`, `stderr`.
- `stdin` - Standard input is the channel through which the process takes input for e.g. shell reading your commands

- `stdout` - Standard Output is the channel through which processes output normal data for e.g. shell displays list of files in given directory after `ls` command 

- `stderr` - Standard Error is the channel through which processes output error details for e.g. when you mistype the command .

Sometimes you need to redirect output (input or error) from one command to another command or a file. You can do this by simply using `>` char in between .

```
echo hi > new_file
```

This will `echo` string `hi` to a file `new_file`. But what if you want to aggregate output from many commands into one file ?. Simple use `>>`.

```
echo hello >> new_file
```

This will keep data from both `echo` commands in separate lines.

```
hacker@dojo:~$ cat my_file
hi
hello
``` 

Redirecting input to programs with `<`.

```
hacker@dojo:~$ echo yo > message
hacker@dojo:~$ cat message
yo
hacker@dojo:~$ rev < message
oy
```

Error redirection using `2>`.

`hacker@dojo:~$ some_command > output.log 2> errors.log` 

Redirect output from `some_command` to `output.log` file & errors to `errors.log`


`sed` (stream editor) command - It processes text line by line, applying the editing commands you specify.

for e.x. replacing words `sed "s/oldword/newword/g"`

where `s` means substitute and `g` - search for all occurrences of the pattern.

You can also delete a given string if you don't specify the second argument and just put 2 `//` like so 

`sed 's/stringtodelete//g`


### Shell Variables

To assign value to a variable you just simply use `=` , e.g. `VAR=1234` .

Then you can access this variable when needed by `$` so in our case `$VAR` 

`
hacker@dojo:~$ VAR=1234
hacker@dojo:~$ echo $VAR
1234
`

You can also assign command output to a variable 

```
FLAG=$(cat /flag)
```

Another thing you can do with variables is assign them a value entered by the user. 


```
read -p "<PROMPT> " <MY_VARIABLE>
``` 

Where `read` is a builtin which read input into a variable . 

`-p` let you specify a prompt message.

`<PROMT>` is a place for a text user will see (will be prompted with)

and finally `<MY_VARIABLE>` as the name of a variable you want to create (read user input in to) 


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


### Pondering path

Sometimes we need to call command by it's absolute path , but how to find it ?
The answer is `which` ! .
```
hacker@path~hijacking-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~hijacking-commands:~$ 
```

Having this path, we can use it with combination of environment variable `PATH` 

```
PATH=/run/dojo/bin/cat
```

so that the shell knows where to look for the command.

But why to do all of this ? ... well you can create your own custom commands to make the shell even more useful for yourself! .

