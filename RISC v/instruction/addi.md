add immediate to register
`addi rd, rs, imm12` this does `rd = rs + (sign-textended)imm12`
## `c.addi`

the compressed form for that is `c.addi rd, nizmm6` `nizmm` stands for non zero sign extended 6 byte immediate
## `c.addi4spn`

`c.addi4spn` stands for `c.add immediate * 16 to stack pointer, non destructive` 

![[Pasted image 20251204134629.png]]

in this case the immediate must be none zero and also its zero extended not sign extended to 64bits before addition

non destructive means that it add to stack pointer but doesn't change it. it just computes the result in some invisible invisible scratch register and adds it to the destination register.

`c.addi4spn rd', sp + nzuimm10` --> `rd' = sp + (zero extended) nzuimm10`

`rd'` can only be `x8 - x15` that mean s0 - s1 , a0 - a5 
`nzuimm10` is scaled by 4 so bottom 2bits are implicit zeros which means only 8 bits from 10 immediate are actually present in the instruction.

just read it like addi !
## `c.addi16sp`

compressed add immediate * 16 to stack pointer

`c.addi16sp sp, nzimm10` = expands to `addi sp, sp, nzimm10`

![[Pasted image 20251206072418.png]]
