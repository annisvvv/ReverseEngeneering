Intel has separate concepts of a “hardware” breakpoint vs. a “software” breakpoint. It is generally possible to set an unlimited number of software breakpoints, because they take the form of a single byte “interrupt 3” (0xCC) instruction which the debugger writes into the instruction stream wherever it would like to break. When the interrupt occurs, it ultimately leads back to the debugger, which can update its metadata about what breakpoint fired where, rewrite the instruction stream so the original instruction can occur, update the UI for the human, and allow the execution to continue.

On the other hand, there are a limited number (4) of dedicated Intel special purpose debug registers. These registers inform the memory management unit that it should watch for read, write, execute, or IO accesses targeted the specified addresses/IO ports. The ba instructions we previously saw are actually utilizing the hardware breakpoints behind the scenes. But we only saw write or read+write breakpoints. They also support break on execute. The advantage of a hardware break on execute is that the memory targeted may not actually be mapped into the program’s memory space yet. But if you know the address it will be at later, once it is mapped in, then you can set a breakpoint for there and the processor will alert the debugger when the breakpoint is hit. This is most useful when dealing with malware which has intentional dynamism to the instructions it executes, or in the kernel where different physical memory can be mapped to the same virtual memory address at different times.

## Hardware Break On Execute

A simplified form of the **b**reak on **a**ccess command is for breaking on execute is:

`ba <access type> <data size> <address>`

Where:

`<access type>` == `e` (for **e**xecute).

`<data size>` == `1` (WinDbg mandates that the size must be 1 if the type is “e").

`<address>` == an absolute address, symbol name, or calculation of an address like `rsp+0x24`.

So for instance to break when address 0000000140001050 is executed, you would enter:

`ba e 1 0000000140001050`

Note: You can’t set a break on access breakpoint from the system debug breakpoint where windbg stops you when you first execute a binary. Because hardware debug registers are saved and restored as part of thread state, and the thread state will be swapped out between the system debug point and the execution of the binary - thus “losing” the hardware breakpoints you may set. Instead, set a software breakpoint like `bp $exentry` (the executable entry point), and set hardware breakpoints from there.

See the [MS documentation for `ba`](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/ba--break-on-access-) for the full syntax and supported forms