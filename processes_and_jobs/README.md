# Processes and Jobs

## listing processes

### In this module we learnt about the ps command which is used to list out ongoing processes

Syntax: 

It has two syntax, standard and BSD.

* Standard: ps -ef, the "e" means list out "e"very process and "f" means to do it in "f"ull format
* BSD: ps aux, "a" means to list processes for "a"ll users, "u" means to do it in a "u"ser readable format and "x" means to list the processes that aren't running in the terminal

```
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 04:43 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /ru
root           7       1  0 04:43 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 04:43 ?        00:00:00 /challenge/7887-run-17771
root          72      68  0 04:43 ?        00:00:00 sleep 6h
hacker        73       0  0 04:44 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        92      73  0 04:45 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/7887-run-17771
Yahaha, you found me! Here is your flag:
pwn.college{oGV_s-XfpRyDSVfM-8cOetcGXOd.dhzM4QDL1ATN0czW}
Now I will sleep for a while (so that you could find me with 'ps')
```

## killing processes

### In this module we learnt about the kill command which is used to stop processes

```
hacker@processes~killing-processes:~$ ps -ef|grep dont_run
hacker        73      71  0 05:02 ?        00:00:00 /challenge/dont_run
hacker        95      75  0 05:04 pts/0    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ ps -ef|grep dont_run
hacker        97      75  0 05:04 pts/0    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{gu0FGrZLSWUSyvROtrwUoMi3-j2.dJDN4QDL1ATN0czW}
```

## interrupting processes

### In this module we learnt how Ctrl + C interrupts any ongoing process that is waiting for an input from the terminal

```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{EPSxc7fx-epBU03Ft2LnFmQeSjQ.dNDN4QDL1ATN0czW}
```

## suspending processes

### In this module we learnt about the usage of Ctrl + Z to suspend a process to the background

```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 05:08 pts/0    00:00:00 bash /challenge/run
root          84      82  0 05:08 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 05:08 pts/0    00:00:00 bash /challenge/run
root          89      65  0 05:08 pts/0    00:00:00 bash /challenge/run
root          91      89  0 05:08 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{0GRrkngd7PTZqlaljo-1hkBU5o-.dVDN4QDL1ATN0czW}
```

## resuming processes

### In this module we learnt about the fg command which puts a suspended process running in the background to the terminal again

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{8zx5eYhX0XM5Tosgs3hYZayTRKa.dZDN4QDL1ATN0czW}
Don't forget to press Enter to quit me!

Goodbye!
```

## backgrounding processes

### In this module we learnt about the bg command which sends a process to the background and keeps it running there (not suspended)

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root          93 S+   bash /challenge/run
root          95 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{USUSxa33Z9WK_6mEYS4cMos6D-j.ddDN4QDL1ATN0czW}
```

## foregrounding process

### In this module we learnt that the fg command can also bring back a process that was backgrounded

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



hacker@processes~foregrounding-processes:~$ Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{YJS7_6ikMgNANKJTBdgVwRIyfRJ.dhDN4QDL1ATN0czW}
```

## starting backgrounded process

### In this challenge we learnt how to start a process in the background right off the bat by appending a "&" after the command

```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 82



hacker@processes~starting-backgrounded-processes:~$ Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{8Re1ISgc0eMWC3QhAYXP2_-A4K7.dlDN4QDL1ATN0czW}

[1]+  Done                    /challenge/run
```

## process exit codes

### In this challenge we learnt how we can retrieve exit codes of the most recently terminated process using echo $? command

```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
92
hacker@processes~process-exit-codes:~$ /challenge/submit-code 92
CORRECT! Here is your flag:
pwn.college{AJI8uXnuCzDKyd3dOSKVKeSOCeU.dljN4UDL1ATN0czW}
```