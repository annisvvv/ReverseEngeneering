subtract word register from word register

`subw rd, rs1, rs2` that translates to `rd = (bottom 32bits)rs1 - (bottom 32bits)rs2`

the 32bits result is sign extended to 64bits.