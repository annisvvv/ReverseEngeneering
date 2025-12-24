# Examination
## Format Specifiers

Many GDB commands support a format specifier, which we will call /FMT (because that’s what it’s called in the gdb help command for each of these commands)

/FMT is the combination of the / character, followed by a number _n_, a format specifier _f_, and a unit size specifier _u_. Each of _n_, _f_, and _u_ are optional, and will default to the last-used values or default initial values if left unspecified.

The command “`display/10i`” we saw before was an _n_ of 10 and a _f_ of ‘i’ for instructions, with no _u_ needing to be specified, because it doesn’t make sense for instructions.

The most common values for format specifier _f_ are:

- ‘**x**’ for he**x**adecimal
- ‘**d**’ for signed **d**ecimal
- ‘**u**’ for **u**nsigned decimal
- ‘**c**’ for ASCII **c**haracters
- ‘**s**’ for a full (presumed-null-terminated) ASCII **s**tring.

The full list of supported formats is given [here](https://web.archive.org/web/20221127202729/https://sourceware.org/gdb/onlinedocs/gdb/Output-Formats.html).

The unit sizes for _u_ are:

- ‘**b**’ for **b**ytes
- ‘**h**’ for **h**alf-words (2 bytes)
- ‘**w**’ for **w**ords (4 bytes)
- ‘**g**’ for **g**iant-words (8 bytes)

**_Intel Note:_** GDB’s terminology for words (4 bytes) is at odds with Intel’s terminology for words (2 bytes)! This will be something you will just have to memorize and keep in mind.

**_RISC-V Note:_** GDB’s terminology for words (4 bytes) matches RISC-V’s terminology for words. The primary terminology difference is that 64-bit (8-byte) values are called “giant-words” in GDB, and “double-words” in RISC-V. This will be something you will just have to memorize and keep in mind.

## Viewing Registers

The “**`info registers`**” (short form: **`info r`**) command will by default print some set of registers which the GDB developers consider most commonly needed.

- **On Intel** these are the general purpose registers, the eflags register, and the segment registers (learned about in [Arch2001](https://ost2.fyi/Arch2001).)
- **On RISC-V** these are the general purpose registers (x0-x31, shown by their ABI names), and the program counter (pc) register.

You can also specify a specific register set that you’d like to view, by listing the registers after “info r”.

[GDB documentation for info registers](https://web.archive.org/web/20221128034353/https://sourceware.org/gdb/onlinedocs/gdb/Registers.html).

You can also use the “**`print`**” command (short form: **`p`**) with a /FMT specifier, using only the _f_ format specifier, to print a single register.

[GDB documentation for print](https://web.archive.org/web/20221208231957/http://www.sourceware.org/gdb/current/onlinedocs/gdb/Data.html#index-printing-data).

The print command requires the register name to be prefixed with a $. The “info r” command requires no such prefix.

- **On Intel** this can lead to confusion with the x86-64 AT&T syntax requirement that immediates are prefixed with a $ whereas registers are prefixed with a %. This will be something you will just have to memorize and keep in mind.

**Intel (x86-64) ‘info r’ example:**

```
(gdb) info r rax rbx rsp
rax            0xface              64206
rbx            0x555555555220      93824992236064
rsp            0x7fffffffe038      0x7fffffffe038
```

**Intel (x86-64) ‘print’ example:**

```
(gdb) p/x $rax
$11 = 0xface
(gdb) p/u $rax
$12 = 64206
(gdb) p/d $rax
$13 = 64206
(gdb) p/d $ax
$14 = -1330
(gdb) p/gd $ax
Size letters are meaningless in "print" command.
(gdb) p/10d $ax
Item count other than 1 is meaningless in "print" command.
```

**RISC-V (RV64I) ‘info r’ example:**

```
(gdb) info r fp sp a4 a5
fp             0x7ffffffffaa8   0x7ffffffffaa8
sp             0x7ffffffff920   0x7ffffffff920
a4             0x7ffffffff940   140737488353600
a5             0x41 65
```

**RISC-V (RV64I) ‘print’ example:**

```
(gdb) p/x $a0
$2 = 0x41
(gdb) p/u $a0
$3 = 65
(gdb) p/d $a0
$4 = 65
(gdb) p/gx $fp
Size letters are meaningless in "print" command.
(gdb) p/10x $fp
Item count other than 1 is meaningless in "print" command.
```

## Viewing (Examining) Memory

The “**`x`**” command (for e**x**amine memory) supports the /FMT specifier.

[GDB documentation of the x command](https://web.archive.org/web/20221127202729/https://sourceware.org/gdb/current/onlinedocs/gdb/Memory.html#index-examining-memory) (which includes discussion of /FMT).

**Intel (x86-64) ‘x’ examine memory example:**

```
(gdb) x/8xb $rsp
0x7fffffffe038: 0xb3    0xd0    0xde    0xf7    0xff    0x7f    0x00    0x00
(gdb) x/4xh $rsp
0x7fffffffe038: 0xd0b3  0xf7de  0x7fff  0x0000
(gdb) x/2xw $rsp
0x7fffffffe038: 0xf7ded0b3  0x00007fff
(gdb) x/1xg $rsp
0x7fffffffe038: 0x00007ffff7ded0b3
(gdb) x/s 0x555555556008
0x555555556008: "First %d elements of the Fibbonacci sequence: "
(gdb) x/3i $rip
=> 0x5555555551a9 <main>:   endbr64 
   0x5555555551ad <main+4>: push   %rbp
   0x5555555551ae <main+5>: mov    %rsp,%rbp
```

**RISC-V (RV64I) ‘x’ examine memory example:**

```
(gdb) x/8xb $sp
0x7ffffffff920: 0x50    0xe0    0xff    0xf7    0xff    0x7f    0x00    0x00
(gdb) x/4xh $sp
0x7ffffffff920: 0xe050  0xf7ff  0x7fff  0x0000
(gdb) x/2xw $sp
0x7ffffffff920: 0xf7ffe050  0x00007fff
(gdb) x/1xg $sp
0x7ffffffff920: 0x00007ffff7ffe050
(gdb) x/s 0x555555555790
0x555555555790: "First %d elements of the Fibbonacci sequence: "
(gdb) x/4i $pc
=> 0x555555555712 <main>:   addi    sp,sp,-32
   0x555555555714 <main+2>: sd  ra,24(sp)
   0x555555555716 <main+4>: sd  s0,16(sp)
   0x555555555718 <main+6>: addi    s0,sp,32
```
# Modifying registers
The “**`set`**” command, when used in conjunction with an equals sign can be used to set registers.

**Intel (x86-64) ‘set’ register value example:**

```
(gdb) set $rax = 0xdeadbeeff00dface
(gdb) p/x $rax
$15 = 0xdeadbeeff00dface
(gdb) set $ax = 0xcafef00d
(gdb) p/x $rax
$16 = 0xdeadbeeff00df00d
```

**Note** that the size written was the size of the register (16 bits, ax) rather than the size of the immediate (32 bits).

**RISC-V (RV64I) ‘set’ register value example:**

```
(gdb) p/x $a0
$4 = 0x41
(gdb) set $a0 = 0xdeadbeeff00dface
(gdb) p/x $a0
$5 = 0xdeadbeeff00dface
```
# modifying memory
Similar to registers, memory can be modified with the “**`set`**” command, also optionally specifying a C-style type in order to specify the length to write.

Immediates which are smaller than the size of the specified memory write are zero-extended, not sign-extended.

**Intel (x86-64) ‘set’ memory example:**

```
(gdb) x/1xg $rsp
0x7fffffffe038: 0x00007ffff7ded0b3
(gdb) set {char}$rsp = 0xFF
(gdb) x/1xg $rsp
0x7fffffffe038: 0x00007ffff7ded0ff
(gdb) set {short}$rsp = 0xFF
(gdb) x/1xg $rsp
0x7fffffffe038: 0x00007ffff7de00ff
(gdb) set {short}$rsp = 0xFFFF
(gdb) x/1xg $rsp
0x7fffffffe038: 0x00007ffff7deffff
(gdb) set {long long}$rsp = 0x1337bee7
(gdb) x/1xg $rsp
0x7fffffffe038: 0x000000001337bee7
```

Note that for the “_`set {short}$rsp = 0xFF`_” it did not sign-extend the 1-byte value to be a 2-byte short value of 0xFFFF. It just zero-extended the 0xFF to 0x00FF, which is why the bottom 2 bytes became 0x00FF.

**RISC-V (RV64I) ‘set’ memory example:**

```
(gdb) x/1xg $sp
0x7ffffffff920: 0x00007ffff7ffe050
(gdb) set {char}$sp = 0xFF
(gdb) x/1xg $sp
0x7ffffffff920: 0x00007ffff7ffe0ff
(gdb) set {short}$sp = 0xFF
(gdb) x/1xg $sp
0x7ffffffff920: 0x00007ffff7ff00ff
(gdb) set {short}$sp = 0xFFFF
(gdb) x/1xg $sp
0x7ffffffff920: 0x00007ffff7ffffff
(gdb) set {long long}$sp = 0x1337bee7
(gdb) x/1xg $sp
0x7ffffffff920: 0x000000001337bee7
```

Note that for the “_`set {short}$sp = 0xFF`_” it did not sign-extend the 1-byte value to be a 2-byte short value of 0xFFFF. It just zero-extended the 0xFF to 0x00FF, which is why the bottom 2 bytes became 0x00FF.
# Updating Stack View

This can be accomplished simply by using the **display** command previously discussed, with a /FMT format specifier indicating how many hex words (32-bit) or giant-words (64-bit) you’d like to display starting at the address in the stack pointer register. You should generally match the size, to that of the pointer size. So words on 32-bit architectures, and giant-words on 64-bit. E.g.

`display/10xg $rsp` on x86 64-bit.

`display/10xw $esp` on x86 32-bit.

`display/10xg $sp` on ARM or RISC-V 64-bit (RV64I).

`display/10xw $sp` on ARM or RISC-V 32-bit (RV32I/RC32E).
# Stack Backtrace

**_backtrace_** (short form: **_bt_**) provides a call stack **b**ack**t**race. The most-recently called function is on top of the backtrace, and the least-recently called function is on the bottom. Or another way to say it is that the function on top was called by the function below it. And the address shown is where the function will return to when it’s done.

E.g. when breaking at the entrypoint of _fibbonacci()_ the first time, _bt_ might yield something like the following output:

```
(gdb) bt
#0  fibbonacci (n=0) at ./fibber.c:4
#1  0x0000555555555742 in main () at ./fibber.c:18
```

Because fibbonacci() is a recursive function, if you continued a ways into the execution, you might instead see output like this:

```
(gdb) bt
#0  fibbonacci (n=3) at ./fibber.c:4
#1  0x00005555555556ea in fibbonacci (n=4) at ./fibber.c:8
#2  0x00005555555556ea in fibbonacci (n=5) at ./fibber.c:8
#3  0x0000555555555742 in main () at ./fibber.c:18
```

[GDB documentation of backtrace](https://web.archive.org/web/20221127202729/https://sourceware.org/gdb/current/onlinedocs/gdb/Backtrace.html#Backtrace)