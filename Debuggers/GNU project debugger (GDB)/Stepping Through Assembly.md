## Step Over vs. Step Into vs. Step Out

As with other debuggers, the notion of “step over” indicates that the UI should step over call instructions - executing all instructions therein, but not showing the debugger UI as stopped until the instruction after the call instruction is reached. “Step into” on the other hand will step into call instructions. “Step out” will step until a function exit is reached (which the debugger heuristically determines as being complete when it executes a “return” type instruction.)

Note: As with other gdb instructions, if you enter return on an empty line, gdb will just re-execute the previous command. This behavior is especially helpful in the context of stepping, because instead of needing to re-type the step instruction each time you want to step, you can instead just keep hitting return.

### Step Over

**_nexti_** (_short form: **ni**_) steps _over_ the **n**ext **i**nstruction, continuing from the instruction after it, especially if it is a control-flow instruction that might return to the same location (like “call” type instructions.)

[GDB documentation for all stepping instructions](https://web.archive.org/web/20221127202729/https://sourceware.org/gdb/current/onlinedocs/gdb/Continuing-and-Stepping.html#Continuing-and-Stepping)

### Step Into

**_stepi_** (_short form: **si**_) **s**teps _into_ the next **i**nstruction, continuing from wherever that instruction would lead, especially if it is a control-flow instruction (like “call” or “jump” type instructions.)

[GDB documentation for all stepping instructions](https://web.archive.org/web/20221127202729/https://sourceware.org/gdb/current/onlinedocs/gdb/Continuing-and-Stepping.html#Continuing-and-Stepping)

### Step Out

**finish** (_short form: **fin**_) steps _out_ of the current function context, _finish_ing executing the rest of the code until the end of the function.

[GDB documentation for all stepping instructions](https://web.archive.org/web/20221127202729/https://sourceware.org/gdb/current/onlinedocs/gdb/Continuing-and-Stepping.html#Continuing-and-Stepping)
# Run Until Address (aka temporary breakpoint)

If you just want to step forward some number of instructions, but don’t want to set and then delete a breakpoint, or don’t want to count how many instructions it is, you can use the “**`until <address>`**” (short form: **`u`**) command.

Note however that if for some reason the address is never reached (e.g. because control flow branches some other direction) the `until` command will also break upon exit from the current function.