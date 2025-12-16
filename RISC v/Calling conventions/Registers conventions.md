note : the caller calls the callee

a callee save register belongs to the caller, if the callee needs to use these registers then it is the callee's responsibility to save the values, so it doesn't break things to the caller.

callee saved registers are preserved across procedure calls

The callee saved registers are from `s0` to `s11` ,`sp`

these registers are saved then reloaded by the callee.

caller save registers belong to the callee, so its the caller's responsibility to save the registers before a call to a subroutine, if it needs to ensure they don't change and to restore the registers after the call returns.

caller saved registers are not preserved across calls

the caller saved registers are from `t0-t6, a0-a7, ra`

![[Pasted image 20251211141021.png]]
