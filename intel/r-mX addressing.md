r/mX refers to r/m8, 16, 32, 64 and is a way to specify the form of a register or memory value.

in intel syntaxes square brackets '[]' means to treat the value within a memory address and fetch the value at that address.
- register --> "rbx"
- memory, base only --> "[rbx]"
- memory, base + index * scale --> "[rebx+rcx*X]"
		for x = 1, 2, 4 or 8
- memory, base + index * scale + displacement --> "[rbx+rcx*X+Y]"
		for y of 1 byte (0-2^8) or 4 bytes (0-2^32)

"[base + index * scale + displacement]" has natural applicability to multidimensional array indexing, arrays of structs, ect