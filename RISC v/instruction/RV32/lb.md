load bytes from memory to register

`lb rd, imm12(rs1)` that translates to `rd = byte from memory at address(rs1 + imm12), sign extended to 32bits`

when used in 64 bits its further sign extended to 64  bits.