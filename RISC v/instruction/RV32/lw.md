load word from memory to register

`lw rd, imm12(rs1)` that means `rd = word memory at address (rs1 + (sign extended)imm12)`