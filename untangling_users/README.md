# Untangling Users

## Becoming root with su

### In this challenge we learnt about the su ("s"witch "u"ser) command which has the SUID bit which enables it to spawn a root shell

```console
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{8AVqgjYDsXT8n51IeAq0NI0Dedl.dVTN0UDL1ATN0czW}
```

## Other users with su

### By default with no arguments su command switches to root user but we can also switch to some other user using the command

```console
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{sRXlPjPz863m8Tt3TTyLNFZiwXO.dZTN0UDL1ATN0czW}
```

## Cracking passwords

### In this module we learnt about John-the-ripper programme that can be used to crack passwords

The passwords of users are stored in a file, /etc/shadow, whenever we enter password in su command, it checks the password from this file, the passwords are one-way encrypted (hashed) and stored in the file, the su command also hashes the password we input and then compares both the hashes, if they match, the entered password was correct and it grants access (since, hashing produces same output for same input). We can use John-The-Ripper programme to decrypt the hashed password from this file and get the actual password.

```console
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04943g/s 287.8p/s 287.8c/s 287.8C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{0PS_qr6Q9zYtTal-XACEoN8RllW.ddTN0UDL1ATN0czW}
```

## Using sudo

### In this challenge we learnt about the use of sudo command

Instead of relying on passwords, sudo ("su"peruser "do") relies on policies that it checks to determine the user's authorization run things as root. These policies are defined in /etc/sudoers. Unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root.

```console
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{ACOUHbabEvB5WUtHkdJJwwgTTQx.dhTN0UDL1ATN0czW}
```