# 32-bit x86 Register Roles (common conventions)

### **General-purpose registers**

|Register|Typical Role|
|---|---|
|**EAX**|Return value, accumulator|
|**EBX**|Callee-saved general register|
|**ECX**|Counter for loops (`rep` instructions)|
|**EDX**|Extension of EAX for 64-bit math, I/O port operations|
|**ESI**|Source index (string/array ops), callee-saved|
|**EDI**|Destination index (string/array ops), callee-saved|
|**EBP**|Frame/base pointer|
|**ESP**|Stack pointer|

### **Special registers**

- **EIP** → instruction pointer
- **EFLAGS** → flags
- **Segment registers** → CS, DS, SS, etc.

---

# 64-bit x86-64 Register Roles (System V / Linux)

### **Function arguments**

| Register | Argument |
| -------- | -------- |
| **RDI**  | arg1     |
| **RSI**  | arg2     |
| **RDX**  | arg3     |
| **RCX**  | arg4     |
| **R8**   | arg5     |
| **R9**   | arg6     |

### **Return value**

- **RAX** → main return value
- **RDX:RAX** → for 128-bit returns

### **Callee-saved registers** (must be preserved by the function)

- RBX
- RBP
- R12–R15
- (and RSP always preserved)

### **Caller-saved registers**

- RAX, RCX, RDX, RSI, RDI, R8–R11