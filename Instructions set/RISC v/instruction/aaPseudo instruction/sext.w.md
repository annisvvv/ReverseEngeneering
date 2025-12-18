Sign extended word in register to double world register

`sext.w rd, rs1` => `rd = bottom 3bits of rs1, sign extended  to 64bits`

this is a pseudo instru for `addiw rd, rx, 0`

the `sext.w` is just an `addiw rd, rs, 0` that just `32bits => 64bits` that's why we add 0.