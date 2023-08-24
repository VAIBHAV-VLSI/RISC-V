<h1>RISC V</h1>

<details>
<summary><strong>Day 1</strong></summary>

 <details><summary><strong>C Program</strong></summary>
 <h3>C program doing sum of numbers from 1 to 6</h3>
 <h4>Code</h4>

```
#include<stdio.h>
int main(){
   int n = 6;
   int i ;
   int sum = 0;
   for(int i =1;i<=6;i++)
   {
   sum = sum +i;}
   printf("The sum of digits from 1 to %d is %d.\n",n,sum);
   return 0;
}

```



</details>
<details> 
<summary><strong>C Program on RISCV64 compiler</strong></summary>

<h3>Code output</h3>
<div align="center">
  <img src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/7406c00f-eedf-4628-82e1-8f7595b908f4">
  

	
</div>
<h3>Assembly code output with o1 attribute</h3>
<div align="center">
	<img src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/c4297a69-d7e2-44b1-a601-46f269318d0b">
</div>

<h3>Assembly code output with ofast attribute</h3>
<div align="center">
	<img src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/acef1efd-12f5-4433-8dbf-2901d72e2911">
</div>

<h3>Step by step observation of code execution</h3>
<div align="center">
  <img src = "https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/75692f76-f88d-4e7c-91c6-389aa1632698">
	
</div>

 <h3>Commands used:</h3>
 
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1to6.o sum1to6.c

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
<summary><strong>Day 3</strong></summary>
	
<details><summary><strong>TL-Verilog and Makerchip IDE</strong></summary>
<p>TL-Verilog, short for Transaction-Level Verilog, is a hardware description and design language used for specifying and designing digital systems, particularly focusing on transaction-level abstraction and high-level design. It extends traditional Verilog and SystemVerilog languages by introducing higher-level constructs that facilitate the design and verification process, making it more suitable for complex system-on-chip (SoC) designs.</p>

 <p>Makerchip is an online Integrated Development Environment (IDE) designed specifically for digital system design and hardware description. It provides a platform for creating, simulating, and visualizing digital designs using various hardware description languages and tools, including SystemVerilog, Verilog, and TL-Verilog. Makerchip aims to simplify the process of designing and simulating digital circuits by offering an accessible and user-friendly interface.</p>
</details>

<details><summary><strong>Introduction to Makerchip IDE</strong></summary>
<h2>Pythagorean Template</h2>
<div align = "center">
<img width="1470" alt="1" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/f05cd1b6-6bb3-4e7a-bcd8-ce1d0efc32b8">
</div>


<h2>Inverter</h2>
<div align = "center">
<img width="1470" alt="2" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/13b6405d-48c7-49ca-8df2-66439ee62553">
</div>

<h2>Multiplexer</h2>
<div align = "center">
<img width="1470" alt="3" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/c672a21a-d4bb-4fe3-98b9-50f8d0d4c29d">
</div>

 <h2>Vector Usage</h2>
<div align = "center">
<img width="1470" alt="4" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/5896b706-a7c1-448d-a645-f6f644f6ea36">
</div>

<h2>Wide Multiplexer</h2>
<div align = "center">
<img width="1470" alt="5" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/710930a4-f1d1-4804-9a9b-69240eff5fc0">
</div>

<h2>Calculator</h2>
<div align = "center">
<img width="1470" alt="6" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/82fe89c8-3992-446c-82ac-fca177f6ac13">
</div>
<br>
<div align="center"><h1>Sequential Logic</h1></div>
<h2>4-bit Up Counter</h2>
<div align = "center">
<img width="1470" alt="8" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/ef610cb6-e4d6-4dfe-9f10-5b0b8366613a">
</div>

<h2>Fibonacci Sequence</h2>
<div align = "center">
	
<img width="959" alt="9" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/4617f62f-8833-40c1-bb8a-08527870239e">
<img width="1470" alt="10" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/c3d1c0aa-16b3-41b3-9e8b-13e6cceed279">
</div>
 <div align="center">
	 <h1>Pipelined Logic</h1>
 </div>
 <h2>2-Cycle Calculator</h2>
<img width="1470" alt="11" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/a17bd09d-8458-4bed-af8f-3997803d5e51">
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
