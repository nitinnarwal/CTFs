# Level 4-5


## level goals

> The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.


## do this
just do `cat ./-file00` repeatedly till you get the password  
or  
`cd inhere`  
`find -type f | xargs file`  
The one with ASCII text is human readable.

## note
`file ./-file00` gives you the type of content of file  
`find -type f` gives you all the files (directories not excluded)  
`xargs` provides arguments to a command. Here it pipes output from `file -type f` to `file` as arguments.
