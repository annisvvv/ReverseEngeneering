branch if not equal

`bne rs1, rs2, offset` 

this translates to if `rs1 != rs2` then `pc = pc + offset (enccoded by a signed imm13, wich is squaled by two`

else `pc = pc + 4` as normal

in practice dissemblers will tend to just show the offset as the absolute target address not the relative displacement.