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

there is a stack frame for the main function also referred as the activation record (a block of memory on the **call stack** that stores all the information a function needs while it’s running — and what’s needed to return to the caller when it finishes.) it exists whenever a function started but yet to complete.

```
#include <stdio,h>

int addMe(int a, int b);

int main(void){
	int result = addMe(2, 3);
	printf("the rsult of the addMe function is %d!\n", result);
	
	return 0;
}
int addMe(int a, int b){
	return a + b;
}
```

For example, inside of the body of the int main(void) there is a call to int addMe(int a, int b) which takes two arguments a and b. There needs to be assembly language code in int main(void) to push the arguments for int addMe(int a, int b) onto the stack.

after compiling this program, running it will print the value 5. (The result of the addMe function is 5!)

Very simply, int main(void) calls int addMe(int a, int b) first and will get put on the stack like this:

![](https://0xinfection.xyz/reversing/imgs/1520144504701.jpg)

You can see that by placing the arguments on the stack, the stack frame for **int main(void)** has increased in size. We also reserved space for the return value which is computed by **int addMe(int a, int b)** and when the function returns, the return value in **int main(void)** gets restored and execution continues in **int main(void)** until it finishes.

Once we get the instructions for **int addMe(int a, int b)**, the function may need local variables so the function needs to push some space on the stack which would look like:

![](https://0xinfection.xyz/reversing/imgs/1520622739277.jpg)

**int addMe(int a, int b)** can access the arguments passed to it from **int main(void)** because the code in **int main(void)** places the arguments just as **int addMe(int a, int b)** expects it. 

For intel CPU's FP is the frame pointer and points to the location where the stack pointer was just before **int addMe(int a, int b)** moved the stack pointer or SP for int **addMe(int a, int b)**’s own local variables. (register `EBP` or `RBP` on x86 CPUs) 

```
         ↑ (higher memory)
+---------------------------+
|  argument b               |  [ebp + 12]
|  argument a               |  [ebp + 8]
|  return address           |  [ebp + 4]
|  old base pointer (EBP)   |  [ebp]
|  local variable 1         |  [ebp - 4]
|  local variable 2         |  [ebp - 8]
+---------------------------+
         ↓ (lower memory)

```

Here’s how it works:

- **Arguments** are _above_ the frame pointer (`ebp + offset`).
    
- **Local variables** are _below_ the frame pointer (`ebp - offset`).

The use of a frame pointer is essential when a function is likely to move the stack pointer several times throughout the course of running the function. The idea is to keep the frame pointer fixed for the duration of **int addMe(int a, int b)**’s stack frame. In the meantime, the stack pointer can change values.

Once it is time to exit **int addMe(int a, int b)**, the stack pointer is set to where the frame pointer is which pops off the **int addMe(int a, int b)** stack frame.

In sum, the stack is a special region of memory that stores temporary variables created by each function including main. The stack is a LIFO which is last in, first out data structure which is managed and optimized by the CPU closely. Every time a function declares a new variable it is pushed onto the stack. Every time a function exists, all of the variables pushed onto the stack by that function are freed or deleted. Once a stack variable is freed, that region of memory becomes available for other stack variables.

When a function exits all of its variables are popped off the stack and lost forever. The stack variables are local. The stack grows and shrinks as functions push and pop local variables.

![[Pasted image 20251111044406.png]]
