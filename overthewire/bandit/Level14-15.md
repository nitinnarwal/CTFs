# Level 12-13


## Level Goals

> The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Commands you may need to solve this level
> ssh, telnet, nc, openssl, s_client, nmap

## do this

The password for bandit14 is in `/etc/bandit_pass/bandit14`  

	cat /etc/bandit_pass/bandit14 | nc localhost 30000
