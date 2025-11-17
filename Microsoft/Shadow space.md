**Shadow store = mandatory 32 bytes reserved by the caller before every call in Windows x64.**  
It acts as a home area for the 4 register-passed arguments (RCX, RDX, R8, R9).  
Functions can spill arguments there or read them after setting up a frame.  
It is required even if the function takes no arguments.
### Shadow store location 
```
[RSP + 0x00] ← (unused, reserved for RCX)
[RSP + 0x08] ← (reserved for RDX)
[RSP + 0x10] ← (reserved for R8)
[RSP + 0x18] ← (reserved for R9)
```
This is how the callee sees it **before it modifies RSP**
### Caller allocation 
```
sub     rsp, 20h      ; 32 bytes shadow space
call    Function
add     rsp, 20h
```
Even if the function takes **0 arguments**, these 32 bytes MUST exist

If the function wants to save its arguments:
```
mov [rsp + 20h], rcx  ; save 1st argument mov [rsp + 28h], rdx  ; save 2nd argument
```

If the function sets up a frame:
```
push rbp 
mov  rbp, rsp 
sub  rsp, <locals>
```

Then the shadow space moves relative to RBP:

```
[rbp + 10h] = RCX home 
[rbp + 18h] = RDX home 
[rbp + 20h] = R8  home 
[rbp + 28h] = R9  home
```
# Difference between callee and caller
The caller is the function that _initiates_ the call.
### The caller’s responsibilities:
✔ Prepare arguments (in registers or on the stack)  
✔ Allocate shadow space (Windows x64 only)  
✔ Preserve some registers (depending on calling convention)  
✔ Execute the `call` instruction  
✔ Clean up the stack after the call (Windows x64)

---

The **callee** is the function that _is being called_. 
### The callee’s responsibilities:
✔ Create a stack frame (optional but common)  
✔ Save registers it will modify (callee-saved registers: RBX, RBP, RDI, RSI, R12–R15 on x64)  
✔ Perform its work  
✔ Restore saved registers  
✔ Return with `ret`