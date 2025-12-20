https://apps.p.ost2.fyi/learning/course/course-v1:OpenSecurityTraining2+Arch1005_IntroRISCV+2024_v1/block-v1:OpenSecurityTraining2+Arch1005_IntroRISCV+2024_v1+type@sequential+block@c01de726c90241a6b2f65d0db11fb385/block-v1:OpenSecurityTraining2+Arch1005_IntroRISCV+2024_v1+type@vertical+block@0575f73947504ec28b116581b7c1a45f

https://apps.p.ost2.fyi/learning/course/course-v1:OpenSecurityTraining2+Arch1005_IntroRISCV+2024_v1/block-v1:OpenSecurityTraining2+Arch1005_IntroRISCV+2024_v1+type@sequential+block@a4e23c4b444b462a9ebf2aa95c83567c/block-v1:OpenSecurityTraining2+Arch1005_IntroRISCV+2024_v1+type@vertical+block@0d31bb4bb16f47fc8e37789733fc5d73

This take a hex value and adds the equivalent hex by bits to the value we wanna shift for example 4 bits adds a zero, 5 bits change all the shifted value.
### 1. The Rule: Shifting = Power of 2

Every time you shift **left by 1 bit**, you are multiplying the number by **2**.

- Shift left by **1** bit → Multiply by 21 (**2**)    
- Shift left by **2** bits → Multiply by 22 (**4**)
- Shift left by **3** bits → Multiply by 23 (**8**)
- Shift left by **4** bits → Multiply by 24 (**16**)
- Shift left by **5** bits → Multiply by 25 (**32**)
### 2. Why Hex is Special (Base 16)

Hexadecimal is "Base 16." Because 16 is exactly 24, a shift of **4 bits** is a very "clean" operation. It moves the entire digit over and fills the gap with a `0`.

When you shifted your value `0x2086FD7D` by **5 bits**, you were doing this:

Value×25=Value×32

Multiplying a number by 32 doesn't just add a zero; it changes all the digits because 32 isn't the base of the hex system.
### 3. The "Power of 2" Cheat Sheet

If you are coding and need to multiply quickly, use this table to know which shift to use:

|**To Multiply by...**|**Shift Left (<<) by...**|
|---|---|
|**2**|1 bit|
|**4**|2 bits|
|**8**|3 bits|
|**16** (Adds 1 hex zero)|**4 bits**|
|**32** (What you did)|5 bits|
|**256** (Adds 2 hex zeros)|8 bits|
# NOTE
its the same for when shifting right however we just divide.

for example when :

```
RV64I CODE:
lui gp, 0x30EED
addi gp, gp, -959
li t0, 24
srlw gp, gp, t0
```

we shift by 24bits so using the "4-to-1" rule: 24 bits \ 4 = 6 Hex digits. that we will add as 0 at the left. take in consideration that its a rv64 and working with words 32bits.

![[Pasted image 20251220062813.png]]

![[Pasted image 20251220062507.png]]

![[Pasted image 20251220062540.png]]

![[Pasted image 20251220062616.png]]

![[Pasted image 20251220062712.png]]

![[Pasted image 20251220062734.png]]

# Note
![[Pasted image 20251220064124.png]]
