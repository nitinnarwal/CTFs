# Level 22-23


## Level Goals

> A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.  


## Commands you may need to solve this level
> cron, crontab, crontab(5) (use “man 5 crontab” to access this)  

## do this

Start with `cron.d`  
Look at the script `cronjob_bandit23` is executing.  

	bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh 
	#!/bin/bash

	myname=$(whoami)
	mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

	echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

	cat /etc/bandit_pass/$myname > /tmp/$mytarget  

`whoami` gives the username.  

Do this `echo I am user bandit23 | md5sum | cut -d " " -f 1` and you're done(follow the script).

