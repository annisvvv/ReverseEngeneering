## Viewing Registers

Create and place a registers window as was shown in the [UI setup video](https://p.ost2.fyi/courses/course-v1:OpenSecurityTraining2+Dbg1011_WinDbg1+2024_v1/course-v1:OpenSecurityTraining2+Dbg1011_WinDbg1+2021_v1/jump_to_id/7152c24403414999bc96ea71e9b928c6).

![](https://p.ost2.fyi/assets/courseware/v1/ce405a8ed7589fa37dfb70e5b1e41ea8/asset-v1:OpenSecurityTraining2+Dbg1011_WinDbg1+2024_v1+type@asset+block/WinDbgToolbar_Window_Regs.png)

or

Type `r` and a comma-deliminated set of register names to print out their values. E.g.

```
0:000> r rax, rsp, bl, r11d
rax=0000000000000002 rsp=000000000014fe08 bl=0 r11d=14fdb0
```

[MS documentation for r](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/r--registers-)  
[MS documentation for viewing & editing registers](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/registers-window)

## Modifying Registers

In the register window, double-click into the desired register and start typing to change the register contents.

or

Use the same `r` command register syntax as viewing registers, but use an equal sign at the end to assign a value to the register. E.g.

```
0:000> r ax = 0xf00d, rbx = 0xdeadfacebeefd00d, bl = 0x0f
0:000> r ax, rbx, bl
ax=f00d rbx=deadfacebeefd00f bl=f
```

[MS documentation for r](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/r--registers-)  
[MS documentation for viewing & editing registers](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/registers-window)

## Viewing Memory

Create and place a memory window as was shown in the [UI setup video](https://p.ost2.fyi/courses/course-v1:OpenSecurityTraining2+Dbg1011_WinDbg1+2024_v1/course-v1:OpenSecurityTraining2+Dbg1011_WinDbg1+2021_v1/jump_to_id/7152c24403414999bc96ea71e9b928c6).

![](https://p.ost2.fyi/assets/courseware/v1/de514d48c72bf833211efb8f92083170/asset-v1:OpenSecurityTraining2+Dbg1011_WinDbg1+2024_v1+type@asset+block/WinDbgToolbar_Window_Memory.png)

or

Utilize the `d*` set of commands, which **d**isplay varying amounts of memory at a given address, with varying sizes.

`db <address> L<number>` == displays `<number>` bytes starting at `<address>`.

`dd <address> L<number>` == displays `<number>` doublewords (4 bytes) starting at `<address>`.

`dq <address> L<number>` == displays `<number>` quadwords (8 bytes) starting at `<address>`.

`da <address>` == displays as **A**SCII string at that address until first null terminator.

e.g.

```
0:000> db rsp L6
00000000`0014fe08  ef be ad de 01 00                                ......
0:000> dd rsp L6
00000000`0014fe08  deadbeef 11100001 00000001 0000693d
00000000`0014fe18  4b054299 00007fff
0:000> dq rsp L6
00000000`0014fe08  11100001`deadbeef 0000693d`00000001
00000000`0014fe18  00007fff`4b054299 00000000`00000000
00000000`0014fe28  00000001`40001a4d 00000000`00000001
0:000> da 00000001`40002220
00000001`40002220  "First %d elements of the Fibbona"
00000001`40002240  "cci sequence: "
```

[MS documentation for full d* forms](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/d--da--db--dc--dd--dd--df--dp--dq--du--dw--dw--dyb--dyd--display-memor)  
[MS documentation for the display range syntax](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/address-and-address-range-syntax)  
[MS documentation for viewing & editing memory](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/memory-window)

## Modifying Memory

Move to the desired location in a memory window, click into the window, and start typing to write values into memory at that location.

or

Utilize the `e*` (**e**dit) forms, similar to the `d*` (**d**isplay) forms, to edit values of a specific size in memory at a given address.

```
0:000> eb rsp 0x11 0x22 0x33 0x44
0:000> db rsp L4
00000000`0014fe08  11 22 33 44                                      ."3D
0:000> ed rsp 0xdeadbeef
0:000> dd rsp L1
00000000`0014fe08  deadbeef
```

[MS documentation for full e* forms](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/e--ea--eb--ed--ed--ef--ep--eq--eu--ew--eza--ezu--enter-values-)  
[MS documentation for the display range syntax](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/address-and-address-range-syntax)  
[MS documentation for viewing & editing memory](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/memory-window)