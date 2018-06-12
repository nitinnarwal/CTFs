# Level 12-13


## Level Goals

> The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

## Commands you may need to solve this level
> ssh, telnet, nc, openssl, s_client, nmap

## Helpful Reading Material
> [SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

## do this

Start with listing files.  

	bandit13@bandit:~$ ls -la
	total 24
	drwxr-xr-x  2 root     root     4096 Dec 28 14:34 .
	drwxr-xr-x 29 root     root     4096 Dec 28 14:34 ..
	-rw-r--r--  1 root     root      220 Sep  1  2015 .bash_logout
	-rw-r--r--  1 root     root     3771 Sep  1  2015 .bashrc
	-rw-r--r--  1 root     root      655 Jun 24  2016 .profile
	-rw-r-----  1 bandit14 bandit13 1679 Dec 28 14:34 sshkey.private
	
There you see `sshkey.private` which is a ssh private key owned by `bandit14`.  

	bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost        

and done.

