load byte unsigned from memory to register

`lbu rd, imm12(rs1)` => `rd = byte from memory at address(rs1 + imm12), zero extended to 32bits` when used with rv64 sign extended to 64bits