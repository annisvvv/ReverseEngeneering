load double world from memory to register.

`ld rd, imm12(rs1)` means `rd = dword memory at address(rs1+(sign extended)imm12)` 
## `c.ldsp`

compressed load double word using stack pointer

`c.ldsp rd, uimm9 (sp)` that means `rd = memeory at address (sp + (ZERO EXTENDED)uimm9)`

uimm9 is scaled by 8 so bottom 3bits are implicit zeros.

just read it like ld !
# `c.ld`

compressed load double word from memory to register

`c.ld rd', uimm8(rs1')` => `rd' = dword memory at address(rs1' + (zero extended)uimm8 )`

`rd' and rs1'` are restricted only inside `x8 - x15`

uimm9 is scaled by 8 so bottom 3bits are implicit zeros.