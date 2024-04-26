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

**1.R-type(register type)**

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

**2.I-type(immediate type)**:

constant of 10bits will be replacing function and source register and that is immediate register(12bits)

it has one sourse register Rs1 and one destination register Rd (each of 5bit)

![i type 1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/abe90461-12cf-454e-8a9e-bab16391073e)

The operations are performed between sourse register (Rs1) and constant value in immediate register so we need to make constant as 32 bit to make it compatable to Rs1 and sign bit is always bit 31,all immediates are sign extended always available at the left

Rd=Rs1+(operation)+immediate value

![i type 2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/9c6e6549-51ba-49a7-8f23-eb958c49556a)
The instructions of I-type are ADDI,SLTI,SLTIU,XORI,ORI,ANDI for shift operations the shift value is stored in "shamt[4:0]" whis is of 5bit of immediate value 

**3.B-type(branch type)**:

This instruction is used for conditional statements(>,>=,<,<=,==,!=,....)

![b type 1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/f4a31058-a158-4a49-af64-634e7df8c0b1)

it has two sourse registers Rs1 and Rs2

It checks the condition between Rs1 and Rs2

a.if condition is "true":

pc=pc+immediate value(incrementing the pc) and jump to next address based on offset value

b.if condition is "false":

pc=pc+4(which execute next input)

![btype2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/507a009d-6c03-4790-b2ae-1d332de25b1b)

Branch instruction are: BEQ(equal to),BNE(not eqial to),BLT(lessthan),BGE(greaterthan),BLTU(lessthan unsigned,BGEU(greaterthan unsigned)

To calculate offset address we need to compose immediate value:IMMD={SXT(IMM[12:1],1'B0}
meaning of above expression is "immediate value is sign extension of immediate value[12:1] and 1st bit at LSB is 0"

**4.S-type(store type)**

1.opcode for "load" is 0000011

2.opcode for "store" is 0100011

![load store 1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/96aa2770-08fa-41e6-af0d-9bb72e2d5146)

**store**

we use STORE instruction to write values into register

address is calculated from Rs1 and immediate value and the value at that location is stored with Rs2 value

address=Rs1+sxt(imm[11:0])
Function defines type of operation:(store hallf word,store full word)

**load**

used to read memory,reads data at particular location and store in Rd(destination) 

let base=0
address=0+offset[11:0]

![load store 2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/3fc853ba-0c66-40e4-839e-38a60ed78c10)

![load store 3](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/196c0e7e-d116-4c55-925a-5bdd77c65c9b)

The instructions are :LB(LOAD BYTE),LH(LOAD HALFWORD),LW(LOAD WORD).,.......


**5.J-type(jump type)**

1.JAL(JUMP AND LINK)

IMMD={sxt(imm[20:1]),1'b0

pc=pc+IMMD(jump addres)

Rd=pc+4(next instruction address)

![jump 1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/b0dd1861-870b-4e8a-bc44-e0ae5462f5a7)

This instruction is used to jump to particular location and address is defined by immediate value and stores next instruction addres in link register

2.JALR(JUMP AND LINK REGISTER)
it is a immediate type ,it is used for long jump

Target address is stored in a register and next instruction address aslo storing address instruction following the JALR instruction into destination register 

JALR:Rd=pc+4,pc={Rs1+immi),1'b0}  here Rs1 is the reason for long jump


![jump 2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/730eddf4-ca29-4346-a7e0-ee24f027fa49)

**IDENTIFYING INSTRUCTIONS AND THEIR OPERATIONS(APPLICATION)**:

![example insructions](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/048fa935-ce74-4284-985c-1ff45ea536d8)

lets solve above instructions with examples.......

**1.add r6,r2,r1**

it is R-type,R2 and r1 are source registers,r6 is destination register

let:   R1=00100,R2=01001

R1+R2=rd=01101

0000000 01001 00100 000 01101 0110011 (funct7   rs2   rs1 fun3   rd  opcode ) 32 bit instruction each followed by format

**2.sub r7,r1,r2**

R7----- destination

r1----- source1

r2------source2

let:   r1=10000, r2=00110

R1 sub R2=r7=01010

32bit code is:0100000 00110 10000 000 0110011


 
