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
- Read/write operations retrieve data from the pipe for file descriptors > 2.
- Blocking/unblocking mechanisms are managed via semaphores based on pipe state.
- Close operations handle end-of-pipe conditions, delivering EOF to readers.
- Ensures data consistency for multiple processes reading/writing to the same pipe.

#### Dup, Dup2, and Pipe System Calls:
- Reference counters track file descriptor pointers to writer/reader sides.
- Allocates and frees file descriptors, manages forked processes, and maintains reference counts.
- Handles close operations and process exits to ensure accurate pipe reference counts.

#### Additional System Calls:
- Implements additional system calls including IOCTL(), FSTAT(), GETPAGESIZE(), SBRK(), EXECVE(), GETPID(), FORK(), GETPPID(), WAIT(), GETDTABLESIZE(), CLOSE() (in limited form).
Provides functionalities for managing processes, memory, and system operations effectively.

### Testing:
#### Unit Testing:
- Comprehensive unit tests cover individual components such as file descriptors, pipe data structure, system calls, and process management.
- Ensures each feature works as expected and handles edge cases appropriately.

#### Integration Testing:
- Tests the integration of different components to ensure seamless interaction and functionality.
- Verifies the coordination between file descriptors, pipe operations, system calls, and process management.

#### System Testing:
- End-to-end system testing simulates real-world scenarios to validate the overall functionality of the operating system.
- Includes scenarios involving multiple processes, concurrent operations, and varying data sizes to assess system stability and performance.

#### Automated Testing:
- Utilizes automated testing frameworks and scripts to streamline testing processes and improve test coverage.
- Automates repetitive test cases, regression tests, and performance tests for efficient testing workflows.

#### Documentation Testing:
- Validates that the system documentation accurately reflects the implemented features, functionalities, and usage instructions.
- Ensures users, developers, and administrators can effectively understand and utilize the operating system.
