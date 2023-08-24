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

In summary, this script performs a series of compilation, linking, and conversion steps to prepare and simulate RISC-V assembly and C code using a combination of tools and scripts. The resulting simulation involve the execution of the RISC-V code within the given constraints and configurations.
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
<h2>PC Logic</h2>
<p>
	A program counter (PC), also known as an instruction pointer (IP) in some architectures, is a fundamental component of a computer's central processing unit (CPU). It's a special register that keeps track of the memory address of the next instruction to be executed in a program. The program counter is used in conjunction with the fetch-execute cycle, which is the basic process through which a CPU carries out instructions.<br><br>

The working of program counter in a nutshell<br><br>

Fetch: The CPU fetches the instruction from memory at the address pointed to by the program counter.<br><br>

Increment: After the fetch, the program counter is incremented to point to the next memory location where the next instruction resides.<br><br>

Execute: The fetched instruction is then executed.<br><br>

 Repeat: The process repeats, with the program counter always indicating the memory address of the next instruction to be fetched and executed.<br><br>
</p>

```
|cpu
      @0
         $reset = *reset;
         $pc[31:0] = >>1$reset ? 0 : >>1$pc + 32'd4;

```

<h4>Output</h4>
<div align ="center">

<img src = "https://github.com/NiteshIIITB/RISC-V/assets/140998787/78bc2a81-d825-4b7f-b928-fd4674861cd6">	

</div>
<br>

<h2>Fetch</h2>
<p>
Let's delve deeper into the fetch stage:
<br><br>
Fetch Instruction: In this stage, the CPU retrieves the next instruction from memory. The address of the instruction to be fetched is provided by the program counter (PC). The program counter holds the memory address of the next instruction to be executed. It is updated during each cycle to point to the next instruction.
<br><br>
Memory Access: The CPU sends a memory read request to the memory unit, specifying the address pointed to by the program counter. The memory unit then retrieves the instruction from the specified memory location and provides it to the CPU.
<br><br>
Instruction Register (IR): The fetched instruction is loaded into a special register called the instruction register (IR). The instruction register temporarily holds the fetched instruction until it's ready to be decoded and executed.
<br><br>
Program Counter Update: After the fetch, the program counter is incremented to point to the memory address of the next instruction. The exact increment depends on the length of the fetched instruction (which can vary between different instructions and architectures).
<br><br>
At this point, the fetched instruction is in the instruction register, and the CPU is ready to move on to the "decode" stage, during which the fetched instruction is interpreted to determine what operation needs to be executed.
</p>

```
|cpu
      @0
         $reset = *reset;
         $pc[31:0] = >>1$reset ? 0 : >>1$pc + 32'd4;
      @1
         $imem_rd_en = !$reset;
         $imem_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
         $instr[31:0] = $imem_rd_data[31:0];
         
      ?$imem_rd_en
         @1
            $imem_rd_data[31:0] = /imem[$imem_rd_addr]$instr;

      
```

<h4>Output</h4>
<div>
	<img src="https://github.com/NiteshIIITB/RISC-V/assets/140998787/46a516f2-35f6-40bb-9413-8ba71f67234c">
</div>

<h4>Viz Output</h4>
<div>
	<img src="https://github.com/NiteshIIITB/RISC-V/assets/140998787/181d7ee4-0523-4760-85b7-f2436cb186d4">
</div>

<h2>Decode Logic</h2>
<h3>Decode Logic code</h3>

```tlv
\m4_TLV_version 1d: tl-x.org
\SV
   // This code can be found in: https://github.com/stevehoover/RISC-V_MYTH_Workshop
   
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/RISC-V_MYTH_Workshop/master/tlv_lib/risc-v_shell_lib.tlv'])

\SV
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV

   // /====================\
   // | Sum 1 to 9 Program |
   // \====================/
   //
   // Program for MYTH Workshop to test RV32I
   // Add 1,2,3,...,9 (in that order).
   //
   // Regs:
   //  r10 (a0): In: 0, Out: final sum
   //  r12 (a2): 10
   //  r13 (a3): 1..10
   //  r14 (a4): Sum
   // 
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;



      // YOUR CODE HERE
      // ...
      @0
         $pc[31:0] = >>1$reset ? 32'd0 : (>>1$taken_branch ? >>1$br_tgt_pc :  (>>1$pc+32'd4));
      @1
         //Instruction Fetch
         $imem_rd_en = !$reset;
         $imem_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
         $instr[31:0] = $imem_rd_data[31:0];
      ?$imem_rd_en
         @1
            $imem_rd_data[31:0] = /imem[$imem_rd_addr]$instr;
      @1
         //Instruction Decode
         $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                       $instr[6:2] ==? 5'b001x0 ||
                       $instr[6:2] ==? 5'b11001 ||
                       $instr[6:2] ==? 5'b11100;
         
         $is_u_instr = $instr[6:2] ==? 5'b0x101;
         
         $is_r_instr = $instr[6:2] ==? 5'b01011 ||
                       $instr[6:2] ==? 5'b011x0 ||
                       $instr[6:2] ==? 5'b10100;
         
         $is_b_instr = $instr[6:2] ==? 5'b11000;
         
         $is_j_instr = $instr[6:2] ==? 5'b11011;
         
         $is_s_instr = $instr[6:2] ==? 5'b0100x;
         
         $imm[31:0] = $is_i_instr ? {{21{$instr[31]}}, $instr[30:20]} :
                      $is_s_instr ? {{21{$instr[31]}}, $instr[30:25], $instr[11:7]} :
                      $is_b_instr ? {{20{$instr[31]}}, $instr[7], $instr[30:25], $instr[11:8], 1'b0} :
                      $is_u_instr ? {$instr[31:12], 12'b0} :
                      $is_j_instr ? {{12{$instr[31]}}, $instr[19:12], $instr[20], $instr[30:21], 1'b0} :
                                    32'b0;
         $opcode[6:0] = $instr[6:0];
         
         $rs2_valid = $is_r_instr || $is_s_instr || $is_b_instr;
         ?$rs2_valid
            $rs2[4:0] = $instr[24:20];
            
         $rs1_valid = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr;
         ?$rs1_valid
            $rs1[4:0] = $instr[19:15];
         
         $funct3_valid = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr;
         ?$funct3_valid
            $funct3[2:0] = $instr[14:12];
            
         $funct7_valid = $is_r_instr ;
         ?$funct7_valid
            $funct7[6:0] = $instr[31:25];
            
         $rd_valid = $is_r_instr || $is_i_instr || $is_u_instr || $is_j_instr;
         ?$rd_valid 
            $rd[4:0] = $instr[11:7]; //rd - Destination Register
            
         $dec_bits [10:0] = {$funct7[5], $funct3, $opcode};
         $is_beq = $dec_bits ==? 11'bx_000_1100011;
         $is_bne = $dec_bits ==? 11'bx_001_1100011;
         $is_blt = $dec_bits ==? 11'bx_100_1100011;
         $is_bge = $dec_bits ==? 11'bx_101_1100011;
         $is_bltu = $dec_bits ==? 11'bx_110_1100011;
         $is_bgeu = $dec_bits ==? 11'bx_111_1100011;
         $is_addi = $dec_bits ==? 11'bx_000_0010011;
         $is_add = $dec_bits ==? 11'b0_000_0110011;
         
      @1
         //Register File Read
         $rf_wr_en = 1'b0;
         $rf_wr_index[4:0] = 5'b0;
         $rf_wr_data[31:0] = 32'b0;
         
         $rf_rd_en1 = $rs1_valid;
         $rf_rd_index1[4:0] = $rs1;
         
         $rf_rd_en2 = $rs2_valid;
         $rf_rd_index2[4:0] = $rs2;
         
         $src1_value[31:0] = $rf_rd_data1;
         $src2_value[31:0] = $rf_rd_data2;
         
      @1
         //ALU
         $result[31:0] = $is_addi ? $src1_value + $imm :
                         $is_add ? $src1_value + $src2_value :
                         32'bx ;
      @1
         //Register File Write
         $rf_wr_en = $rd_valid && $rd != 5'b0;
         $rf_wr_index[4:0] = $rd;
         $rf_wr_data[31:0] = $result;
         
      @1
         //Branch Instructions
         $taken_branch = $is_beq ? ($src1_value == $src2_value):
                         $is_bne ? ($src1_value != $src2_value):
                         $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])):
                         $is_bge ? (($src1_value >= $src2_value) ^ ($src1_value[31] != $src2_value[31])):
                         $is_bltu ? ($src1_value < $src2_value):
                         $is_bgeu ? ($src1_value >= $src2_value):
                                    1'b0;
         `BOGUS_USE($taken_branch)
         $br_tgt_pc[31:0] = $pc + $imm;
      // Note: Because of the magic we are using for visualisation, if visualisation is enabled below,
      //       be sure to avoid having unassigned signals (which you might be using for random inputs)
      //       other than those specifically expected in the labs. You'll get strange errors for these.

   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      m4+imem(@1)    // Args: (read stage)
      m4+rf(@1, @1)  // Args: (read stage, write stage) - if equal, no register bypass is required
      //m4+dmem(@4)    // Args: (read/write stage)
      //m4+myth_fpga(@0)  // Uncomment to run on fpga

   m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic. @4 would work for all labs.
\SV
   endmodule

```

<h4>Schematic output</h4>
<div align="center">
	<img src="https://github.com/NiteshIIITB/RISC-V/assets/140998787/4b430d5e-9893-4322-8846-b4a2b0767378">
</div>

<h4>Waveform output</h4>
<div align="center">
	<img src="https://github.com/NiteshIIITB/RISC-V/assets/140998787/e1ad1aa4-09b5-45fc-a4de-1ecfc6f40126">
</div>




</details>

<details>
<summary><strong>Day 5</strong></summary>
</details>
 
<h2>References</h2>
 <ul>
<li><a href ="https://github.com/kunalg123/">Kunal Ghosh Github(Mentor)</a></li>
	
 </ul>
