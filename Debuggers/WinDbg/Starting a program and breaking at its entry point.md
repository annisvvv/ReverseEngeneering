## Starting a program and breaking at its entry point

By default when you open an executable in WinDbg, it will stop at a breakpoint in the `ntdll.dll` file, after your program is loaded, but before `main()` is called. This will give you an opportunity to set breakpoints within the target executable.

If you have symbols (definitions for functions, variables, etc) for the executable, a breakpoint can be set based on a symbol name. But in many cases you will not have symbols, unless you’re debugging code you wrote, or Microsoft wrote and which they provide symbols for. Therefore you can generically set a breakpoint at the first assembly instruction of that binary by issuing the command `bp $exentry`.

However, this will typically be within the C runtime, “function which calls `main()`”, rather than `main()` itself. Therefore you may need to step over some boilerplate executable setup in order to find the `main()` code. Doing this on a reference executable like `Fibber.exe`, as shown in the below video, can help you get a sense of what C runtime library waypoints you might see on your way to `main()` (though this will differ based on whether you’re testing on a debug-built vs. release-built executable.)
## Setting Code Breakpoints:

Click on the source/assembly and hit shortcut F9 to insert a breakpoint.

or

Enter `bp <address or symbol name>` in the Command window (for **B**reak**P**oint)

[MS Documentation for bp 1](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/methods-of-controlling-breakpoints)

[MS Documentation for bp 2](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/bp--bu--bm--set-breakpoint-)

## Listing Code Breakpoints:

`bl` in the Command window (for “**B**reakpoint **L**ist")

Note the numbers for each breakpoint, as those numbers will be used for other commands like the “bc” below

[MS documentation for bl](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/bl--breakpoint-list-)

## Unsetting Code Breakpoints:

`bc <breakpoint number given by bl>` in the Command window (for **B**reakpoint **C**lear)

or

Click the “clear” link shown for a given breakpoint in the `bl` output

[MS Documentation for bc](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/bc--breakpoint-clear-)
## Break On Write-Only Access

A simplified form of the **b**reak on **a**ccess command is:

`ba <access type> <data size> <address>`

Where:

`<access type>` == `w` (for write-access)

`<data size>` == `1, 2, 4, or 8` (bytes)

`<address>` == an absolute address, symbol name, or calculation of an address like `rsp+0x24`.

So for instance to break when 4 bytes are written to address 000000000014fdf4, you would enter:

`ba w 4 000000000014fdf4`

See the [MS documentation for `ba`](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/ba--break-on-access-) for the full syntax and supported forms.

## Break On Read-And-Write Access

The `ba` instruction does not support a “break on read-only” capability, because Intel hardware does not have this capability. Some debuggers _simulate_ this, by setting both a break on read/write and a break on write, and then determining if the break must have been a read-only access. But this takes up twice as many hardware breakpoints (discussed more later). WinDbg however does not offer this capability. Therefore it is your job to determine based on the assembly instruction which the code is stopped at whether it was a read or a write.

Therefore the syntax to set a “break on read _and_ write” access is the same as the above, but with the `r` access type. I.e.:

`ba r 4 000000000014fdf4`

See the [MS documentation for `ba`](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/ba--break-on-access-) for the full syntax and supported forms.

## Break On Read-Only Access

I just said, there’s no support for that :P
## Disabling Breakpoints:

`bd <breakpoint number given in bl>` in the Command window.

Or clicking the “Disable” link in the `bl` output, if the breakpoint is currently enabled.

[MS Documentation for bd](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/bd--breakpoint-disable-)

## Enabling Breakpoints:

`be <breakpoint number given in bl>` in the Command window (for **B**reakpoint **E**nable).

Or clicking the “Enable” link in the `bl` output if a breakpoint is currently disabled.

[MS Documentation for be](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/be--breakpoint-enable-)