# Pondering Paths

## The Root

### In this challenge we learnt about root directory of linux

The linux filesystem starts with / and paths are written like /path

```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{srML2na9eBxkqC6s7crOyjwqoFW.dhzN5QDL1ATN0czW}
```

## Program and absolute paths

### In this challenge we learnt about the usage of absolute path in linux filesystem

Absolute path = /path/filename

```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{sCAegtJwNO4izJ5VBka4ZjJIxlq.dVDN1QDL1ATN0czW}
```

## Position thy self

### In this challenge we learnt how to navigate the linux filesystem

We have to use cd (change directory) command

```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ ls
l
hacker@paths~position-thy-self:~$ cd ..
hacker@paths~position-thy-self:/home$ ls
hacker
hacker@paths~position-thy-self:/home$ cd ..
hacker@paths~position-thy-self:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~position-thy-self:/$ cd var
hacker@paths~position-thy-self:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{IyoNLl8rhcX_xHnBIBW4NYHFgLB.dZDN1QDL1ATN0czW}
```

## Position elsewhere

```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/build-essential directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd ..
hacker@paths~position-elsewhere:/home$ cd ..
hacker@paths~position-elsewhere:/$ cd /usr/share/
hacker@paths~position-elsewhere:/usr/share$ cd build-essential/
hacker@paths~position-elsewhere:/usr/share/build-essential$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{wDD4pF29AnaUrPoi5V_wJpSu6h-.ddDN1QDL1ATN0czW}
hacker@paths~position-elsewhere:/usr/share/build-essential$
```

## Position yet elsewhere

```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /tmp directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd ..
hacker@paths~position-yet-elsewhere:/home$ cd ..
hacker@paths~position-yet-elsewhere:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~position-yet-elsewhere:/$ cd tmp
hacker@paths~position-yet-elsewhere:/tmp$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{Ez8_AxfNFncsbn26mL8s_xILEL-.dhDN1QDL1ATN0czW}
```

## implicit relative paths, from /

### In this challenge we learnt about the usage of relative paths

Relative paths are given without / and are relative to the current working directory

```
hacker@paths~implicit-relative-paths-from-:~$ cd ..
hacker@paths~implicit-relative-paths-from-:/home$ cd ..
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0jPPwuB7aRyCNgEzRFByIsoNQjj.dlDN1QDL1ATN0czW}
```

## explicit relative paths, from /

### In this challenge we learn the use of explicit relative paths

. refers to the same directory and .. refers to the parent directory

1. challenge
2. ./challenge
3. ./././challenge
4. challenge/.

are all identical to each other

```
hacker@paths~explicit-relative-paths-from-:~$ ls
l
hacker@paths~explicit-relative-paths-from-:~$ cd ..
hacker@paths~explicit-relative-paths-from-:/home$ ls
hacker
hacker@paths~explicit-relative-paths-from-:/home$ cd ..
hacker@paths~explicit-relative-paths-from-:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Q9KcPYZP8WjuPZQFqmHpU2fRlDi.dBTN1QDL1ATN0czW}
```

## implicit relative path

Linux doesn't allow the use of "naked" relative paths to run anything as safety measure so that we don't accidentally run core system commands trying to run our program and vice versa, therefore we have to use explicit relative paths to execute the commands while still using relative paths

```
hacker@paths~implicit-relative-path:~$ cd ..
hacker@paths~implicit-relative-path:/home$ cd ..
hacker@paths~implicit-relative-path:/$ cd challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{YRy_p8u2KeocsKb9Q49tWGPIsQz.dFTN1QDL1ATN0czW}
```

## home sweet home

In linux we'll often work in our home directory so linux provides a shorthand method to mention the absolute path of home directory using "~" symbol

```
hacker@paths~home-sweet-home:~$ /challenge/run ~/l
Writing the file to /home/hacker/l!
... and reading it back to you:
pwn.college{A8prEDPYQQIWQdtgvpVZvFhYP0V.dNzM4QDL1ATN0czW}
```