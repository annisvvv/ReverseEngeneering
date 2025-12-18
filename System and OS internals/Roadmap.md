# phase 0
x86 basics
# phase 1 firmware foundations
1. Arch4021 - introduction UEFI
2. HW1101 - intel SPI analysis
3. Arch4031 - intro coreboot
# phase 2 intel firmware security
1. Arch4001 - x86-64 intel frimware attack and defense
# phase 3 Windows boot & kernel internals
1. windows boot process
2. Arch2821 - Windows kernel internals
# phase 4 Windows kernel exploitation
1. windows kernel exploitation courses

---
Platform_Security_and_Vulnerability_Research_Roadmap
====================================================

FOUNDATION
----------
- Programming
  - C (mandatory)
  - x86-64 Assembly (reading & writing)
- Computer Architecture
  - x86 execution modes (real/protected/long)
  - Paging (4-level, EPT)
  - Rings & privilege transitions
  - Interrupts, exceptions, IDT/GDT
  - MSRs
  - SMM fundamentals

REVERSE_ENGINEERING_CORE
------------------------
- Static Analysis
  - Ghidra / IDA
  - Control flow analysis
  - Compiler optimizations & artifacts
- Dynamic Analysis
  - WinDbg (user + kernel)
  - QEMU / Bochs
  - Breakpoints, memory tracing
- Binary Formats
  - PE / COFF
  - EFI binaries

FIRMWARE_AND_PLATFORM_SECURITY
-------------------------------
- UEFI
  - SEC / PEI / DXE / SMM phases
  - Boot vs Runtime Services
  - Secure Boot
  - UEFI drivers & protocols
- Intel SPI
  - SPI flash layout
  - Flash Descriptor
  - BIOS / ME / GbE regions
  - Read/write permissions
  - CHIPSEC analysis
- coreboot
  - Boot stages (ROM/RAM)
  - CBFS
  - Payloads (SeaBIOS, Tianocore)
  - Root of Trust concepts
- Intel Firmware Security
  - Boot Guard
  - ACMs & fuses
  - SMM attacks
  - Firmware persistence
  - Defense & hardening

WINDOWS_BOOT_AND_KERNEL
-----------------------
- Windows Boot Chain
  - bootmgfw.efi
  - winload.efi
  - Measured Boot
  - ELAM
- Windows Kernel Internals
  - ntoskrnl architecture
  - Memory manager
  - Object manager
  - Processes & threads
  - IRQLs
  - Driver model (WDM / KMDF)
  - PatchGuard, DSE, VBS
- Kernel Debugging
  - WinDbg local & remote
  - Symbols & PDBs
  - Crash dump analysis

WINDOWS_KERNEL_EXPLOITATION
---------------------------
- Vulnerability Classes
  - Use-after-free
  - Pool corruption
  - Integer overflows
  - Logic bugs
- Exploitation
  - Privilege escalation
  - Bypass mitigations
  - Kernel rootkits
- Driver Exploitation
  - IOCTL attack surface
  - Signed driver abuse

VULNERABILITY_RESEARCH_METHODS
-------------------------------
- Attack surface discovery
- Trust boundary analysis
- Patch diffing
- Root cause analysis
- Variant analysis
- Responsible disclosure

FUZZING_AND_AUTOMATION
-----------------------
- Coverage-guided fuzzing
  - AFL++
  - WinAFL
- Kernel fuzzing concepts
  - Syzkaller (theory)
- Firmware fuzzing basics
- Harness development

VIRTUALIZATION_AND_EMULATION
-----------------------------
- QEMU internals
- Firmware emulation (UEFI + QEMU)
- Snapshot-based debugging
- VM-based exploit testing

OPTIONAL_ELITE_TOPICS
----------------------
- DMA & PCIe
- IOMMU
- Side-channel awareness
- Supply-chain firmware attacks

RESEARCH_OUTPUT
----------------
- Writeups & exploit reports
- Proof-of-concept code
- Public blog / GitHub
- Conference-quality research mindset
