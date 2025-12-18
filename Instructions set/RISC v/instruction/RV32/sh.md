Store half world from register to memory

`sh rs2, imm12(rs1)` => `half world memory at address(rs1 + (sign extended)imm12) = rs2`