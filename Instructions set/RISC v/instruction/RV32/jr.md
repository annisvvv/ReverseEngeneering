jump to register `jr rs` means `pc = rs`

pseudo of `jalr x0, rs, 0`
# `c.jr`
Compressed jump to register, RV32C/RV64C are encoded in the instruction stream with only 16bits, instead of the usual 32bit