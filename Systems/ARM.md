
# ARM 9
## Registers
* All modes
  * r0 - r15: general purpose registers
    * r7 : syscall number
    * r11 / **fp** : Frame Pointer (bottom of the stack frame)
    * r12 / **ip** : Intra Procedural
    * r13 / **sp** : Stack Pointer (top of the stack)
    * r14 / **lr** : Link Register (r15 return address on BL/BLX Branch with Link)
    * r15 / **pc** : Program Counter ([31:2] in ARM, [31:1] in Thumb)
  * CPSR: Current Program Status Register

## Load and store
* ldr R_to, \[R_@\_from]
* str R_from, \[R_@\_to]

## Function call
C++:
```c++
int i;

struct A {
    A() : i(42) {}
    int i;
};

void f(A a) {
    i = a.i;
    return;
}

int main(int argc, char* argv[]) {
    A a;
    f(a);
    return 33;
}
```
Gcc non-optimized assembly:
```asm
i:
A::A() [base object constructor]:
        str     fp, [sp, #-4]!   \ Prologue
        add     fp, sp, #0        |
        sub     sp, sp, #12       |
        str     r0, [fp, #-8]    /
        ldr     r3, [fp, #-8]
        mov     r2, #42
        str     r2, [r3]
        ldr     r3, [fp, #-8]
        mov     r0, r3
        add     sp, fp, #0       \ Epilogue
        ldr     fp, [sp], #4      |
        bx      lr               /
f(A):
        str     fp, [sp, #-4]!   \ Prologue
        add     fp, sp, #0        | 
        sub     sp, sp, #20       |
        str     r0, [fp, #-16]   /
        ldr     r3, [fp, #-8]    \ Body
        ldr     r2, .L4           | 
        str     r3, [r2]          |
        nop                      / return
        add     sp, fp, #0       \ Epilogue
        ldr     fp, [sp], #4      |
        bx      lr               /
main:
        push    {fp, lr}         \ Prologue
        add     fp, sp, #4        |
        sub     sp, sp, #16       |
        str     r0, [fp, #-16]    |
        str     r1, [fp, #-20]   /
        sub     r3, fp, #8       \ A::A()
        mov     r0, r3            |
        bl      A::A() [complete object constructor]
        ldr     r0, [fp, #-8]    \ f(A)
        bl      f(A)             /
        mov     r3, #33          \ return 33
        mov     r0, r3           /
        sub     sp, fp, #4       \ Epilogue    
        pop     {fp, pc}         /
```
Gcc optimized:
```asm
f(A):
        ldr     r3, .L3
        str     r0, [r3]
        bx      lr
.L3:
        .word   .LANCHOR0        // gcc "pointers": i is .LANCHOR0, even if it is L3 for f() and L6 for main()
main:
        mov     r2, #42
        ldr     r3, .L6
        mov     r0, #33
        str     r2, [r3]
        bx      lr
.L6:
        .word   .LANCHOR0
i:
```
# Links
https://azeria-labs.com/functions-and-the-stack-part-7/
