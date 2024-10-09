# File Globbing

## matching with *

### In this challenge we learnt about how linux shell treats * as a "wildcard" and will try to replace * with whatever matches the pattern

```console
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /c*
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{EpSet7kfKRXmcjYhrJCEWaNgGXf.dFjM4QDL1ATN0czW}
```

## matching with ?

### In this challenge we learnt ? works similar to * but only replaces a single character to match the pattern

```console
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{IIsGfYHUW34Bnpc_zJ17if4nd37.dJjM4QDL1ATN0czW}
```

## matching with []

### [] works like ? but enables us to give option to replace only with the characters present in the brackets

```console
hacker@globbing~matching-with-:~$ cd /challenge/files/
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{I5MROQ-aISNtvt8cZWZzPOlf0Jm.dNjM4QDL1ATN0czW}
```

## matching paths with []

```console
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{keBZUu9aZ5Y2QMnPo7a16s3OyiY.dRjM4QDL1ATN0czW}
```

## mixing globs

Approach: Take the first letter and put it in [] glob and use * glob to replace whatever matches the pattern

```console
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{kp-1byAODN0Isbq3Wi97UKneY9u.dVjM4QDL1ATN0czW}
```

## exclusionary globbing

### In this challenge, we learnt that when we use ! or ^ before the elements inside, the linux shell will invert the globbing, i.e it'll look for elements that do not match the pattern inside []

```console
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{g2nGSfr2DtOd2cj1xovo-HwTOeO.dZjM4QDL1ATN0czW}
```