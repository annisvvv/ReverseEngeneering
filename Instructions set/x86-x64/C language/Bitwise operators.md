this means using the and, or, xor and not operators in bits. [[AND - OR - XOR - NOT]], or the Shift [[SHL - SHR & SAR - SAL]]
## Bitwise Operators Table

| Operator        | Name                     | Description                                   | Example (binary)                   | Result         |
| --------------- | ------------------------ | --------------------------------------------- | ---------------------------------- | -------------- |
| `&`             | AND                      | Keeps a bit **only if both** bits are 1       | `1101 & 1011`                      | `1001`         |
| `               | `                        | OR                                            | Keeps a bit if **either** bit is 1 | `1100 \| 1010` |
| `^`             | XOR                      | Keeps a bit if the two bits are **different** | `1101 ^ 1011`                      | `0110`         |
| `~`             | NOT (bitwise invert)     | Flips every bit (0→1, 1→0)                    | `~ 0000 1111`                      | `1111 0000`    |
| `<<`            | Left shift               | Shift bits left, filling with 0               | `0001 << 2`                        | `0100`         |
| `>>`            | Right shift (arithmetic) | Shift bits right, filling with **sign bit**   | `1000 >> 2`                        | `0010`         |
| `>>>` (Java/JS) | Logical right shift      | Shift right, filling with **0**               | `1000 >>> 2`                       | `0010`         |
