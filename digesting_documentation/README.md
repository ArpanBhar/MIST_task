# Digesting Documentation

## learning from documentation

### In this challenge we learnt about documentation of commands in linux

```console
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{AYqfjbvI8gFBfAro2hVqzDEpzXs.dRjM5QDL1ATN0czW}
```

## learning complex usage

### In this challenge we learnt about arguments which themselves take arguments

```console
hacker@man~learning-complex-usage:/$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{Mw7o0aNHTB6RWP7nIcSEWXa31m2.dVjM5QDL1ATN0czW}
```

## reading manuals

### In this challenge we learn about manpages of commands

Approach: Reading the man page of the challenge command, we get the method to extract flag

```console
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                                      Challenge Commands                                     CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --mbqvaa NUM
              print the flag if NUM is 868

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)
hacker@man~reading-manuals:~$ /challenge/challenge --mbqvaa 868
Correct usage! Your flag: pwn.college{8YN6KmWb8Y9qHVvAaaPYhLgcpzt.dRTM4QDL1ATN0czW}
```

## searching manuals

### In this challenge we learnt how to search for keywords within man pages.

Approach: go to man page of challenge then search for the keyword "flag"

```console
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge  --yzrkl
Initializing...
Correct usage! Your flag: pwn.college{4XY26uCj9AsBgBeBzdhTvWh0fiB.dVTM4QDL1ATN0czW}
```

## searching for manuals

### In this challenge we learn how to find the manpage of something using keyword

Resources used: Youtube, to figure out how to navigate man pages properly

Approach: go to the man page of man command to find a flag that enables us to search for a manpage containing a specific keyword ("flag" in this case)

```console
hacker@man~searching-for-manuals:~$ /challenge/challenge  --kekbst 868
Correct usage! Your flag: pwn.college{k8ekb6sHtfJxZtABZB8DKSYGgHE.dZTM4QDL1ATN0czW}
```

## helpful programs

Approach: Use the -h flag of challenge to get the help page of challenge function, which has instructions to get the flag

```console
hacker@man~helpful-programs:~$ /challenge/challenge -h
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 366
hacker@man~helpful-programs:~$ /challenge/challenge -g 366
Correct usage! Your flag: pwn.college{wSyAqNX3TVNlmgWRAwcUym66ay1.ddjM4QDL1ATN0czW}
```

## help for builtins

Approach: Here challenge is a shell builtin, we use help command to see the manual for challenge command and get the flag

```console
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "43zdZ-mI".
hacker@man~help-for-builtins:~$ challenge --secret 43zdZ-mI
Correct! Here is your flag!
pwn.college{43zdZ-mIF2L0SxCgP2KQSag8Oct.dRTM5QDL1ATN0czW}
```