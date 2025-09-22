# Challenge 1 Intro to Commands

In this challenge, you will invoke your first command! When you type a command and hit enter, the command will be invoked, as so:

```sh
hacker@dojo:~$ whoami
hacker
hacker@dojo:~$
```

Here, the user executed the whoami command, which simply prints the username (hacker) to the terminal. When the command terminates, the shell once again displays the prompt, ready for the next command.

In this level, invoke the hello command to get the flag! Keep in mind: commands in Linux are case sensitive: hello is different from HELLO.

## Solution:
Just need to enter hacker(invokes the hacker command present in the hacker(~) directory)

## Commands ran:
```sh
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{Ag08Q_HagSo-ZcmwkhOTnmdqz2r.QX3YjM1wyM5kjNzEzW}
```

## Flag: 

```
pwn.college{Ag08Q_HagSo-ZcmwkhOTnmdqz2r.QX3YjM1wyM5kjNzEzW}
```
### Notes:
There are different users and in this problem we the user were the hacker 
and ~ just represents the hacker's home directory aka (/home/user)

## Challenge 2 Intro to Arguments
Let's try something more complicated: a command with arguments, which is what we call additional data passed to the command. When you type a line of text and hit enter, the shell actually parses your input into a command and its arguments. The first word is the command, and the subsequent words are arguments. Observe:

```sh
hacker@dojo:~$ echo Hello
Hello
hacker@dojo:~$
In this case, the command was echo, and the argument was Hello. echo is a simple command that "echoes" all of its arguments back out onto the terminal, like you see in the session above.
```

Let's look at echo with multiple arguments:
```sh
hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
hacker@dojo:~$
```
In this case, the command was echo, and Hello and Hackers! were the two arguments to echo. Simple!
In this challenge, to get the flag, you must run the hello command (NOT the echo command) with a single argument of hackers. Try it now!

## Solution:
Need to invoke hello command with the hackers argument

##Commands ran:
```sh
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{YrQjYn36zhC2UniALgNvXE32Yq-.QX4YjM1wyM5kjNzEzW}
```

## Flag:
pwn.college{YrQjYn36zhC2UniALgNvXE32Yq-.QX4YjM1wyM5kjNzEzW}

### Notes:
Leart about how there can be commands for eg echo was given, in case of the problem it was hello and we pass in arguments for that.

##Challenge 3 Command History:
You're going to type a lot of commands, and typing everything from scratch can be annoying. Luckily, the shell saves a history of every command you invoke.

You can scroll through those saved commands with the up/down arrow keys, and we'll practice that in this challenge. This challenge will inject the flag into your history. Bring up a terminal, hit the up arrow, and grab it! In other challenges, the history will contain the log of the commands you've run, so if you need to run a similar command again, you can use the arrow keys to scroll through and find it!

## Solution:
Need to traverse the terminal history, the server injected the flag in my terminal history
so I just needed to press up key a few times to pop it out.

## Commands ran:
```sh
hacker@hello~command-history:~$ the flag is pwn.college{wSLeeHhbYJB3LaV41bQnsrbepqZ.0lNzEzNxwyM5kjNzEzW}
bash: the: command not found
```
#Flag:
pwn.college{wSLeeHhbYJB3LaV41bQnsrbepqZ.0lNzEzNxwyM5kjNzEzW}

### Notes:
Just terminal history, nothing more in particular

