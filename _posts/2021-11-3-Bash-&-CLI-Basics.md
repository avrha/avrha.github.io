---
title: Bash & CLI Basics
published: true
---

Bash is the default Unix shell installed on the majority of Linux distributions. Like any other shell, Bash uses a command-line interface (CLI) so its users can utilize the operating system. Therefore, knowledge of Bash's CLI is necessary for working with most Linux systems. This post covers the basics of Bash and the shell's CLI. 

## Command Overview
Before diving into Bash specifics, here is a quick summary of some useful Unix-like commands. 
- ``` pwd ``` prints the working directory. (The directory the user is currently in).
- ``` ls ``` lists directory contents. 
- ``` cd ``` change directory, used to move around the filesystem.
-  ``` cat ``` concatenate files and print standard output (stdout).
- ``` grep ``` search for patterns in a file using regex. 
- ``` find ``` search for files within a filesystem. 
- ``` file ``` determine file type.
- ``` sort ``` sort lines in a text file.

## Special Characters
Bash evaluates some characters to have a non-literal meaning when typed in the command line. These characters carry out a *special* instruction in the shell are called **special characters**, and can modify the function of a command.  

### ``` . ``` Home Directory
A period ```. ``` represents the current directory. Typically periods are used in relative and absolute paths. For example, if a user wanted to run a script from the current directory, they would run the file like this:

```
./script.sh
```
This tells Bash to look in the current directory for the ``` script.sh ``` file. 
### ``` .. ``` Parent Directory
The double period or double dot ``` .. ``` represents the parent directory of the current directory. ``` .. ``` is used to move up one level in the directory tree.

```
cd ..
```
![Double Dot](photos/Bash&CLI/doubledot.png)

### ``` / ``` Path Separator
Forward slash ``` / ```, often called slash, separates the directories in a pathname. Used for absolute and relative paths. 

![Slash 1](photos/Bash&CLI/slash.png)

### ``` * ``` Character Sequence Wildcard
The use case of the wildcard ``` * ``` stands for any *sequence* of characters, including *no characters*. Consider the following :
```
ls track*
```

This matches all of the following:
![ls-1](photos/Bash&CLI/ls-1.png)

The wildcard matches any file with the string before it. The wildcard can also match any file with the string after it.
```
ls *.flac
```
![Slash 2](photos/Bash&CLI/slash-2.png)

## Arguments, Options and Parameters
A *command* is split into an array of strings named **arguments**. Normally, argument 0 is the command name. Argument 1 is the first element following argument 0, and so on.

```
#long list all files in /tmp and /var/tmp
$ ls -la /tmp /var/tmp 
arg0 = ls
arg1 = -la
arg2 = /tmp
arg3 = /var/tmp
```

An **option** is a type of *argument* modifying the behavior of a *command*. For example ``` -l ``` commonly means "long", ``` -a ``` means "all". ``` -la ``` are *two* options combined in a *single* argument.

```
$ ls -la /tmp /var/tmp
option1= -l
option2= -a
```

A [parameter](https://en.wikipedia.org/wiki/Parameter#Computing) is an argument that provides information to either the *command* or one of its options. For example in ``` -o file ```, *file* is the parameter of the ``` -o ``` option. Unlike options, parameters are not hardcoded. Bash does this so users are free to use whatever string suits their needs.

```
$ ls -la /tmp /var/tmp
parameter1= /tmp
parameter2= /var/tmp
```