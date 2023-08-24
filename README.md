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

