Functions are the most fundamental feature in software development. A function allows you to organize code in a logical way to execute a specified task. When a program starts a certain section of memory is set aside for the program this is called the stack.

The **stack pointer** is the register that points to the top of the stack it contains the smallest address, such that any address smaller then it is considered garbage and the greater valid. It tells the CPU where to push new data and where to pop data from. Changing it (via `push`/`pop`, `call`/`ret`, `sub`/`add`) moves the top-of-stack and thereby allocates or frees stack memory.

![](https://0xinfection.xyz/reversing/imgs/1520235829712.jpg)

the diagram shows what actually happening in memory, others can show the opposite (arrow up). because in reality the stack is growing downward from higher to lower memory.
- The stack bottom is the largest valid address of the stack and is located in the larger address area on top of the memory model. This can be confusing as the stack bottom is higher in memory. The stack grows downward in memory and it is critical that you understand that now as we go forward.
- The stack limit is the smallest valid address of the stack. If the stack pointer gets smaller than this, there is a stack overflow which can corrupt a program to allow an attacker to take control of a system. Malware attempts to take advantage of stack overflows. As of recent, there are protections build into modern OS that attempt to prevent this from happening.
- the stack top is the current stack pointer (a smaller address if it grew).

There are two types of operators on stack the push and pop, When you **push** a register, you are **copying its content from the CPU into memory** (onto the stack). At the same time, the stack pointer (**ESP**) moves _down_ (because the stack grows downward in memory). When you pop its the opposite by copying the data from the stack to the registers, then to add a value to the stack pointer.
### stack and functions
For each function call there is a section of the stack reserved for the function. This is called the stack frame.

```
#include <stdio.h>
#include <stdlib.h>

void unreachablefunction(void) {
	printf("iam hacked!");
	exit(0);
}
int main(void) {
	printf("hello world");
	
	return(0);
}
```

here we can see two functions, the first is an unreachable function which will never execute and the main function to be called on the stack

![](https://0xinfection.xyz/reversing/imgs/1520622738609.jpg)

