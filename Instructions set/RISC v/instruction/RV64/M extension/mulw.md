multiply keep low word sized.

`mulw rd, rs1, rs2` => `rd = (signe extended) low32( low32(rs1) * low32(rs2))`

![[Pasted image 20251223105135.png]]

when using int