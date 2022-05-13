## Step for use this tool

1. prepare two linux envirements (Oracle VM 6.1.34, CentOS 8)
2. make sure they can ping each other (Server: 192.168.0.111, Client: 192.168.0.114)
3. install ftp client in client server (CentOS 8 : yum install ftp)(ftp-0.17-78.el8.x86_64)
4. put the target file (01.txt ~ 03.txt) to ftp server (/tmp/skywatch_2/01~03.txt)
5. execute with ./ftp in server
6.	1. [client] cd /
	2. [client] mkdir /tmp/skywatch_2/
	3. [client] ftp 192.168.0.111 8021 (Fixed port: 8021)
	4. [client] usernames (Valid usernames : "ftp","anonymous","public","anon","test","foo","siim")
	5. [client] password (None)
	6. [client] mget /tmp/skywatch_2/*.txt (will copy muti file from remote to local at the same file path)

#refference leet code 44

========================================================================
# Simple ftp server


## How to install:

```
cd to the ftp dir
make
execute with ./ftp
```

## Commands that are currently implemented:

* USER PASS - anonymous ftp only at the moment
* PASV LIST CWD PWD MKD RMD RETR STOR DELE SIZE ABOR QUIT TYPE NOOP

### TODO
* user log in
* get file
* put file
* mkdir, rm, rmdir

Server currently works with linux only because of splice() and sendfile() functions.
It should be easy enough to implement RETR and STOR for other systems too, so it is 
in my todo list.

This server currently doesn't support ASCII mode but this sould not be a
problem with any modern system or ftp client.
