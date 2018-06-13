# Level 16-17


## Level Goals

> The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

## Commands you may need to solve this level
> ssh, telnet, nc, openssl, s_client, nmap

## do this

Scan for open ports using `nmap`  
`nmap -v -sV -p31000-32000 localhost`  
##### Note
* `-v` verbose  
* `-sV` service detection  
* `-p` ports range  

Check which `ssl` service on the open ports and do `openssl` as done in the last level.
