Their are five control registers which are used to determine the operating mode of the CPU and the characteristics of the current executing task. So, these registers define **how** the processor behaves, not just what data it processes.

| Ctrl register | function                                                                                 |
| ------------- | ---------------------------------------------------------------------------------------- |
| CR0           | System flag that control the operating mode and various states of the processor.         |
| CR1           |                                                                                          |
| CR2           | Memory page fault information.                                                           |
| CR3           | Memory page directory information.                                                       |
| CR4           | Flags that enable processor feathers and indicate feature capabilities of the processor. |
The values on each control register cant be directly accessed however moved to one of the GP registers and there a program can examine the bit flags to determine the operating status of the processor in conjunction with the current running task. This is because CR are critical to system stability changing them can crash the OS and break the memory management.

```
mov eax, cr0     ; Copy CR0 → EAX
# example of moving
```

If a change is required to a control register flag value, the change can be made to the data in the GP register and the register moved to the CR.