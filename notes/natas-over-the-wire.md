# Natas - Over the wire game   

## Game progress 9 / 34 lvl

### Lvl 0 - 1
Inspect web page. 

### Lvl 1 - 2
Use keyboard shortcut. 

### Lvl 2 - 3
Directory listing - WWW server function to display list of files inside a folder.
Check if pages is loading some resources (e.x. images) and open parent folder vis URL

### Lvl 3 - 4
Tip inside commented text inside HTML - file for crawlers what not to index

### Lvl 4 - 5

`curl` request to `natas4 URL` with `refrerer Header` of `natas5`

``` curl -v -u <USER_NAME>:<PASSWORD> -H "<HEADER>: <NATAS5_URL>" <NATAS$_URL>```

### Lvl 5 - 6
Use flag `-v` and read what response brings you back.

Use `cookies` flag to pass the appropriate value and log in 

### Lvl 6 - 7
Read and try to understand source code written in `PHP`. 

`TIP:` where `$secret` comes from ?

### Lvl 7 - 8
`LFI (Local File Inclusion)` - a web application security vulnerability that happens when an application uses unvalidated or unsanitized user-controlled input to load files from the local server.

Pass the path to file with password to URL as `?page=` parameter value 


### Lvl 8 - 9
Revers the function to decode the secret 

### Lvl 9 - 10
`command injection` vulnerability .

Pass your own command as input value to `break out` of the original command and use it to your own good.

Analyse PHP code & HTTP request.

`TIP1:` Browser is just plain HTML + HTTP , you can see everything throw curl the same way. 

`TIP2:` If there's no form method in HTML - it's `GET` by default.  
