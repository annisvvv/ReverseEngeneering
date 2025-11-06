# General purpose register GPR
A **general-purpose register** is a **type of register** — one that can hold _any_ kind of data the CPU needs to work with (integers, pointers, counters, etc.). It’s “general-purpose” because it’s not restricted to a single function.

| GPR name | function                                                                                                                                                                                                                          |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| EAX      | Main register used for arithmetic calculations, also known as accumulator as it holds results of arithmetic operations and function return values.                                                                                |
| EBX      | The Base Register. Pointer to data in the DS segment. Used to store the base address of the program.                                                                                                                              |
| ECX      | The Counter register is often used to hold a value representing the number of times a process is to be repeated. Used for loop and string operations.                                                                             |
| EDX      | A general purpose register. Additionally used for I/O operations. In addition will extend EAX to 64-bits.                                                                                                                         |
| ESI      | Source Index register. Pointer to data in the segment pointed to by the DS register. Used as an offset address in string and array operations. It holds the address from where to read data.                                      |
| EDI      | Destination Index register. Pointer to data (or destination) in the segment pointed to by the ES register. Used as an offset address in string and array operations. It holds the implied write address of all string operations. |
| EBP      | Base Pointer. Pointer to data on the stack (in the SS segment). It points to the bottom of the current stack frame. It is used to reference local variables.                                                                      |
| ESP      | Stack Pointer (in the SS segment). It points to the top of the current stack frame. It is used to reference local variables.                                                                                                      |
# Register size hierarchy
All of these registers are 32bit in length and can be referenced to AX and subdivided.

```
# on 32bit systems

EAX   → 32 bits # Same for EBX, ECX, EDX
	AX   → lower 16 bits of EAX
		AH   → high 8 bits of AX
		AL   → low 8 bits of AX
```

![](https://0xinfection.xyz/reversing/imgs/1520145792750.jpg)
In this picture EAX have AX as its 16bit segment subdivided to AL (the low 8bits) and AH (the high 8bits)

In addition, the ESI, EDI, EBP and ESP can be referenced by their 16-bit equivalent which is SI, DI, BP, SP.

![](https://0xinfection.xyz/reversing/imgs/1520613988729.jpg)

```
RAX, RBX, RCX, RDX, RSI, RDI, RBP, RSP  → 64 bits
EAX, EBX, ECX, EDX, ESI, EDI, EBP, ESP  → lower 32 bits
AX,  BX,  CX,  DX,  SI,  DI,  BP,  SP   → lower 16 bits
AL,  BL,  CL,  DL                       → lower 8 bits
```
