# Level 18-19


## Level Goals

> The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.


## Commands you may need to solve this level
> ssh, ls, cat

## do this

Here `.bashrc` is logging you out.
You can login without `source`ing `.bashrc` by forcing ssh to open shell other than `/bin/bash`.   
`/bin/sh` wouldn't `source` `.bashrc`.  
`ssh -t bandit18@bandit.labs.overthewire.org -p 2220 /bin/sh`
