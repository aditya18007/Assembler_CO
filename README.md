# Assembler
Make two-pass assembler for the 12 bit accumulator architecture
--------------------------------------
|Opcode | Assembly Opcode   |Meaning |
|-------|--------------------|------------------|
|'0000'   |     'CLA'            | *Clear* accumulator |
|'0001'   |     'LAC'            | *Load* into accumulator **from address**|
|'0010'   |     'SAC'            | *Store* accumulator contents **into address**|
|'0011'   |     'ADD'            | *Add* **address** contents to accumulator contents|
|'0100'   |     'SUB'            | *Subtract* **address contents** from accumulator contents|
|'0101'   |     'BRZ'            | Branch **to address** if *accumulator contains **zero***|
|'0110'   |     'BRN'            | Branch **to address** if *accumulator contains **negative** value*|
|'0111'   |     'BRP'            | Branch **to address** if *accumulator contains **positive** value*|
|'1000'   |     'INP'            | Read from terminal and put **in address**|
|'1001'   |     'DSP'            | Display value **in address** on terminal|
|'1010'   |     'MUL'            | *Multiply accumulator contents* and **address contents**|
|'1011'  |     'DIV'            |*Divide accumulator contents* by **address content**. Quotient **in R1** and remainder in **R2**|
|'1100'   |     'STP'            | *Stop* execution|
