**RISK-V INSTRUCTION FORMAT AND INSTRUCTION TYPES**

#risc-v has 6 instruction types

they are classified as:

1.R-type(register type)

2.I-type(immediate type)

3.S-type(store type)

4.B-type(branch type)

5.U-type(upper immediate type)

6.J-type(jump type)

![risc v informat](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/44a340a2-a0c8-4d8f-8ba1-fc7d5f99ac9d)

above figure is explaining how each instruction occupying 32 bits and what makes the difference between each type

lets get into details of each type of instruction............

**R-type**

it has :

a.two source registers-Rs1,Rs2(each of 5-bits

b.one destination register-Rd(5-bits)

c.two functions-function3 (3-bits),function7(7bits)

d.opcode is 7 bits(0110011) it defines R-type

![r-type1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/54400be0-aef4-43e1-af4d-73e03a603050)


what is the operation here?......

based on function3 and function7 the operation is defined 
in above table ADD and SUB has same function3 value that is "000" but 30th bit value in function7 made difference in the same way every instruction has different function values which define them as shown in above table

![r type 2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/0d40a01c-3b5f-4dfd-bbe8-145bc4993e10)

here instructions are ADD,SUB,XOR,OR,SLA(shift left logic),SRL(shift right logic),SRA(shift right arithematic),slt(set lessthan),sltu(set lessthan unsigned)

**I-type**:

constant of 10bits will be replacing function and source register and that is immediate register(12bits)

![i type 1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/abe90461-12cf-454e-8a9e-bab16391073e)

The operations are performed between sourse register (Rs1) and constant value in immediate register so we need to make constant as 32 bit to make it compatable to Rs1 and sign bit is always bit 31,all immediates are sign extended always available at the left

Rd=Rs1+(operation)+immediate value

![i type 2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/9c6e6549-51ba-49a7-8f23-eb958c49556a)
The instructions of I-type are ADDI,SLTI,SLTIU,XORI,ORI,ANDI for shift operations the shift value is stored in "shamt[4:0]" whis is of 5bit of immediate value 
