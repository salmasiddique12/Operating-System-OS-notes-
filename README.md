# Operating-System-OS-notes-

📘 OPERATING SYSTEM — STET + SSC JE NOTES
1. Operating System Basics ⭐⭐⭐⭐⭐
What is an Operating System?
An Operating System (OS) is system software.
It acts as an interface between the user/application and hardware.
It manages computer resources such as:
CPU
Memory
Files
I/O devices
Storage
Simple Example

When you open Chrome:

User
 ↓
Chrome
 ↓
Operating System
 ↓
CPU + RAM + Disk + Network

The OS decides how these resources are used.

Examples
Windows
Linux
macOS
Android
iOS
Main Functions of OS
Process Management
Memory Management
File Management
Device/I/O Management
Secondary Storage Management
Security and Protection
Resource Allocation
User Interface
🧠 Memory Trick

P-M-F-I-S-S

Process
Memory
File
I/O
Storage
Security

2. Types of Operating Systems ⭐⭐⭐⭐
A. Batch Operating System
Jobs are collected and executed in batches.
Little or no direct interaction with the user during execution.
Example

Payroll processing for thousands of employees.

Job 1
Job 2
Job 3
Job 4
 ↓
Batch
 ↓
Execution
Memory Trick

Batch = Jobs together

B. Multiprogramming OS
Multiple programs are kept in memory.
When one program waits for I/O, CPU can execute another.
Main goal → keep CPU busy.
Example
P1 → Waiting for disk
        ↓
CPU → Executes P2
Memory Trick

Multiprogramming = Many programs in memory

C. Multitasking / Time-Sharing OS
CPU time is divided among processes/tasks.
Gives the appearance that many programs are running simultaneously.
Example

You can:

Play music
Browse Chrome
Download a file

at the same time.

Memory Trick

Time-sharing = Time slices

D. Multiprocessing OS
Uses multiple processors/CPU cores.
Multiple processes/threads can execute in parallel.
Example

A multicore computer running several workloads simultaneously.

Memory Trick

Multiprocessing = Multiple processors/cores

E. Real-Time Operating System — RTOS ⭐⭐⭐⭐
Must respond within specified timing constraints.
Used where timing is important.
Examples
Industrial control
Robotics
Automotive control systems
Medical equipment
Types

Hard Real-Time

Missing a deadline can be unacceptable.

Soft Real-Time

Deadline is important, but occasional misses may be tolerated.
Memory Trick

Hard = Deadline must be met

F. Distributed Operating System
Manages resources across multiple connected computers.
Attempts to provide coordinated system services across nodes.
Example

A distributed computing environment where multiple machines cooperate on tasks.

G. Network Operating System
Provides network-related services.
Manages:
Users
Shared files
Printers
Network resources
3. Kernel ⭐⭐⭐⭐⭐
The kernel is the core part of an operating system.
It manages communication between software and hardware.
It handles:
CPU/process management
Memory management
Device management
System calls
Resource management
Example

When an application requests data from a disk:

Application
    ↓
System Call
    ↓
Kernel
    ↓
Device Driver
    ↓
Disk
🧠 Memory Trick

Kernel = Core of OS

4. User Mode and Kernel Mode

Modern OSs commonly use privilege levels.

User Mode
Applications normally execute here.
Restricted access.
Cannot directly perform privileged hardware operations.
Kernel Mode
OS kernel executes here.
Higher privileges.
Can perform privileged operations.
Example

A normal application cannot directly control a disk controller. It requests the OS through a system call.

🧠 Trick

User = Limited

Kernel = Privileged

5. System Calls ⭐⭐⭐⭐⭐
A system call is a controlled interface through which a user program requests an OS service.
Common categories
Process control
File management
Device management
Information maintenance
Communication
Protection
Examples

Linux/POSIX examples include:

fork() → create a process
exec() → replace process image
open() → open file
read() → read data
write() → write data
close() → close file
Example
Program
   ↓
read()
   ↓
System Call
   ↓
Kernel
   ↓
File/device
🧠 Memory Trick

System Call = Program asks OS for service

6. Program vs Process ⭐⭐⭐⭐⭐
Program
Passive.
Set of instructions.
Stored in secondary storage.
Process
Program in execution.
Has:
State
Program counter
Registers
Memory
Resources
Example

calculator.exe stored on disk → Program

Calculator currently running → Process

🧠 Trick

Program = Passive
Process = Running

7. Process States ⭐⭐⭐⭐⭐

Common five states:

New
Ready
Running
Waiting/Blocked
Terminated
             New
              ↓
            Ready
              ↓
           Running
          ↙   ↓    ↘
     Waiting  Ready  Terminated
        ↓
      Ready
New
Process is being created.
Ready
Process is ready to execute.
Waiting for CPU.
Running
Process is currently executing.
Waiting/Blocked
Process is waiting for an event/I/O.
Terminated
Process has finished or has been terminated.
🔥 Most Important Trick

Ready → Waiting for CPU

Waiting → Waiting for I/O/event

8. Process Control Block — PCB ⭐⭐⭐⭐⭐
OS maintains a PCB for each process.
PCB stores information needed to manage the process.
PCB contains
Process ID
Process state
Program counter
CPU registers
Scheduling information
Memory-management information
I/O status information
Accounting information
Example

During context switching:

P1 Running
   ↓
Save P1 information in PCB
   ↓
Load P2 information
   ↓
P2 Running
🧠 Trick

PCB = Process's identity + state + execution information

9. Context Switching ⭐⭐⭐⭐⭐
CPU switches from one process/thread to another.
OS saves the current execution context and loads the next one.
Example
P1 → CPU
 ↓
Save P1 context
 ↓
Load P2 context
 ↓
P2 → CPU
Important
Context switching is overhead.
Too many context switches can reduce performance.
🧠 Trick

Context Switch = Save + Load

10. Threads ⭐⭐⭐⭐
A thread is a basic unit of CPU execution within a process.
Threads of the same process share many resources, especially the address space.
Process vs Thread
Process	Thread
Heavier unit	Lighter execution unit
Separate address space generally	Threads of same process share address space
More isolation	Less isolation
Communication generally more expensive	Communication can be easier due to shared memory
Example

A web browser may use multiple processes and threads for different tasks.

🧠 Trick

Process = Resource container
Thread = Execution unit

11. CPU Scheduling ⭐⭐⭐⭐⭐

CPU scheduling decides:

Which ready process should get the CPU next?

Important Algorithms
FCFS
SJF
SRTF
Priority
Round Robin
Multilevel Queue
Multilevel Feedback Queue
12. FCFS — First Come First Serve
Process that arrives first gets CPU first.
Usually non-preemptive.
Example

Arrival order:

P1 → P2 → P3

Execution:

P1 → P2 → P3
Advantage
Simple
Easy to implement
Disadvantage
Can cause convoy effect.
🧠 Trick

FCFS = First Arrival → First CPU

13. SJF — Shortest Job First
Process with the smallest CPU burst is selected first.
Standard SJF is non-preemptive.
Example
P1 = 8 ms
P2 = 3 ms
P3 = 5 ms

Order:

P2 → P3 → P1
Important

SJF can provide minimum average waiting time under the standard ideal assumptions when burst lengths are known.

🧠 Trick

SJF = Shortest Burst First

14. SRTF — Shortest Remaining Time First
Preemptive version of SJF.
Process with shortest remaining CPU time gets CPU.
Example

P1 is running.

A new process P2 arrives with a shorter remaining time.

→ P1 can be preempted.

🧠 Trick

SRTF = SJF + Preemption

15. Priority Scheduling
CPU is assigned according to priority.
Can be:
Preemptive
Non-preemptive
Problem

Starvation

Low-priority process may wait for a very long time.

Solution

Aging

Gradually increase priority of waiting processes.

🧠 Trick

Aging → Prevents starvation

16. Round Robin ⭐⭐⭐⭐⭐
Designed for time-sharing systems.
Each process gets a fixed time quantum.
Preemptive.

Example:

Quantum = 2 ms

P1 → P2 → P3 → P1 → P2 → ...
Important

If time quantum is:

Too small → many context switches

Too large → behavior approaches FCFS

🧠 Trick

Round Robin = Time Quantum

17. Scheduling Formulas ⭐⭐⭐⭐⭐
Turnaround Time
$$ \boxed{TAT = Completion\ Time - Arrival\ Time} $$
Waiting Time
$$ \boxed{WT = Turnaround\ Time - Burst\ Time} $$
Response Time
$$ \boxed{RT = First\ CPU\ Start\ Time - Arrival\ Time} $$
Example

Suppose:

Arrival = 2
Completion = 10
Burst = 5
First CPU start = 4

Then:

$$ TAT=10-2=8 $$ $$ WT=8-5=3 $$ $$ RT=4-2=2 $$
18. Scheduling Numerical — Golden Method

Whenever question gives:

Process	AT	BT
P1	0	5
P2	1	3
P3	2	2

Do this:

Step 1

Draw Gantt Chart.

Step 2

Find completion time.

Step 3
$$ TAT=CT-AT $$
Step 4
$$ WT=TAT-BT $$
Step 5
$$ Average\ WT=\frac{\sum WT}{n} $$
🧠 Trick

Gantt → CT → TAT → WT

19. Synchronization ⭐⭐⭐⭐⭐

When multiple processes/threads access shared data, synchronization is required to avoid incorrect results.

Race Condition
Occurs when the result depends on the timing/order of concurrent operations.
Example

Bank balance = ₹1000.

Two threads simultaneously withdraw ₹700.

Without proper synchronization, both may read ₹1000 before either update is stored, producing an incorrect final state.

20. Critical Section ⭐⭐⭐⭐⭐
Part of a program where shared data/resource is accessed.

A correct critical-section solution should satisfy:

1. Mutual Exclusion

Only one process can be in its critical section for the same shared resource at a time.

2. Progress

If no process is in the critical section, selection of the next process should not be postponed indefinitely.

3. Bounded Waiting

A process should not wait forever after requesting entry.

🧠 Trick

M-P-B

Mutual Exclusion
Progress
Bounded Waiting

21. Semaphore ⭐⭐⭐⭐⭐

A semaphore is a synchronization primitive used to coordinate concurrent processes/threads.

Common operations:

wait() / P
signal() / V
Binary Semaphore
Usually represents two states, commonly 0/1.
Can be used for mutual exclusion.
Counting Semaphore
Can represent multiple available instances of a resource.
Example

Suppose there are 3 identical printers.

A counting semaphore can initially have value:

$$ 3 $$

Each allocation reduces the count; releasing a printer increases it.

🧠 Trick

Semaphore = Synchronization

Counting semaphore = Resource count

22. Mutex ⭐⭐⭐⭐
Mutex means Mutual Exclusion.
Used to protect a critical section/resource.
Normally has ownership semantics: the thread that locks it is the one expected to unlock it.
Mutex vs Semaphore
Mutex	Semaphore
Mainly mutual exclusion	Synchronization/resource counting
Ownership-oriented	Generally no ownership requirement
Typically locked/unlocked	wait/signal operations
Often binary	Binary or counting
23. Deadlock ⭐⭐⭐⭐⭐

Deadlock occurs when a group of processes becomes permanently blocked because each is waiting for a resource/event held by another.

Example
P1 holds Printer
P1 waits for Scanner

P2 holds Scanner
P2 waits for Printer

Neither can continue.

24. Four Necessary Conditions of Deadlock ⭐⭐⭐⭐⭐

All four must hold for deadlock to occur:

1. Mutual Exclusion

Resource cannot be shared simultaneously.

2. Hold and Wait

Process holds one resource while waiting for another.

3. No Preemption

Resource cannot be forcibly taken away.

4. Circular Wait

Processes form a circular chain of waiting.

P1 → P2
↑     ↓
P4 ← P3
🧠 Super Trick

M H N C

Mutual Exclusion
Hold and Wait
No Preemption
Circular Wait

25. Deadlock Handling
Prevention

Break at least one necessary condition.

Avoidance

System checks whether granting a request keeps it in a safe state.

Banker's Algorithm ⭐

Used for deadlock avoidance.

Detection

Allow deadlock, then detect it.

Recovery
Terminate processes
Resource preemption
Rollback
⚠️ Exam Trap

Banker's Algorithm → Avoidance

Not prevention.

26. Safe vs Unsafe State
Safe State

There exists a sequence in which all processes can complete while respecting resource constraints.

Unsafe State

No guaranteed safe sequence.

⚠️ Unsafe does not necessarily mean deadlock has already occurred.

27. Memory Management ⭐⭐⭐⭐⭐

OS manages:

Allocation
Deallocation
Protection
Address translation
Sharing

Important techniques:

Contiguous allocation
Paging
Segmentation
Virtual memory
28. Contiguous Memory Allocation

Each process gets a continuous block of memory.

Allocation methods
First Fit

Allocate first sufficiently large hole.

Best Fit

Allocate smallest hole that is sufficient.

Worst Fit

Allocate largest available hole.

🧠 Trick

First = First suitable

Best = Smallest suitable

Worst = Largest suitable

29. Fragmentation ⭐⭐⭐⭐⭐
Internal Fragmentation

Unused space inside an allocated block.

Example:

A process needs 18 KB but gets a 20 KB fixed block.

Unused:

$$ 2KB $$

→ Internal fragmentation.

External Fragmentation

Enough total free memory exists, but it is divided into small scattered holes.

🧠 Trick

Internal = Inside

External = Outside/scattered

30. Paging ⭐⭐⭐⭐⭐

Paging divides:

Logical memory → Pages
Physical memory → Frames

Both are fixed-size.

Logical Memory
P0 P1 P2 P3
 ↓ ↓ ↓ ↓
Page Table
 ↓ ↓ ↓ ↓
F3 F1 F7 F2
Physical Memory
Page Table

Maps:

$$ \boxed{Page \rightarrow Frame} $$
Advantages
No external fragmentation due to contiguous allocation requirement.
Processes do not need to occupy contiguous physical memory.
Disadvantage
Internal fragmentation can occur.
31. Logical and Physical Address
Logical Address
Generated by CPU/program.
Also called virtual address in many modern systems.
Physical Address
Actual address in physical memory.
MMU

Memory Management Unit

translates logical/virtual addresses into physical addresses.

CPU
 ↓
Logical Address
 ↓
MMU
 ↓
Physical Address
 ↓
RAM
32. Page Fault ⭐⭐⭐⭐⭐

A page fault occurs when a process accesses a page that is not currently in physical memory.

Steps:

Page requested
      ↓
Page not in RAM
      ↓
Page Fault
      ↓
OS obtains page from backing storage
      ↓
Page loaded into frame
      ↓
Page table updated
      ↓
Execution continues
Important

Page fault does not mean hardware is necessarily faulty.

It is a normal virtual-memory event, though expensive.

33. Virtual Memory ⭐⭐⭐⭐⭐

Virtual memory allows processes to use a logical address space larger than the available physical RAM.

It uses techniques such as:

Paging
Demand paging
Example

Computer has:

8 GB RAM

A process may have a virtual address space much larger than 8 GB, although not all of it is resident in RAM at once.

Benefits
Large address spaces
Better multiprogramming
Memory isolation/protection
Efficient RAM usage
🧠 Trick

Virtual Memory = Not all required pages need to be in RAM simultaneously

34. Page Replacement ⭐⭐⭐⭐⭐

If a required page is not in memory and no free frame exists:

→ OS must choose a page to remove.

Important algorithms:

FIFO

Removes the page that entered memory first.

Oldest page → Replace

Optimal

Removes the page whose next use is farthest in the future.

Gives minimum possible page faults for a given reference string under the ideal model.
Future references are not known in practice.
LRU

Removes the page that has not been used for the longest time in the past.

🧠 Super Trick

FIFO → Oldest

LRU → Least recently used

Optimal → Future farthest

35. Belady's Anomaly ⭐⭐⭐⭐
In some cases, increasing the number of page frames can increase page faults.
Classic example: FIFO.
Important

Belady's anomaly is not a general property of every page replacement algorithm.

36. Thrashing ⭐⭐⭐⭐
System spends excessive time handling page faults/swapping instead of doing useful computation.

Symptoms:

Very high page-fault rate
Poor CPU utilization
Slow system
🧠 Trick

Thrashing = Too much paging, too little useful work

37. Segmentation ⭐⭐⭐⭐

Memory is divided according to logical program units.

Examples:

Code segment
Data segment
Stack segment

Segments are variable-sized.

Segment Table

Typically stores:

Base
Limit
Paging vs Segmentation
Paging	Segmentation
Fixed-size	Variable-size
Pages	Segments
Page → Frame	Segment → physical location
Internal fragmentation possible	External fragmentation possible
38. File System ⭐⭐⭐⭐⭐

OS manages files and directories.

File operations
Create
Open
Read
Write
Close
Delete
Seek
File attributes
Name
Type
Size
Location
Protection
Timestamps
39. File Allocation Methods ⭐⭐⭐⭐
Contiguous Allocation

File occupies consecutive blocks.

Advantage

Fast access.

Disadvantage

External fragmentation can occur.

Linked Allocation

Each file block points to the next block.

Advantage

No external fragmentation from contiguous allocation requirement.

Disadvantage

Random access is inefficient.

Indexed Allocation

An index block contains pointers to file blocks.

Advantage

Supports direct/random access better than linked allocation.

🧠 Trick

Contiguous → Consecutive

Linked → Chain

Indexed → Index/Pointers

40. Directory Structures ⭐⭐⭐⭐

Types:

Single-level
Two-level
Tree-structured
Acyclic graph
General graph
Most common conceptual model
Root
├── Documents
│   ├── A.txt
│   └── B.txt
└── Pictures
    └── photo.jpg
41. I/O Management ⭐⭐⭐⭐

OS manages communication between CPU/memory and I/O devices.

Important concepts:

Device drivers
Interrupts
Buffering
Caching
Spooling
DMA
42. Device Driver
Software that allows OS to communicate with a hardware device.

Example:

OS
 ↓
Printer Driver
 ↓
Printer
🧠 Trick

Driver = Software interface for hardware device

43. Buffering
Temporary storage used while transferring data.
Helps handle differences in data production/consumption rates.
Example

Video streaming uses buffers so playback can continue smoothly when possible.

44. Spooling ⭐⭐⭐⭐

Spooling = Simultaneous Peripheral Operations On-Line

Jobs are temporarily stored in a queue/storage area for a slower device.
Best example

Print Spooling

P1 ─┐
P2 ─┼→ Print Queue → Printer
P3 ─┘
🧠 Trick

Spooling → Printing

45. DMA — Direct Memory Access ⭐⭐⭐⭐
Allows an I/O device to transfer data directly to/from main memory with limited CPU intervention.
A DMA controller manages much of the transfer.
Advantage
Reduces CPU overhead for bulk data transfer.
🧠 Trick

DMA = Device ↔ Memory, less CPU involvement

46. Disk Scheduling ⭐⭐⭐⭐

Used to decide the order in which pending disk requests are served.

Important algorithms:

FCFS

Serve in arrival order.

SSTF

Shortest Seek Time First

Choose request requiring the shortest seek distance from current head position.

SCAN

Disk head moves in one direction serving requests, then reverses.

Elevator algorithm

C-SCAN

Services in one direction and then returns to the beginning/end without servicing requests on the return sweep, depending on implementation description.

LOOK

Like SCAN, but reverses at the last pending request rather than going all the way to the physical end.

C-LOOK

Circular version of LOOK.

🧠 Memory Trick

SSTF → Nearest

SCAN → Elevator

C-SCAN → Circular Elevator

47. Protection and Security ⭐⭐⭐
Protection

Controls how authorized processes/users access system resources.

Security

Protects the system/data from unauthorized access and attacks.

Authentication

Who are you?

Examples:

Password
OTP
Biometrics
Authorization

What are you allowed to do?

🧠 Trick

Authentication = Identity

Authorization = Permission

🎯 STET + SSC JE Must-Remember Sheet
Process

Program in execution

Ready

Waiting for CPU

Waiting

Waiting for I/O/event

PCB

Process management information

Context Switch

Save old + Load new

FCFS

First arrival first

SJF

Shortest burst first

SRTF

Preemptive SJF

Round Robin

Time quantum

Aging

Prevents starvation

Critical Section

Shared-resource code

Semaphore

Synchronization

Deadlock

M-H-N-C

Banker's Algorithm

Deadlock avoidance

Paging

Page → Frame

Page Fault

Required page absent from RAM

FIFO

Oldest page

LRU

Least recently used

Optimal

Future-farthest use

Thrashing

Excessive paging

DMA

Direct device-memory transfer

Spooling

Print queue

Authentication

Who are you?

Authorization

What can you access?

🧠 10 Super-Fast Memory Tricks
Program → Passive; Process → Running
Ready → CPU wait
Blocked → I/O/event wait
PCB → Process information
RR → Time Quantum
Aging → Starvation
M-H-N-C → Deadlock conditions
Page → Frame
FIFO → Oldest; LRU → Least recently used
Authentication → Who; Authorization → What
