Move with zero extend and move with sign extend are used to small value from smaller types into larger registers holding larger types.

Zero extend means the CPU unconditionally fills the high order bits of the larger register with zeros (from small to big register), Sign extend means the CPU fills the high order bits of the destination larger register with whatever the sign is set to on the small value.

Move with sign extend MOVSX only sign extends values from 8 to 16bits value. MOVSXD is used to move d word values to 64bits looking at the side extension if its 1 it will put ones (treated as a negative value) if its 0 it will fill with zeros

![[Pasted image 20251114062301.png]]
