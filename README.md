# Linux Systems Programming Practice

A collection of Linux and POSIX concurrency practice programs written in C. The repository currently focuses on using **POSIX threads**, **semaphores**, **mutexes**, and shared memory patterns to understand operating-system concepts.

## Topics Covered

### Thread-Based Array Operations

The first group of examples uses `pthread_create()` and `pthread_join()` to perform array operations in worker threads:

- Calculate the average of an integer array
- Find the maximum value
- Find the minimum value
- Return results from a thread using dynamically allocated memory

### Producer–Consumer Problem

The producer–consumer example demonstrates synchronization with two semaphores:

- `e` — tracks whether the buffer is empty
- `f` — tracks whether the buffer contains data
- A single-slot shared buffer is used between producer and consumer threads

### Readers–Writers Problem

The readers–writers example demonstrates synchronization using:

- A mutex for safely updating the reader count
- A writer mutex for exclusive write access
- Multiple readers sharing access while writers are blocked

## Repository Contents

```text
Linux/
├── c.c       # C programs demonstrating POSIX threads and synchronization
└── README.md  # Documentation
```

## Requirements

- Linux, WSL, or another POSIX-compatible environment
- GCC or another C compiler
- POSIX threads support
- POSIX semaphore support

Install GCC on Debian or Ubuntu with:

```bash
sudo apt update
sudo apt install build-essential
```

## Important Note About `c.c`

`c.c` contains multiple independent demonstrations, and each demonstration has its own `main()` function. Therefore, the complete file is intended as a collection of practice snippets and should not be compiled as one translation unit.

To run an individual example:

1. Copy the required code section into a separate `.c` file.
2. Compile it with GCC.
3. Run the generated executable.

For example:

```bash
gcc -Wall -Wextra -pthread average.c -o average
./average
```

For the semaphore-based producer–consumer example, use:

```bash
gcc -Wall -Wextra -pthread producer_consumer.c -o producer_consumer
./producer_consumer
```

## Example Input

The array examples expect input in this format:

```text
5
10 20 30 40 50
```

Example output from the average program:

```text
Average = 30.00
```

## Learning Goals

This repository is intended to provide hands-on practice with:

- Creating and joining POSIX threads
- Passing results from worker threads
- Dynamic memory allocation with `malloc()` and `free()`
- Protecting shared data with mutexes
- Coordinating threads with semaphores
- Implementing classic operating-system synchronization problems
- Understanding race conditions and critical sections

## Safety and Improvement Notes

The examples are educational exercises. When extending them, consider adding:

- Return-value checks for `pthread_create()`, `pthread_join()`, `sem_init()`, and mutex operations
- Input validation and bounds checking for the fixed-size array
- Proper cleanup with `sem_destroy()` and mutex destruction where appropriate
- Separate source files for each experiment
- Thread arguments instead of global variables
- A build system such as a `Makefile`

## License

This repository is intended for educational and practice purposes.
