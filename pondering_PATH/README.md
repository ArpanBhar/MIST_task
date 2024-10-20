# Pondering PATH

## The PATH Variable

### In this challenge we learnt about the PATH variable that has the paths to various commands, without the PATH variable, shell won't be able to execute commands like ls, rm etc.

Approach: /challenge/run deletes the flag using the rm command, by blanking out the PATH variable, the /challenge/run command can't access the rm command anymore since it doesn't have the path to it, and thus it gives us the flag

```console
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{korYF6mO9MSWez0XSHlg2UFlqwo.dZzNwUDL1ATN0czW}
```

## Setting PATH

### In this challenge we learnt how to set the PATH variable

Approach: /challenge/run uses a command called win which is in the directory /challenge/more_commands, setting the PATH variable to that directory ensures the shell can find the path of win command

```console
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{UrRh78mOv4QiWLr3I8YEhxF2MZM.dVzNyUDL1ATN0czW}
```

## Adding Commands

### In this challenge we learnt how to add our own commands to the PATH variable

Approach: 

* Make a shell executable called win which invokes the command "cat /flag"
* Add the path of that executable to the PATH variable
* Run /challenge/run

```console
hacker@path~adding-commands:~$ echo "cat /flag" > win
hacker@path~adding-commands:~$ chmod u+x win
hacker@path~adding-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{MZnCgWbo8_OA3XPbjuitkiiLDV9.dZzNyUDL1ATN0czW}
```

## Hijacking Commands

### Approach:

* The /challenge/run command invokes rm to delete the flag
* Create a new executable called rm in /home/hacker, this executable will contain commands to show us the flag
* Set PATH variable as /home/hacker
* Now when the /challenge/run command tries to invoke rm, it'll run our executable instead

```console
hacker@path~hijacking-commands:~$ echo "read var < /flag;echo \$var" > rm
hacker@path~hijacking-commands:~$ chmod u+x rm
hacker@path~hijacking-commands:~$ PATH=/home/hacker
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{4jWi2IsD6GEbvaR8z8TTp4rRq0O.ddzNyUDL1ATN0czW}
```