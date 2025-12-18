jump and link

`jal rd, imm12` 

effect 1 : `pc = pc +(sign extended)imm21
	like jaler it sets the least significant bit of the final address = 0, so it doesn't gets misaligned (start at address multiple of 2)

effect 2 : `rd = address after jal instruction (aka pc + 4)`
	so you can get back there later if necessary

very similar to jalr except the jump is always pc relative, you cant specify a starting address in a register. and the Simm is 21 bits instead of 12 that means that it can jump back/forward 2^21 bytes (-+ 1MB)