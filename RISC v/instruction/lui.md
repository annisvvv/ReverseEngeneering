niload upper immediate

`lui rd, Uimm20` = `upper 20bits of rd[31:12] = Uimm20`

lui sets the upper 20bits and sets the lower 2 bots to 0, so to create a 32bit imm do lui then addi not the inverse.