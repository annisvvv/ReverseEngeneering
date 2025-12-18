A **calling convention** is simply _the rules that define how functions are called_:
- How arguments are passed (registers or stack)
- Who cleans the stack (caller or callee)
- Where the return value is stored
- How registers must be preserved (“saved”)
# 32bit calling convention
### **1. stdcall**
Used by Windows API (32-bit).
- **Arguments:** pushed on **stack**, right-to-left
- **Stack cleanup:** callee (`ret 0x10` for example)
- **Return value:** `EAX`
- **Preserved registers:** `EBX`, `ESI`, `EDI`, `EBP`

### **2. cdecl**
Used by most C programs.
- **Arguments:** stack, right-to-left
- **Stack cleanup:** caller (`add esp, X`)
- **Return value:** `EAX`

### **3. fastcall**
Used to make calls faster.
- **Arguments:** first 2 arguments in registers
    - Microsoft fastcall → `ECX`, then `EDX`
    - GCC fastcall → different rules
- Rest go on the stack
- **Return:** `EAX`

```
push 5
push 2
call func
add esp, 8
```
# **64-bit Calling Conventions (x86-64)**

Here things change a LOT.  
Most parameters are passed in **registers**, not the stack.

## **1. Windows x64 Calling Convention**
(Used by ALL 64-bit Windows code.)
- **Arguments:**
    - RCX = 1st
    - RDX = 2nd
    - R8 = 3rd
    - R9 = 4th
    - Others → stack
- **Return value:** RAX
- **Shadow space:** Caller reserves **32 bytes** before calling  
    (Windows-specific)
- **Preserved registers:**
    - RBX, RBP, RDI, RSI
    - R12, R13, R14, R15  
        (callee must restore them)

Example:
```
mov rcx, 10     ; arg1 
mov rdx, 20     ; arg2 
call func
```
## **2. System V AMD64 Calling Convention**
Used on **Linux, macOS**, BSD etc.
- **Arguments:**
    - RDI
    - RSI
    - RDX
    - RCX
    - R8
    - R9
    - (same order for integer args)
- **Return value:** RAX
- **Preserved registers:**
    - RBX, RBP, R12–R15

Example:
```
mov rdi, 10 
mov rsi, 20 
call func
```
# Differences Between 32-bit and 64-bit Calling Conventions

|Feature|32-bit x86|64-bit x86-64|
|---|---|---|
|**Arguments**|Mainly on **stack**|Mostly in **registers**|
|**Return value**|EAX|RAX|
|**Stack cleanup**|Depends on convention|Always caller|
|**Shadow space**|No|Windows only|
|**Registers**|8 general-purpose|16 general-purpose|
|**Pointer size**|4 bytes|8 bytes|

# notes
- visual studio puts the first argument to a function in rcx
- eax or rax is the place where the return value returns from a c function