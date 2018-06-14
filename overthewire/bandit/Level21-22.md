# Level 21-22


## Level Goals

> A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.


## Commands you may need to solve this level
> cron, crontab, crontab(5) (use “man 5 crontab” to access this)

## do this

Start with looking into `cron.d` directory.  
	bandit21@bandit:~$ cd /etc/cron.d
	bandit21@bandit:/etc/cron.d$ ls -la
	total 28
	drwxr-xr-x   2 root root 4096 Dec 28 14:34 .
	drwxr-xr-x 100 root root 4096 Mar 12 09:51 ..
 	-rw-r--r--   1 root root  102 Apr  5  2016 .placeholder
	-rw-r--r--   1 root root  120 Dec 28 14:34 cronjob_bandit22
	-rw-r--r--   1 root root  122 Dec 28 14:34 cronjob_bandit23
	-rw-r--r--   1 root root  120 Dec 28 14:34 cronjob_bandit24
	-rw-r--r--   1 root root  190 Oct 31  2017 popularity-contest  
	 
`cronjon_bandit22` looks interesting and we have read permissions.  

	bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22 
	@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
	* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null  

This shows that this script `/usr/bin/cronjob_bandit22.sh` is running at every `reboot` and at every minute of everyday. Let's have a look at it.

	bandit21@bandit:/etc/cron.d$ ls -la /usr/bin/cronjob_bandit22.sh
	-rwxr-x--- 1 bandit22 bandit21 130 Dec 28 14:34 /usr/bin/cronjob_bandit22.sh  
	
`bandit21` has read permissions.

	bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
	#!/bin/bash
	chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
	cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv  
	
Voila! it is storing `bandit22` password in `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` giving `bandit21` read permissions.  

##### Note:
Permissions:  
`4` `read`  
`2` `write`  
`1` `execute`  
 So `6` means `4+2` i.e. read & write  
 and `7` means all the three.  



