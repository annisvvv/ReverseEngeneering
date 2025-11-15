A 64-bit CPU uses **64-bit registers** → **8 bytes per register**. Memory is naturally aligned in **8-byte slots** for pointers, saved registers, local variables, return addresses, etc.
So each stack entry (one “line” in your diagram) is:
`8 bytes  =  0x8`

That’s why the offset increases or decreases by **0x8** each time.