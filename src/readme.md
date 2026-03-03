```text
part1.c: A standalone user-space utility mimicking standard Linux commands. It recursively searches for a given string in all regular files present in a directory sub-tree and outputs the matching lines with their full file paths.

boot_64.S: The assembly entry point. This complies with Multiboot specifications to load the kernel, sets up the initial stack pointer, and transitions the CPU into the C kernel environment (kmain). It also contains low-level wrappers for handling interrupts, page faults, and system calls.

entry.c: The bridge between user-space requests and kernel execution. It contains the main do_syscall multiplexer and handles critical hardware exceptions like page faults (do_page_fault) and divide-by-zero errors.

context.c: The process manager. It handles the creation, initialization, and destruction of exec_context structures (your version of a Process Control Block). It also clones memory spaces during a fork or clone operation.

file.c: The Virtual File System (VFS) layer. It translates user-space file descriptor requests into actual file operations, managing the file object reference counts and routing read/write requests to either standard I/O, regular files, or pipes.

fs.c: The implementation of the physical flat file system. It manages the superblock, allocates continuous physical memory for inodes, and handles the raw byte-level reading and writing to the storage medium.

apic.c: Manages the Advanced Programmable Interrupt Controller. It sets up the timer ticks necessary for the OS scheduler to preempt processes and manage CPU time.

copy.sh: A deployment script used to compile the kernel and push the resulting binary into an isolated Docker container for safe execution and testing.
```
