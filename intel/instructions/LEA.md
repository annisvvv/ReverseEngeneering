Load effective address or LEA  is an instruction in x86/x64 assembly used to **compute an address or arithmetic expression** _without actually reading memory_. It _loads the calculated result_ directly into a register.

LEA uses the r/mX form but is the exception to the rule that the square brackets [] syntax means dereference (value at), the things in [] are just calculated.

- Pointer arithmetic
	`lea rax, [rbx + rcx*4 + 8]`
	This **does NOT access memory**.  
	It computes:
	`rax = rbx + rcx*4 + 8`
	
	Useful when you want to compute new pointers/offsets quickly.	

- Fast integer arithmetic
	`LEA` can combine add, multiply (by 1,2,4,8), and offset in one instruction:
	
	```
	lea eax, [eax + eax*2]   ; eax = eax*3 
	lea edx, [rcx + rbx]     ; edx = rcx + rbx
	```
	
	This avoids using `ADD`, `INC`, or `IMUL`, and sometimes the compiler prefers LEA for optimization.

 - Getting the address of a variable
	In position-dependent code:
	`lea rax, [rip + _variable]`
	Used to get the **address**, not the value.

- Stack frame shortcuts
	Instead of multiple adds/subs:
	`lea rsp, [rbp-0x40]      ; restore stack pointer`
## **What LEA does _not_ do**
- It **does not load a value from memory**
- It **does not dereference** the pointer
- It **does not move data** except the computed result
# example
```
rbx = 0x20
rdx = 0x1000

lea rax, [rdx+rbx*8+5]

rax = 0x1015 this is not the value at 0x1015 its not an address
```