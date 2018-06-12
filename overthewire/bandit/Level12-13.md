# Level 12-13


## Level Goals

> The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv  

## Helpful Reading Material
[Hex dump on Wikipedia](http://en.wikipedia.org/wiki/Hex_dump)

## do this

> bandit12@bandit:\~$ ls  
data.txt  
bandit12@bandit:\~$ mkdir /tmp/mypwd  
bandit12@bandit:\~$ cp data.txt /tmp/mypwd/  
bandit12@bandit:\~$ cd /tmp/mypwd/  
bandit12@bandit:/tmp/mypwd$ ls  
data.txt  


As per description, this is hexdump of a repeatedly compressed file. So use `xxd -r` to convert back to its original form.

> bandit12@bandit:/tmp/mypwd$ xxd -r data.txt > dump  
bandit12@bandit:/tmp/mypwd$ ls   
data.txt  dump   

use `file dump` to know the filetype. It should be a compressed file as per discription.  
> bandit12@bandit:/tmp/mypwd$ file dump   
dump: gzip compressed data, was "data2.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix   

and yes! it is.
  
##### Remember file extensions:

* `.gz` for `gzip`  
* `.bz2`for `bzip2`  
* `.tar` for `tar`  

So, change the filename as per the file type.
  
> bandit12@bandit:/tmp/mypwd$ mv dump dump.gz  
bandit12@bandit:/tmp/mypwd$ ls   
data.txt  dump.gz    

Use `gzip -d` to decompress gzip files  
Use `bzip2 -d` to decompress bzip2 files.  
Use `tar -xvf` to untar  
> bandit12@bandit:/tmp/mypwd$ gzip -d dump.gz     
bandit12@bandit:/tmp/mypwd$ ls    
data.txt  dump      

Now, repeat this procedure.  

> bandit12@bandit:/tmp/mypwd$ file dump  
dump: bzip2 compressed data, block size = 900k  
  
> bandit12@bandit:/tmp/mypwd$ mv dump dump.bz2
bandit12@bandit:/tmp/mypwd$ bzip2 -d dump.bz2  
bandit12@bandit:/tmp/mypwd$ ls  
data.txt  dump

again..  

>bandit12@bandit:/tmp/mypwd$ file dump  
dump: gzip compressed data, was "data4.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix  
bandit12@bandit:/tmp/mypwd$ mv dump dump.gz  
bandit12@bandit:/tmp/mypwd$ gzip -d  dump.gz    
bandit12@bandit:/tmp/mypwd$ ls   
data.txt  dump  

again..

> bandit12@bandit:/tmp/mypwd$ file dump   
dump: POSIX tar archive (GNU)  
bandit12@bandit:/tmp/mypwd$ mv dump dump.tar  
bandit12@bandit:/tmp/mypwd$ tar -xvf dump.tar   
data5.bin  
bandit12@bandit:/tmp/mypwd$ ls  
data.txt  data5.bin  dump.tar

#####`tar`  [options]  
* `-x` extract files
* `-v` verbosely list files
* `-f` use archive file 

         
again..

> bandit12@bandit:/tmp/mypwd$ file data5.bin  
data5.bin: POSIX tar archive (GNU)  
bandit12@bandit:/tmp/mypwd$ mv data5.bin   data5.tar  
bandit12@bandit:/tmp/mypwd$ tar -xvf data5.tar  
data6.bin  

again..

> bandit12@bandit:/tmp/mypwd$ file data6.bin  
data6.bin: bzip2 compressed data, block size = 900k  
bandit12@bandit:/tmp/mypwd$ mv data6.bin data6.bz2  
bandit12@bandit:/tmp/mypwd$ bzip2 -d data6.bz2  
bandit12@bandit:/tmp/mypwd$ ls  
data.txt  data5.tar  data6  dump.tar  
bandit12@bandit:/tmp/mypwd$ file data6  
data6: POSIX tar archive (GNU)

again..

> bandit12@bandit:/tmp/mypwd$ mv data6 data6.tar  
bandit12@bandit:/tmp/mypwd$ tar -xvf data6.tar  
data8.bin  
bandit12@bandit:/tmp/mypwd$ ls  
data.txt  data5.tar  data6.tar  data8.bin    dump.tar  
bandit12@bandit:/tmp/mypwd$ file data8.bin  
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix  

again..

> bandit12@bandit:/tmp/mypwd$ mv data8.bin   data8.gz  
bandit12@bandit:/tmp/mypwd$ gzip -d data8.gz  
bandit12@bandit:/tmp/mypwd$ ls  
data.txt  data5.tar  data6.tar  data8  dump.tar  
bandit12@bandit:/tmp/mypwd$ file data8  
data8: ASCII text   

and data8 is the password file.  
Uff!! done..

