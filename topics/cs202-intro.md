### CSCI-UA.202: Operating Systems

#### Prof. Allan Gottlieb, Spring 2021

# Chapter 1: Introduction

__Virtual machine:__ software emulation of some hardware. 
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

*Difference between multiprogramming and multiprocessing???*

## Computer Hardware Review
<!-- elaborate? -->

__bus:__ a set of wires that connect two or more devices.

__trap:__ instruction that atomically switches the processor into privileged mode and jumps to a pre-defined physical address.

## System Calls

User directly interacts with the OS (ex. `read()` ). This is done using the assembly trap instruction.

