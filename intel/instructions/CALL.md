call job is to transfer control to a different function in a way that control later be resumed where it let off, it pushes first the address of the next instruction onto the stack and move the RSP by 8 then it gonna serve as a return address used by the RET return instruction to get back to the calling function. Then the RIP (really longue instruction pointer) get changed to the address given by the instruction.

The destination address can be absolute or relative (relative to the end of an instruction or some other register)

RET takes two forms :
- pop the top of the stack into RIP (pop implicitly increments stack pointer RSP)
- pop the top of the stack into RIP and also add a constant number of bytes to RSP