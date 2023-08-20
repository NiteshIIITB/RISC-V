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

 <h3>Commands used:</h3>
 
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

```

<h4>Explaination:</h4>
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
</p>


</details>
</details>

<details>
<summary><strong>Day 2</strong></summary>
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
