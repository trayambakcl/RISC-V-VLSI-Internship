# RISC-V INSTRUCTION TYPES
## The RISC-V has various types of instruction formats which we can be grouped in two types : 
#### BASE INSTRUCTION FORMATS :
In the base RV32I ISA , there are four main instruction formats mainly the R-Type , I - type , S - type and U - type .
All are 32 bits long.The base ISA has IALIGN=32, meaning that instructions must be aligned on a four-byte boundary in memory.
If there is an misalignment an exception is taken such it branches or there will occur an unconditional jump , techincally *instruction-address-misaligned exception*.

![image](https://github.com/user-attachments/assets/ba58b088-d2c8-4fe9-bf97-87fd1d983aef)

**As in the image there are source resistors termed as **rs** *(These are the registers that hold the input values for a particular operation or instruction)*.  and destination resisters **rd** *(This register holds the result of the operation performed by the instruction.)* . The **funct3** is a 3-bit field *(field refers to a specific segment or portion of an instruction that contains particular information necessary for the processor to execute that instruction)*  and **funct7** a 7-bit field  and opcode *(an instruction that specifies the operation to be done by the processor)* and imm[x:y] means that the immediate value *(a constant data value embedded directly within an instruction)* is derived from the bits in the instruction ranging from position y to position x.
The RISC-V ISA keeps the source (rs1 and rs2) and destination (rd) registers at the same position in all
formats to simplify decoding.**

####  Immediate Encoding Variants 
There are a further two variants of the instruction formats   based on the handling of immediates namely B-Type and J-Type


![image](https://github.com/user-attachments/assets/fda21dc2-3feb-49a3-9fd8-9af8128fd977)
![image](https://github.com/user-attachments/assets/b624e997-6112-40cd-9702-5d9823d0a4b7)

____________________________________________________________________________________________________________________________

### **R-TYPE** : 

![image](https://github.com/user-attachments/assets/5e7a9d07-6329-4bef-921f-fb0dae0cbe1f)


the R-Type is an instruction format in the RISC-V architecture to perform arithmetic and logical operations using registers.
As from above

opcode(6-0)  identifies the operation to be performed (add,subtract,etc) ,

rd(11-7) is the destination register  where the result is stored ,

funct3(14-12) specifies the operation within the opcode category ,

rs1(19-15) indicates the first source register that contains one of the operands for the operation ,

rs2(24-20) indicates the 2nd source register that contains the other operand for the operation ,

funct7(31-25) provides the operation, aloowing for more variations of instructions that share the same opcode and funct3 values.



### **I-Type** :

![image](https://github.com/user-attachments/assets/9e4042df-ee63-4428-b8ba-95d41067dc30)

the  I-Type instruction format in the RISC-V architecture is designed for operations that involve immediate values and registers. 

opcode(6-0)  identifies the operation to be performed (load,add immediate) ,

rd(11-7) is the destination register  where the result is stored ,

funct3(14-12) specifies the operation within the opcode category ,

rs1(19-15) indicates the first source register that contains one of the operands for the operation ,

imm[11:0] (31:20) is a 12 bit immediate value which is a constant directly embedded in the instruction.

### **S-Type** :

![image](https://github.com/user-attachments/assets/0a634506-04d6-48f3-a015-90e53db5c9fd)

the S-Type instruction format in the RISC-V architecture is specifically designed for store operations, which involve writing data from registers to memory.

opcode(6-0) identifies the operation to be performed (SW - for store word) ,

imm[4:0] (11-7) these 5 bits of the immediate value specifies an offset *(an offset is an adjustment made to an address)* to be added to the address in rs1 ,

funct3(14-12) specifies the type of storage operation ,

rs1(19-15) first source register that contains the base address where data will be stored ,

rs2(24-20) 2nd source register that contains the data to be stored in memory ,

imm[11:5] (31:25) 7 bits of upper immediate value which complete 12 bit immediate value used as an offset ,


### **U-Type** :

![image](https://github.com/user-attachments/assets/063ad859-81ec-4f4a-a303-f0f555936882)

the U-Type instruction format in the RISC-V architecture is designed for operations that involve a 20-bit immediate value, primarily used for loading upper immediate values into registers. 

opcode(6-0) identifies the operation to be performed (LUI - for loading an upper immediate value) ,

rd(11-7) destination register where the result of the operation will be stored ,

imm[31:12] (31:12) 20 bit immediate value which is loaded into the upper part of the destination structure


### **B-Type** :

![image](https://github.com/user-attachments/assets/2ca54226-95ae-4225-aed6-a7bbc2363a82)

the B-Type instruction format in the RISC-V architecture is primarily used for branch instructions, which control the flow of a program based on certain conditions.

opcode(6-0) identifies the operation to be performed (BEQ - equals to , BNE - not equal to) ,

funct3(14-12) specifies the type of branch operation ,

rs1(19-15) is a first source register that contains one of the oprands for the comparision ,

rs2(24-20) the 2nd register that contains the operand for the comparision ,

imm[4:1] (11:7) the lower bits of the immediate value used as part of the offset ,

imm[10:5] (30:25) the middle bits of the immediate value which are also part of the offset for branching ,

imm(1 bit) sign bit of the immediate value, which is used to complete the 13-bit immediate offset for branching .


### **J-Type** :

![image](https://github.com/user-attachments/assets/143c16f6-d955-4954-b870-ba0ef1616d87)

the J-Type instruction format in the RISC-V architecture is specifically used for jump instructions, which allow for unconditionally transferring control to a new instruction address.

opcode(6-0) identifies the operation to be performed (JAL - jump and link) ,

rd(11-7) destination register where the return address will be stored ,

imm[19:12] (31:12) middle bits of the immediate value which are part of the target address to jump to ,

imm(1 bit) sign bit of the immediate value,which helps in determining the direction of the jump ,

imm[10:1] (30:21) lower bits of the immediate value which are also part of the target address for jumping ,

imm(1 bit) this bit is included to help with sign extension when calculating the jump address .
