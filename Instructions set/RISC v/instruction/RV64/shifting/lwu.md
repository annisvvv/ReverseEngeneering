load word unsigned from memory to register

`lwu rd, imm12(rs1)` that translates to `rd = zero extended word(32bit) from memory at address(rs1 + imm12)`