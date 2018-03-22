---
title: "Install VisualStudioCode on Raspberry Pi"
last_modified_at: 2018-03-22T19:17:05-05:00
categories: 
  - Raspberry Pi
tags:
  - Raspberry Pi
  - Raspbian
  - SSH
---

## Setting up

First, use this command to check your ssh status:
```
$ sudo service ssh status
```
If it's running, you'll see something like `sshd[2222] Server Listening on :: port 22`.
Otherwise, it will shows `Active: inactive(dead)`

In this case, you need to open ssh from the settings by this :
```
$ sudo raspi-config
```
It shows settings of Raspbian, 
Select `Interfacing Options` >> `P2 SSH` >>
```
Would you like to start SSH ?
>> YES <<
```
Then come back to terminal use the first command again `$ sudo service ssh status` and it should be up and running.

## Connecting

- **You can NOT logged via ssh with default password** :
The default password for user `pi` is `raspberry`, you must change it now, using `$ passwd`

- Run the sshd :

```
$ sudo service ssh status
```
-  Connection :
```
$ ssh pi@192.168.7.148
...
(yes/no)? $ yes
```
-  Success !
```
Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Thu Mar 22 19:27:40 2018 from 192.168.7.148
pi@raspberrypi:~ $
```

