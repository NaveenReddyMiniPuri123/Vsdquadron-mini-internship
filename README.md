TASK 1

1.Download Oracle Virtual machine and allocated 4GB RAM,100GB HDD

2.Installation of Ubuntu 22.04 using Virtual Machine

3.Installation of RISC-V GNU Toolchain

4.Installation of Yosys

5.Installation of iverilog

6.Installation of gtkwave

1.Installation of Ubuntu 22.04 using Virtual Machine
![vm box and ubuntu installed](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/b696d824-4385-4cba-8cb9-3b5b5c27abdc)

2.Installation of RISC-V GNU Toolchain

$ sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev
$ git clone https://github.com/riscv/riscv-gnu-toolchain

./configure --prefix=/opt/riscv make linux

![gnu toolchain](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/5959ded2-dfcd-47f1-bbae-04c73d04e5b4)

3.Installation of Yosys

$ git clone https://github.com/YosysHQ/yosys.git

$ sudo apt install make

$ cd yosys

$ sudo apt-get install build-essential clang bison flex libreadline-dev gawk tcl-dev libffi-dev git graphviz xdot pkg-config python3 libboost-system-dev libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc

$ make

$ sudo make install

Yosys

![yosys installed2](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/3ab62a52-76ee-4c34-9269-d999c348a6ba)

4.Installation of iverilog

sudo apt-get install iverilog 

![iverilog](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/fda35b0b-02cf-4be6-80b1-1f814e350258)

5.Installation of gtkwave

sudo apt update

sudo apt install gtkwave
![gtk wave](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/4611cdf4-8489-451e-a0fe-06767a34cf7d)

![gtk wave install](https://github.com/NaveenReddyMiniPuri123/Vsdquadron-mini-internship/assets/167668786/0f257ceb-d9ff-4375-ac5f-bcf45b609d7d)

