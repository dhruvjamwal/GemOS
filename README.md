# GemOS: Academic Operating System Implementation

This repository contains the source code and implementations for various core operating system components built on top of GemOS, a minimal, 64-bit academic operating system. 

The project focuses on building foundational OS primitives from scratch, managing hardware interruptions, virtual memory, and developing a custom file system. 

GemOS-Architecture/
├── README.md
├── src/
│   ├── apic.c
│   ├── boot_64.S
│   ├── context.c
│   ├── entry.c
│   ├── file.c
│   └── fs.c
├── utils/
│   └── mygrep.c
└── scripts/
    └── copy.sh

## Key Features & Implementations

* Memory Management & Paging: Implemented virtual memory translation and page fault handling. The system handles demand paging and dynamic memory expansion/shrinkage using multi-level page tables.
* Process Management: Developed process control blocks (exec_context) and system calls for process lifecycle management, including `fork`, `clone`, `sleep`, and `exit`. 
* Custom File System: Engineered a flat file system with a functional superblock and inode structures. Implemented core file operations: `open`, `read`, `write`, `close`, `lseek`, and file descriptor duplication (`dup`, `dup2`).
* Inter-Process Communication (IPC): Built pipe functionality to enable data transfer and synchronization between processes.
* System Utilities: Includes a standalone, from-scratch implementation of core Linux utilities like `grep` for recursive directory string matching and directory size calculation.
* Kernel Debugging: Integrated page table dumping and kernel-level print utilities (`dprintk`) to trace system calls and memory faults.

## Architecture

The kernel operates in 64-bit mode and handles transitions between user space and kernel space via hardware interrupts and syscall instructions. 

### Core System Calls Implemented
* **Process & Memory:** `getpid`, `fork`, `clone`, `exit`, `sleep`, `expand`, `shrink`, `alarm`, `signal`
* **File Operations:** `open`, `read`, `write`, `close`, `lseek`, `dup`, `dup2`, `pipe`

## Building and Running

The project requires a cross-compiled GCC toolchain for x86_64. A `copy.sh` script is provided to streamline the deployment of the compiled `gemOS.kernel` binary into the testing container.

