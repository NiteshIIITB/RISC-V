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
