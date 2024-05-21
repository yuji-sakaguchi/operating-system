# Operating System 

### Description: 
This GitHub repository contains the implementation of an operating system lab focusing on file descriptors, pipe data structure, system calls, and process management. The lab aims to create a functional operating system environment capable of handling standard I/O operations, memory management, and process execution.

### Key Features:
#### File Descriptors and Pipe Data Structure:
- File descriptors are managed as integers referring to structures in the PCB (Process Control Block).
- Special handling for file descriptors 0, 1, and 2 (stdin, stdout, stderr) directs them to the keyboard and console.
- Implementation includes flags in the file descriptor data structure for console association.
- Duplication of file descriptors maintains associated flags.
- Open/close operations manage console reference flags.
- Pipe data structure resembles a bounded buffer, managing writers and readers.
- FIFO order is maintained for data entering and exiting the pipe.
- Supports multiple writers/readers with round-robin scheduling and atomic read/write calls.
- Handles different data sizes gracefully.

#### Read and Write System Calls:
- Read/write operations retrieve data from the pipe.
- Blocking/unblocking mechanisms are managed via semaphores based on pipe state.
- Close operations handle end-of-pipe conditions, delivering EOF to readers.
- Ensures data consistency for multiple processes reading/writing to the same pipe.

#### Dup, Dup2, and Pipe System Calls:
- Reference counters track file descriptor pointers to writer/reader sides.
- Allocates and frees file descriptors, manages forked processes, and maintains reference counts.
- Handles close operations and process exits to ensure accurate pipe reference counts.

#### File System Interaction:
- Manages file descriptors, handles file operations like opening, closing, and duplicating file descriptors, and supports inter-process communication using pipes.

#### Memory Management:
- Implements memory allocation using the sbrk system call (do_sbrk), allowing processes to dynamically allocate memory within their address space.

#### Concurrency Control:
- Employs semaphore-based synchronization (P_kt_sem, V_kt_sem) for managing concurrency issues and controlling access to shared resources like pipes and buffers.

#### Process Management:
- Utilizes Process Control Block (PCB) structures for managing process information, including PID, file descriptors, register values, and parent-child relationships.
- Functions like make_pcb, make_file_descriptor, and get_new_pid are used for process management operations.

#### Process Creation and Termination:
- Supports process creation (do_fork, do_execve) and termination (do_exit) operations, manages parent-child relationships, PID assignment, and resource cleanup.

#### Error Handling:
- Includes error-checking mechanisms for system calls, file operations, memory allocation, and critical operations to ensure robustness and prevent crashes.

#### Additional System Calls:
- Implements additional system calls including IOCTL(), FSTAT(), GETPAGESIZE(), SBRK(), EXECVE(), GETPID(), FORK(), GETPPID(), WAIT(), GETDTABLESIZE(), CLOSE() (in limited form).
Provides functionalities for managing processes, memory, and system operations effectively.

### Testing:
#### Unit Testing:
- Comprehensive unit tests cover individual components such as file descriptors, pipe data structure, system calls, and process management.
- Ensures each feature works as expected and handles edge cases appropriately.

#### Integration Testing:
- Verifies the coordination between file descriptors, pipe operations, system calls, and process management.

