# Computer Design
## Terminology
* **Instruction Set Architecture (ISA)**: Describes hardware interface (ex: x86)
  * Machine code
  * *Classification: Reduced Instruction Set Computer (RISC - ex: ARM) vs Complex Instruction Set Computer (CISC - ex: x86)*
* **Application Binary Interface (ABI)**: Describes machine code interface (ex: Linux Standard Base) 
  * OS ABI:
    * Processor instruction set (register file structure, stack organization, memory access types, ...) and basic data types (sizes, layouts, and alignments)
    * Function calling convention (register arguments, return value, stack order, ...) and system calls to OS
    * Executable file format (Executable and Linkable Format (ELF) for linux, Portable Executable (PE) for windows, ...)
    * C++ (name mangling, exception propagation, ...)
* **Application Programming Interface (API)**: Describes code source interface (ex: POSIX)
  * Subroutine and protocols

* Microarchitecture: Implementation of an ISA (ex: Intel Pentium)
* Microcode: Interpreter between the CPU and the programmer-visible ISA

## Performances
* Task
  * Execution/Response time: total time to complete a task (including CPU, OS, IO, ...)
  * Throughput/Bandwidth: number of tasks completed per unit time
  * CPU time: time spent by CPU
  * user CPU time: time in a program itself
  * system CPU time: time in OS on behalf of a program
* Clock
  * Clock period: length of a clock cycle
  * Clock cycle/tick: time for one clock period
* Instruction
  * clock Cycles Per Instruction (CPI): average number of clock cycles per instructions
  * Instructions Per clock Cycle (IPC): invert of CPI
  * Instruction count: number of instructions executed (affected by ISA)

CPU time = Instruction count * CPI / Clock cycle

* Instruction mix: dynamic frequency of instructions (affecting CPI)

## CPU
* **Stored-Program Concept**: instructions and data are stored in memory as numbers
* Architecture
  * Von Neumann: instructions and data are stored in the same memory system (accessed in turn)
  * Harvard: instructions and data are stored in separated memory systems
  * Modified Harvard: relaxed separation (most common type: separated in caches backed by a common address space)
  
## OS
* Memory
  * Addressing
  * Management
* Processes
  * Synchronization
  * Communication
  * Address Space
  * System Calls
* Asynchronous
  * Time
  * Interrupts and Exceptions
  * Signals
* Device
  * File system
  * I/O Architecture and Device Driver
