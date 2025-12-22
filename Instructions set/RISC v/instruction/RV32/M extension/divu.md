divide unsigned

`divu rd, rs1, rs2` => `rd = (unsigned)rs1 / (unsigned)rs2` and round everything towards zero because in c we cant get a floating point result when dividing integers so the remainder is stored elsewhere.

![[Pasted image 20251222131739.png]]
