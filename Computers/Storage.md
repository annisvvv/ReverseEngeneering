### 🔹 **Basic Units**

|Name|Abbreviation|Size in Bits|Size in Bytes|
|---|---|---|---|
|**Bit**|b|1 bit|1/8 byte|
|**Nibble**|—|4 bits|0.5 byte|
|**Byte**|B|8 bits|1 byte|

---

### 🔹 **Standard Memory Units (Binary, used by computers)**

(These use power-of-2 sizes: 1024, not 1000)

|Name|Abbreviation|Bytes|
|---|---|---|
|**Kilobyte**|KB|1,024 bytes|
|**Megabyte**|MB|1,024 KB = 1,048,576 bytes|
|**Gigabyte**|GB|1,024 MB|
|**Terabyte**|TB|1,024 GB|
|**Petabyte**|PB|1,024 TB|

---

### 🔹 **Word Sizes (Assembly / CPU architecture)**

These sizes depend on the CPU (16-bit, 32-bit, 64-bit), but the **names stay the same**:

|Name|Meaning|Bits|Bytes|
|---|---|---|---|
|**Byte**|Smallest addressable unit|8|1|
|**Word**|Basic CPU unit|16|2|
|**Dword**|Double Word|32|4|
|**Qword**|Quad Word|64|8|
|**Oword**|Octa Word|128|16|
|**Yword**|256-bit (AVX register)|256|32|
|**Zword**|512-bit (AVX-512)|512|64|

---

### 🔹 **How these are used in assembly (x86/x64)**

|Instruction Size|Bits|Bytes|Example Registers|
|---|---|---|---|
|Byte|8|1|AL, BL, CL, DL|
|Word|16|2|AX, BX, CX, DX|
|Dword|32|4|EAX, EBX, ECX, EDX|
|Qword|64|8|RAX, RBX, RCX, RDX, R8–R15|
|Oword|128|16|XMM0–XMM15|
|Yword|256|32|YMM0–YMM15|
|Zword|512|64|ZMM0–ZMM31|

---

### 🔹 **C Type Sizes (common defaults on 64-bit systems)**

(_These can vary by compiler, but this is the typical layout_)

| C Type        | Bits   | Bytes    |
| ------------- | ------ | -------- |
| `char`        | 8      | 1        |
| `short`       | 16     | 2        |
| `int`         | 32     | 4        |
| `long`        | 64     | 8        |
| `long long`   | 64     | 8        |
| `float`       | 32     | 4        |
| `double`      | 64     | 8        |
| `long double` | 80/128 | 10 or 16 |