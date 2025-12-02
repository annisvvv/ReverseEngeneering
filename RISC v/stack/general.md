a stack is a last in first out data structure where data is pushed on to the top of the stack and popped off the top.

the stack grows to lower memory addresses. contrary to the heap.

sp points to the top of the stack thus the lower address.

on the stack we find local variables, return addresses, save space for registers so functions can share registers without smashing the value for each other, dynamically allocated memory via allocs() or maloc(), stack cookies or canary, arguments passed on the stack, save space for spilled registers when the compiler juggle too many in a function. 