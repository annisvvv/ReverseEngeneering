## GDB Commands File

Often you will be starting and stopping the same or different executables multiple times in gdb. You may want to always run the same commands each time you start gdb, to set up a view of a common set of registers, memory, or instructions. Or you may want to set some common breakpoints. This can be accomplished by creating a plain text file (e.g. ~/x.cfg), and entering the set of gdb commands which you want to be executed in gdb on startup, one per line. Then when you start gdb, specify the commands file with the -x option (e.g. **`-x ~/x.cfg`**).

## Intel (x86-64) recommended starting commands

Copy and paste these to your own ~/x.cfg commands text file:

```
display/10i $rip
display/x $rbp
display/x $rsp
display/x $rax
display/x $rbx
display/x $rcx
display/x $rdx
display/x $rdi
display/x $rsi
display/x $r8
display/x $r9
display/x $r12
display/x $r13
display/x $r14
display/10gx $rsp
start
```

## RISC-V (RV32I/RV64I) recommended starting commands

Copy and paste these to your own ~/x.cfg commands text file:

```
display/x $ra
display/x $a0
display/x $a1
display/x $a4
display/x $a5
display/x $s0
display/10gx $sp
display/10i $pc
start
```
# Changing Disassembly Syntax (RISC-V)

You can disable the use of ABI register names, and revert to just using the x0-x31 register names, with:

**`set disassembler-options numeric`**

You can disable the use of pseudo-instructions (aliases) in assembly output, with:

**`set disassembler-options no-aliases`**

**NOTE: I believe there is currently a bug**, because “set disassembler-options”, which should clear these options, does not unset the options (and the “unset disassembler-options” command also does not work). The only way to undo these options is to quit and restart gdb. (But if you find another way, LMK!)