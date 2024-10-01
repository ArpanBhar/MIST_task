# Comprehending Commands

## cat: not the pet, but the command!

### cat is used to read out files and it will concatenate the data of files and output them if multiple arguments are given

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{UKNO4IIIyeQbbt0kkRvxchGKAir.dFzN1QDL1ATN0czW}
```

## catting absolute paths

```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{AVSKIYfxzxvUrYchCHpJCKTXQ7f.dlTM5QDL1ATN0czW}
```

## more catting practice

```
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /opt/tcpdump/tests/flag. Go cat it out **without** cding into that
directory!
hacker@commands~more-catting-practice:~$ cat /opt/tcpdump/tests/flag
pwn.college{k37_2lwTBTCROe-Uc3yXxwUxSk5.dBjM5QDL1ATN0czW}
```

## grepping for a needle in a haystack

### In this challenge we learnt about the grep command which is used to search for a line of text which contains a particular string

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{IL7vyhuKo4_2odDdOkLyFW7JpLw.ddTM4QDL1ATN0czW}
```

## listing files

### In this challenge we learnt about the ls command

ls will list all the files and folders in the specified directory

```
hacker@commands~listing-files:~$ ls /challenge
28331-renamed-run-13080  DESCRIPTION.md
hacker@commands~listing-files:~$ cd /challenge
hacker@commands~listing-files:/challenge$ ./28331-renamed-run-13080
Yahaha, you found me! Here is your flag:
pwn.college{4JxAvhZ71w3BsdiB_nttVPLE5Ot.dhjM4QDL1ATN0czW}
```

## touching files

### In this challenge we create a blank file using the touch command

```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{AdL0QW-O8mYAdiyUzLz6bEpizD5.dBzM4QDL1ATN0czW}
```

## removing files

### In this challenge we learn how to remove a file using the rm command

```
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{MI-RXVOWlSV3kxTgcPlxhwSSeLX.dZTOwUDL1ATN0czW}
```

## hidden files

### In linux, the ls command doesn't show the files starting with . to see those files too we use the -a flag

```
hacker@commands~hidden-files:~$ ls -a
.  ..  .bash_history  .bash_logout  .bashrc  .profile  l
hacker@commands~hidden-files:~$ cd ..
hacker@commands~hidden-files:/home$ ls -a
.  ..  hacker
hacker@commands~hidden-files:/home$ cd ..
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv             bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-263722491024356  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat .flag-263722491024356
pwn.college{wmoIWtMk5qUJT0bXALZdcjZzmRs.dBTN4QDL1ATN0czW}
```

## An Epic Filesystem Quest

### In this challenge we had to follow the clues step-by-step which led to the flag

```
hacker@commands~an-epic-filesystem-quest:/$ ls
SECRET  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin     challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.   .dockerenv  bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
..  SECRET      boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@commands~an-epic-filesystem-quest:/$ cat SECRET
Yahaha, you found me!
The next clue is in: /opt/busybox/busybox-1.33.2/testsuite/bunzip2
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/busybox/busybox-1.33.2/testsuite/bunzip2
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/testsuite/bunzip2$ ls
SNIPPET  bunzip2-reads-from-standard-input  bunzip2-removes-compressed-file
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/testsuite/bunzip2$ cat SNIPPET
Great sleuthing!
The next clue is in: /opt/aflplusplus/qemu_mode/qemuafl/docs/specs

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/testsuite/bunzip2$ cd  /opt/aflplusplus/qemu_mode/qemuafl/docs/specs
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/qemu_mode/qemuafl/docs/specs$ ls
MEMO                         acpi_nvdimm.txt       nvme.txt               ppc-spapr-numa.rst       standard-vga.txt
_templates                   acpi_pci_hotplug.txt  pci-ids.txt            ppc-spapr-uv-hcalls.txt  tpm.rst
acpi_cpu_hotplug.txt         edu.txt               pci-serial.txt         ppc-spapr-xive.rst       vmcoreinfo.txt
acpi_hest_ghes.rst           fw_cfg.txt            pci-testdev.txt        ppc-xive.rst             vmgenid.txt
acpi_hw_reduced_hotplug.rst  index.rst             ppc-spapr-hcalls.txt   pvpanic.txt              vmw_pvscsi-spec.txt
acpi_mem_hotplug.txt         ivshmem-spec.txt      ppc-spapr-hotplug.txt  rocker.txt
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/qemu_mode/qemuafl/docs/specs$ cat MEMO
Tubular find!
The next clue is in: /usr/lib/ruby/gems/2.7.0/gems/readline-ext-0.1.0

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/qemu_mode/qemuafl/docs/specs$ cd /usr/lib/ruby/gems/2.7.0/gems/readline-ext-0.1.0
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/readline-ext-0.1.0$ ls
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/readline-ext-0.1.0$ ls -a
.  ..  .WHISPER
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/readline-ext-0.1.0$ cat .WHISPER
Great sleuthing!
The next clue is in: /opt/capstone/suite/MC/SystemZ

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/readline-ext-0.1.0$ cat /opt/capstone/suite/MC/SystemZ
cat: /opt/capstone/suite/MC/SystemZ: Is a directory
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/readline-ext-0.1.0$ ls /opt/capstone/suite/MC/SystemZ
NOTE-TRAPPED  insn-good-z196.s.cs  insn-good.s.cs  regs-good.s.cs
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/readline-ext-0.1.0$ cat /opt/capstone/suite/MC/SystemZ/NOTE-TRAPPED
Lucky listing!
The next clue is in: /opt/radare2/libr/flag

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/readline-ext-0.1.0$ cd  /opt/radare2/libr/flag
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ ls
LEAD  Makefile  d  flag.c  flag.d  flag.o  libr_flag.so  meson.build  tags.c  tags.d  tags.o  zones.c  zones.d  zones.o
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ cat LEAD
Yahaha, you found me!
The next clue is in: /opt/angr-management/_internal/angr/procedures/win_user32

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ cat /opt/angr-management/_internal/angr/procedures/win_user32/
GIST-TRAPPED   __init__.py    __pycache__/   chars.py       keyboard.py    messagebox.py
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ cat /opt/angr-management/_internal/angr/procedures/win_user32/
GIST-TRAPPED   __init__.py    __pycache__/   chars.py       keyboard.py    messagebox.py
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ cat /opt/angr-management/_internal/angr/procedures/win_user32/
GIST-TRAPPED   __init__.py    __pycache__/   chars.py       keyboard.py    messagebox.py
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ cat /opt/angr-management/_internal/angr/procedures/win_user32/GIST-TRAPPED
Great sleuthing!
The next clue is in: /usr/share/docutils/parsers/rst/include

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ cat /usr/share/docutils/parsers/rst/include/
README.txt          isoamsr.txt         isogrk3.txt         isomopf-wide.txt    mmlalias.txt
REVELATION-TRAPPED  isobox.txt          isogrk4-wide.txt    isomopf.txt         mmlextra-wide.txt
isoamsa.txt         isocyr1.txt         isogrk4.txt         isomscr-wide.txt    mmlextra.txt
isoamsb.txt         isocyr2.txt         isolat1.txt         isomscr.txt         s5defs.txt
isoamsc.txt         isodia.txt          isolat2.txt         isonum.txt          xhtml1-lat1.txt
isoamsn.txt         isogrk1.txt         isomfrk-wide.txt    isopub.txt          xhtml1-special.txt
isoamso.txt         isogrk2.txt         isomfrk.txt         isotech.txt         xhtml1-symbol.txt
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ cat /usr/share/docutils/parsers/rst/include/REVELATION-TRAPPED
Tubular find!
The next clue is in: /usr/share/racket/pkgs/typed-racket-lib/typed

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ cat /usr/share/racket/pkgs/typed-racket-lib/typed/.
./    ../   .CUE
hacker@commands~an-epic-filesystem-quest:/opt/radare2/libr/flag$ cat /usr/share/racket/pkgs/typed-racket-lib/typed/.CUE
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{AoeNPUaSCCyOSQ5WPlA1W3Cx9DP.dljM4QDL1ATN0czW}
```

## making directories

### In this challenge we learn how to make directories using the mkdir command

```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{UQZ90a3kr36DI33d9pLmbzuyRwp.dFzM4QDL1ATN0czW}
```

## finding files

### In this challenge we learnt about the find command of linux terminal

Approach: Use the find command with name parameter = flag, use hit and trial to see which one is correct

```
hacker@commands~finding-files:~$ cd /
hacker@commands~finding-files:/$ find -name flag
find: ‘./root’: Permission denied
find: ‘./etc/ssl/private’: Permission denied
find: ‘./tmp/tmp.G9qthVCks5’: Permission denied
./usr/local/share/radare2/5.9.5/flag
./usr/local/lib/python3.8/dist-packages/pwnlib/flag
./usr/share/javascript/mathjax/unpacked/localization/es/flag
find: ‘./var/cache/apt/archives/partial’: Permission denied
find: ‘./var/cache/ldconfig’: Permission denied
find: ‘./var/cache/private’: Permission denied
find: ‘./var/log/private’: Permission denied
find: ‘./var/log/apache2’: Permission denied
find: ‘./var/log/mysql’: Permission denied
find: ‘./var/lib/apt/lists/partial’: Permission denied
find: ‘./var/lib/mysql-keyring’: Permission denied
find: ‘./var/lib/php/sessions’: Permission denied
find: ‘./var/lib/private’: Permission denied
find: ‘./var/lib/mysql-files’: Permission denied
find: ‘./var/lib/mysql’: Permission denied
find: ‘./run/mysqld’: Permission denied
find: ‘./run/sudo’: Permission denied
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/1/task/1/fd’: Permission denied
find: ‘./proc/1/task/1/fdinfo’: Permission denied
find: ‘./proc/1/task/1/ns’: Permission denied
find: ‘./proc/1/fd’: Permission denied
find: ‘./proc/1/map_files’: Permission denied
find: ‘./proc/1/fdinfo’: Permission denied
find: ‘./proc/1/ns’: Permission denied
find: ‘./proc/7/task/7/fd’: Permission denied
find: ‘./proc/7/task/7/fdinfo’: Permission denied
find: ‘./proc/7/task/7/ns’: Permission denied
find: ‘./proc/7/fd’: Permission denied
find: ‘./proc/7/map_files’: Permission denied
find: ‘./proc/7/fdinfo’: Permission denied
find: ‘./proc/7/ns’: Permission denied
./opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
./opt/radare2/libr/flag
./nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
./nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:/$ cat ./usr/local/share/radare2/5.9.5/flag
cat: ./usr/local/share/radare2/5.9.5/flag: Is a directory
hacker@commands~finding-files:/$ cat ./usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: ./usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:/$ cat ./usr/share/javascript/mathjax/unpacked/localization/es/flag
pwn.college{4dCF7Ks5fTwwOTq3lwSFSXYTI92.dJzM4QDL1ATN0czW}
```

## linking files

### In this challenge, we learnt about symlinks in linux, symlinks are created using ln -s source_file destination_file

Approach: The /challenge/catflag program reads out /home/hacker/not-the-flag, so we have to create a symlink of /flag to /home/hacker/not-the-flag to trick the system into giving the flag

```
hacker@commands~linking-files:/$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:/$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{4hPW8keCcC0aeEu5L0fP04O2Giy.dlTM1UDL1ATN0czW}
```