**TASK-3**

**COMPILING C PROGRAMME USING RISCV COMPILER**

**A).followed below command to install leafpad**

$cd

$leafpad sum1ton.c &

$sudo apt install leafpad

**B).execution of c program**

$gcc sum1ton.c

$ls -ltr

$./a.out


![sum1ton output](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/4ebbb5e3-dc19-499c-a01a-e6f35484ba83)

sum of 1 to 5 is 15

**C).compilimg c program using riscv gcc**

$cat sum1ton.c


![cat sum1ton](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/3eb3a05e-6e2f-41ed-bb2b-ef9caac41c9f)

$riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
$ls -ltr sum1ton.o

![aftercat](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/a816d2f6-0009-4c8a-8a63-ade3d5dfecb4)


**D).assembly code c programme**

$riscv64-unknown-elf-objdump -d sum1ton.o
$riscv64-unknown-elf-objdump -d sum1ton.o | less
/main


![10184](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/3907b8ec-a9bd-4cae-a4fc-16e0edc991d1)

The address of the main section is 10184 and its byte addressing. Every next instruction address can be found by adding 4 bytes to the current address.

**E).calculation of number of instructions**

Number of instrustions = (memory addresses of the start of the next instruction block - memory addresses of the start of the current instruction block)/4

=(101b0 -10184)/4

=(B)/4 =(11)

So, in total 11 instructions are present in main() function.

$riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
$riscv64-unknown-elf-objdump -d sum1ton.o | less
/main


![ls ltr sum1](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/83acd7f0-7264-4bfd-bdd1-a836e47a8d96)

**F).calculation of number of instructions**

Number of instrustions = (memory addresses of the start of the next instruction block - memory addresses of the start of the current instruction block)/4

=(100dc -100b0)/4

=(2C)/4

=(11)

So, in total 11 instructions are present in main() function.

**G).CONCLUSION**

"While the number of instructions hasn't changed, the program's size has decreased. This change is noticeable in the byte address of the main() function, which previously started with 101b0 but now starts with 100dc."








