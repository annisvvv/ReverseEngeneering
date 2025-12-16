the struct is stored as it is on the stack, no modification on the storage order.

when using struct and storing a small variable to the stack an initialization is made with the short variable like the folowing :

![[Pasted image 20251210053704.png]]

so the `__attribute__((packed))` is used to squish everything