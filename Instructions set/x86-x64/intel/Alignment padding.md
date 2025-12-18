in memory data is usually stored at addresses that satisfy certain boundary 1byte, 2byte, 4byte, 8byte, 16byte... the padding is the extra unused bytes inserted by the compiler to ensure proper alignment.

for example if something is 16bit aligned it must start at an address that is multiple of 2:
```
0x...00  OK
0x...02  OK
0x...04  OK
0x...06  OK
0x...01  NOT OK
0x...03  NOT OK
```

Example in 2byte alignment:
a 2bytes = 16bits short must be stored at an address divisible by 2 if the rsp is at 0x1003 the compiler inserts a 1byte padding so that the 2byte short is stored at 0x1004.

in 16byte alignment data start at address divisible by 16:
```
0x...00   OK
0x...10   OK
0x...20   OK
0x...30   OK

0x...08   NOT OK
0x...18   NOT OK
```

this is because SSE, AVX, and stack frames often require the stack pointer **RSP** to be aligned to 16 bytes before a `call`.

before calling a function the system v requires that the rsp is at a 16byte aligned address however when the call execute it takes 8bytes so inside the function that is called the stack becomes misaligned, so the function reserves to realign it `sub rsp, 16   ; padding to restore 16-byte alignment`

To keep variables or the stack at the required alignment boundary:
- **Compiler inserts padding between variables in structs**
- **The function prologue adds padding to keep RSP aligned**
- **Stack frames may include unused bytes only for alignment**
### Calculations
If an object has alignment **A**, then its address must satisfy:
	Address mod  A = 0
for example : - 16-byte alignment → address % 16 = 0 / - 8-byte alignment → address % 8 = 0

to calculate padding:
	padding = (A− (current_address mod A)) mod A
	
### Example:
`sub rsp, 24`
Why 24?  
Because:
- The function needs locals (e.g., 8 + 8 + 4 bytes)
- Plus padding to restore 16-byte alignment