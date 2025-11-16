look first if the operation is signed or unsigned like there [[IMUL and MUL]] if its signed + or - or unsigned only +
### example:
If the MSB = 0 → **positive**  
If the MSB = 1 → **negative**

lets take 0x84 that is 8bit
	If it's an **unsigned** value
	`0x84 = 132` → **positive**.
	
	If it's a **signed 8-bit** value (two’s complement)
	Range: −128 to +127
	
	`0x84` in binary: `1000 0100`  
	MSB = 1 → **negative**
	
	So **as an 8-bit signed value**, yes:
	
	**0x84 is negative**
	Let’s find the actual number:
	1. Invert bits:  
	    `1000 0100` → `0111 1011`
	2. Add 1:  
	    `0111 1011 + 1 = 0111 1100` (0x7C)
	3. Convert to decimal:  
	    `0x7C = 124`
	
	So the value is:
	**0x84 (signed 8-bit) = −124**

what about 0x84 that is 32bit
	Value: **0x84** → becomes **0x00000084** in 32-bit
	
	Binary (32-bit MSB starts with 0):  
	`00000000 00000000 00000000 10000100`
	
	- MSB = **0** → **positive**

So as **32-bit signed**,  
➡️ **0x84 = +132**