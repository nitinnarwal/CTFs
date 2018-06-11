# Level 5-6


## level goals

> The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:  
    human-readable  
    1033 bytes in size  
    not executable



## do this
`cd inhere`  
`find -type f -size 1033c | xargs cat`  


