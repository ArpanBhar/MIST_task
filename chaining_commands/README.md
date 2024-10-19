# Chaining Commands

## Chaining with semicolons

### In this challenge we learnt that we can chain commands using semicolons

```console
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{gry78tWez54VyO3r1NnOxD6Cl-0.dVTN4QDL1ATN0czW}
```

## Your first shell script

### In this challenge we learnt what shells scripts are and how to use them

```console
hacker@chaining~your-first-shell-script:~$ echo "/challenge/pwn;/challenge/college">x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{ooH6Ax5G8sspXJb3fuEli0ghR9E.dFzN4QDL1ATN0czW}
```

## Redirecting Script Output

### In this challenge we learnt how to redirect the output of several programs to one commands

We just redirect the output of the bash script to the command

```console
hacker@chaining~redirecting-script-output:~$ printf "/challenge/pwn\n/challenge/college\n" > x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{kRG55mjlXYrv92ngbVzd4QoPWGf.dhTM5QDL1ATN0czW}
```

## Executable shell scripts

### In this challenge we learnt how to run a shell script without using the bash command

To do that we have to add executable permission to the file

```console
hacker@chaining~executable-shell-scripts:~$ echo /challenge/solve > x.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x ./x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{sBBmmthTwFT9_yf2bjVLh_45oEr.dRzNyUDL1ATN0czW}
```