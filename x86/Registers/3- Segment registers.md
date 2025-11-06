# Segment registers
Segment registers hold the starting address of memory segments which are distinct blocks of memory used to organize a program's code, data, and stack. The processor combines the 16-bit value in a segment register with a 16-bit offset to calculate a 20-bit physical address. an offset is an integer value representing the distance from a starting point to a specific location, typically within a data structure like an array or a file.

| Seg register | function                                                                                                                                                            |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CS           | Code segment register stores the base location of the code section (.text section) which is used for data access.                                                   |
| DS           | Data segment register stores the default location for variables (.data section) which is used for data access.                                                      |
| ES           | Extra segment register which is used during string operations.                                                                                                      |
| SS           | Stack segment register stores the base location of the stack segment and is used when implicitly using the stack pointer or when explicitly using the base pointer. |
| FS           | Extra segment register.                                                                                                                                             |
| GS           | Extra segment register.                                                                                                                                             |
Each of these segments are 16bits and contains the pointer to the start of the memory-specific segment.

The CS register contains the pointer to the code segment in memory. The code segment is where the instruction codes are stored in memory. The processor retrieves instruction codes from memory based on the CS register value and an offset value contained in the instruction pointer (EIP) register. Keep in mind no program can explicitly load or change the CS register. The processor assigns its values as the program is assigned a memory space.

The DS, ES, FS and GS segment registers are all used to point to data segments. Each of the four separate data segments help the program separate data elements to ensure that they do no overlap. The program loads the data segment registers with the appropriate pointer value for the segments and then reference individual memory locations using an offset value.

The stack segment register (SS) is used to point to the stack segment. The stack contains data values passed to functions and procedures within the program.

Segment registers are considered part of the operating system and can neither read nor be changed directly in almost all cases. When working in the protected mode flat model (x86 architecture which is 32-bit), your program runs and receives a 4GB address space to which any 32-bit register can potentially address any of the four billion memory locations except for those protected areas defined by the operating system. Physical memory may be larger than 4GB however a 32-bit register can only express 4,294,967,296 different locations. If you have more than 4GB of memory in your computer, the OS must arrange a 4GB region within memory and your programs are limited to that new region. This task is completed by the segment registers and the OS keeps close control of this.