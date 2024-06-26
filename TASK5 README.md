**TASK-5 : SIMULATION OF VCD FILE USING IVERILOG AND GTKWAVE TOOLS**

**1.Ccreating a new directory**

$ cd Desktop

$ mkdir naveen

$ cd naveen

**2.creating  .v and tb.v file (iv_gt.v and iv_gt_tb.v) in github repo**

$ git clone https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship.git

$ cd Vsdquadron-mini-internship

**3.To run and simulate verilog code**

$ iverilog -o Vsdquadron-mini-internship iv_gt.v iv_gt_tb.v

$ vvp Vsdquadron-mini-internship

**4. To view simulation waveform in GTKwave**

$ gtkwave iv_gt.vcd


![1it](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/8106b057-efed-4036-81dc-351970e70299)





![lstr ivtb](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/accf9448-1862-4ea4-a59c-5eec0260d3e5)



![vcd last](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/0e74edd6-3049-493d-b404-ff7e98762a83)



![last iv](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/3bee923d-5f56-4d9f-80f2-33264199ef77)



![last2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/cef1461c-d10e-47f4-a29d-dbc82d6097d0)


**Tables of instructions defined with a specific hexa number**

<img width="288" alt="ins values" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/d41b5619-8b08-49ef-bb41-56a134da6942">


**1.Add r6,r1,r2**

<img width="330" alt="addi r11,4,5" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/3d662750-c117-44f1-b02d-01330a5f40d2">

A=1,B=2,R16 is stored with 003

**2.sub r7,r1,r2**

<img width="365" alt="sub" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/858bd39d-883e-494c-a800-df72f2febb83">

 r1 is 1 and r2 is 2, r17 is -1

 **3.And r8,r1,r3**

<img width="336" alt="and binary binry" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/a4201278-1a30-4359-9274-d2aed888f42b">

 r1= 0001 ,r2=0101,and r8 is stored with 101

 **4.or r10,r1,r4**

 <img width="336" alt="orbinary" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/3c08a311-ba83-4b76-8386-7ca2fee268b5">
 
 r1=0001,r4=0100 and r10 is stored with 0101

 **5.xor r10,r1,r4**

 <img width="335" alt="xor r1 and r10" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/597a0537-0f22-4ae2-a205-58c69202080d">

 r1=0010,r2=0100 and r10 is stored with 0110

 **6.slt r11,r2,r4**

 r4=5,r2=2 is shifted 5 times and result is stored in r11 as 00001

 **7.addi r12,r4,5**

 <img width="330" alt="addi r11,4,5" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/09f5cd65-1953-4f30-b2a4-844994071cd9">

 r4=4 and it is added with immediate value 5 and get stored in r12 that is  00009

 **8.BEQ r0,r0,15**

 <img width="332" alt="beq ro,ro,15" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/dc6f5462-7ca7-4f59-9e40-62132556f42f">

 r0==ro  so it jumps to location of 15 addresses from present location so so r0=0000 then it jumps to 00f

 **9.LW R13,R1,2**

 <img width="335" alt="LW R13,R1,2" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/6dc44bad-2077-4408-a64b-32898570e50b">

 R1=01,R2=02 and R13 is loaded with content at memory address 03

 **10.SW R3,R1,2**
 
<img width="336" alt="SW INS" src="https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/9eab462e-20eb-4ba4-9079-225348d89580">

RD=03 after R1=01 and immediate value is 02 then "ID EX IMMEDIATE" is stored with 02 which is content from R3=03



 
