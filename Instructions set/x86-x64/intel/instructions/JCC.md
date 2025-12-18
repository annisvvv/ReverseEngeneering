Jump if condition code is met `jcc` instructions are `jne` jump if not equal, `jle` jump less or equal, `jge` jump greater or equal.

If a condition is true, the jump is taken otherwise it proceeds to the next instruction.

![[Pasted image 20251118132931.png]]
- jump if not sign (jns) if SF = 0, jump if sign if SF = 1

![[Pasted image 20251118133015.png]]
[[CMP]]

![[Pasted image 20251119043956.png]]

for unsigned `jne, jbe, jae` where as for signed `jne, jle, jge` ect
### Some examples
Jump Zero (jz) == Jump Equal (je), which is taken when the Zero Flag is set to 1 after some arithmetic operation yields a result of zero in a register

Jump Not Zero (jnz) == Jump Not Equal (jne), which is taken when the Zero Flag is set to 0 after some arithmetic operation yields a result of non-zero in a register

This level adds in the **unsigned** comparison mnemonics of
- Jump Above (ja) == Jump Not Below or Equal (jnbe)
- Jump Not Above (jna) == Jump Below or Equal (jbe)
- Jump Below (jb) == Jump Not Above or Equal (jnae)
- Jump Not Below (jnb) == Jump Above or Equal (jae)

This level adds in the **signed** comparison mnemonics of
- Jump Greater-than (jg) == Jump Not Less-than or Equal (jnle)
- Jump Not Greater-than (jng) == Jump Less-than or Equal (jle)
- Jump Less-than (jl) == Jump Not Greater-than or Equal (jnge)
- Jump Not Less-than (jnl) == Jump Greater-than or Equal (jge)
