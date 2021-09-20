---
title: Linux FHS Explained
published: true
---

The Linux filesystem confuses many n00bs at first but is not complicated once learned. Knowing how and where system data is stored helps one understand the Linux internals. Detailed resources about the Linux FHS exist, but my post explains the essential aspects simply.           

## What is FHS?
FHS stands for Filesystem Hierarchy Standard and defines the directory structure in Linux distributions. In other words, FHS defines how files and directories become arranged in Linux operating systems. 


## Directory Structure
In the FHS, all files and directories appear under the root directory ```/```, even if they are store on different physical or virtual devices. Seen in the figure below is a typical Ubuntu filesystem hierarchy. The directories listed generally exist in all UNIX systems and are used the same way. 

![Ubuntu Filesystem Hierarchy](https://upload.wikimedia.org/wikipedia/commons/d/d6/Ubuntu_Filesystem_Hierarchy.png)

Initially, the structure Linux uses for its filesystem is intimidating. When broken down and explained, it is easy to understand and remember.

### / (Root)
``` / ``` is the primary hierarchy root and root directory of the entire file system hierarchy. 

- Every single file and directory starts from the root directory. 
- Only the root user (admin) has the right to write under the root directory.
- ``` /root ``` is the root user's home directory, which is not the same as ``` / ```.

### /bin 
``` /bin ``` stores essential command binaries needed in single-user mode to attain minimal functionality for booting and repairing a system. 
- Contains binary executables
- Common linux commands (ls,ping,cp) are stored here

### /boot
``` /boot ``` stores boot loader files. The software responsible for booting a computer is in this directory.
- Kernel initrd, vmlinux, grub. 

### /dev
``` /dev ``` include device files. A device file is an interface to a device driver that appears as an ordinary file. 
- Any device attached to the system, like USB, is included here.

### /etc
``` /etc ``` contains configuration files required by all programs.
- For example, the configuration files for running the popular web server Apache would be here.
- ``` /etc ``` also contains startup and shutdown shell script used to start/stop programs. 

### /home
``` /home ``` is users' home directories, not root. 
- Home directories for user accounts store personal files for them (Photos, Documents, Videos).
- Example: ``` home/john ``` is the home directory for the user john.

### /lib /lib32 /lib64 /libx32
``` /lib ``` stores libraries essential for the binaries in ``` /bin ``` and ``` /sbin ```
- Contains kernel modules and share images needed to boot the system.
- Identifiable through the filename extension ``` *.so ```.

### /lost+found
Files appearing in ``` /lost+found ``` are typically unlinked (i.e their name had been erased) but still opened by some process (so the data wasn't erased yet) when the system halted suddenly (kernel panic or power failure).

Files can also appear in ``` /lost+found ``` becuase the file system experienced a software or hardware bug. In such case, the directory serves a way for the user to find a file that was lost but salvaged by the system repair. 

tldr - You'll find recovered bits of file here. 

### /media
``` /media ``` is a mount directory for removable media such as CD-ROMs and USB Flash Drives. 
- Example: ``` /media/cdrom ``` for CD-ROM.

### /mnt 
``` /mnt ``` is a temporary mount directory for mounting filesystems.

### /opt
``` /opt ``` stores add-on application software packages.
- Packages from individual vendors (i.e Google Chrome by Google).