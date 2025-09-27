# Challenge 1 Learning From Documentation:

The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line. This module will mostly dig into that concept, as a proxy for figuring out how to use the programs in general. Through the rest of the module, you'll go through various ways of asking the environment for help for the programs, but first, we'll dig into the concept of reading documentation.

The correct usage of programs depends, in a large part, on the proper specification of arguments to them. Recall the -a of ls -a in the hidden files challenge of the Basic Commands module: that -a was an argument that told ls to list out hidden files as well as non-hidden files. Because we wanted to list out hidden files, invoking ls with the -a argument was the correct way to use it in our scenario.

The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!

Given that knowledge, go get the flag!

## Commands run:

```sh
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{k-qngDTZ8kwkQY5ZJlFybyj3fdu.QX0ITO0wyM5kjNzEzW}
```

## Flag:

```
pwn.college{k-qngDTZ8kwkQY5ZJlFybyj3fdu.QX0ITO0wyM5kjNzEzW}
```

## Solution:
Invoke the challenge/challenge program with the right argument aka --giveflag.

# Challenge 2 Learning Complex Usage:

While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

Here is this level's documentation for /challenge/challenge:

Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Given that documentation, go get the flag!

## Commands run:

```sh
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{wh4fA93uH4KNufubdPRX6NzmEaa.QX1ITO0wyM5kjNzEzW}
```

## Flag:

```
pwn.college{wh4fA93uH4KNufubdPRX6NzmEaa.QX1ITO0wyM5kjNzEzW}
```

## Solution:
Needed to pass a file path in this case flag to the --printfile argument for our /challenge/challenge.

# Challenge 3 Reading Manuals:

This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is a real command):

```sh
hacker@dojo:~$ man yes
This will display the manual page for yes, which will look something like this:

YES(1)                           User Commands                          YES(1)

NAME
       yes - output a string repeatedly until killed

SYNOPSIS
       yes [STRING]...
       yes OPTION

DESCRIPTION
       Repeatedly output a line with all specified STRING(s), or 'y'.

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
       Report any translation bugs to <https://translationproject.org/team/>

COPYRIGHT
       Copyright  ©  2020  Free Software Foundation, Inc.  License GPLv3+: GNU
       GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
       This is free software: you are free  to  change  and  redistribute  it.
       There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation <https://www.gnu.org/software/coreutils/yes>
       or available locally via: info '(coreutils) yes invocation'

GNU coreutils 8.32               February 2022                          YES(1)
The important sections are:

NAME(1)                           CATEGORY                          NAME(1)

NAME
	This gives the name (and short description) of the command or
	concept discussed by the page.

SYNOPSIS
	This gives a short usage synopsis. These synopses have a standard
	format. Typically, each line is a different valid invocation of the
	command, and the lines can be read as:

	COMMAND [OPTIONAL_ARGUMENT] SINGLE_MANDATORY_ARGUMENT
	COMMAND [OPTIONAL_ARGUMENT] MULTIPLE_ARGUMENTS...

DESCRIPTION
	Details of the command or concept, with detailed descriptions
	of the various options.

SEE ALSO
	Other man pages or online resources that might be useful.

COLLECTION                        DATE                          NAME(1)
```

You can scroll around the manpage with your arrow keys and PgUp/PgDn. When you're done reading the manpage, you can hit q to quit.

Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).

The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!

## Commands run:

```sh
hacker@man~reading-manuals:~$ /challenge/challenge 
Incorrect usage! Please read the challenge man page!
hacker@man~reading-manuals:~$ /challenge/challenge --pqnsbe 500
Correct usage! Your flag: pwn.college{AE5pX0O0qWDnAs8beMjDs3_Senl.QX0EDO0wyM5kjNzEzW}
hacker@man~reading-manuals:~$
```

## Flag:

```
pwn.college{AE5pX0O0qWDnAs8beMjDs3_Senl.QX0EDO0wyM5kjNzEzW}
```

## Solution:
Needed to go through the manual of /challenge/challenge, in the manual the correct command with the value to pass in as argument was given to get the flag, doing so
printed the flag.

# Challenge 4 Searching Manuals:
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

Find the option that will give you the flag by reading the challenge man page.

## Commands run:

```sh
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ 
hacker@man~searching-manuals:~$ /challenge/challenge --sx
Initializing...
Correct usage! Your flag: pwn.college{4QJksnF8l3xzoe4nF1PPiWfndi0.QX1EDO0wyM5kjNzEzW}
hacker@man~searching-manuals:~$ 
```

## Flag:

```
pwn.college{4QJksnF8l3xzoe4nF1PPiWfndi0.QX1EDO0wyM5kjNzEzW}
```

## Solution:
First searched for the flag keyword in the manual of challenge, then run that argument to get the flag.
## Notes:
In this question even if were to execute /challenge/challenge --sx 90909 or any random number it will still execute the flag.

# Challenge 5 Searching for Manuals:

This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the manpages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right manpage, read the man page manpage by doing: man man!

HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge

HINT 2: though the manpage is randomly named, you still actually use /challenge/challenge to get the flag!

## Commands run:

```sh
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ 
hacker@man~searching-for-manuals:~$ man -k challenge
snnrlhdwyk (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man snnrlhdwyk
hacker@man~searching-for-manuals:~$ 
hacker@man~searching-for-manuals:~$ /challenge/challenge --snnrlh 909
Correct usage! Your flag: pwn.college{sLKADZnP9Onr0_l9E1hNAO5Hd7Q.QX2EDO0wyM5kjNzEzW}
hacker@man~searching-for-manuals:~$ 
```

## Flag:

```
pwn.college{sLKADZnP9Onr0_l9E1hNAO5Hd7Q.QX2EDO0wyM5kjNzEzW}
```

## Solution:
First opened the manual for man using man man, it showed that -k prints out the manual of any manual page name for a keyword. It then showed a manual which is supposed to print the flag, then I open that manual and search for flag keyword and it showed that snnrlh prints the flag with the correct argument which was also mentioned.

# Challenge 6 Helpful Programs:
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).

In this level, you will practice reading a program's documentation with --help. Try it out!

## Commands run:

```sh
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                            [-g GIVE_THE_FLAG]
                                            [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g
                        option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 316
hacker@man~helpful-programs:~$ /challenge/challenge -g 316
Correct usage! Your flag: pwn.college{Ywh3sHlgeExogUTeb16hPkKoIL4.QX3IDO0wyM5kjNzEzW}
```

## Flag:

```
pwn.college{Ywh3sHlgeExogUTeb16hPkKoIL4.QX3IDO0wyM5kjNzEzW}
```

## Solution:
Needed to use the -p argument to print the required **KEY** and then pass in the key with the -g argument.

# Challenge 7 Help for Builtins:

Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help, as so:

```sh
hacker@dojo:~$ help
```

You can get help on a specific one by passing it to the help builtin. Let's look at a builtin that we've already used earlier, cd!

```sh
hacker@dojo:~$ help cd
cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.
    
    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable.
...
```

Some good information! In this challenge, we'll practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program. Like before, you need to lookup its help to figure out the secret value to pass to it!

## Commands run:

```sh
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune        display a fortune
      --version        display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "YulIATml".
hacker@man~help-for-builtins:~$ /challenge/challenge --secret YulIATml
bash: /challenge/challenge: No such file or directory
hacker@man~help-for-builtins:~$ challenge --secret YulIATml
Correct! Here is your flag!
pwn.college{YulIATmlqGGXf4zpn2H2Vq4ROFr.QX0ETO0wyM5kjNzEzW}
```

## Flag:

```
pwn.college{YulIATmlqGGXf4zpn2H2Vq4ROFr.QX0ETO0wyM5kjNzEzW}
```

## Solution:
First get the list of shell builtins using help, it showed a built in secret which if passed with correct value prints the flag, which it told to be YulIATml.
