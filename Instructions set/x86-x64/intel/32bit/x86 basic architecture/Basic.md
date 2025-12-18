The basic architecture is made up of a CPU, memory and I/O devices which are input/output devices which are all connected by a system bus as detailed below.

![](https://0xinfection.xyz/reversing/imgs/1520249055678.jpg)

#### The CPU consists of 4 parts which are:

1)Control Unit - Retrieves and decodes instructions from the CPU and then storing and retrieving them to and from memory.
2)Execution Unit - Where the execution of fetching and retrieving instructions occurs.
3)Registers - Internal CPU memory locations used a temporary data storage.
4)Flags - Indicate events when execution occurs.

![](https://0xinfection.xyz/reversing/imgs/1520178351635.jpg)

a 32-bit CPU first fetches a double word (4 bytes or 32-bits in length) from a specific address in memory and is read from memory and loaded into the CPU. At this point the CPU looks at the binary pattern of bits within the double word and begins executing the procedure that the fetched machine instruction directs it to do.

Upon completion of executing an instruction, the CPU goes to memory and fetches the next machine instruction in sequence. The CPU has a register, which we will discuss registers in a future tutorial, called the EIP or instruction pointer that contains the address of the next instruction to be fetched from memory and then executed.