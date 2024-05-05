**STEPS TO USE SPIKE AND PK(PROXY KERNAL)**

I have followed the method in which spike and pk are pre-installed and i accessed them by using below commands

**1.compilling c code using gcc compiler**

$ riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

$ gcc sum1ton.c

$ ./a.out   

This commands provide output of sum of numbers from 1 to n using gcc compiler

**2.compiling and debugging c code using riscv compiler (Ofast)**

$ riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

$ spike pk sum1ton.o



This commands provide the output sum of numbers from 0 to n using riscv compiler

 ![1n](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/53d6d67c-8dca-4c6a-9c5e-e81e721f6012)

 
 
**3.after dumping the instructions**

we get the set of instruction involved in running our c code ,here are the instructions involed in execution

$ riscv64-unknown-elf-objdump -d sum1ton.o | less

2.   ![2n](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/ee239e38-e108-4eca-bbec-2c4f2a851564)



**3.debugging and analyzing each instruction**

$ spike -d pk sum1ton.o

1.(spike) until pc 0 101b0

the program counter is loaded with address "0 100bo"

2.(spike) reg 0 a0

register 0 is loaded contents of a0 that is "0x0000000000000001"

The content of register "a0" has been updated due to the lui a0,0x21 instruction. which loads the upper immediate value 0x21 into the upper bits of register "a0".The 0x prefix signifies that 21 is a hexadecimal value.

3.(spike) until pc 0  100b4

program conter loaded with next address of next instruction that is 0 101b4

4.(spike) reg 0 sp

The current value stored in the stack pointer "(sp)" is "0x3ffffffb50".Press enter to run the second instruction.

The addi sp,sp,-16 instruction in the compressed instruction set (rv64c) performs an addition of the immediate value -16 to the stack pointer (sp), effectively subtracting decimal 16 from the current value of the stack pointer.

The value of (16) in decimal is equivalent to (10) in hexadecimal. The stack pointer (sp) value before the execution of addi sp,sp, -16 was 0x3ffffffb50, and subtracting 0x10 from it yields "0x3ffffffb40".

![3n](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/f0c4a0b6-ca2a-4098-97be-d66fea8fc15b)








**COMPILING AND DEBUGGING C CODE WITH RISCV(O1)**

$ riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

$ spike pk sum1ton.o

$ spike -d pk sum1ton.o

![1nnnnn](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/99cd4648-9e18-49c2-8775-2f5d2cd3eb54)



**dumping the instructions**

$ riscv64-unknown-elf-objdump -d sum1ton.o | less

![1nn](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/fe9b39bd-bf54-4b4e-835a-e144f40ee479)





  
