there is two form of control flow:
## conditional 
go to some where if a condition is met. like if statement, loops, switches.

if statements manifest with [[JCC]] and [[CMP]]
## unconditional 
always go somewhere like functions call, goto, exceptions, interrupts.

functions calls manifest themselves as call/ret in asm [[CALL]]

goto manifests itself as jump in asm [[JMP]]

goto example:
```
#include <stdio.h>

int main() {
    int x = 10;

    if (x > 5) {
        goto print_message; // Jumps to the 'print_message' label
    }

    printf("This line will be skipped.\n"); // This line is skipped

print_message: // Label definition
    printf("Value of x is: %d\n", x);

    return 0;
}
```

The `goto` statement in C is a control flow statement that allows for an unconditional jump to a labeled point within the same function. It provides a mechanism to alter the normal sequential execution of a program.