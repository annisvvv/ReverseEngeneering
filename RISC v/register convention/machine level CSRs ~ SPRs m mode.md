
### **Machine Information Registers**

|Address|Name|Description|
|---|---|---|
|0xF11|`mvendorid`|Vendor ID|
|0xF12|`marchid`|Architecture ID|
|0xF13|`mimpid`|Implementation ID|
|0xF14|`mhartid`|Hardware thread (hart) ID|

### **Machine Trap Setup**

|Address|Name|Description|
|---|---|---|
|0x300|`mstatus`|Machine status register|
|0x301|`misa`|ISA & extensions|
|0x302|`medeleg`|Exceptions delegated to S-mode|
|0x303|`mideleg`|Interrupts delegated to S-mode|
|0x304|`mie`|Interrupt enable|
|0x305|`mtvec`|Trap vector|
|0x306|`mcounteren`|Counter enable for lower priv.|

### **Machine Trap Handling**

|Address|Name|Description|
|---|---|---|
|0x340|`mscratch`|Scratch register|
|0x341|`mepc`|Exception program counter|
|0x342|`mcause`|Trap cause|
|0x343|`mtval`|Trap value / bad address|
|0x344|`mip`|Interrupt pending|

### **Machine Memory Protection**

|Address|Range|Name|
|---|---|---|
|0x3A0–0x3AF|`pmpcfg0`–`pmpcfg15`|PMP configuration|
|0x3B0–0x3EF|`pmpaddr0`–`pmpaddr63`|PMP regions|

### **Machine Counters/Timers**

|Address|Name|Description|
|---|---|---|
|0xB00|`mcycle`|Cycle counter|
|0xB02|`minstret`|Retired instruction counter|
|0xB03–0xB1F|`mhpmcounter3..31`|Hardware perf counters|

### **Counter/Timer Upper Words (RV32 only)**

|Address|Name|
|---|---|
|0xB80|`mcycleh`|
|0xB82|`minstreth`|
|0xB83–0xB9F|`mhpmcounter3h..31h`|

### **Machine Performance Monitor Setup**

| Address     | Name                               |
| ----------- | ---------------------------------- |
| 0x320       | `mcountinhibit`                    |
| 0x323–0x33F | `mhpmcounter3..31 event selectors` |