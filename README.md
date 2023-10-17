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


