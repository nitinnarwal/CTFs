# Level 19-20


## Level Goals

> To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.


## do this


	bandit19@bandit:~$ ls -la
	total 28
	drwxr-xr-x  2 root     root     4096 Dec 28 14:34 .
	drwxr-xr-x 29 root     root     4096 Dec 28 14:34 ..
	-rw-r--r--  1 root     root      220 Sep  1  2015 .bash_logout
	-rw-r--r--  1 root     root     3771 Sep  1  2015 .bashrc
	-rw-r--r--  1 root     root      655 Jun 24  2016 .profile
	-rwsr-x---  1 bandit20 bandit19 7408 Dec 28 14:34 bandit20-do  

Here `bandit20-do` has permissions for user `bandit20`.
	
	bandit19@bandit:~$ ./bandit20-d  
	Run a command as another user.
	  Example: ./bandit20-do id  
	  
	bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20

