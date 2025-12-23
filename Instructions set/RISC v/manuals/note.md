https://riscv.org/technical/specifications/

learn how to use the man:
https://apps.p.ost2.fyi/learning/course/course-v1:OpenSecurityTraining2+Arch1005_IntroRISCV+2024_v1/block-v1:OpenSecurityTraining2+Arch1005_IntroRISCV+2024_v1+type@sequential+block@077ee46d496f4b9fa1b2fb535392e396/block-v1:OpenSecurityTraining2+Arch1005_IntroRISCV+2024_v1+type@vertical+block@747d70f474d94fb9b66c0f1cfdb14753

http://riscvbook.com/greencard-20181213.pdf

difference between privileged that concern arch2005 riscv os internals, unprivileged is what this class is about.

full:
![[Pasted image 20251223124036.png]]

instructions encoding:
![[Pasted image 20251223122403.png]]

op code encoding lookup table:
![[Pasted image 20251223123040.png]]
the opcode of riscv is alway 11 in the inst[1:0]

![[Pasted image 20251223123308.png]]

whats funct3:
the minor opcode, with 3bits. since instru can have the same opcode.
![[Pasted image 20251223123627.png]]

register subset:
![[Pasted image 20251223123812.png]]
![[Pasted image 20251223123850.png]]
![[Pasted image 20251223124150.png]]
c1 means literally 01, c0 0,c2 2...