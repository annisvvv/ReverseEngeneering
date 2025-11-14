| Data Type                     | Typical Size              | Description                                                                     |
| ----------------------------- | ------------------------- | ------------------------------------------------------------------------------- |
| `char`                        | 1 byte                    | Stores a single character; can be signed or unsigned.                           |
| `unsigned char`               | 1 byte                    | Only positive values (0 to 255).                                                |
| `signed char`                 | 1 byte                    | Can be negative (-128 to 127).                                                  |
| `short` / `short int`         | 2 bytes                   | Small integer; range: -32,768 to 32,767.                                        |
| `unsigned short`              | 2 bytes                   | 0 to 65,535.                                                                    |
| `int`                         | 4 bytes                   | Standard integer; range: -2,147,483,648 to 2,147,483,647.                       |
| `unsigned int`                | 4 bytes                   | 0 to 4,294,967,295.                                                             |
| `long` / `long int`           | 8 bytes                   | Larger integer; range: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807. |
| `unsigned long`               | 8 bytes                   | 0 to 18,446,744,073,709,551,615.                                                |
| `long long` / `long long int` | 8 bytes                   | Very large integer; same range as `long` on 64-bit.                             |
| `unsigned long long`          | 8 bytes                   | 0 to 18,446,744,073,709,551,615.                                                |
| `float`                       | 4 bytes                   | Single-precision floating-point number.                                         |
| `double`                      | 8 bytes                   | Double-precision floating-point number.                                         |
| `long double`                 | 16 bytes (on most x86_64) | Extended precision floating-point.                                              |