```
gdb ./program

(gdb) b main # set break point to main
(gdb) r # run the program
# program stops at main
(gdb) disas # shows the assembly instructions of the current function or address range
(gdb) si # step one instruction
		s # step one source line
		c # continue to the next breakpoint

# optional depends on what you want
(gdb) info registers
(gdb) x/10x $rsp
(gdb) c

```