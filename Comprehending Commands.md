# Challenge 1 cat: not the pet, but the command! :
One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:
cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:

```sh
hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!
```

Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with cat!

## Commands ran:

```sh
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{4VCvDFs6JrZBQGdgpP417GDE4zE.QXxcTN0wyM5kjNzEzW}
hacker@commands~cat-not-the-pet-but-the-command:~$ 
```
## Flag:

```
pwn.college{4VCvDFs6JrZBQGdgpP417GDE4zE.QXxcTN0wyM5kjNzEzW}
```

## Solution:
Just needed to read the file without executing it!

# Challenge 2 catting absolute paths:
In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's arguments as absolute paths:

```sh
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
```

In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:
...
In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.

FUN FACT: /flag is where the flag always lives in pwn.college, but unlike in this challenge, you typically can't access that file directly.

## Commands ran:

```sh
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{MmRCCQY_Zd7Cwj27nwSgXiFTpa7.QX5ETO0wyM5kjNzEzW}
hacker@commands~catting-absolute-paths:~$ cd ..
hacker@commands~catting-absolute-paths:/home$ cf /
bash: cf: command not found
hacker@commands~catting-absolute-paths:/home$ cd /
hacker@commands~catting-absolute-paths:/$ cat flag
pwn.college{MmRCCQY_Zd7Cwj27nwSgXiFTpa7.QX5ETO0wyM5kjNzEzW}
hacker@commands~catting-absolute-paths:/$ 
```

## Flag:

```
pwn.college{MmRCCQY_Zd7Cwj27nwSgXiFTpa7.QX5ETO0wyM5kjNzEzW}
```

## Solution:
Had to call the absolute path while reading the file

## Notes:
I also tried calling it relatively by going to the root directory and it worked as well
hence this time they weren't checking which directory your reading flag from.


# Challenge 3  more catting practice:

You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must retrieve the flag by absolute path, wherever it is.

## Commands ran:

```sh
hacker@commands~more-catting-practice:~$ ls -a
.   .ICEauthority  .cache   .dbus   .mozilla  Downloads
..  .bash_history  .config  .local  Desktop   f
hacker@commands~more-catting-practice:~$ ls -aa /
.           bin        dev   lib    libx32  nix   root  srv  usr
..          boot       etc   lib32  media   opt   run   sys  var
.dockerenv  challenge  home  lib64  mnt     proc  sbin  tmp
hacker@commands~more-catting-practice:~$ ls -a /challenge
.  ..  .bashrc  .hide_flag  .init  DESCRIPTION.md  run
hacker@commands~more-catting-practice:~$ cat /challenge/.hide_flag
#!/opt/pwn.college/bash

if [ -f /tmp/.flag-path ]
then
	read OLD_PATH < /tmp/.flag-path
else
	OLD_PATH=/
fi

read NEW_PATH < <(dirname $(su -c "ls -d /{usr,lib,bin,opt}/{,*,*/*}/." hacker | sort -R | head -n1))
mv "$OLD_PATH/flag" "$NEW_PATH/flag"
echo "$NEW_PATH" > /tmp/.flag-path
hacker@commands~more-catting-practice:~$ cat /tmp/.flag
cat: /tmp/.flag: No such file or directory
hacker@commands~more-catting-practice:~$ ls -a /temp
ls: cannot access '/temp': No such file or directory
hacker@commands~more-catting-practice:~$ cat /challenge/run
#!/bin/bash

fold -s < /challenge/DESCRIPTION.md
hacker@commands~more-catting-practice:~$ /challenge/run
You can specify all sorts of paths as arguments to commands, and we'll practice 
some more with `cat`.
In this level, I'll put the flag in some crazy directory, and I will not allow 
you to change directories with `cd`, so no `cat flag` for you.
You must retrieve the flag by absolute path, wherever it is.
hacker@commands~more-catting-practice:~$ ls -a /tmp
.  ..  .ICE-unix  .X0-lock  .X11-unix  .crates.toml  .crates2.json  .dojo  .flag-path  .xfsm-ICE-B61QD3  bin  dbus-7fkJoWVsbj  hsperfdata_root  ssh-XXXXXXZGPiuV  tmp.TpSOPGOVKK
hacker@commands~more-catting-practice:~$ /tmp/.flag-path
bash: /tmp/.flag-path: Permission denied
hacker@commands~more-catting-practice:~$ cat /tmp/.flag-path
/usr/share/terminfo
hacker@commands~more-catting-practice:~$ ls -a
.  ..  .ICEauthority  .bash_history  .cache  .config  .dbus  .local  .mozilla  Desktop  Downloads  f
hacker@commands~more-catting-practice:~$ ls -Desktop
ls: invalid option -- 'e'
Try 'ls --help' for more information.
hacker@commands~more-catting-practice:~$ ls Desktop
hacker@commands~more-catting-practice:~$ ls Downloads
hacker@commands~more-catting-practice:~$ ls .local
share
hacker@commands~more-catting-practice:~$ ls /
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~more-catting-practice:~$ ls -
ls: cannot access '-': No such file or directory
hacker@commands~more-catting-practice:~$ ls /
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~more-catting-practice:~$ ls /home
hacker
hacker@commands~more-catting-practice:~$ ls /home/hacker
Desktop  Downloads  f
hacker@commands~more-catting-practice:~$ cat f
pwn.college{Aoo7r0qnkL_tdOs6iFknDgbjMFR.QXzMDO0wyM5kjNzEzW}
hacker@commands~more-catting-practice:~$ ls /challenge
DESCRIPTION.md  run
hacker@commands~more-catting-practice:~$ cat /challenge/DESCRIPTION.md
You can specify all sorts of paths as arguments to commands, and we'll practice some more with `cat`.
In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with `cd`, so no `cat flag` for you.
You must retrieve the flag by absolute path, wherever it is.
hacker@commands~more-catting-practice:~$ cat /usr/share/terminfo
cat: /usr/share/terminfo: Is a directory
hacker@commands~more-catting-practice:~$ ls /usr/share/terminfo
flag
hacker@commands~more-catting-practice:~$ cat /usr/share/terminfo/flag
pwn.college{wbLTvBLz0TlQtKVyn4KuWfPnPCA.QXwITO0wyM5kjNzEzW}
```

## Flag:

```
pwn.college{wbLTvBLz0TlQtKVyn4KuWfPnPCA.QXwITO0wyM5kjNzEzW}
pwn.college{Aoo7r0qnkL_tdOs6iFknDgbjMFR.QXzMDO0wyM5kjNzEzW}

```

## Solution:
I kind of messed around with the hidden files and found a .hide_flag file in challenge
Then when I read it it showed me the new path for flag which was /tmp/.flag-path
On reading that file it gave me an directory location.
On reading that directory gives me a flag but the interesting thing is if I listed the files in /home/hacker it showed me another flag 
SO THERE WERE 2 flags and both of them were accepted as right.

# Challenge 4 grepping for a needle in a haystack:

Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! We'll learn it in this challenge.
There are many ways to grep, and we'll learn one way here:

```sh
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
```

Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.
In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!
HINT: The flag always starts with the text pwn.college.

## Commands ran:

```sh
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{YG8yuCPnJz4CWmCClWiKE1vP9eQ.QX3EDO0wyM5kjNzEzW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ 
```

## Flag:
```
pwn.college{YG8yuCPnJz4CWmCClWiKE1vP9eQ.QX3EDO0wyM5kjNzEzW}
```

## Solution:
Just needed to search for the initials of the flag in the data.txt file using grep command.

# Challenge 5 Comparing Files:
When looking for changes between similar files, eyeballing them might not be the most efficient approach! This is where the diff command becomes invaluable.

diff compares two files line by line and shows you exactly what's different between them. For example:

```sh
hacker@dojo:~$ cat file1
hello
world
hacker@dojo:~$ cat file2
hello
universe
hacker@dojo:~$ diff file1 file2
2c2
< world
---
> universe
```

The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the second file (>).

Sometimes, when new lines are added, you'll see something like:

```sh
hacker@dojo:~$ cat old
pwn
hacker@dojo:~$ cat new
pwn
college
hacker@dojo:~$ diff old new
1a2
> college
```

This tells us that after line 1 in the first file, the second file has an additional line (1a2 means "after line 1 of file1, add line 2 of file2").

Now for your challenge! There are two files in /challenge:

### /challenge/decoys_only.txt contains 100 fake flags
### /challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag
Use diff to find what's different between these files and get your flag!

## Commands ran:

```sh
hacker@commands~comparing-files:~$ cd /challenge
hacker@commands~comparing-files:/challenge$ diff decoys_only decoys_and_real
diff: decoys_only: No such file or directory
diff: decoys_and_real: No such file or directory
hacker@commands~comparing-files:/challenge$ diff decoys_only.txt decoys_and_real.txt
29a30
> pwn.college{YcLAv3Y10E1zefErTQuaqX06svl.01MwMDOxwyM5kjNzEzW}
hacker@commands~comparing-files:/challenge$
```

## Flag:
```
pwn.college{YcLAv3Y10E1zefErTQuaqX06svl.01MwMDOxwyM5kjNzEzW}
```
## Solution:
Needed to compare both text files and the difference in text was the flag.

## Note:
Realised I need to specific with even the file extension, name is not enough.

# Challenge 6 Listing Files:


So far, we've told you which files to interact with. But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:

```sh
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
```

In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.


## Commands run:

```sh
hacker@commands~listing-files:~$ ls /challenge
17107-renamed-run-15566  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/17107-renamed-run-15566
Yahaha, you found me! Here is your flag:
pwn.college{AmN2MvZZOiBsjTeZ1xQVA6bZtXW.QX4IDO0wyM5kjNzEzW}
hacker@commands~listing-files:~$ 
```

## Flag:
```
pwn.college{AmN2MvZZOiBsjTeZ1xQVA6bZtXW.QX4IDO0wyM5kjNzEzW}
```
## Solution:
Needed to list the files present in challenge directory.

# Challenge 7 Touching Files :
Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:

```sh
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ touch pwnfile
hacker@dojo:/tmp$ ls
pwnfile
hacker@dojo:/tmp$
```

It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!


## Commands run:

```sh                                                                 
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{s7LN-hybifP0-cYb_cHa6P3gYoB.QXwMDO0wyM5kjNzEzW}
hacker@commands~touching-files:~$ 
```

## Flag:
```
pwn.college{s7LN-hybifP0-cYb_cHa6P3gYoB.QXwMDO0wyM5kjNzEzW}
```

## Solution:
Needed to create two files one is pwn in tmp directory and one is college in the same tmp directory and then just execute run as the conditions for the challenge are met.

# Challenge 8 removing files:
Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:

```sh
hacker@dojo:~$ touch PWN
hacker@dojo:~$ touch COLLEGE
hacker@dojo:~$ ls
COLLEGE     PWN
hacker@dojo:~$ rm PWN
hacker@dojo:~$ ls
COLLEGE
hacker@dojo:~$
```

Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!


## Commands run:

```sh
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{Qdrkx1L2qqEIjRDG5EllotwYo3a.QX2kDM1wyM5kjNzEzW}
hacker@commands~removing-files:~$ 
```

## Flag:

```
pwn.college{Qdrkx1L2qqEIjRDG5EllotwYo3a.QX2kDM1wyM5kjNzEzW}
```

## Solution:
Just needed to remove the delete_me files using rm.

# Challenge 9 Moving Files:
You can also move files around with the mv command. The usage is simple:

```sh
hacker@dojo:~$ ls
my-file
hacker@dojo:~$ cat my-file
PWN!
hacker@dojo:~$ mv my-file your-file
hacker@dojo:~$ ls
your-file
hacker@dojo:~$ cat your-file
PWN!
hacker@dojo:~$
```

This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /challenge/check, which will check things out and give the flag to you.


## Commands run:

```sh
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{MVojCP_yrerIQv--385DPQKP1pk.0VOxEzNxwyM5kjNzEzW}
```
## Flag:

```
pwn.college{MVojCP_yrerIQv--385DPQKP1pk.0VOxEzNxwyM5kjNzEzW}
```

## Solution:
Needed to move the file to hack-the-planet directory.


# Challenge 10 Hidden Files:

Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:

```sh
hacker@dojo:~$ touch pwn
hacker@dojo:~$ touch .college
hacker@dojo:~$ ls
pwn
hacker@dojo:~$ ls -a
.college	pwn
hacker@dojo:~$
```

Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.


## Commands run:

```sh
hacker@commands~hidden-files:~$ ls -a /
.                      bin        etc    lib64   nix   run   tmp
..                     boot       home   libx32  opt   sbin  usr
.dockerenv             challenge  lib    media   proc  srv   var
.flag-113841419625071  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:~$ cat /.flag-113841419625071
pwn.college{I03HT-2SxWg9aWmRA8_hzrNzPaq.QXwUDO0wyM5kjNzEzW}
hacker@commands~hidden-files:~$ 
```
## Flag:

```
pwn.college{I03HT-2SxWg9aWmRA8_hzrNzPaq.QXwUDO0wyM5kjNzEzW}
```
## Solution:
Needed to list the hidden files in the root directory then run the file starting with flag.

## Notes:
Just like file extensions need to mention . as well while working with them through the temrinal!

# Challenge 11 An Epic Filesystem Quest:

With your knowledge of cd, ls, and cat, we're ready to play a little game!

We'll start it out in /. Normally:

```sh
hacker@dojo:~$ cd /
hacker@dojo:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr
```

That's a lot of contents! One day, you will be quite familiar with them, but already, you might recognize the flag file and the challenge directory.

In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:

Your first clue is in /. Head on over there.
Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
cat that file to read the clue!
Depending on what the clue says, head on over to the next directory (or don't!).
Follow the clues to the flag!

## Commands run:

```sh
hacker@commands~an-epic-filesystem-quest:~$ ls -a /
.  ..  .dockerenv  TEASER  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~an-epic-filesystem-quest:~$ cat /TEASER
Tubular find!
The next clue is in: /usr/include/x86_64-linux-gnu/c++/9/bits

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:~$ cd /usr/include/x86_64-linux-gnu/c++/9/bits
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ ls -a
.     atomic_word.h   c++config.h  cpu_defines.h   cxxabi_tweaks.h    gthr-default.h  gthr.h              os_defines.h  time_members.h
..    basic_file.h    c++io.h      ctype_base.h    error_constants.h  gthr-posix.h    messages_members.h  stdc++.h
MEMO  c++allocator.h  c++locale.h  ctype_inline.h  extc++.h           gthr-single.h   opt_random.h        stdtr1c++.h
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ cat MEMO
Lucky listing!
The next clue is in: /usr/share/locale/gu/LC_MESSAGES
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ ls -a /usr/share/locale/gu/LC_MESSAGES
.  ..  HINT  iso_3166-1.mo  iso_3166-3.mo  iso_3166.mo  iso_639-2.mo  iso_639-3.mo  iso_639.mo  iso_639_3.mo
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ cat /usr/share/locale/gu/LC_MESSAGES/HINT
Tubular find!
The next clue is in: /usr/share/racket/pkgs/redex-doc/redex/scribblings/long-tut/code

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ ls -a /usr/share/racket/pkgs/redex-doc/redex/scribblings/long-tut/code
.              close.rkt   delivered-mon-aft.rkt  delivered-wed-aft.rkt      extend-lookup.rkt  lab-tue-mor.rkt  tc-common.rkt  wed-aft.rkt
..             common.rkt  delivered-tue-aft.rkt  delivered-wed-mor-exn.rkt  lab-mon-aft.rkt    lab-wed-mor.rkt  tue-aft.rkt    wed-mor.rkt
TRACE-TRAPPED  compiled    delivered-tue-mor.rkt  delivered-wed-mor.rkt      lab-tue-aft.rkt    mon-aft.rkt      tue-mor.rkt
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ cat /usr/share/racket/pkgs/redex-doc/redex/scribblings/long-tut/code/TRACE-TRAPPED
Tubular find!
The next clue is in: /opt/linux/linux-5.4/drivers/dma
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ ^C
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ ls -a /opt/linux/linux-5.4/drivers/dma
.                 acpi-dma.c       built-in.a       dw                 fsldma.c       iop-adma.h        moxart-dma.c   pl330.c        st_fdma.h          tegra210-adma.c   xilinx
..                acpi-dma.o       coh901318.c      dw-axi-dmac        fsldma.h       ipu               mpc512x_dma.c  ppc4xx         ste_dma40.c        ti                zx_dma.c
.acpi-dma.o.cmd   altera-msgdma.c  coh901318.h      dw-edma            hsu            k3dma.c           mv_xor.c       pxa_dma.c      ste_dma40_ll.c     timb_dma.c
.built-in.a.cmd   amba-pl08x.c     coh901318_lli.c  ep93xx_dma.c       idma64.c       lpc18xx-dmamux.c  mv_xor.h       qcom           ste_dma40_ll.h     txx9dmac.c
.dmaengine.o.cmd  at_hdmac.c       dma-axi-dmac.c   fsl-edma-common.c  idma64.h       mcf-edma.c        mv_xor_v2.c    s3c24xx-dma.c  stm32-dma.c        txx9dmac.h
.virt-dma.o.cmd   at_hdmac_regs.h  dma-jz4780.c     fsl-edma-common.h  img-mdc-dma.c  mediatek          mxs-dma.c      sa11x0-dma.c   stm32-dmamux.c     uniphier-mdmac.c
DISPATCH          at_xdmac.c       dmaengine.c      fsl-edma.c         imx-dma.c      mic_x100_dma.c    nbpfaxi.c      sh             stm32-mdma.c       virt-dma.c
Kconfig           bcm-sba-raid.c   dmaengine.h      fsl-qdma.c         imx-sdma.c     mic_x100_dma.h    of-dma.c       sirf-dma.c     sun4i-dma.c        virt-dma.h
Makefile          bcm2835-dma.c    dmaengine.o      fsl_raid.c         ioat           mmp_pdma.c        owl-dma.c      sprd-dma.c     sun6i-dma.c        virt-dma.o
TODO              bestcomm         dmatest.c        fsl_raid.h         iop-adma.c     mmp_tdma.c        pch_dma.c      st_fdma.c      tegra20-apb-dma.c  xgene-dma.c
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ cat /opt/linux/linux-5.4/drivers/dma/DISPATCH
Tubular find!
The next clue is in: /usr/lib/x86_64-linux-gnu/libcanberra-0.30

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/include/x86_64-linux-gnu/c++/9/bits$ cd /usr/lib/x86_64-linux-gnu/libcanberra-0.30
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/libcanberra-0.30$ ls -a
.  ..  README  libcanberra-alsa.so
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/libcanberra-0.30$ cat README
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/arch/riscv

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/libcanberra-0.30$ ls -a /opt/linux/linux-5.4/arch/riscv
.  ..  BRIEF-TRAPPED  Kbuild  Kconfig  Kconfig.debug  Kconfig.socs  Makefile  boot  configs  include  kernel  lib  mm  net
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/libcanberra-0.30$ cat /opt/linux/linux-5.4/arch/riscv/BRIEF-TRAPPED
Lucky listing!
The next clue is in: /opt/busybox/busybox-1.33.2/include/config/feature/suid/config

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/libcanberra-0.30$ ls -a /opt/busybox/busybox-1.33.2/include/config/feature/suid/config
.  ..  .CUE  quiet.h
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/libcanberra-0.30$ cat /opt/busybox/busybox-1.33.2/include/config/feature/suid/config/.CUE
Tubular find!
The next clue is in: /usr/share/iptables

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/libcanberra-0.30$ ls -a /usr/share/iptables
.  ..  ALERT-TRAPPED  iptables.xslt
hacker@commands~an-epic-filesystem-quest:/usr/lib/x86_64-linux-gnu/libcanberra-0.30$ cat /usr/share/iptables/ALERT-TRAPPED
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{8BZnF-T1gyFD0NvTsHRgXQiYURm.QX5IDO0wyM5kjNzEzW}
```
## Flag:

```
pwn.college{8BZnF-T1gyFD0NvTsHRgXQiYURm.QX5IDO0wyM5kjNzEzW}
```
## Solution:
Needed to follow all the hidden clues to get to the flag finally.

# Challenge 12 Making Directories:
We can create files. How about directories? You make directories using the mkdir command. Then you can stick files in there!

Watch:
```sh
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ mkdir my_directory
hacker@dojo:/tmp$ ls
my_directory
hacker@dojo:/tmp$ cd my_directory
hacker@dojo:/tmp/my_directory$ touch my_file
hacker@dojo:/tmp/my_directory$ ls
my_file
hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
/tmp/my_directory/my_file
hacker@dojo:/tmp/my_directory$
```

Now, go forth and create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag!
## Commands run:

```sh
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{wFtlxjmN_gu1ltV5ded3M7IksjO.QXxMDO0wyM5kjNzEzW}
hacker@commands~making-directories:~$ 
```
## Flag:
```
pwn.college{wFtlxjmN_gu1ltV5ded3M7IksjO.QXxMDO0wyM5kjNzEzW}
```

## Solution:
Same thing as the make file using touch challenge just instead of touch we used mkdir to make a directory instead of file.

# Challenge 13 Finding Files:
So now we know how to list, read, and create files. But how do we find them? We use the find command!

The find command takes optional arguments describing the search criteria and the search location. If you don't specify a search criteria, find matches every file. If you don't specify a search location, find uses the current working directory (.). For example:

```sh
hacker@dojo:~$ mkdir my_directory
hacker@dojo:~$ mkdir my_directory/my_subdirectory
hacker@dojo:~$ touch my_directory/my_file
hacker@dojo:~$ touch my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find
.
./my_directory
./my_directory/my_subdirectory
./my_directory/my_subdirectory/my_subfile
./my_directory/my_file
hacker@dojo:~$
```

And when specifying the search location:

```sh
hacker@dojo:~$ find my_directory/my_subdirectory
my_directory/my_subdirectory
my_directory/my_subdirectory/my_subfile
hacker@dojo:~$
```

And, of course, we can specify the criteria! For example, here, we filter by name:

```sh
hacker@dojo:~$ find -name my_subfile
./my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find -name my_subdirectory
./my_directory/my_subdirectory
hacker@dojo:~$
```

You can search the whole filesystem if you want!

```sh
hacker@dojo:~$ find / -name hacker
/home/hacker
hacker@dojo:~$
```

Now it's your turn. I've hidden the flag in a random directory on the filesystem. It's still called flag. Go find it!

Several notes. First, there are other files named flag on the filesystem. Don't panic if the first one you try doesn't have the actual flag in it. Second, there're plenty of places in the filesystem that are not accessible to a normal user. These will cause find to generate errors, but you can ignore those; we won't hide the flag there! Finally, find can take a while; be patient!

## Commands run:

```sh
```sh
hacker@commands~finding-files:~$ find / -name flag
find: ‘/tmp/tmp.4mK6TfTSUV’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/root’: Permission denied
/opt/linux/linux-5.4/tools/perf/util/include/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/nix/store/ka6xbd6z6wj5d6frl7ym4nzfc6p2wkdx-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/f31j0igg7ms3yrj5gm3cm76bjcmdl8w5-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/n6vb30rd7kkwjj595pgm0dmsmfaqi6i5-rizin-0.7.3/share/rizin/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/8qvj9mzdq2qxgjigw4ysqgbkcx1zi80y-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/dz2qxywk6d8hc1gkarpwbhyxb50sh2ak-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
hacker@commands~finding-files:~$ cat /nix/store/dz2qxywk6d8hc1gkarpwbhyxb50sh2ak-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
cat: /nix/store/dz2qxywk6d8hc1gkarpwbhyxb50sh2ak-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /opt/linux/linux-5.4/tools/perf/util/include/flag
pwn.college{Q8Dvugvwg5ljcEKlwSI641yyK2T.QXyMDO0wyM5kjNzEzW}
```
## Flag:

```
pwn.college{Q8Dvugvwg5ljcEKlwSI641yyK2T.QXyMDO0wyM5kjNzEzW}
```

## Solution:
Searched the entire root for file named flag a lot of valid paths showed up but I ran the second one and its flag got accepted.

# Challenge 14 Linking Files:

If you use Linux (or computers) for any reasonable length of time to do any real work, you will eventually run into some variant of the following situation: you want two programs to access the same data, but the programs expect that data to be in two different locations. Luckily, Linux provides a solution to this quandary: links.

Links come in two flavors: hard and soft (also known as symbolic) links. We'll differentiate the two with an analogy:

A hard link is when you address your apartment using multiple addresses that all lead directly to the same place (e.g., Apt 2 vs Unit 2).
A soft link is when you move apartments and have the postal service automatically forward your mail from your old place to your new place.
In a filesystem, a file is, conceptually, an address at which the contents of that file live. A hard link is an alternate address that indexes that data --- accesses to the hard link and accesses to the original file are completely identical, in that they immediately yield the necessary data. A soft/symbolic link, instead, contains the original file name. When you access the symbolic link, Linux will realize that it is a symbolic link, read the original file name, and then (typically) automatically access that file. In most cases, both situations result in accessing the original data, but the mechanisms are different.

Hard links sound simpler to most people (case in point, I explained it in one sentence above, versus two for soft links), but they have various downsides and implementation gotchas that make soft/symbolic links, by far, the more popular alternative.

In this challenge, we will learn about symbolic links (also known as symlinks). Symbolic links are created with the ln command with the -s argument, like so:

```sh
hacker@dojo:~$ cat /tmp/myfile
This is my file!
hacker@dojo:~$ ln -s /tmp/myfile /home/hacker/ourfile
hacker@dojo:~$ cat ~/ourfile
This is my file!
hacker@dojo:~$
```

You can see that accessing the symlink results in getting the original file contents! Also, you can see the usage of ln -s. Note that the original file path comes before the link path in the command!

A symlink can be identified as such with a few methods. For example, the file command, which takes a filename and tells you what type of file it is, will recognize symlinks:

```sh
hacker@dojo:~$ file /tmp/myfile
/tmp/myfile: ASCII text
hacker@dojo:~$ file ~/ourfile
/home/hacker/ourfile: symbolic link to /tmp/myfile
hacker@dojo:~$
```

Okay, now you try it! In this level the flag is, as always, in /flag, but /challenge/catflag will instead read out /home/hacker/not-the-flag. Use the symlink, and fool it into giving you the flag!

## Commands run:

```sh
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{o7m0VqJdeCUsLXIeRRgfwiGvjQZ.QX5ETN1wyM5kjNzEzW}
hacker@commands~linking-files:~$
```
## Flag

```
pwn.college{o7m0VqJdeCUsLXIeRRgfwiGvjQZ.QX5ETN1wyM5kjNzEzW}
```

## Solution:
On running catflag it was executing not-the-flag so to overcome this I linked not-the-flag file to the flag so when it was being executed by the catflag it instead refered to the flag hence it ran.
