# Assembler
Make two-pass assembler for the 12 bit accumulator architecture
--------------------------------------
|Opcode | Assembly Opcode   | Parameters |Meaning |
|-------|--------------------|-----------|------------------|
|`0000`   |     `CLA`            | - |*Clear* accumulator |
|`0001`   |     `LAC`            | &`x` |*Load* into accumulator **from address**|
|`0010`   |     `SAC`            | &`x` |*Store* accumulator contents **into address**|
|`0011`   |     `ADD`            | &`x` |*Add* **address** contents to accumulator contents|
|`0100`   |     `SUB`            | &`x` |*Subtract* **address contents** from accumulator contents|
|`0101`   |     `BRZ`            | &`x` |Branch **to address** if *accumulator contains **zero***|
|`0110`   |     `BRN`            | &`x` |Branch **to address** if *accumulator contains **negative** value*|
|`0111`   |     `BRP`            | &`x` |Branch **to address** if *accumulator contains **positive** value*|
|`1000`   |     `INP`            | &`x` |Read from terminal and put **in address**|
|`1001`   |     `DSP`            | &`x` |Display value **in address** on terminal|
|`1010`   |     `MUL`            | &`x` |*Multiply accumulator contents* and **address contents**|
|`1011`   |    `DIV`             | &`x` |*Divide accumulator contents* by **address content**. Quotient **in R1** and remainder in **R2**|
|`1100`   |     `STP`            | -  |*Stop* execution|

-----------------------------------------------------------------------
Assemble Opcode | Possible Errors|
|--------------|------------------|
|`CLA` || 
|`LAC` &`x` | **Value in address not defined**|
|`SAC` &`x` | **Value in address not defined**|
|`ADD` &`x` | **Value in address not defined**|
|`SUB` &`x` | **Value in address not defined**|
|`BRZ` &`x` | **Value in address not defined**|
|`BRN` &`x` | **Value in address not defined**|
|`BRP` &`x` | **Value in address not defined**|
|`INP` &`x` | **Value in address not defined**|
|`DSP` &`x` | **Value in address not defined**|
|`MUL` &`x` | **Value in address not defined**|
|`DIV` &`x` | **Value in address not defined** , **Zero division error**|
|`STP`||
