# General Format of an instruction    
  
`/*`    
*Comments*    
`*/`    

`Label` **:** `Opcode` *operands* **;** `//`*Comments*    
  
--------------
|Token |What |Usage|
|-----|-----|-----|
| `Label` |Any Valid Variable name |Used to mark an instruction as well as Data.Instruction may or may not contain Label. **Compulsary** to mark an instruction when using `Branching` Operation. **ALSO , when declaring a variable `Label` should clearly be `DATA` OR when assigning value to a variable , `Label` must be `DATA`**. `SEE` : Labels | 
|`:` | To be used after *Label*. **To be used even if there is no `Label`**| Tells the assembler about end of label. **Every Instruction must use :** *Throws an error otherwise* |
|`Opcode` | The string representing instruction.|**Must be from the list given below.** If not , throw an error|
|`Operands` | Operands to be used with Opcode. | **Must be defined in this procedure** , **Variable name should be valid** , **Number of operands must be equal to those demanded by Opcode** |
|`;` | End of Instruction | **Compulsary to use in every instruction. if `:` is reached directly after `;` Or file ends and `;` is not present , then throw error.**|
|`\\` | Single line comments | Everything after `;` is ignored **as long as it is in same line**|
|`/*`  *Comments*  `*/` | Multi-line comments | Everything in between `/\*` and  `\*/` is ignored. **Throw error if either of two is missing**|  


# Labels   
   
Labels are of two types : 
-----------------------
Variable Types | What |
|-------------|------|
|`ADDRESS` | Represents an address. Defined as `Label`|
|`DATA` | Represents Data eg. 2,5,16 etc., Declared explicitly|
    
`DATA` is a reserved keyword. Whenever defining a variable the label must clearly be `DATA`.    
`General Format` DATA : *type* **variable name** , *value* **;**    
Eamples :     
`>>` DATA : int y , 10 ; //variable y declared and assigned value 10    
`>>` DATA : int y ; //variable y declared but not assigned any value.    
`>>` DATA : y = 10 ; //Already assigned vaiable attached a value.    

`ADDRESS` is **not a keyword**. Any valid variable name can be used to mark address of an instruction    
Examples :   
`>>` Addition : Add x ; //Labeled Addition     
`>>` : BRZ Addition ; // No label to it. But can jump to "Address"    

`VALID VARIABLE NAME` :    
1) Can contain English alphabets , digits 0-9 and **only one special character** `_`.     
2) **Cannot** Start with a digit.   
3) **Cannot contain** tabs , spaces new line etc.     

**Possible Errors**    

1)Variable name not valid    
2)Variable is already declared    

# Opcodes   
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
|`CLA` |-| 
|`LAC` `x` | **Variable not defined** , **Variable Type : `DATA` expected ** , **Value not assigned to variable**|
|`SAC` `x` | **Variable not defined** , **Variable Type : `DATA` expected ** , **Value not assigned to variable**|
|`ADD` `x` | **Variable not defined** , **Variable Type : `DATA` expected ** , **Value not assigned to variable**|
|`SUB` `x` | **Variable not defined** , **Variable Type : `DATA` expected ** , **Value not assigned to variable**|
|`BRZ` `ADDRESS` | **Variable not defined** , **Variable Type : `ADDRESS` expected **|
|`BRN` `ADDRESS` | **Variable not defined** , **Variable Type : `ADDRESS` expected **|
|`BRP` `ADDRESS` | **Variable not defined** , **Variable Type : `ADDRESS` expected **|
|`INP` `x` |   **Variable not defined** , **Variable Type : `DATA` expected ** , **Value not assigned to variable**|
|`DSP` `x` | **Variable not defined** , **Variable Type : `DATA` expected ** , **Value not assigned to variable**|
|`MUL` `x` | **Value not defined** ,**Variable Type : `DATA` expected ** , **Value not assigned to variable**|
|`DIV` `x` , `R1` , `R2`  | **Variable not defined , Zero division error , Variable Type : `DATA` expected  , Value not assigned to variable**|
|`STP`|*If anything after* `STP` , **Not reachable Code**|
    
    
# Errors Defined
<pre>     
(1) typeMismatchError :          
        (i) `DATA` expected and `ADDRESS` passed and ice-versa.                
        (ii) In `ADD`,`MUL`,`SUB`,`DIV` Type of opperand different from accumulator type.         
        (iii) Variable defied type `A` and found to be type `B`.         
        
(2) variableError :         
        (i) Variable name invalid.     
        (ii) Variable not defined.     
              (a) `ADDRESS` not defined,     
              (b) `DATA` not defined,     
        (iii) Value not assigned.      

(3) syntaxError :     
        (i)`:` missing.     
        (ii) `;` missing.     
        (iii) Opcode invalid.    
        (iv) Possible variable defination , but not labelled `DATA`     
        (v) Multiline comment :   
            (a) Not starting , but ending.     
            (b) Not ending but start found.
            
(4) mathEror :       
    (i)zeroDivisionError       
