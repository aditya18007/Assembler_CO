# Assembler
Make two-pass assembler for the 12 bit accumulator architecture  
**General Format of an instruction**  

`/\*`  
*Comments*  
`\*/`  

`Label` **:** `Opcode` *operands* **;** `//`*Comments*  
  
--------------
|Token |What |Usage|
|-----|-----|-----|
| `Label` |Any Valid Variable name |Used to mark an instruction.Instruction may or may not contain Label.**Compulsary** to mark an instruction when using `Branching` Operation.| 
|`:` | To be used after *Label*. **To be used even if there is no `Label`**| Tells the assembler about end of label. **Every Instruction must use :** *Throws an error otherwise* |
|`Opcode` | The string representing instruction.|**Must be from the list given below.** If not , throw an error|
|`Operands` | Operands to be used with Opcode. | **Must be defined in this procedure** , **Variable name should be valid** , **Number of operands must be equal to those demanded by Opcode** |
|`;` | End of Instruction | **Compulsary to use in every instruction. if `:` is reached directly after `;` Or file ends and `;` is not present , then throw error.**|
|`\\` | Single line comments | Everything after `;` is ignored **as long as it is in same line**|
|`/\*`  *Comments*  `\*/` | Multi-line comments | Everything in between `/\*` and  `\*/` is ignored. **Throw error if either of two is missing|  


--------------------------------------
|Opcode | Assembly Opcode   | Parameters |Meaning |
|-------|--------------------|-----------|------------------|
|`0000`   |     `CLA`            | - |*Clear* accumulator |
|`0001`   |     `LAC`            | `x` |*Load* into accumulator **from address**|
|`0010`   |     `SAC`            | `x` |*Store* accumulator contents **into address**|
|`0011`   |     `ADD`            | `x` |*Add* **address contents** to accumulator contents|
|`0100`   |     `SUB`            | `x` |*Subtract* **address contents** from accumulator contents|
|`0101`   |     `BRZ`            | `ADDRESS` |Branch **to address** if *accumulator contains **zero***|
|`0110`   |     `BRN`            | `ADDRESS` |Branch **to address** if *accumulator contains **negative** value*|
|`0111`   |     `BRP`            | `ADDRESS` |Branch **to address** if *accumulator contains **positive** value*|
|`1000`   |     `INP`            | `x` |Read from terminal and put **in address**|
|`1001`   |     `DSP`            | `x` |Display value **in address** on terminal|
|`1010`   |     `MUL`            | `x` |*Multiply accumulator contents* and **address contents**|
|`1011`   |    `DIV`             | `x` , `R1` , `R2` |*Divide accumulator contents* by **address content **. Quotient **in R1** and remainder in **R2**|
|`1100`   |     `STP`            | -  |*Stop* execution|

-----------------------------------------------------------------------
Assemble Opcode | Possible Errors|
|--------------|------------------|
|`CLA` || 
|`LAC` `x` | **Value in address not defined** , **Value expected**|
|`SAC` `x` | **Value in address not defined** , **Value expected**|
|`ADD` `x` | **Value in address not defined** , **Value expected**|
|`SUB` `x` | **Value in address not defined** , **Value expected**|
|`BRZ` `x` | **Value in address not defined** , **Address expected**|
|`BRN` `x` | **Value in address not defined** , **Address expected**|
|`BRP` `x` | **Value in address not defined** , **Address expected**|
|`INP` `x` |   **Address expected**|
|`DSP` `x` | **Warning : Value not defined in this routine** , **Address expected**|
|`MUL` `x` | **Value in address not defined** , **Value expected**|
|`DIV` `x` | **Value in address not defined** , **Zero division error** , **Value Expected**|
|`STP`||
