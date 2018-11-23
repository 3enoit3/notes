# Hardware
## Gates
<br>![](https://physicsabout.com/wp-content/uploads/2018/02/logic-gates-min-300x181.png)<br>
All logical functions can be implemented with:
* AND, OR and NOT
* NOR or NAND (universal)
## Combitional Logic
### Decoders
* input: n bits  -> output: 2^n bits (called n-to-2^n decoder)
<br>![](https://cs.nyu.edu/courses/fall07/V22.0436-001/lectures/diagrams/decoder.png)<br>
### Multiplexors
* input: n selector/control bits + m data bits -> output: 1 data bit
<br>![](https://cs.nyu.edu/courses/fall07/V22.0436-001/lectures/diagrams/mux4.png)<br>
### Programmable Logic Arrays
* canonical form or two-level representation: 
  * every input is either a  true  or  complemented  variable
  * two levels of gates (AND then OR or OR then AND)
  * every output is either a  true  or  complemented  variable
* sum (OR) of products (AND): A.B + C.D ... (product of sums also exists)
<br>![](https://cs.nyu.edu/courses/fall07/V22.0436-001/lectures/diagrams/pla3.png)<br>
### Read Only Memories
* input: n address bits (2^n adressable entries: height) -> output: m data bits (width)
* fully decoded: it contains a full output word for every possible input
### Arithmetic Logic Units
<br>![](https://cs.nyu.edu/courses/fall07/V22.0436-001/lectures/diagrams/alu-symbol.png)<br>
### Clocks
* clocking methodollogy: when data is valid and stable relative to the clock (edge-triggered clocking)
<br>![](https://cs.nyu.edu/courses/fall07/V22.0436-001/lectures/diagrams/clock.png)<br>

## Zynq
* Programmable Logic (PL): FPGA
* Processing System (PS): Cortex A9
* AXI busses: connects PS to PL
