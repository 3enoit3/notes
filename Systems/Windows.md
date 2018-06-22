# C++
* Argument Passing
On x86 plaftorms:
  * **Arguments**: widened to 32 bits, pushed onto the stack from right to left
  * **Return values**:
    * 32 bits are widened to 32 bits and returned in EAX
    * 64 bits structures are returned in EDX:EAX
    * larger structures are returned in EAX as pointers to hidden return structures
    * Non-POD structures are not returned in registers
  * **Registers**: the compiler generates prolog and epilog code to save and restore the ESI, EDI, EBX, and EBP registers, if they are used in the function.
  * **Calling Conventions**
    * \__cdecl: stack is cleaned up by the caller (it pops passed arguments after the call)
    * \__stdcall: stack is cleaned up by the callee (it pops its own arguments)

# Tools
* Binary content
```bash
dumpbin /exports my.dll
```
