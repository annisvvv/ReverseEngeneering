jump and link register

`jalr rd, rs, imm12` means `pc - rs + (si) imm12`
this make a calculus to jump to a new location set the least significant bit of final address = 0, so its doesn't get mis-aligned(since all RISC-V instructions will start at an address that is a multiple of 2 for compressed or 4 for uncompressed

`rd` will be the address after the `jalr` instruction (aka pc+4 from before pc changes) so code can get back later if necessary by a `RET` for example.