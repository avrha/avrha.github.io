---
title: Bash & CLI Basics
published: true
---

Bash is the default Unix shell installed on the majority of Linux distributions. Like any other shell, Bash uses a command-line interface (CLI) so its users can utilize the operating system. Therefore, knowledge of Bash's CLI is necessary for working with most Linux systems. This post covers the basics of Bash and the shell's CLI. 

## Command Overview
Before diving into Bash specifics, here is a quick summary of some useful Unix-like commands. 
- ```pwd``` prints the working directory. (The directory the user is currently in).
- ```ls``` lists directory contents. 
- ```cd``` change directory, used to move around the filesystem.
-  ```cat``` concatenate files and print standard output (stdout).
- ```grep``` search for patterns in a file using regex. 
- ```find``` search for files within a filesystem. 
- ```file``` determine file type.
- ```sort``` sort lines in a text file.
- ```date``` print or set the system date and time.

## Special Characters
Bash evaluates some characters to have a non-literal meaning when typed in the command line. These characters carry out a *special* instruction in the shell are called **special characters**, and can modify the function of a command.  

### ```.``` Current Directory
A period ```.``` represents the current directory. Typically periods are used in relative and absolute paths. For example, if a user wanted to run a script from the current directory, they would run the file like this:

```
./script.sh
```
This tells Bash to look in the current directory for the ```script.sh``` file. 
### ```..``` Parent Directory
The double period or double dot ```..``` represents the parent directory of the current directory. ```..``` is used to move up one level in the directory tree.

```
cd ..
```
![Double Dot](photos/Bash&CLI/doubledot.png)

### ```/``` Path Separator
Forward slash ```/```, often called slash, separates the directories in a pathname.

![Slash 1](photos/Bash&CLI/slash.png)

### ```*``` Wildcard
The wildcard ```*``` matches any number of characters based upon its placement in a string. Consider the following:

```
ls track*
```
Matches all characters with the string *track* before ```*```

![ls-1](photos/Bash&CLI/ls-1.png)

```
ls *.flac
```
Matches all characters with the string *.flac* after ```*```

![Slash 2](photos/Bash&CLI/slash-2.png)

The wildcard character ``` * ``` is often used in file searches so the full name does not need to be typed.

### ```<```  Input Operator
The input redirector pulls data in a stream from a given source. Usually, programs receive their data from the keyboard. However, data can be pulled from another source, like a file.

Let's use the ```sort``` command as an example. The file ```fruits.txt``` contains the following lines:

```
watermelon
cantaloupe
honeydew
apple
banana
``` 
Notice the fruit is not in alphabetical order. A user can pull the data from the file into the ``` sort ``` command by using the ``` < ``` operator.

![input-redirect](photos/Bash&CLI/input-redirect.png)

### ``` < ``` Output Operator
The output redirector ``` > ``` redirects a program's output to somewhere else. In this case, I'm going to redirect the results to a file named time.txt.

![output-redirect](photos/Bash&CLI/output-redirect.png)

Please note, the ``` > ``` redirector outputs overwrites any existing data in a file. You can use the ``` >> ``` redirector to append any new changes to a file.

### ``` | ``` Pipe Operator
The pipe operator ``` | ``` is one of my favorite operators. The pipe takes the output of the first command and makes it the input of the second command. Let's say a user wants to list all directories and files in the ``` /etc ``` directory. They know that's going to be a long list and that most of the output will scroll off the top of the screen. The ``` less ``` command will break the output into pages, and the user can scroll upward or downward through the results.   

![Pipe](photos/Bash&CLI/pipe.png)



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

An **option** is a type of *argument* modifying the behavior of a *command*. For example ```-l``` commonly means "long", ```-a``` means "all". ```-la``` are *two* options combined in a *single* argument.

```
$ ls -la /tmp /var/tmp
option1= -l
option2= -a
```

A [parameter](https://en.wikipedia.org/wiki/Parameter#Computing) is an argument that provides information to either the *command* or one of its options. For example in ```-o file```, *file* is the parameter of the ```-o``` option. Unlike options, parameters are not hardcoded. Bash does this so users are free to use whatever string suits their needs.

```
$ ls -la /tmp /var/tmp
parameter1= /tmp
parameter2= /var/tmp
```

## Manual Pages
Linux has built-in documentation for the majority of commands installed on the system. Descriptions about the command's use case, operation, and functionality are all found in the manual pages. To pull up the manual pages for a command, simply type ``` man ``` in the CLI and the command's name. 

Pull up the manual pages for ```grep```.

![man-grep-cli](photos/Bash&CLI/man-grep-cli.png)

The following is then displayed.

![man-grep](photos/Bash&CLI/man-grep.png)

### SYNOPSIS Header
The header SYNOPSIS tells you how to run the command. In this example 
``` grep ``` takes in two mandatory arguments, the pattern to match by, and the file to search in. ```grep``` also takes in options, but remember, **options are optional**. They are not required to run the command. 

### DESCRIPTION Header
The header DESCRIPTION is self-explanatory, providing a brief description of the command and how to use it.

### OPTIONS Header
The header OPTIONS lists and describes all the available options for the commands. Knowing a command's options is important to extend its functionality. 

### Navigation & Help
Navigating the manual pages is easy.  Use the arrows keys to scroll up and down, or if you are a vim user, use j and k. The forward slash ```/``` is used to search for keywords. Use n and N to shift through search matches. 

Funny enough, there are manual pages for the manual pages. Press h to pull up documentation for the program ```man```. 

![man-help](photos/Bash&CLI/help-man.png)

Once done browsing the manual pages, press q to exit the program.