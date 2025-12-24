## Listing source code lines

This option is only relevant to situations in which you have the source code for the program being debugged, and it was built with symbols enabled (the -g or -ggdb flags to gcc). It will not be useful when reverse engineering opaque binaries,.

The **_`list`_** command will show you source code surrounding the current location you are stopped at.

The **_`list <function name>`_** command will show source code before and after the given function.

The **_`list <source file name>:<line number>`_** command will show source code before and after the given line in the given file.
## Breakpoints as offets vs. addresses in memory

Note in the below how when breakpoints are initially printed out, they are small numbers. But then when the program is started, and they are printed out again, they are larger numbers. This is because before the program is **r**un, the “address” is really just an offset from the start of the code execution of the executable. The debugger doesn’t yet know where the program will be loaded into memory, until it’s actually executed. This is also true because operating systems may randomize where the executable is loaded in memory (a mechanism called Address Space Layout Randomization (ASLR), which is designed to help mitigate some security vulnerabilities.) Therefore, after the executable is started, the debugger now can display the real addresses for the executable after it has been loaded in memory and started.
## One-time Disassembly Display

The **_`disassemble`_** command (_short form: **disas**_) _by itself_ will show you assembly surrounding the current location you are stopped at.

The **_`disassemble <address or symbol name>`_** command will disassemble the memory specified by the address or symbol name.

You can optionally give the **_/r_** argument after _disassemble_ to display the **_r_**_aw bytes_ which make up the instructions.

You can optionally give the **_/m_** argument after _disassemble_ to **_m_**_ix source code and assembly_.

To give both arguments simultaneously, they must be combined as “/rm”.

Alternatively, one form of the **_x_** (e**x**amine memory) command (which we’ll learn more about later), can display some number of instructions (10 in the below example) at a given address. That form is:

**_`x/10i <address>`_**