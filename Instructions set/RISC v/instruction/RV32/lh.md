
load half world from memory to register

`lh rd, imm12(rs1)` => `rd = half world (16bit) from memory address at address(ts1 + imm12), sign extended to 32bits` when used in rv64 it will be sing extended to 64bits
# lhu
load half world unsigned from memory to register

`lhu rd, imm12(rs1)` => `rd = half world(16bit) from memory at address(rs1 + imm12), zero extended (bc unsigned) to 32bits`