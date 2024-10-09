# Perceiving Permissions

## changing file ownership

### In this challenge we learnt how to use chown (**ch**ange **own**ner) command to change the owner of a file

Syntax: chown \[username] \[file]

```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{k532o7cSdj42fALL_GH2G3Dr3Wk.dFTM2QDL1ATN0czW}
```
## groups and files

### In this challenge we learnt how to use chgrp (**ch**ange **gr**oup) command to change the group ownership of a file

```
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{ogXczlmhT06xJGgmRGftUcMboEd.dFzNyUDL1ATN0czW}
```

## fun with group names

### In this challenge we learnt how to use id command to figure out which groups the user is a part of

```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp187) groups=1000(grp187)
hacker@permissions~fun-with-groups-names:~$ chgrp grp187 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{oM6gBlClqjMXutarccCZ4VtnlUr.dJzNyUDL1ATN0czW}
```

## changing permissions

### In this challenge we learnt how to change permissions of a file using chmod (**ch**ange **m**ode) command

Syntax: chmod \[OPTIONS] MODE **FILE**

MODE can be specified as a modification of the existing permissions mode, or as a completely new mode to overwrite the old one

Format of MODE: who +/- what ; who = \[**u**ser/**g**roup/**a**ll] and what = \[**r**ead/**w**rite/e**x**ecute]

Examples:

* u+r adds read access to the user's permissions
* g+wx adds write and execute access to the group's permissions
* o-w removes write access for other users
* a-rwx removes all permissions for the user, group, and world

Approach: flag file is owned by root user and root group and other users have no access to it, we modify it so that other users have read access to it

```
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{Y1XVQ8XzhAoxKywI9maa4ZlLpEW.dNzNyUDL1ATN0czW}
```

## executable files

### In this challenge we learnt how to add executable permissions to a file

Approach: /challenge/run is owned by hacker user without executable permission, we add executable permission to it using `chmod u+x /challenge/run`

```
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jul  4 06:37 /challenge/run
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{4aBcvRLAO-GX2B8d5cUpzDGnYp-.dJTM2QDL1ATN0czW}
```

## permission tweaking practice

