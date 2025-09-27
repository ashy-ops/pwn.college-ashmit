# Challenge 1 The Root:

Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to as an "absolute path".

Start the challenge, launch a terminal, invoke the pwn program using its absolute path, and Capture that Flag! Good luck!

## Commands ran:

```sh
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{ckA-irVxwRuIbS05DU7_Ri_Vb7m.QX4cTO0wyM5kjNzEzW}
```
## Flag:

```
pwn.college{ckA-irVxwRuIbS05DU7_Ri_Vb7m.QX4cTO0wyM5kjNzEzW}
```

## Notes:
Just need to run the pwn file that is under the root directory using the absolute path, I tried invoking it later after changing directory to root and invoking it relatively
but the challenge doesn't allow that.

# Challenge 2 Program and absolute paths:

Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge directory is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

This challenge again requires you to execute it by invoking its absolute path. You'll want to execute the run file that is in the challenge directory that is, in turn, in the / directory. If you invoke the challenge correctly, it will give you the flag. Good luck!

## Commands ran:

```sh
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{E5hG1bjl2BNcHvrli_SjMdraSeA.QX1QTN0wyM5kjNzEzW}
```

## Flag:

```
pwn.college{E5hG1bjl2BNcHvrli_SjMdraSeA.QX1QTN0wyM5kjNzEzW}
```
## Notes:
Same as previous but an added directory.

# Challenge 3 Position thy self:
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

```sh
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.
```

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

## Commands ran:

```sh
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /home directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /home
hacker@paths~position-thy-self:/home$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{MEW8iptWw_A616IzB-Yc_xvK2vl.QX2QTN0wyM5kjNzEzW}
```

## Flag:

```
pwn.college{MEW8iptWw_A616IzB-Yc_xvK2vl.QX2QTN0wyM5kjNzEzW}
```
## Notes:

The run program also returns the flag when ran by the absolute path while being in the correct directory

# Challenge 4 Position elsewhere:

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

```sh
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

## Commands ran:

```sh
chacker@paths~position-elsewhere: $ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory. Please use the 'cd` utility to change directory appropriately. hacker@paths~position-elsewhere:~$ cd Chacker@paths~position-elsewhere: ~$ ls
Desktop Downloads
hacker@paths~position-elsewhere: $ cd .. 
hacker@paths~position-elsewhere: /home$ ls hacker
-hacker@paths~position-elsewhere: /home$ cd hacker
hacker@paths~position-elsewhere:~$ cd /var/lib/apt/lists
hacker@paths-position-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{ESCt1IKA_xqRs-grn5kL15_3kVz.QX3QTN0wyM5kjNzEzW} hacker@paths~position-elsewhere:/var/lib/apt/lists$
```
## Flag:
```
pwn.college{ESCt1IKA_xqRs-grn5kL15_3kVz.QX3QTN0wyM5kjNzEzW} hacker@paths~position-elsewhere:/var/lib/apt/lists$
```

## Solution:
Just had to invoke the absolute path from the right directory

# Challenge 5:

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

```sh
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.
```

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

## Commands ran:

```sh
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /home directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /home
hacker@paths~position-yet-elsewhere:/home$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{kUik-eKKBfkqU0adT-Y0RPbxmnH.QX4QTN0wyM5kjNzEzW}
```

## Flag:
```
pwn.college{kUik-eKKBfkqU0adT-Y0RPbxmnH.QX4QTN0wyM5kjNzEzW}
```
## Solution:
Had to invoke it from the right directory which was given /home in this case

# Challenge 6 implicit relative paths, from /
Now you're familiar with the concept of referring to absolute paths and changing directories. If you put in absolute paths everywhere, then it really doesn't matter what directory you are in, as you likely found out in the previous three challenges.

However, the current working directory does matter for relative paths.

A relative path is any path that does not start at root (i.e., it does not start with /).
A relative path is interpreted relative to your current working directory (cwd).
Your cwd is the directory that your prompt is currently located at.
This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at /tmp/a/b/my_file.

If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
If my cwd is /tmp, then a relative path to the file is a/b/my_file.
If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.
Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /. For this level, I'll give you a hint. Your relative path starts with the letter c 😊

## Commands run:

```sh
hacker@paths~implicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~implicit-relative-paths-from-:~$ challenge/run
bash: challenge/run: No such file or directory
hacker@paths~implicit-relative-paths-from-:~$ cd challenge
bash: cd: challenge: No such file or directory
hacker@paths~implicit-relative-paths-from-:~$ cd /challenge
hacker@paths~implicit-relative-paths-from-:/challenge$ challenge/run
bash: challenge/run: No such file or directory
hacker@paths~implicit-relative-paths-from-:/challenge$ run
bash: run: command not found
hacker@paths~implicit-relative-paths-from-:/challenge$ cd ..
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{I2kCzhW_PLf8oCJUNJssY9OTscJ.QX5QTN0wyM5kjNzEzW}
hacker@paths~implicit-relative-paths-from-:/$ cat challenge/run
#!/opt/pwn.college/bash

NEEDED="/"

if [ "$PWD" != "$NEEDED" ]
then
	echo -e "${COLOR_RED}Incorrect...${COLORLESS}"
	echo "You are not currently in the $NEEDED directory."
	echo 'Please use the `cd` utility to change directory appropriately.'
	exit 1
fi

if [ "${0:0:1}" == "/" ]
then
	echo -e "${COLOR_RED}Incorrect...${COLORLESS}"
	echo "You invoked this challenge with an absolute path. This challenge needs a relative path!"
	exit 1
fi

if [ "${0:0:1}" == "." ]
then
	echo -e "${COLOR_RED}Incorrect...${COLORLESS}"
	echo "This challenge must be invoked with a relative path that starts with a letter!"
	exit 1
fi

echo -e "${COLOR_GREEN}Correct!!!${COLORLESS}"
echo "$0 is a relative path, invoked from the right directory!"
echo "Here is your flag:"
/bin/cat /flag
hacker@paths~implicit-relative-paths-from-:/$ ls -a
.           bin        dev   home   lib64   mnt  proc  sbin  tmp
..          boot       etc   lib    libx32  nix  root  srv   usr
.dockerenv  challenge  flag  lib32  media   opt  run   sys   var
hacker@paths~implicit-relative-paths-from-:/$ cat bin/flag
cat: bin/flag: No such file or directory
hacker@paths~implicit-relative-paths-from-:/$ cat flag
cat: flag: Permission denied
hacker@paths~implicit-relative-paths-from-:/$ /bin/cat /flag
/bin/cat: /flag: Permission denied
```

## Flag:
```
pwn.college{I2kCzhW_PLf8oCJUNJssY9OTscJ.QX5QTN0wyM5kjNzEzW}
```
## Solution:
This time needed to change the directory and call the RELATIVE PATH instead of absolute!

## Notes:
Tried to run the hidden flag file manually just to experiment but it didn't give anything as permission denied.
Got The flag files location by reading the /challenge/run

# Challenge 7 explicit-relative-paths,from / :
Previously, your relative path was "naked": it directly specified the directory to descend into from the current directory. In this level, we're going to explore more explicit relative paths.

In most operating systems, including Linux, every directory has two implicit entries that you can reference in paths: . and ... The first, ., refers right to the same directory, so the following absolute paths are all identical to each other:

/challenge
/challenge/.
/challenge/./././././././././
/./././challenge/././
The following relative paths are also all identical to each other:

challenge
./challenge
./././challenge
challenge/.
Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute paths.

This challenge will get you using . in your relative paths. Get ready!

## Commands run:

```sh                                                                 
hacker@paths~explicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{UNawHjhg_SeTR7LktrMt7mkanKK.QXwUTN0wyM5kjNzEzW}
hacker@paths~explicit-relative-paths-from-:/$ cd challenge
hacker@paths~explicit-relative-paths-from-:/challenge$ ./run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~explicit-relative-paths-from-:/challenge$ 
```

## Flag:
```
pwn.college{UNawHjhg_SeTR7LktrMt7mkanKK.QXwUTN0wyM5kjNzEzW}
```

## Solution:
. refers to the current directory so instead of calling for /challenge/run i just need to call ./challenge/run where . still refers to the root directory
which I think should techincally be equivalent to the absolute path.

# Challenge 8 implicit relative path:
In this level, we'll practice referring to paths using . a bit more. This challenge will need you to run it from the /challenge directory. Here, things get slightly tricky.

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:

```sh
hacker@dojo:~$ cd /challenge
hacker@dojo:/challenge$ run
```

This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:

```sh
bash: run: command not found
```
We'll explore the mechanisms behind this concept later, but in this challenge, we'll learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels. Give it a try now!

## Commands run:

```sh
hacker@paths~implicit-relative-path:~$ cd /
hacker@paths~implicit-relative-path:/$ cd challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{4Nyb_qFnFw_jF_OZ_MeVm0dvXIQ.QXxUTN0wyM5kjNzEzW}
```

## Flag:

```
pwn.college{4Nyb_qFnFw_jF_OZ_MeVm0dvXIQ.QXxUTN0wyM5kjNzEzW}
```

## Solution:
Same concept as the last question but instead of doing it from the root directory we did it from the challenge directory here . refers to the challenge directory.


# Challenge 9 home sweet home:
Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user, and your home directory is /home/hacker. The home directory is typically where users store most of their personal files. As you make your way through pwn.college, this is where you'll store most of your solutions.

Typically, your shell session will start with your home directory as your current working directory. Consider the initial prompt:

```sh
hacker@dojo:~$
```

The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker. Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. Thus, whenever bash sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home directory. Consider:

```sh
hacker@dojo:~$ echo LOOK: ~
LOOK: /home/hacker
hacker@dojo:~$ cd /
hacker@dojo:/$ cd ~
hacker@dojo:~$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~
hacker@dojo:~$ cd /home/hacker/asdf
hacker@dojo:~/asdf$
```

Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that ~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.

Fun fact: cd will use your home directory as the default destination:

```sh
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ cd
hacker@dojo:~$
```

Now it's your turn to play! In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

Your argument must be an absolute path.
The path must be inside your home directory.
Before expansion, your argument must be three characters or less.
Again, you must specify your path as an argument to /challenge/run as so:

```sh
hacker@dojo:~$ /challenge/run YOUR_PATH_HERE
```

## Commands run:

```sh
hacker@paths~home-sweet-home:~$ ls-a
bash: ls-a: command not found
hacker@paths~home-sweet-home:~$ ls -a
.   .ICEauthority  .cache   .dbus   .mozilla  Downloads
..  .bash_history  .config  .local  Desktop
hacker@paths~home-sweet-home:~$ cd
hacker@paths~home-sweet-home:~$ /challenge /run ~/f
bash: /challenge: Is a directory
hacker@paths~home-sweet-home:~$ /challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{Aoo7r0qnkL_tdOs6iFknDgbjMFR.QXzMDO0wyM5kjNzEzW}
```
## Flag:

```
pwn.college{Aoo7r0qnkL_tdOs6iFknDgbjMFR.QXzMDO0wyM5kjNzEzW}
```
## Solution:
needed to write a file in the /challenge/run I named it f and since I wrote the file it detected it and wrote back the flag to me.

```
pwn.college{Aoo7r0qnkL_tdOs6iFknDgbjMFR.QXzMDO0wyM5kjNzEzW}
```

## Notes:
I tried to see if in this also there was some hidden flag file in root though there was no use for me running that as permission would be denied.
