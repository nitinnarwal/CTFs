# Level 20-21


## Level Goals

> There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).  
   
NOTE: Try connecting to your own network daemon to see if it works as you think


## Commands you may need to solve this level
> ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)

## write-up

`suconnect` will transmit the password for `bandit21` if we can send the password of `bandit20` and we can do so by creating a listening port(any port which is not in current use).  
Open another session of `bandit20` and start listening on a port(say 1234).
`nc -l -v 1234`  
Then submit the `bandit20` password here.  
  
In the other session  
`./suconnect 1234`  

#### Note:
You can check for ports using `nmap`.


