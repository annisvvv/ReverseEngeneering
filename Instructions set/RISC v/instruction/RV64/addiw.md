add immediate to world

`addiw rd, rs1, imm12` => `rd = bottom 32bits of rs1 + 32bit sign extended imm12, yielding a 32bit result, sign extended to 64bits`

ignore overflow when summing

the `sext.w` is just an `addiw rd, rs, 0` that just `32bits => 64bits` that's why we add 0.
# c.addiw
compressed add immediate to word

`c.addiw rd, imm6` expended to `addiw rd, rd, imm6` with `rd not equal x0`