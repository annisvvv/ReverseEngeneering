 mutiply keep high XLEN, unsigned * unsigned

`mulhu rd, rs1, rs2` => `rd = highXLEN((unsigned)rs1 * (unsigned)rs2)`

note: here the `__int128` used so the integer have a 128 bit size.

![[Pasted image 20251222140049.png]]