subtract register from register

`sub rd, rs1, rs2` that means `rd = rs1 - rs2`

# `c.sub`
compressed subtract register from register

`c.sub rd', rs2` => `rd' = rd' - rs2'`

`c.sub` can only use the `x8-x15` registers