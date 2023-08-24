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
<summary><strong>Day 2</strong></summary>
<h2>The New Algorithm For Sum 1ton c program</h2>	

<div align="center">
<img width="737" alt="Screenshot 2023-08-24 at 12 11 19 PM" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/52586927-3aed-4df1-8a72-f34503e5449d">
</div>

<h2>Code</h2>

```c
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

```asm
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
[	<img src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/e2ad21ce-829a-4717-86be-519fe047ce59">
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

<img width="1470" alt="1" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/2b9bb42f-549c-44f2-a881-dca6499ec7db">

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
<img width="1467" alt="2" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/cee6dff3-4a1e-4cca-a8b4-00c244e3dda9">
</div>

<h4>Viz Output</h4>
<div>
<img width="854" alt="3" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/e3f7e3b3-ea34-4240-8e0f-c122b411e21a"></div>

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
<img width="764" alt="4" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/2f49c70d-0879-4ce9-8536-ce1561b7490e">
</div>

<h4>Waveform output</h4>
<div align="center">
<img width="905" alt="5" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/ba9436e0-ebfc-4ef1-9e67-87271aa14dfe">
</div>


</details>

</div>
</detail>



















<details>

<summary><strong>Day 5</strong></summary>
<p>
<h2>Pitfalls of Pipelining: Navigating Branch Instruction Hazards</h2>

Pipelining, a technique aimed at bolstering processor speed, subdivides instruction execution into discrete phases. However, the introduction of pipelining also ushers in challenges known as hazards—obstacles that can disrupt the fluid progression of instructions. Among these, the "branch instruction hazard," commonly recognized as the "branch penalty," stands out prominently.

**1. Structural Clash:**

A structural hazard arises when resource conflicts emerge within the pipeline. For instance, a branch instruction might vie for access to the same processing unit or memory segment already occupied by another instruction in the pipeline. This clash forces a pipeline pause, during which resources are either redistributed or the conflict is resolved. Structural hazards sow inefficiency and chip away at performance by delaying instruction completion.

**2. Data Tug-of-War:**

Data hazards manifest when instructions hinge on outcomes from earlier instructions, yet the requisite data remains elusive. In the context of branch instructions, data hazards crop up when succeeding instructions lean on the result of a prior branch instruction. However, the actual outcome of the branch—whether it's taken or not—remains uncertain. Mismanagement of this can yield inaccurate results. Techniques like forwarding or stalling resolve data hazards, ensuring that instructions access accurate data for proper execution.

**3. Control Conundrum (Branch Hazard):**

Control hazards take center stage when grappling with branch instructions in pipelining. They stem from the ambiguity surrounding a branch's outcome—whether it will be taken or bypassed. In a pipelined processor, instructions are proactively fetched to sustain pipeline flow. Yet, the actual verdict of a branch might only materialize during the execution phase. If the branch's outcome diverges from the prediction formed during the fetch phase, subsequent instructions procured after the branch could prove erroneous.

In response to control hazards, contemporary processors leverage branch prediction techniques to formulate educated guesses about a branch's likelihood of being taken. Accurate predictions facilitate seamless pipeline advancement. However, if predictions falter, a process labeled "pipeline flushing" comes into play. This entails discarding all instructions procured after the misjudged branch, effectively resetting the pipeline to the correct sequence. Such flushing exacts a performance toll, termed the "branch penalty," as it squanders effort and triggers pipeline halts.

In summation, branch instructions introduce hazards to pipelining due to the demand for judgment calls concerning instruction sequence, resource allotment, and data interdependencies. Skillful hazard management through strategies like branch prediction and pipeline flushing proves pivotal in upholding pipeline efficiency and amplifying processor performance.
</p>	

<p>
<h2>Unveiling the Waterfall Logic Paradigm</h2>

Waterfall logic, often referred to as the "waterfall model," is a sequential software development approach that encapsulates the essence of linear progression. This methodology is characterized by a structured, step-by-step framework, where each phase flows into the next like a cascading waterfall. This document delves into the key aspects of the waterfall logic paradigm, elucidating its stages, merits, and limitations.

**1. Phases of Waterfall Logic:**

The waterfall model comprises distinct, well-defined phases, each building upon the accomplishments of the preceding one:

**a. Requirements Gathering:** Inception involves capturing comprehensive project requirements, setting the stage for the subsequent phases.

**b. System Design:** This phase outlines the overall system architecture, identifying components and their relationships.

**c. Implementation:** Here, the actual coding takes place, translating design concepts into functional software.

**d. Testing:** Rigorous testing verifies the software's functionality against requirements, identifying defects for rectification.

**e. Deployment:** The fully tested software is deployed to the intended environment, making it accessible to users.

**f. Maintenance:** Post-deployment, ongoing maintenance tackles bug fixes, updates, and enhancements.

**2. Advantages of Waterfall Logic:**

- **Clarity and Predictability:** The linear nature of waterfall logic offers clarity in project progression, making it easier to estimate timelines and resources.
  
- **Comprehensive Documentation:** Each phase mandates documentation, resulting in a well-documented project lifecycle for future reference.
  
- **Early Planning:** Rigorous initial planning ensures a solid foundation, reducing the likelihood of major changes down the line.
  
- **Clear Milestones:** Well-defined phase boundaries provide clear milestones, aiding project tracking and assessment.
  
**3. Limitations and Criticisms:**

- **Inflexibility:** Once a phase is completed, revisiting it can be challenging, making it less adaptive to changing requirements.
  
- **Late User Involvement:** Stakeholder input typically occurs early, potentially leading to a mismatch between the final product and user needs.
  
- **Uncertainty Handling:** Inadequate provisions for addressing uncertainties or evolving requirements may hinder adaptability.
  
- **Real-world Application Suitability:** Ideal for projects with well-understood requirements, but may not align with projects that demand iterative exploration.
  
**4. Variations and Modern Adaptations:**

Over time, variations and adaptations of the waterfall model have emerged, such as the "V-Model," which emphasizes rigorous testing in conjunction with each development phase, and the "W-Model," which incorporates maintenance and user feedback loops.

**Conclusion:**

The waterfall logic paradigm, reminiscent of a cascading waterfall, offers a structured, methodical approach to software development. Its sequential nature fosters clarity and predictability, yielding comprehensive documentation and clear milestones. However, its rigidity and potential lack of adaptability to evolving requirements have prompted the development of more flexible methodologies. As the software development landscape evolves, waterfall logic remains a foundational model that continues to inspire adaptations and innovations.

<div align="center">
<img width="1470" alt="1" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/80781a78-38dd-410f-9b55-3f6f48599f81">
</div>

<h4>Final 4 stage implementation code</h4>

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
   m4_asm(SW, r0, r10, 100)
   m4_asm(LW, r15, r0, 100)
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;
              //Fetch1   
         $pc[31:0] = >>1$reset ? 32'b0 :
                     >>3$valid_taken_br ? >>3$br_tgt_pc :
                     >>3$valid_load ? >>3$inc_pc : 
                     (>>3$valid_jump && >>3$is_jal) ? >>3$br_tgt_pc :
                     (>>3$valid_jump && >>3$is_jalr) ? >>3$jalr_tgt_pc :
                     >>1$inc_pc;
                     
                    
      @1
         $inc_pc[31:0] = $pc + 32'd4 ;
         $imem_rd_en = !>>1$reset;    
         $imem_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2]; 
      @3
                
         $valid = !(>>1$valid_taken_br || >>2$valid_taken_br || >>1$valid_load || >>2$valid_load 
                    || >>1$valid_jump || >>2$valid_jump) ;
                    
         $valid_load = $valid && $is_load ;
         $valid_jump = $valid && $is_load;
                       
                       
                 
            //$valid_load = $valid && $is_load ;
                
            //Fetch2 
      @1
         $instr[31:0] = $imem_rd_data[31:0]; 
               
          //Instructions type decode 
         $is_i_instr = $instr[6:2] ==? 5'b0000x || 
                       $instr[6:2] ==? 5'b001x0 || 
                       $instr[6:2] ==? 5'b11001 ;
         $is_r_instr = $instr[6:2] ==? 5'b011x0 || 
                       $instr[6:2] ==? 5'b01011 || 
                       $instr[6:2] ==? 5'b10100 ; 
         $is_s_instr = $instr[6:2] ==? 5'b0100x ;
         $is_b_instr = $instr[6:2] ==? 5'b11000 ;
         $is_j_instr = $instr[6:2] ==? 5'b11011 ;
         $is_u_instr = $instr[6:2] ==? 5'b0x101 ;
         
           //Instruction immediate decode
         $imm[31:0] = $is_i_instr ? {{21{$instr[31]}},$instr[30:20] }:
                      $is_s_instr ? {{21{$instr[31]}},$instr[30:25],$instr[11:8],$instr[7]} :
                      $is_b_instr ? {{20{$instr[31]}},$instr[7],$instr[30:25],$instr[11:8],1'b0} :
                      $is_u_instr ? {$instr[31], $instr[30:20],$instr[19:12],12'b0 }:
                      $is_j_instr ? {{12{$instr[31]}},$instr[19:12],$instr[20],$instr[30:21],1'b0} :
                      32'b0 ;
         $opcode[6:0] = $instr[6:0];

           //b. func7 decode

         $func7_valid = $is_r_instr ;
         ?$func7_valid
            $func7[6:0] = $instr[31:25];
         //c. rs2 decode

         $rs2_valid = $is_r_instr || $is_s_instr || $is_b_instr ;
         ?$rs2_valid
            $rs2[4:0] = $instr[24:20];

          //d. rs1 valid

         $rs1_valid = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr ;
         ?$rs1_valid
            $rs1[4:0] = $instr[19:15] ;

          //e. func3 valid

         $func3_valid = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr ;
         ?$func3_valid
            $func3[2:0] = $instr[14:12] ;

         $rd_valid = $is_r_instr || $is_i_instr || $is_u_instr || $is_j_instr ;
         ?$rd_valid
            $rd[4:0] = $instr[11:7];     
      
         $dec_bits[10:0] = {$func7[5], $func3, $opcode} ;
         $is_beq = $dec_bits ==? 11'bx_000_1100011 ;
         $is_bne = $dec_bits ==? 11'bx_001_1100011 ;
         $is_blt = $dec_bits ==? 11'bx_100_1100011 ;
         $is_bge = $dec_bits ==? 11'bx_101_1100011 ;           
         $is_bltu = $dec_bits ==? 11'bx_110_1100011 ;
         $is_bgeu = $dec_bits ==? 11'bx_111_1100011 ;  
         $is_addi = $dec_bits ==? 11'bx_000_0010011 ;
         $is_add = $dec_bits ==? 11'b0_000_0110011 ;
         
         $is_load = $dec_bits ==? 11'bx_xxx_0000011;
         
         $is_sb = $dec_bits ==? 11'bx_000_0100011;
         $is_sh = $dec_bits ==? 11'bx_001_0100011;
         $is_sw = $dec_bits ==? 11'bx_010_0100011;
         $is_slti = $dec_bits ==? 11'bx_010_0010011;
         $is_sltiu = $dec_bits ==? 11'bx_011_0010011;
         $is_xori = $dec_bits ==? 11'bx_100_0010011;
         $is_ori = $dec_bits ==? 11'bx_110_0010011;
         $is_andi = $dec_bits ==? 11'bx_111_0010011;
         $is_slli = $dec_bits ==? 11'b0_001_0010011;
         $is_srli = $dec_bits ==? 11'b0_101_0010011;
         $is_srai = $dec_bits ==? 11'b1_101_0010011;
         $is_sub = $dec_bits ==? 11'b1_000_0110011;
         $is_sll = $dec_bits ==? 11'b0_001_0110011;
         $is_slt = $dec_bits ==? 11'b0_010_0110011;
         $is_sltu = $dec_bits ==? 11'b0_011_0110011;
         $is_xor = $dec_bits ==? 11'b0_100_0110011;
         $is_srl = $dec_bits ==? 11'b0_101_0110011;
         $is_sra = $dec_bits ==? 11'b1_101_0110011;
         $is_or = $dec_bits ==? 11'b0_110_0110011;
         $is_and = $dec_bits ==? 11'b0_111_0110011;
         $is_lui = $dec_bits ==? 11'bx_xxx_0110111;
         $is_auipc = $dec_bits ==? 11'bx_xxx_0010111;
         $is_jal = $dec_bits ==? 11'bx_xxx_1101111;
         $is_jalr = $dec_bits ==? 11'bx_000_1100111;
         $is_jump = $is_jal || $is_jalr ;
         
         `BOGUS_USE($is_beq $is_bne $is_blt $is_bge $is_bltu $is_bgeu $is_addi $is_add) 
      @2
         
            //Register file read
         $rf_rd_en1 = $rs1_valid && >>2$result ;
         $rf_rd_index1[4:0] = $rs1 ;
         $rf_rd_en2 = $rs2_valid && >>2$result;
         $rf_rd_index2[4:0] = $rs2 ;

      //Branch_instruction2
         $br_tgt_pc[31:0] = $pc + $imm ;

     //source to alu assigned with o/p of read register
         $src1_value[31:0] = 
              (>>1$rf_wr_index == $rf_rd_index1) && >>1$rf_wr_en ?
                 >>1$result :
                  $rf_rd_data1;
         $src2_value[31:0] = 
              (>>1$rf_wr_index == $rf_rd_index2) && >>1$rf_wr_en ?
                 >>1$result :
                   $rf_rd_data2;
                   
      //dmem:1-R/W memory             
      @4
         $dmem_wr_en = $is_s_instr && $valid ;
         $dmem_addr[3:0] = $result[5:2] ;
         $dmem_wr_data[31:0] = $src2_value ;
         $dmem_rd_en = $is_load ;
        
      @4
         //LOAD DATA
         $ld_data[31:0] = $dmem_rd_data ;
      @3
         $jalr_tgt_pc[31:0] = $src1_value + $imm ;
      
      @3
     //Assigning aadi and add value to alu
         $sltu_rslt[31:0] = $src1_value < $src2_value ;
         $sltiu_rslt[31:0]  = $src1_value < $imm ;
         
         $result[31:0] =
              $is_addi ? $src1_value + $imm :
              $is_add ? $src1_value + $src2_value :
              $is_andi ? $src1_value & $imm :
              $is_ori  ? $src1_value | $imm :
              $is_xori ? $src1_value ^ $imm :
              $is_slli ? $src1_value << $imm[5:0] :
              $is_srli ? $src1_value >> $imm[5:0] :
              $is_and ? $src1_value & $src2_value :
              $is_or ? $src1_value | $src2_value :
              $is_xor ? $src1_value ^ $src2_value :
              $is_sub ? $src1_value - $src2_value :
              $is_sll ? $src1_value << $src2_value[4:0] :
              $is_srl ? $src1_value >> $src2_value[4:0] :
              $is_sltu ? $src1_value < $src2_value :
              $is_sltiu ? $src1_value < $imm :
              $is_lui ? {$imm[31:12], 12'b0} :
              $is_auipc ? $pc + $imm : 
              $is_jal ? $pc + 32'd4 :
              $is_jalr ? $pc + 32'd4 :
              $is_srai ? {{32{$src1_value[31]}}, $src1_value} >> $imm[4:0] :
              $is_slt ? ($src1_value[31] == $src2_value[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
              $is_slti ? ($src1_value[31] == $imm[31]) ? $sltiu_rslt : {31'b0, $src1_value[31]} :
              $is_sra ? {{32{$src1_value[31]}}, $src1_value} >> $src2_value[4:0] :
              $is_load || $is_s_instr ? $src1_value + $imm :
              32'bx ;
        //Register file write
         $rf_wr_en = $rd_valid && $rd != 5'b0 && $valid || >>2$valid_load ;
         $rf_wr_index[4:0] = >>2$valid_load ? >>2$rd : $rd ;
         $rf_wr_data[31:0] = >>2$valid_load ? >>2$ld_data : $result ;

        //Branch insturctions
         $taken_br = $is_beq ? ($src1_value == $src2_value):
                     $is_bne ? ($src1_value != $src2_value):
                     $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])):
                     $is_bge ? (($src1_value >= $src2_value) ^ ($src1_value[31]!= $src2_value[31])):
                     $is_bltu ? ($src1_value > $src2_value) :
                     $is_bgeu ? ($src1_value >= $src2_value) :
                     1'b0 ;
           //for invalid instruction
         $valid_taken_br = $valid && $taken_br ;
         
         // Note: Because of the magic we are using for visualisation, if visualisation is enabled below,
         //       be sure to avoid having unassigned signals (which you might be using for random inputs)
         //       other than those specifically expected in the labs. You'll get strange errors for these.
         // Assert these to end simulation (before Makerchip cycle limit).
          //*passed = *cyc_cnt > 40;
   *passed = |cpu/xreg[15]>>5$value == (1+2+3+4+5+6+7+8+9);
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      m4+imem(@1)    // Args: (read stage)
      m4+rf(@2, @3)  // Args: (read stage, write stage) - if equal, no register bypass is required
      m4+dmem(@4)    // Args: (read/write stage)
   
   m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic. @4 would work for all labs.
\SV
   endmodule

```

<h4>Schematic output</h4>
<div align="center">
<img width="446" alt="2" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/2b43b622-0ab1-4779-98dd-d934ad29fd3f">
</div>	

<h4>Waveform</h4>
<div align="center">
<img width="922" alt="3" src="https://github.com/VaibhavTiwari-IIITB/RISCV/assets/140998525/6c5230c9-6408-4e7b-a5dc-5ca41850c0a9">
</div>	

</p>

</details>
 
 

 ## Reference 
 
- https://github.com/kunalg123/
- https://www.vsdiat.com
- https://en.wikipedia.org/wiki/Toolchain
- https://en.wikipedia.org/wiki/GNU_toolchain
- https://github.com/riscv/riscv-gnu-toolchain
- https://github.com/riscv-software-src/homebrew-riscv/tree/main
- https://github.com/NiteshIIITB/RISC-V
- https://redwoodeda.com
- https://ieeexplore.ieee.org/document/8119264
- https://github.com/stevehoover




