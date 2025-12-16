store byte from register to memory

`sb rs2, imm12(rs1)` => `byte at address(rs1 + (sign extended) imm12)=(bottom byte of)rs2`