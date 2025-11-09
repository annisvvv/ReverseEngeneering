- There are unsigned CMOV instructions such as:

	CMOVA or CMOVNBE = Above [Carry Flag or Zero Flag = 0]
	
	CMOVAE or CMOVNB = Above Or Equal [Carry Flag = 0]
	
	CMOVNC = Not Carry [Carry Flag = 0]
	
	CMOVB or CMOVNAE = Below [Carry Flag = 1]
	
	CMOVC = Carry [Carry Flag = 1]
	
	CMOVBE or CMOVNA = Below Or Equal [Carry Flag or Zero Flag = 1]
	
	CMOVE or CMOVZ = Equal [Zero Flag = 1]
	
	CMOVNE or CMOVNZ = Not Equal [Zero Flag = 0]
	
	CMOVP or CMOVPE = Parity [Parity Flag = 1]
	
	CMOVNP or CMOVPO = Not Parity [Parity Flag =0]

- There are also signed CMOV instructions such as:

	CMOVGE or CMOVNL = Greater Or Equal [Sign Flag xor Overflow Flag = 0]
	
	CMOVL or CMOVNGE = Less [Sign Flag xor Overflow Flag = 1]
	
	CMOVLE or CMOVNG = Less Or Equal [Sign Flag xor Overflow Flag or ZF = 1]
	
	CMOVO = Overflow [Overflow Flag = 1]
	
	CMOVNO = Not Overflow [Overflow Flag = 0]
	
	CMOVS = Sign NEGATIVE [Sign Flag = 1]
	
	CMOVNS = Not Sign POSITIVE [Sign Flag = 0]
## what is CMOV
CMOV stands for Conditional Move a family of x86 assembly instructions that perform a move operation depending on a condition (like a flag in the CPU).

In other words, instead of using a traditional _branch_ (`if` / `jmp`) to decide which value to move, `cmov` checks the status flags (like `ZF`, `SF`, `CF`, `OF`) and moves data only if the condition is true.
## The difference between signed and unsigned instructions
The difference between **signed** and **unsigned** instructions in x86 assembly comes down to **how the CPU interprets the bits in a register or memory** — **not** the operation itself (like ADD or SUB), but **how comparisons and conditions are evaluated**.

|Type|Meaning|Example (8-bit)|
|---|---|---|
|**Unsigned**|Bits = pure number (0 to 255)|11111111 = **255**|
|**Signed** (Two's Complement)|MSB = sign bit (0=positive, 1=negative)|11111111 = **-1**|

| Operation     | Unsigned   | Signed                |
| ------------- | ---------- | --------------------- |
| **Is A > B?** | JA (Above) | JG (Greater)          |
| **Is A < B?** | JB (Below) | JL (Less)             |
| **Is A ≥ B?** | JAE / JNB  | JGE                   |
| **Is A ≤ B?** | JBE        | JLE                   |


When a comparison is done in assembly :
```
cmp eax, ebx
```

It sets the **CPU flags** (Zero Flag `ZF`, Sign Flag `SF`, Overflow Flag `OF`, Carry Flag `CF`) based on `eax - ebx`. But how you **interpret** those flags depends on whether you’re comparing **signed** or **unsigned** numbers.
## Unsigned Conditional Moves
Unsigned conditions use **Carry Flag (CF)** and **Zero Flag (ZF)**

|Instruction|Condition|Meaning (unsigned)|Example|
|---|---|---|---|
|`cmova`|CF=0 and ZF=0|**Above**|move if `eax > ebx`|
|`cmovae`|CF=0|**Above or equal**|move if `eax >= ebx`|
|`cmovb`|CF=1|**Below**|move if `eax < ebx`|
|`cmovbe`|CF=1 or ZF=1|**Below or equal**|move if `eax <= ebx`|
These are for **unsigned integers** (like `unsigned int` in C).

## Signed Conditional Moves
Signed conditions use **Sign Flag (SF)** and **Overflow Flag (OF)**.

| Instruction | Condition      | Meaning (signed)     | Example              |
| ----------- | -------------- | -------------------- | -------------------- |
| `cmovg`     | ZF=0 and SF=OF | **Greater**          | move if `eax > ebx`  |
| `cmovge`    | SF=OF          | **Greater or equal** | move if `eax >= ebx` |
| `cmovl`     | SF≠OF          | **Less**             | move if `eax < ebx`  |
| `cmovle`    | ZF=1 or SF≠OF  | **Less or equal**    | move if `eax <= ebx` |
These are for **signed integers** (like `int` in C).
# recap
The CPU can’t tell whether you’re using signed or unsigned numbers — it just sees bits.  
So you must choose the right conditional instruction depending on how your values should be interpreted.