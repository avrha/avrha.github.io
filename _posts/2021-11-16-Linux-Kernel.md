---
title: Linux Kernel 101
published: true
---

The Linux kernel is arguably the most important piece of software written in the age of computing. Conceived and created in 1991 by Linus Torvalds, it was adopted as the kernel for the GNU operating system, a free replacement for UNIX. Since then, Linus’ kernel has spawned numerous OS distributions commonly called Linux.  

## Overview on Operating Systems 
An operating system (OS) is system software that manages computer hardware, software resources, and provides common services for computer programs. Simply, an OS supports a computer’s basic function. 

A computer consists of hardware, an operating system and application programs. The hardware consists of the CPU, I/O, memory, etc. Application programs consist of software intended for the end user; business and database programs are examples.

![Computer System View](photos/Kernel-101/OS-Placement.png)

An operating system acts as a middleman between the application and hardware, coordinating the use of the hardware among different applications for various users. Hence, the OS provides an environment in which an user can execute programs conveniently and efficiently.  

The components of an operating system exist in order to ensure different parts of the computer work accordingly together. Remember, all user software needs to through the OS before touching any hardware.

Operating System's Main Components.
- Kernel
- Networking
- Security
- User Interface

The **kernel** is the core of an operating system and has complete control over everything in the system. The most important part of an OS, the kernel, facilitates interactions between the hardware and software.

![Kernel Layout](photos/Kernel-101/kernel.svg)

The **networking** component consists of communication systems for sending and retrieving data between systems. The **security** component consists of hardcoded features to ensure all technologies are behaving properly. The **user interface** is a program, typically called the **shell**, that gives the user a means to interact with the system.

### User Space and Kernel Space
An operating system segregates virtual memory into **kernel space** and **user space**. Primarily, this separation serves to provide memory and hardware protection from malware. 

Kernel space is reserved for running a privileged kernel, kernel extensions, and most device drivers. In contrast, user space is the memory area where application software and some drivers execute. 

![User Space and Kernel Space](photos/Kernel-101/spaces.png)

System calls will be covered later. For now, understand operating systems segregate virtual memory into two parts.   

### User Mode and Kernel Mode 
A computer operates in two modes: user mode and kernel mode. When any application is running, the program is in user mode. 