zero extend byte in register to double world register

`zext.b rd, rs` => `rd = bottom 8bits of rs, zero extended to 64bits`

this is s a sudo instruction of `andi rd, rs, 255`