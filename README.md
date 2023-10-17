# Makerchip

Navigate to [Makerchip](https://www.makerchip.com/sandbox/)  IDE

Makerchip is a web-based platform for digital design and development. It provides tools and resources for creating and simulating digital circuits and systems, with a focus on the development of custom microprocessors and system-on-chip (SoC) designs. Makerchip offers a collaborative and integrated environment that includes a code editor, a simulator, and various libraries for hardware description and simulation.

- **SystemVerilog Support**: Makerchip allows users to write and simulate digital designs using the SystemVerilog hardware description language, making it suitable for both     beginners and experienced designers.
- **RISC-V and Custom Microprocessor Design**: It provides tools for designing custom RISC-V processors or creating entirely new microprocessor architectures.
- **Code Simulation**: Users can simulate their designs to test functionality and identify potential issues before moving on to the actual hardware implementation.
- **Collaboration**: Makerchip supports collaborative work, enabling multiple users to work on the same project simultaneously.
- **Online Platform**: As a web-based tool, Makerchip eliminates the need for users to install and maintain specialized software, making it accessible from various   devices with an internet connection.


# Lab
# Week 1
<details>
  <summary> Day 1 - Introduction to RISCV ISA and GNU Compiler Toolchain </summary>
  <br>



## C program That calculates sum from 1 to N
____Compiling it using C compiler____
```
gcc sum1ton.c 
./a.out
```

![sum1ton](https://github.com/ramdev604/pes_asic_class/assets/43489027/e8bd87eb-8e11-4623-a420-0eefff9888cc)

____Compiling using RISCV compiler____
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
spike pk sum1ton.o
riscv64-unknown-elf-objdump -d 1_to_N.o | less (in new tab)
```
## Spike Simulation

![spike1](https://github.com/ramdev604/pes_asic_class/assets/43489027/ae1e51b5-80fd-4633-8f3b-6884fbaf1316)

## Write a C program for Signed And Unsigned Numbers 
![unsigned](https://github.com/ramdev604/pes_asic_class/assets/43489027/474784ca-5318-4a01-abd9-995b25a5eaff)



```
vim unsignedHighest.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o unsignedHighest.o unsignedHighest.c
spike pk unsignedHighest.o
```
![WhatsApp Image 2023-08-21 at 22 56 11](https://github.com/ramdev604/pes_asic_class/assets/43489027/55e39c44-6d41-405c-b23c-ce8dd7204f6d)





## For the signed number 

  ![3](https://github.com/ramdev604/pes_asic_class/assets/43489027/dcecc5ae-fe61-4a96-bab9-8889851ad0fe)



```
vim signedHighest.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o signedHighest.o signedHighest.c
spike pk signedHighest.o
```

![4](https://github.com/ramdev604/pes_asic_class/assets/43489027/5e15b6ff-edb2-43c4-acce-e382fc390a72)
</details>

<details>
  <summary> Day 2 - Introduction to ABI and Basic Verification Flow </summary>
  <br>

# Introduction to ABI and basic verification flow

### Download the load.S , 1to9_count.c files from 
https://github.com/kunalg123/riscv_workshop_collaterals/tree/master/labs




```
cat 1to9_custom.c
cat load.S
```



![ss1](https://github.com/ramdev604/pes_asic_class/assets/43489027/087362a5-5c13-4923-a2a2-a0ffbd3c02a0)


![3](https://github.com/ramdev604/pes_asic_class/assets/43489027/832a281f-0b6f-4d96-bfed-a3d324d1a56e)

```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o 1to9_custom.o 1to9_custom.c load.S
spike pk 1to9_custom.o
riscv64-unknown-elf-objdump -d 1to9_custom.o | less
```

## Spike Simulation

![Screenshot from 2023-08-21 09-10-32](https://github.com/ramdev604/pes_asic_class/assets/43489027/64e49c93-a6e6-42f4-a187-1c789809ce21)
</details>

<details>
<summary>DAY-3 : Digital Logic with TL-Verilog in Makerchip IDE</summary>
<br>

#### Task-2 : Lab - Makerchip
To use Makerchip IDE, you need to visit makerchip website at [http://makerchip.com/](http://makerchip.com/) and launch Makerchip IDE
To access a specific example, please follow these steps:
1) **Navigate to the 'Learn' section**
2) **Click on 'Examples'**
3) **Load 'FGPA Multiplier' Example**

**B) XOR Gate**
```
$out = ! $in;
$out1 = ($in1 ^ $in2);
```
![B](https://github.com/ramdev604/ramdev_riscv/assets/43489027/3e441e19-8f0f-431c-9b02-e6d01f06eab8)



**C) Vectors**
```
$out[4:0] = $in1[3:0] + $in2[3:0];
```
![C](https://github.com/ramdev604/ramdev_riscv/assets/43489027/c50cfb6b-c373-4c78-8399-9925f91f9695)

**D) Mux without vector & with vectors**

```
$out = $sel ? $in1 : $in2;
```
![D](https://github.com/ramdev604/ramdev_riscv/assets/43489027/c37ffbd6-c070-4077-83af-6fe5416e2932)


**E) Simple Claculator**

```
$val1[31:0] = $rand1[3:0]; 
$val2[31:0] = $rand2[3:0];
$sum[31:0] = $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$qut[31:0] = $val1 / $val2;
$out[31:0] = $op[1] ? ($op[0] ? $qut: $prod): ($op [0] ? $diff: $sum);
```
![E](https://github.com/ramdev604/ramdev_riscv/assets/43489027/0cd4df26-c7a7-49d6-9265-f5d7c6a25b31)

#### Task-4 : Sequential logic 
```
$fib[31:0] = $reset ? 1 : (>>1$fib + >>2$fib); 
```
![F](https://github.com/ramdev604/ramdev_riscv/assets/43489027/91cc0b90-5233-488c-9e07-90ff26243579)

**B) Up-Counter**

```
$num[2:0] = $reset ? 0 : (>>1$num + 1); 
```


![G](https://github.com/ramdev604/ramdev_riscv/assets/43489027/eff2bd80-dd0e-4090-a220-0331e5b8b5ab)

**C) Sequential Calculator**

```
$val1[31:0] = (>>1$out); 
$val2[31:0] = $rand2[3:0]; 
$sum[31:0] = $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$qut[31:0] = $val1 / $val2;
$out[31:0] = $op[1] ? ($op[0] ? $qut: $prod): ($op [0] ? $diff: $sum); 
```


![H](https://github.com/ramdev604/ramdev_riscv/assets/43489027/ef7c26e6-a1c3-45d9-8860-26471b65a572)


#### Task-5 : Pipelined logic

```
`include "sqrt32.v"
|calc
      @1
         $aa_sq[31:0] = $aa[3:0] * $aa;
         $bb_sq[31:0] = $bb[3:0] * $bb;
      @2
         $cc_sq[31:0] = $aa_sq + $bb_sq;
      @3
         $cc[31:0] = sqrt($cc_sq);
```


![I](https://github.com/ramdev604/ramdev_riscv/assets/43489027/c0504f06-eb5a-4875-ab2f-f7bea40e07ef)


**Pipeline Implementation**

```
|comp
      @1
         $err1 = $bad_input || $illegal_op;
      @2
         $err2 = $err1 || $over_flow;
      @3
         $err3 = $div_by_zero || $err2;
```


![J](https://github.com/ramdev604/ramdev_riscv/assets/43489027/4967a2af-bf07-4566-bfb6-9922952174e0)


#### Task-6 : Validity
+ Easier debug
+ Cleaner design
+ Better error checking
+ Automated clock gating

**2 cycle calculator with validity**

```
|calc
      @0
         $reset = *reset;
         
      @1
         $val1 [31:0] = >>2$out [31:0];
         $val2 [31:0] = $rand2[3:0];
         
         $valid = $reset ? 1'b0 : >>1$valid + 1'b1;
         $valid_or_reset = $valid || $reset;
         
      ?$valid_or_reset
      @1
         $sum [31:0] = $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $qut [31:0] = $val1 / $val2;
         
      @2
         $out [31:0] = $reset ? 32'b0 :
                      ($op[1:0] == 2'b00) ? $sum :
                      ($op[1:0] == 2'b01) ? $diff :
                      ($op[1:0] == 2'b10) ? $prod :
                                              $qut ;
```

![K](https://github.com/ramdev604/ramdev_riscv/assets/43489027/d7ae3d73-f6d0-49ee-b21f-a00526f193ce)


**Distance Calculator**
```
|calc
      @1
         $reset = *reset;
         
      ?$valid
         @1
            $aa_sq[31:0] = $aa[3:0] * $aa;
            $bb_sq[31:0] = $bb[3:0] * $bb;;
         @2
            $cc_sq[31:0] = $aa_sq + $bb_sq;;
         @3
            $cc[31:0] = sqrt($cc_sq);
      @4
         $total_distance[63:0] =
            $reset ? 0 :
            $valid ? >>1$total_distance + $cc :
                     >>1$total_distance;
```
![L](https://github.com/ramdev604/ramdev_riscv/assets/43489027/e03dbae4-05ed-4cd5-a7c6-ec5580c48d6f)

**Calulator Memory**
```
|calc
      @0
         $reset = *reset;
         
      @1
         $val1 [31:0] = >>2$out [31:0];
         $val2 [31:0] = $rand2[3:0];
         
         $valid = $reset ? 1'b0 : >>1$valid + 1'b1;
         $valid_or_reset = $valid || $reset;
         
      ?$valid_or_reset
      @1
         $sum [31:0] = $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $qut [31:0] = $val1 / $val2;
         
      @2
         $mem[31:0] = $reset ? 32'b0 :
                      ($op[2:0] == 3'b101) ? $val1 : >>2$mem ;
         
         $out [31:0] = $reset ? 32'b0 :
                      ($op[2:0] == 3'b000) ? $sum :
                      ($op[2:0] == 3'b001) ? $diff :
                      ($op[2:0] == 3'b010) ? $prod :
                      ($op[2:0] == 3'b011) ? $qut  :
                      ($op[2:0] == 3'b100) ? >>2$mem : >>2$out ;
```


![M](https://github.com/ramdev604/ramdev_riscv/assets/43489027/c93d95d8-7754-4a91-a12d-090f305c293b)
</details>

<details>
<summary>DAY 4 : Basic RISC-V CPU Micro Architecture</summary>
<br>

# RISC-V Architecture Block Diagram

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/1695d5f6-eab9-4279-9419-b2817800b002)

## Overview
This RISC-V Architecture Block Diagram illustrates the fundamental components and their interactions within a computer system based on the RISC-V instruction set architecture. RISC-V is a modular and customizable architecture, providing a versatile framework for designing processors tailored to specific application requirements.

## Components
1. **CPU (Central Processing Unit)**
   - *Description*: The CPU serves as the core of the RISC-V processor, responsible for executing instructions. It includes multiple stages:
     - Instruction Fetch (IF): Fetches instructions from memory.
     - Instruction Decode (ID): Decodes the fetched instructions.
     - Execution (EX): Performs arithmetic and logic operations.
     - Memory (MEM): Manages data memory access.
     - Write Back (WB): Writes results back to registers.

2. **Instruction Memory**
   - *Description*: This memory component stores the program's instructions that the CPU fetches and executes. It's essential for the program's proper execution.

3. **Data Memory**
   - *Description*: Data Memory stores data used by the CPU during program execution. It is crucial for data manipulation and storage.

4. **Registers**
   - *Description*: Registers are a set of general-purpose storage units used for temporary data storage and manipulation by the CPU. They play a pivotal role in instruction execution.

5. **Control Unit**
   - *Description*: The Control Unit manages control signals and coordinates the activities of the CPU's components, ensuring the proper execution of instructions.

6. **ALU (Arithmetic Logic Unit)**
   - *Description*: The ALU performs arithmetic and logic operations as directed by the CPU's instructions. It is the computational workhorse of the processor.

7. **Instruction Decoder**
   - *Description*: The Instruction Decoder interprets and decodes instructions fetched from memory. It translates instructions into actions for the CPU to execute.

8. **Cache Memory**
   - *Description*: Cache Memory provides fast access to frequently used instructions and data. It helps improve the system's overall performance by reducing memory access times.

9. **Bus Interface**
   - *Description*: The Bus Interface facilitates data transfer between the CPU, memory, and peripherals. It ensures efficient communication within the system.

10. **Peripherals**
    - *Description*: Peripherals are external devices such as input/output controllers, timers, and more. They connect to the CPU, enhancing the system's functionality by allowing interaction with the outside world.

For the consecutive labs, we will use the "RISC-V lab starting point code" from https://github.com/stevehoover/RISC-V_MYTH_Workshop.

Use the following links : [Link for the starter code](https://myth.makerchip.com/sandbox?code_url=https:%2F%2Fraw.githubusercontent.com%2Fstevehoover%2FRISC-V_MYTH_Workshop%2Fmaster%2Frisc-v_shell.tlv#)

#### Task-1 : Program Counter
![1](https://github.com/ramdev604/ramdev_riscv/assets/43489027/5e6a0708-0b36-466e-89d7-752df87e29a5)


#### Task-2 : Instruction Fetch

![2](https://github.com/ramdev604/ramdev_riscv/assets/43489027/f0fc2b62-666b-47db-9eb0-684dc0f4a7ee)

#### Task-3 : Instruction Decode
![3](https://github.com/ramdev604/ramdev_riscv/assets/43489027/6a93a93f-941b-447c-a63a-ef020f481146)


#### Task-4 : Instruction Decode with validity
![4](https://github.com/ramdev604/ramdev_riscv/assets/43489027/bf643b3c-7a05-4d6f-a7d9-6c497809ae18)


#### Task-5 : Individual Instruction decode

![5](https://github.com/ramdev604/ramdev_riscv/assets/43489027/1afaa73c-f639-4693-9e73-e93102983b84)

#### Task-6 : Register File Read
![6](https://github.com/ramdev604/ramdev_riscv/assets/43489027/a7bf1d22-4eee-4107-8225-151474b4910d)


#### Task-7 : ALU
![7](https://github.com/ramdev604/ramdev_riscv/assets/43489027/0bb9a648-8a14-4dc4-b285-796d48041509)


#### Task-8 : Register File Write
![8](https://github.com/ramdev604/ramdev_riscv/assets/43489027/29f141b3-9175-42ce-8050-d27241606554)


#### Task-9 : Branch Instructions
![9](https://github.com/ramdev604/ramdev_riscv/assets/43489027/52178131-01de-4d98-80b8-0a2efe2e12c2)


#### Task-10 : Testbench to check functionality
![10](https://github.com/ramdev604/ramdev_riscv/assets/43489027/b3346ed1-98fd-48f8-9162-38104ca7baeb)
