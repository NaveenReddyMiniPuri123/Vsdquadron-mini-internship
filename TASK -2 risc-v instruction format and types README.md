**RISK-V INSTRUCTION FORMAT AND INSTRUCTION TYPES**

#risc-v has 6 instruction types

they are classified as:

1.R-type(register type)

2.I-type(immediate type)

3.S-type(store type)

4.B-type(branch type)

5.U-type(upper immediate type)

6.J-type(jump type)


![instruction format](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/45e9906d-8357-485b-8b13-8e3884653f1c)

above figure is explaining how each instruction occupying 32 bits and what makes the difference between each type

lets get into details of each type of instruction............

**1.R-type(register type)**

it has :

a.two source registers-Rs1,Rs2(each of 5-bits

b.one destination register-Rd(5-bits)

c.two functions-function3 (3-bits),function7(7bits)

d.opcode is 7 bits(0110011) it defines R-type

![r-type1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/cdb8d060-f86c-4ac0-b783-649bf185cd3b)

what is the operation here?......

based on function3 and function7 the operation is defined 
in above table ADD and SUB has same function3 value that is "000" but 30th bit value in function7 made difference in the same way every instruction has different function values which define them as shown in above table

here instructions are ADD,SUB,XOR,OR,SLA(shift left logic),SRL(shift right logic),SRA(shift right arithematic),slt(set lessthan),sltu(set lessthan unsigned)

**2.I-type(immediate type)**:

constant of 10bits will be replacing function and source register and that is immediate register(12bits)

it has one sourse register Rs1 and one destination register Rd (each of 5bit)

![immediate1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/bec62784-4c00-40c4-bcab-0f2cece41a82)

The operations are performed between sourse register (Rs1) and constant value in immediate register so we need to make constant as 32 bit to make it compatable to Rs1 and sign bit is always bit 31,all immediates are sign extended always available at the left

Rd=Rs1+(operation)+immediate value

![immediate2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/8ea3006c-1f0f-48c3-9499-f601f6a9fb02)

The instructions of I-type are ADDI,SLTI,SLTIU,XORI,ORI,ANDI for shift operations the shift value is stored in "shamt[4:0]" whis is of 5bit of immediate value 

**3.B-type(branch type)**:

This instruction is used for conditional statements(>,>=,<,<=,==,!=,....)

it has two sourse registers Rs1 and Rs2

![branch1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/7d7eb444-c31a-47dc-9872-19f95f27b819)

It checks the condition between Rs1 and Rs2

a.if condition is "true":

pc=pc+immediate value(incrementing the pc) and jump to next address based on offset value

b.if condition is "false":

pc=pc+4(which execute next input)

Branch instruction are: BEQ(equal to),BNE(not eqial to),BLT(lessthan),BGE(greaterthan),BLTU(lessthan unsigned,BGEU(greaterthan unsigned)

To calculate offset address we need to compose immediate value:IMMD={SXT(IMM[12:1],1'B0}
meaning of above expression is "immediate value is sign extension of immediate value[12:1] and 1st bit at LSB is 0"

**4.S-type(store type)**

1.opcode for "load" is 0000011

2.opcode for "store" is 0100011

![store1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/f00c9630-ad37-4617-ba5c-fe027e45953a)

**store**

we use STORE instruction to write values into register

address is calculated from Rs1 and immediate value and the value at that location is stored with Rs2 value

address=Rs1+sxt(imm[11:0])
Function defines type of operation:(store hallf word,store full word)

**load**

used to read memory,reads data at particular location and store in Rd(destination) 

let base=0
address=0+offset[11:0]

![store2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/7d81e5e6-85ac-4c15-af66-0628b7a6fb7a)

The instructions are :LB(LOAD BYTE),LH(LOAD HALFWORD),LW(LOAD WORD).,.......


**5.J-type(jump type)**

1.JAL(JUMP AND LINK)

IMMD={sxt(imm[20:1]),1'b0

pc=pc+IMMD(jump addres)

Rd=pc+4(next instruction address)

![jump1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/07941c88-4cdc-42f3-bf63-5c0ebab8e9a2)

This instruction is used to jump to particular location and address is defined by immediate value and stores next instruction addres in link register

2.JALR(JUMP AND LINK REGISTER)
it is a immediate type ,it is used for long jump

Target address is stored in a register and next instruction address aslo storing address instruction following the JALR instruction into destination register 

![jump2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/bc9181d9-43d9-4054-8b9f-9fbb65773952)

JALR:Rd=pc+4,pc={Rs1+immi),1'b0}  here Rs1 is the reason for long jump


**IDENTIFYING INSTRUCTIONS AND THEIR OPERATIONS(APPLICATION)**:

![list of instructions](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/b467d84e-abc4-498e-a09a-8a19b06fbaea)

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

**3.and r8,r1,r3**
r8---- destination

r1 and r3 sources

let :r1=00110,R2=10110

R1 and R2 = Rd=00110

32 bit code: 0000000 10110 111 00110 0110011

**4.or r9,r2,r5**

R9 ----- destination

r2-------source1

r5-------source2

let:R1=00000,R2=11111

R1 or R2=Rd=11111

32bit code:0000000 11111 00000 110 11111 0110011

**5.SLT r11,r2,r4 (set lessthan)**

r11------destination

r2-------source1

r4-------source2

let: r2=00010,r4=10000

r2<r4==True,set r11 to 1

r11=00001

32bit code:0000000 00010 010 00001 0110011

**6.addi r12,r4,5**
r4--- source

5----immediate

let r4=01000

r4+5=01101

32bit code= 000000000101 01000 000 01101 0010011

**7.SW r3,r1,2(store word)**

r3 having data "16"-10000

r1 having address "12" -01100

immediate value=IMMD=2-00010

store address=rs1+immd
 
store addre=14
 
data "16" from r3 is stored at location "14"

32 bit:0000000 00010 01100 010 00010 0100011

**8.LW r13,r1,2(load word)**
 
let: r1 having address=12-01100

immd=2-00010

immd+r1=14

load the value to r13 from location 14

32bit:000000000010 01100 010 01110

**9.beq r0,r0,15**

The content in r0 will be always equal to itself

ro==ro

32bit: 0 000000 00000 00000 000 11110 1100011

pc=pc+15;program counter will execute instruction after 15 instructions from current instruction

**10.bne r0,r1,20**

if ro!=r1-- if it is true

pc=pc+20----execute 20th instruction from current instruction

if r0!=r1---if it is false

pc=pc+4 executes next instruction

**11.SLL r15,r1,r2(2)**

r2(2) is the  left-shift amount to be performed on r1

let: r1= 00110

1shift =01100

2shift=11000=24

24 is stored into r15

**12.SRL r16,r14,r2(2)**

 r2(2) is the right-shift amount to be performed on r1

 let:r14=6--00110

 1shift=00011

 2shift=00001=1
 1 is stored into r16
 









 
