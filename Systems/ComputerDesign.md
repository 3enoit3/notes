# Computer Design
## Generalities
* **Instruction Set Architecture (ISA)**: Describes hardware interface (ex: x86)
  * Machine code
  * *Classification: Reduced Instruction Set Computer (RISC - ex: ARM) vs Complex Instruction Set Computer (CISC - ex: x86)
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
