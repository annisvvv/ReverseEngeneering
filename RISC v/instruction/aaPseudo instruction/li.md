Load immediate to register `li rd, imm12` so `rd = (sign-extended) imm12`

li is actually a pseudo of `addi rd, x0, imm12`