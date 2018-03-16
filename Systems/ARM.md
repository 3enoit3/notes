
# ARM 9
## Registers
* All modes
  * r0 - r15: general purpose registers
    * r13 = SP: Stack Pointer
    * r14 = LR: Link Register (r15 return address on BL/BLX Branch with Link)
    * r15 = PC: Program Counter ([31:2] in ARM, [31:1] in Thumb)
  * CPSR: Current Program Status Register
