### CSCI-UA.202: Operating Systems

#### Prof. Allan Gottlieb, Spring 2021

*PROGRAMMING LANGUAGE IS C/C++*

# Chapter 1: Introduction

- __Virtual machine:__ software emulation of some hardware. 
	- makes it look like the hardware has the features you like (eg, TCP/IP)
	- makes the process think it has all the memory, cpu, hardware etc. 
	- provides portability, eg, Java.

Virtual machine abstraction:
1. apps and utilities
2. UI
3. libraries
4. the OS proper (kernel)
5. hardware

<img src="../pictures/virtual-machine.png" width="400">

Kernel runs in __privileged/supervisor__ mode. Programs and others run in __user__ mode. Programs will call to the kernel to perform I/O.

Kernal layers:
1. (Machine independent) files and filesystems.
2. (Machine independent) I/O.
3. (Machine dependent) device drivers.

## What is an Operating System

Raises abstraction (see above)

*Resource manager:* the Central Processing Unit (CPU/processor) can only work on one process at a time. OS manages which processes to run.

## History of Operating Systems

__Batch OS:__ similar jobs (processes) grouped in batches and completed together. *uniprogrammed*

Sometimes a job would need to leave the CPU to whatever reason. Waiting CPU is idle, inefficient.

__Multiprogramming:__ no longer the need to wait for a job to finish. Starts on the next job until the original job returns. *Time-sharing* is multiprogramming with rapid switching between jobs, giving the impression of multiple jobs running simultaneously.

*Difference between multiprogramming and multiprocessing???* They're pretty similar. Don't confuse it with multiprocessor.

## Computer Hardware Review
<!-- elaborate? -->

__bus:__ a set of wires that connect two or more devices.

__trap:__ assembly instruction that switches (jumps) from user to kernal mode.

## System Calls

User directly interacts with the OS (ex. `read()`). This is done using trap.

<img src="../pictures/syscall.png" width="300">

Below are a few syscall commands/functions:

<img src="../pictures/syscalls-list.PNG" width="400">

## Operating System Structure

Everything inside the dotted line is part of the OS:

<img src="../pictures/os-components.png" width="250">

__Monolitic approach:__ one big program, like above. Too fat, makes implementation and maintainance hard.

__Layered approach:__ Top layer is UI, middle is OS, bottom is hardware. The programmer is responsible for designing which component goes into what layer.

__Microkernals:__ Have the kernal (the supervisor mode) as small as possible. All other components are implemented on user level. Kernal acts just as a messenger. Good to prevent crashes.

__Client-server:__ Good for *distributed systems*, storing lots of data. Allows one computer to send operating system code to another computer.

## Metric Units

- nano = 10^-9 or 2^-30
- micro = 10^-6 or 2^-20
- milli = 10^-3 or 2^-10
- kilo = 10^3 or 2^10
- mega = 10^6 or 2^20
- giga = 10^9 or 2^30
- tera = 10^12 or 2^40