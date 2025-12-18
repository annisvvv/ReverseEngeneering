
### **User Trap Setup**

|Address|Name|
|---|---|
|0x000|`ustatus`|
|0x004|`uie`|
|0x005|`utvec`|

### **User Trap Handling**

|Address|Name|
|---|---|
|0x040|`uscratch`|
|0x041|`uepc`|
|0x042|`ucause`|
|0x043|`utval`|
|0x044|`uip`|

### **User Counters (always visible but writable only via S/M permissions)**

|Address|Name|
|---|---|
|0xC00|`cycle`|
|0xC01|`time`|
|0xC02|`instret`|
|0xC03–0xC1F|`hpmcounter3..31`|

Upper words for RV32:  
`cycleh`, `timeh`, `instreth`, etc. (0xC80+)