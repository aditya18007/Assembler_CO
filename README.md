# Assembler
Make two-pass assembler for the 12 bit accumulator architecture   
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

**General Format of an instruction**    
  
`/*`    
*Comments*    
`*/`    

`Label` **:** `Opcode` *operands* **;** `//`*Comments*    
  
--------------
|Token |What |Usage|
|-----|-----|-----|
| `Label` |Any Valid Variable name |Used to mark an instruction as well as Data.Instruction may or may not contain Label. **Compulsary** to mark an instruction when using `Branching` Operation. **ALSO , when declaring a variable `Label` should clearly be `DATA`**. For example `>>`   
DATA : int x , 10 ; //x is defined an assigned value 10.   
`>>`   
DATA : int y ; //Variable is declared. **Must be assigned value , else throw error**   
`>>`   
DATA : y , 10 ;//Variable assigned value. **Throw error if y is declared before**    
| 
|`:` | To be used after *Label*. **To be used even if there is no `Label`**| Tells the assembler about end of label. **Every Instruction must use :** *Throws an error otherwise* |
|`Opcode` | The string representing instruction.|**Must be from the list given below.** If not , throw an error|
|`Operands` | Operands to be used with Opcode. | **Must be defined in this procedure** , **Variable name should be valid** , **Number of operands must be equal to those demanded by Opcode** |
|`;` | End of Instruction | **Compulsary to use in every instruction. if `:` is reached directly after `;` Or file ends and `;` is not present , then throw error.**|
|`\\` | Single line comments | Everything after `;` is ignored **as long as it is in same line**|
|`/\*`  *Comments*  `\*/` | Multi-line comments | Everything in between `/\*` and  `\*/` is ignored. **Throw error if either of two is missing|  

-----------------------
Variable Types | What |
|-------------|------|
|`ADDRESS` | Represents an address. Defined as `Label`|
|`DATA` | Represents Data eg. 2,5,16 etc., Declared explicitly|

-----------------------------------------------------------------------
Assemble Opcode | Possible Errors|
|--------------|------------------|
|`CLA` |-| 
|`LAC` `x` | **Value not defined** , **Variable Type : `DATA` expected **|
|`SAC` `x` | **Value not defined** , **Variable Type : `DATA` expected **|
|`ADD` `x` | **Value not defined** , **Variable Type : `DATA` expected **|
|`SUB` `x` | **Value not defined** , **Variable Type : `DATA` expected **|
|`BRZ` `ADDRESS` | **Value not defined** , **Variable Type : `ADDRESS` expected **|
|`BRN` `ADDRESS` | **Value not defined** , **Variable Type : `ADDRESS` expected **|
|`BRP` `ADDRESS` | **Value not defined** , **Variable Type : `ADDRESS` expected **|
|`INP` `x` |   **Variable Type : `DATA` expected **|
|`DSP` `x` | **Warning : Value not defined in this routine** , **Variable Type : `DATA` expected **|
|`MUL` `x` | **Value not defined** ,**Variable Type : `DATA` expected **|
|`DIV` `x` , `R1` , `R2`  | **Value not defined** , **Zero division error** , **Variable Type : `DATA` expected **|
|`STP`|*If anything after* `STP` , **Not reachable Code**|
