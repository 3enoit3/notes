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
* base for Look Up Tables
### Arithmetic Logic Units
<br>![](https://cs.nyu.edu/courses/fall07/V22.0436-001/lectures/diagrams/alu-symbol.png)<br>
### Clocks
* clocking methodollogy: when data is valid and stable relative to the clock (edge-triggered clocking)
<br>![](https://cs.nyu.edu/courses/fall07/V22.0436-001/lectures/diagrams/clock.png)<br>
### Flipflops
## FPGA
### Generalities
* Composed of:
  * Logic blocs (Configurable Logic Bloc CLB)
  * Routing
  * I/O blocks
<br>![](https://www.allaboutcircuits.com/uploads/articles/Figure1_LUT.jpg)<br>
* Technology:
  * SRAM
  * Flash
  * Anti-fuse
### Configurable Logic Bloc (CLB)
* Transistors <-> Processors: NANDs, MUXs, LUTs, PALs
* Basic Logic Elements (BLEs) : LUTs + Flipflops + Multiplexors
<br>![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSQgAJwFn5wp0rOTyevMoViccLEa2jBjKeVG2KCPBB83i6wTxua)<br>
* CLBs contain a cluster of BLEs (4 to 10)
<br>![](https://image1.slideserve.com/1986670/fpga-architecture-2-3-n.jpg)<br>
### Routing
* Island-Style Routing
<br>![](https://image.slidesharecdn.com/2015-03-11-ieice-150311094144-conversion-gate01/95/fpga-5-638.jpg?cb=1426113772)<br>
<br>![](https://images.slideplayer.com/26/8671945/slides/slide_6.jpg)<br>
### Software flow
* Logic synthesis
  * HDL -> gates + flipflops : Directed Acyclic Graph DAG
* Techonology mapping
  * DAG -> independent k-LUTs
* Clustering/Packing
  * Independent k-LUTs -> clusters of k-LUTs : Logic Blocks
  * Algorithms:
    * Bottom-up
    * Top-down
* Placement
  * LB -> FPGA CLBs
  * Algorithms:
    * Simulated Annealing
    * Partionning
* Routing
  * FPGA CLBs -> FPGA routes
  * Algorithms:
    * Pathfinder
* Timing
  * FPGA CLBs + routes -> speed + slack
* Bitstream generation
  * FPGA CLBs + routes -> SRAM
## Zynq
* Programmable Logic (PL): FPGA
* Processing System (PS): Cortex A9
* AXI busses: connects PS to PL
