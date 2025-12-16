Add world register to word register

`addw rd, rs1, rs2` => `rd = bottom 32bits of rs1 + bottom 32bits of rs2, yielding a 32bits result sign extended to 64bits`

the instruction doesn't care about overflow when dong the sum of the two immediate
# c.addw
compressed add world register to word register

`c.addw rd', rs2'` expended to `addw rd', rd', rs2'`