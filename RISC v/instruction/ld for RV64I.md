load double world from memory to register.

`ld rd, imm12(rs1)` means `rd = dword memory at address(rs1+(sign extended)imm12)`