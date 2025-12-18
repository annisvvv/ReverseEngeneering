immediate is a constant value that is hardcoded into the assembly instruction.

in RISC-v when an instructions ends with an I like `addi` it means it can take an immediate as an argument

`immN` for N-bit immediate
`uimmN` unsigned N-bit immediate (zero extended not sign extended)
`nzimmN` non zero signed N bit immediate 
`UimmN` upper N bit immediate

imm12 are always shown in decimals in gdb