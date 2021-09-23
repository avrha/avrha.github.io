---
title: Linux FHS Explained
published: true
---

The Linux filesystem confuses many n00bs at first but is not complicated once learned. Knowing how and where system data is stored helps one understand the Linux internals. Detailed resources about the Linux FHS exist, but my post explains the essential aspects simply.           

## What is FHS?
FHS stands for Filesystem Hierarchy Standard and defines the directory structure in Linux distributions. In other words, FHS defines how files and directories become arranged in Linux operating systems. 


## Directory Structure
In the FHS, all files and directories appear under the root directory ```/```, even if they are store on different physical or virtual devices. Seen in the figure below is a typical Ubuntu filesystem hierarchy. The directories listed generally exist in all UNIX systems and are used the same way. 

![Ubuntu Filesystem Hierarchy](photos/FHS/FHS-root.png)

Initially, the structure Linux uses for its filesystem is intimidating. When broken down and explained, it is easy to understand and remember.

## / (Root)
``` / ``` is the primary hierarchy root and root directory of the entire file system hierarchy. 

- Every single file and directory starts from the root directory. 
- Only the root user (admin) has the right to write under the root directory.
- ``` /root ``` is the root user's home directory, which is not the same as ``` / ```.

## /bin 
``` /bin ``` stores essential command binaries needed in single-user mode to attain minimal functionality for booting and repairing a system. 
- Contains binary executables.
- Common linux commands (ls,ping,cp) are stored here.

## /sbin
``` /sbin ``` stores system administration binaries.
- Similiar to ``` /bin ```, ``` /sbin ``` contains binary excutables necessary for system administration. 
- Common sysadmin commands (iptables, fdisk, ifconfig) are stored here.

## /boot
``` /boot ``` stores boot loader files. The software responsible for booting a computer is in this directory.
- Kernel initrd, vmlinux, grub. 

## /dev
``` /dev ``` is where the system's devices live. Due to Unix standards, all system hardware (CPU, Memory, I/O, etc.) are device files. Device files allow drivers to access the devices themselves.  

## /etc
``` /etc ``` contains configuration files required by all programs.
- For example, the configuration files for running the popular web server Apache would be here.
- ``` /etc ``` also contains startup and shutdown shell script used to start/stop programs. 

## /home
``` /home ``` is users' home directories, not root. 
- Home directories for user accounts store personal files for them (Photos, Documents, Videos).
- Example: ``` home/john ``` is the home directory for the user john.

## /lib /lib32 /lib64 /libx32
``` /lib* ``` stores libraries needed for the essential binaries in ``` /bin ``` and ``` /sbin ```
- In Software Development, libraries are files that applications can use to perform various functions.  
- Contains kernel modules and share images needed to boot the system.
- Identifiable through the filename extension ``` *.so ```.

## /lost+found
``` lost+found ``` contains recovered files once corrupted. 
- If the file system crashes, a file system check performs at the next boot. 
- Corrupted files are moved to the ``` lost+found ``` directory, so a user can attempt to recover the data.  

## /media
``` /media ``` is a mount directory for removable media.
- Removable media would include hard disks, USB drives, CD-ROMs, etc.
- Example: ``` /media/cdrom ``` for CD-ROM.

## /mnt 
``` /mnt ``` is a temporary mount directory for manually mounting filesystems.

## /opt
``` /opt ``` stores add-on application software packages.
- Packages from individual vendors (i.e Google Chrome by Google).

## /proc
``` /proc ``` is a virtual filesystem created when the system boots and dissolves when the system shuts down. ```/proc ``` contains special files that represent system and process information. The figure below is a snapshot of ``` /proc ``` from my Ubuntu machine.

![Proc Snapshot](photos/FHS/FHS-proc.png)

Listing out ``` /proc ``` content with ``` ls -l ``` displays each PID (Process Identifier) for every process currently running. 

Information about a running process is in a directory named after their PID and shown in a file. For example, information about systemd's process status is in the directory ``` /proc/1 ``` (systemd PID) and shown in the file ``` /proc/1/status ```.

Unlike processes, system resource files are not stored in subdirectories. All are found in ```/proc ```. For example, information about installed cryptographic ciphers used by the Kernel is found in the file ``` /proc/crypto ```. 

## /root
``` /root ``` is the root user's home directory. 
- ``` /root ``` is distinct from ``` / ```, which is the system root directory.

## /run
``` /run ``` stores run time information operated by processes that start early in the boot procedure. ``` /run ``` operates in RAM, meaning that everything in it is gone when the system is rebooted or shut down.

## /snap
``` /snap ``` is where packages installed from the package manager Snap are stored.
- Snap is natively installed on desktop versions of Ubuntu.
- Snap packages are self-contained applications that run differently than regular packages. 

## /srv
``` /srv ``` stores service data.
- Services like FTP and Apache would store files inside ``` /srv ``` for external users to have access. This allows for better security since ``` /srv ``` is at the root of the drive and is easily mountable from another hard drive.  

## /sys
``` /sys ``` contains information about devices, drivers, and some kernel features. 
- Similar to ``` /run ```, ``` /sys ``` is not written on the disk. It is created each time the system boots up. 

## /tmp
``` /tmp ``` is a directory for temporary files.
- Applications, such as word processors, store temporary files in ``` /tmp ```. 
- Files are often not preserved between system reboots. 

## /usr
 ``` /usr ``` contains the majority of user utilities and applications. 
- The data inside ``` /usr ``` is non-essential since the system can boot without it. 
- For example,  non-essentials command binaries (not needed in single-user-mode) is found in ``` /usr/bin ```.

## /var
``` /var ``` stores variable data.
- Variable data are files whose content expects continually change during the operation of the system.  
- Logs, spool files, and temporary e-mail files are prime examples. 