The EIP register is the most important register, it keeps track of the next instruction code to execute. having control over that pointer gives complete control over the program.
#### Practice
Hello world app in c
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

The "unreachablefunction" is not called in this main function of the program, we could hack that and run it using the EIP register.

first the code is compiled
```
gcc -m32 -ggdb -o example example.c
# this compile the code to be working with the IA32
```

Using the GDB debugger and passing all the step using the EIP examination we ca see the EIP pointing to an address to main+17.

![](https://0xinfection.xyz/reversing/imgs/1520173635003.jpg)

after examining the function unre... we can see where it starts in memory and write down the address,

![](https://0xinfection.xyz/reversing/imgs/1520572373912.jpg)

next step is to set EIP to address 0x0804843b so that we hijack program flow to run the unreachableFunction.

![](https://0xinfection.xyz/reversing/imgs/1520572373288.jpg)

and we can run it

![](https://0xinfection.xyz/reversing/imgs/1520192688705.jpg)
