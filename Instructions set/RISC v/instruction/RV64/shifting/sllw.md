shift left logical by register, word size

`sllw rd, rs1, rs2`

shift rs1 left by the number of bits specified by the bottom 5 bits of rs2.

![[Pasted image 20251220053240.png]]
Since its a word we only take 0x55667788 shift it sign extend it to 64bits.

![[Pasted image 20251220053629.png]]

so treat it as 32bits and then sign extend it.