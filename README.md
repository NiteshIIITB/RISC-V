<h1>RISC V</h1>

<details>
<summary><strong>Day 1</strong></summary>

 <details><summary><strong>C Program</strong></summary>
 <h3>C program doing sum of numbers from 1 to n</h3>
 <h4>Code</h4>

```
#include<stdio.h>
int main(){
   int n = 10;
   int i ;
   int sum = 0;
   for(int i =1;i<=10;i++)
   {
   sum = sum +i;}
   printf("The sum of digits from 1 to %d is %d.\n",n,sum);
   return 0;
}

```

<h4>Output</h4>
<div align = "center">
<img src = "https://user-images.githubusercontent.com/140998787/261832228-b6025cd0-2ace-452e-9627-9c7bbc235785.png">
	
</div>
</details>
<details> 
<summary><strong>C Program on RISCV64 compiler</strong></summary>

<h3>Code output</h3>
<div align="center">
  <img src="https://github.com/NiteshIIITB/RISC-V/assets/140998787/d296bf4f-e301-47ec-bca9-1172c89d5825">
	
</div>
<h3>Assembly code output with o1 attribute</h3>
<div align="center">
	<img src="https://github.com/NiteshIIITB/RISC-V/assets/140998787/81e48eaa-107c-419e-9c9c-4ca62f3e7397">
</div>

<h3>Assembly code output with ofast attribute</h3>
<div align="center">
	<img src="https://user-images.githubusercontent.com/140998787/261853142-51bd6b4b-791b-45d0-bda4-6bf338c5de81.png">
</div>

<h3>Step by step observation of code execution</h3>
<div align="center">
  <img src = "https://github.com/NiteshIIITB/RISC-V/assets/140998787/ac44eada-3427-4604-9548-3a70ab895b66">
	
</div>

 <h3>Commands used:</h3>
 
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

```

<h4>Explanation:</h4>
<p>
	<ul>
	<li>  <strong> riscv64-unknown-elf-gcc:</strong> 
        This is the command to invoke the RISC-V GCC compiler. It's used to compile C and C++ code for RISC-V architectures.
        riscv64 specifies the target architecture, which is the 64-bit version of RISC-V.
        unknown-elf indicates the target environment. The "ELF" part stands for "Executable and Linkable Format," which is a common file format for executables, object code, and shared libraries.
         </li> 
    <li><strong>-O1:</strong>
        This flag specifies the optimization level for the compiler. -O1 indicates optimization level 1.
        Optimization levels control how aggressively the compiler optimizes the code. Level 1 provides basic optimizations to improve code performance without spending excessive time on compilation.
        </li> 
  <li> <strong> -mabi=lp64:</strong>
        The -mabi flag specifies the ABI (Application Binary Interface) to use for the compilation.
        lp64 indicates that the ABI uses 64-bit data types (long and pointer) and is commonly used in RISC-V systems.</li> 

  <li> <strong> -march=rv64i:</strong>
        The -march flag specifies the target RISC-V architecture to generate code for.
        rv64i indicates the RISC-V architecture specification. Here, rv64 specifies a 64-bit RISC-V architecture, and i indicates the "I" base integer instruction set. This set includes the fundamental integer arithmetic and control flow instructions.</li> 

   <li><strong> -o sum1ton.o:</strong>
        The -o flag specifies the output file name for the compiled code.
        sum1ton.o is the name of the output file. The .o extension indicates that it's an object file, which contains the compiled machine code ready to be linked with other object files to create an executable.</li> 

   <li><strong>sum1ton.c:</strong>
        This is the source file that you want to compile.
        sum1ton.c is the name of the C source file that contains the code to be compiled.</li> 

 </ul>
 
</p><br>

```
riscv64-unknown-elf-objdump -d sum1ton.o

```
<p>
	<h4>Explanation :</h4>
	It is used to disassemble an object file (sum1ton.o) produced by a RISC-V toolchain. The objdump command is commonly used to analyze and display information about object files, executable files, and libraries.<br>

In this specific case,the riscv64-unknown-elf-objdump command, which is part of the RISC-V toolchain and is used to disassemble RISC-V machine code into human-readable assembly instructions.

When the command is run, it will generate a disassembly listing of the instructions contained within the sum1ton.o object file. This can be particularly useful for inspecting the assembly code produced by the compiler or for debugging purposes.<br>

The -d flag specifies that we want to disassemble the code, and sum1ton.o is the name of the object file you want to disassemble.


</p>

</details>
</details>

<details>
<summary><strong>Day 2</strong></summary>
<h2>The New Algorithm For Sum 1ton c program</h2>	

<div align="center">
	<img src ="https://github.com/NiteshIIITB/RISC-V/assets/140998787/ba90f4dc-352d-4c36-90ea-1cda1342a1d0">
</div>

<h2>Code</h2>

```
#include <stdio.h>

extern int load(int x, int y); 

int main() {
	int result = 0;
       	int count = 9;
    	result = load(0x0, count+1);
    	printf("Sum of number from 1 to %d is %d\n", count, result); 
}

```

<h2>Assembly Code For Load Function</h2>

```
.section .text
.global load
.type load, @function

load:
	add 	a4, a0, zero //Initialize sum register a4 with 0x0
	add 	a2, a0, a1   // store count of 10 in register a2. Register a1 is loaded with 0xa (decimal 10) from main program
	add	a3, a0, zero // initialize intermediate sum register a3 by 0
loop:	add 	a4, a3, a4   // Incremental addition
	addi 	a3, a3, 1    // Increment intermediate register by 1	
	blt 	a3, a2, loop // If a3 is less than a2, branch to label named <loop>
	add	a0, a4, zero // Store final result to register a0 so that it can be read by main program
	ret

```
<h2>Execution</h2>
<div align="center">
	<img src="https://github.com/NiteshIIITB/RISC-V/assets/140998787/2767f0a4-d194-41fe-97e4-dc22856c0b25">
</div>

<h2>Execution of C program on RISC V CPU</h2>
<div align="center">
	<img src="https://github.com/NiteshIIITB/RISC-V/assets/140998787/cc445a13-1411-4946-a67e-9946525b66d3">
</div>

<h2>Contents of rv32im.sh(Shell script file)</h2>

```
riscv64-unknown-elf-gcc -c -mabi=ilp32 -march=rv32im -o 1to9_custom.o 1to9_custom.c
riscv64-unknown-elf-gcc -c -mabi=ilp32 -march=rv32im -o load.o load.S

riscv64-unknown-elf-gcc -c -mabi=ilp32 -march=rv32im -o syscalls.o syscalls.c
riscv64-unknown-elf-gcc -mabi=ilp32 -march=rv32im -Wl,--gc-sections -o firmware.elf load.o 1to9_custom.o syscalls.o -T riscv.ld -lstdc++
chmod -x firmware.elf
riscv64-unknown-elf-gcc -mabi=ilp32 -march=rv32im -nostdlib -o start.elf start.S -T start.ld -lstdc++
chmod -x start.elf
riscv64-unknown-elf-objcopy -O verilog start.elf start.tmp
riscv64-unknown-elf-objcopy -O verilog firmware.elf firmware.tmp
cat start.tmp firmware.tmp > firmware.hex
python3 hex8tohex32.py firmware.hex > firmware32.hex
rm -f start.tmp firmware.tmp
iverilog -o testbench.vvp testbench.v picorv32.v
chmod -x testbench.vvp
vvp -N testbench.vvp

```

<h3>Explanation</h3>
<p>
<br>

1. `riscv64-unknown-elf-gcc -c -mabi=ilp32 -march=rv32im -o 1to9_custom.o 1to9_custom.c`
   - This command compiles the C source file `1to9_custom.c` into an object file `1to9_custom.o`. It uses the RISC-V GCC compiler targeting the ILP32 ABI (Application Binary Interface) and the RV32IM architecture.
<br>

2. `riscv64-unknown-elf-gcc -c -mabi=ilp32 -march=rv32im -o load.o load.S`
   - Similar to the previous command, this compiles the assembly source file `load.S` into an object file `load.o`.
<br>

3. `riscv64-unknown-elf-gcc -c -mabi=ilp32 -march=rv32im -o syscalls.o syscalls.c`
   - This compiles another C source file `syscalls.c` into an object file `syscalls.o`.
<br>

4. `riscv64-unknown-elf-gcc -mabi=ilp32 -march=rv32im -Wl,--gc-sections -o firmware.elf load.o 1to9_custom.o syscalls.o -T riscv.ld -lstdc++`
   - This links the previously compiled object files (`load.o`, `1to9_custom.o`, `syscalls.o`) along with the necessary libraries and linker script `riscv.ld` to create an ELF executable named `firmware.elf`. The linker is instructed to perform garbage collection on unused sections.
<br>

5. `chmod -x firmware.elf`
   - This command changes the permissions of the `firmware.elf` file to remove its execute permission.
<br>

6. `riscv64-unknown-elf-gcc -mabi=ilp32 -march=rv32im -nostdlib -o start.elf start.S -T start.ld -lstdc++`
   - Similar to step 4, this compiles and links an assembly source file `start.S` with libraries and linker script `start.ld` to create another ELF executable named `start.elf`. The `-nostdlib` flag indicates that the standard library should not be included.
<br>

7. `chmod -x start.elf`
   - Similar to step 5, this changes the permissions of the `start.elf` file to remove its execute permission.
<br>

8. `riscv64-unknown-elf-objcopy -O verilog start.elf start.tmp`
   - This command uses the `objcopy` tool to convert the `start.elf` file into a Verilog memory initialization file `start.tmp` in the "verilog" format.
<br>

9. `riscv64-unknown-elf-objcopy -O verilog firmware.elf firmware.tmp`
   - Similar to step 8, this converts the `firmware.elf` file into a Verilog memory initialization file `firmware.tmp`.
<br>

10. `cat start.tmp firmware.tmp > firmware.hex`
    - This concatenates the content of `start.tmp` and `firmware.tmp` files to create a combined Verilog memory initialization file `firmware.hex`.
<br>

11. `python3 hex8tohex32.py firmware.hex > firmware32.hex`
    - This step involves a Python script named `hex8tohex32.py`, which takes the `firmware.hex` file (assumed to contain 8-bit memory data) and converts it to 32-bit memory data format, saving the result in `firmware32.hex`.
<br>

12. `rm -f start.tmp firmware.tmp`
    - This removes the temporary Verilog memory initialization files.
<br>

13. `iverilog -o testbench.vvp testbench.v picorv32.v`
    - This compiles Verilog source files `testbench.v` and `picorv32.v` using the Icarus Verilog compiler to create a simulation executable `testbench.vvp`.
<br>

14. `chmod -x testbench.vvp`
    - This removes the execute permission from the simulation executable.
<br>

15. `vvp -N testbench.vvp`
    - This runs the compiled simulation executable using the VVP (Verilog VVP) simulator.
<br>

In summary, this script performs a series of compilation, linking, and conversion steps to prepare and simulate RISC-V assembly and C code using a combination of tools and scripts. The resulting simulation should involve the execution of the RISC-V code within the given constraints and configurations.
</p>


</details>

<details>
<summary><strong>Day 3</strong></summary>
	
<details><summary><strong>TL-Verilog and Makerchip IDE</strong></summary>
<p>TL-Verilog, short for Transaction-Level Verilog, is a hardware description and design language used for specifying and designing digital systems, particularly focusing on transaction-level abstraction and high-level design. It extends traditional Verilog and SystemVerilog languages by introducing higher-level constructs that facilitate the design and verification process, making it more suitable for complex system-on-chip (SoC) designs.</p>

 <p>Makerchip is an online Integrated Development Environment (IDE) designed specifically for digital system design and hardware description. It provides a platform for creating, simulating, and visualizing digital designs using various hardware description languages and tools, including SystemVerilog, Verilog, and TL-Verilog. Makerchip aims to simplify the process of designing and simulating digital circuits by offering an accessible and user-friendly interface.</p>
</details>

<details><summary><strong>Introduction to Makerchip IDE</strong></summary>
<h2>Pythagorean Template</h2>
<div align = "center">
	<img src = "https://user-images.githubusercontent.com/140998787/261842578-9d2e71b4-ea48-4691-bf26-ee91cae9c1a4.png">
</div>


<h2>Inverter</h2>
<div align = "center">
	<img src = "https://user-images.githubusercontent.com/140998787/261837324-cf6aee8b-14c1-4195-8023-f6ea5ba345b0.png">
</div>

<h2>Multiplexer</h2>
<div align = "center">
	<img src = "https://user-images.githubusercontent.com/140998787/261837187-b054221a-0ef7-4254-a3c9-1ce5c5b6dc29.png">
</div>

 <h2>Vector Usage</h2>
<div align = "center">
	<img src = "https://user-images.githubusercontent.com/140998787/261837103-e6417fb9-6d79-4dd5-ba50-5b8304fd1a05.png">
</div>

<h2>Wide Multiplexer</h2>
<div align = "center">
	<img src = "https://user-images.githubusercontent.com/140998787/261837419-40c37c7e-4efe-4983-b8a9-ef6905a00e6b.png">
</div>

<h2>Calculator</h2>
<div align = "center">
	<img src = "https://user-images.githubusercontent.com/140998787/261842057-4c5f33ec-14d1-47fc-87a7-52689d6d37d2.png">
</div>
<br>
<div align="center"><h1>Sequential Logic</h1></div>
<h2>4-bit Up Counter</h2>
<div align = "center">
	<img src= "https://github.com/NiteshIIITB/RISC-V/assets/140998787/9ff4911b-1b21-4b54-bfa7-60e8ec4abfae">
</div>

<h2>Fibonacci Sequence</h2>
<div align = "center">
	
<img src = "https://user-images.githubusercontent.com/140998787/261844311-caf5358c-1726-4ec3-bb04-40569a0002aa.png">
        <img src = "https://user-images.githubusercontent.com/140998787/261844482-e3f54fd2-95a4-469e-bc72-6eee7a9e166f.png">
</div>
 <div align="center">
	 <h1>Pipelined Logic</h1>
 </div>
 <h2>2-Cycle Calculator</h2>
 <img src="https://github.com/NiteshIIITB/RISC-V/assets/140998787/ce531a3d-04b7-45c3-8ad4-d6084c9fa417">
<br>
 <div align="center">
	 <h1>Validity</h1>
 </div>
 <p>In logic circuits and digital design, "validity" typically refers to the concept of ensuring that signals or data within a system are in a valid or reliable state before they are processed or used in subsequent stages. Validity plays a crucial role in maintaining the correctness and proper functioning of digital systems. </p>
 <h3>Advantages of Validity</h3>
 <p>
	 <ul>
		 <li> Reliable Operation: Validity guarantees that the system operates reliably and produces accurate results. Without ensuring the validity of inputs, the output of digital circuits could be unpredictable or incorrect.</li>
		 <li>Validity ensures that data transitions are synchronized with clock edges, which leads to consistent behavior and predictable outputs. This is especially important in synchronous digital systems.</li>
		 <li>Design Verification: Validity considerations are crucial during design verification and testing. Ensuring inputs are in valid states allows for more targeted testing and easier debugging of issues.</li>
		 <li>Power Efficiency: Validity checks can prevent unnecessary switching of logic values when inputs are changing rapidly. This helps reduce dynamic power consumption in the system.</li>
	 </ul>
 </p>
 </details>

</details>

<details>
<summary><strong>Day 4</strong></summary>
</details>

<details>
<summary><strong>Day 5</strong></summary>
</details>
 
<h2>References</h2>
 <ul>
<li><a href ="https://github.com/kunalg123/">Kunal Ghosh Github(Mentor)</a></li>
	
 </ul>
