store double world from register to memory.

`sd rs2, imm12 (rs1)` that means `dword memory at address(rs1 + (sign extended) imm12) = rs2`