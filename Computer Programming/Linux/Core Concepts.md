# Kernel Purpose
Linux was written by Linus Torvalds in 1991 when attempting to recreate the commercial kernel, Unix. And the rest is history. Linux is a kernel, which means it serves as an interface between a computers hardware and software applications. Linux uses a modular design, meaning a user can 'attach' individual software modules the kernel that define hardware devices and explain how they behave. For example, if you wanted to deploy linux on a smartphone, you can write a module describing the way a touchscreen works or the accelerometer, and this component now becomes part of the kernel (ish). 
![[_attachments/Screenshot 2026-07-29 at 4.41.35 PM.png]]

This is how Android works, which uses the linux kernel, as well as the linux kernel being used in pretty much every possible things. Because linux is modular, you can use just the kernel, then add and remove modules to make it as bare bones or as accelerated as possible.
## Entry Point
