# Computer Design
## Generalities
* **Instruction Set Architecture (ISA)**: Described hardware interface (ex: x86)
  * Machine code
* Microarchitecture: Implementation of an ISA
* **Application Binary Interface (ABI)**: Described machine code interface (ex: Linux Standard Base) 
  * OS ABI:
    * Processor instruction set (register file structure, stack organization, memory access types, ...) and basic data types (sizes, layouts, and alignments)
    * Function calling convention (register arguments, return value, stack order, ...) and system calls to OS
    * Executable file format (Executable and Linkable Format (ELF) for linux, Portable Executable (PE) for windows, ...)
    * C++ (name mangling, exception propagation, ...)
* **Application Programming Interface (API)**: Described code source interface (ex: POSIX)
  * Subroutine and protocols
