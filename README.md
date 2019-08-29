# Assembler_CO
Make two-pass assembler for the 12 bit accumulator architecture

Opcode  Assembly Opcode     Meaning    
0000        CLA             Clear accumulator 
0001        LAC             Load into accumulator from address LAC
0010        SAC             Store accumulator contents into address SAC
0011        ADD             Add address contents to accumulator contents  ADD
0100        SUB             Subtract address contents from accumulator contents SUB
0101        BRZ             Branch to address if accumulator containszero BRZ
0110        BRN             Branch to address if accumulator containsnegative value BRN
0111        BRP             Branch to address if accumulator containspositive valueBRP
1000        INP             Read from terminal and put in address INP
1001        DSP             Display value in address on terminal DSP
1010        MUL             Multiply accumulator and address contents MUL
1011        DIV             Divide accumulator contents by address content. Quotient in R1 and remainder inR2 DIV
1100        STP             Stop execution STP
