# Level 6-7


## level goals

> The password for the next level is stored somewhere on the server and has all of the following properties:  
owned by user bandit7    
owned by group bandit6  
33 bytes in size




## do this
`cd /`  
`find -size 33c -type f | xargs ls -la | grep bandit7 `  

There is output only one file with user bandit7 and group bandit6.  

`cat /var/lib/dpkg/info/bandit7.password`   


