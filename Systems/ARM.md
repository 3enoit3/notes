
# ARM 9
## Registers
* All modes
  * r0 - r15: general purpose registers
    * r13 / sp: Stack Pointer
    * r14 / lr: Link Register (r15 return address on BL/BLX Branch with Link)
    * r15 / pc: Program Counter ([31:2] in ARM, [31:1] in Thumb)
  * CPSR: Current Program Status Register
