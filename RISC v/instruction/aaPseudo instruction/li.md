Load immediate to register `li rd, imm12` so `rd = (sign-extended) imm12`

li is actually a pseudo of `addi rd, x0, imm12`

# `c.li` 
compressed load immediate to register

`c.li rd, imm6` that means `rd = (sign extended)imm6`