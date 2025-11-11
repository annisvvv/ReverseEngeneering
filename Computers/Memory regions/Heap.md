important the heap grows upward and the stack grows downward.

![](https://0xinfection.xyz/reversing/imgs/1520241941781.jpg)

The heap is the region of your computer's memory that is not managed automatically for you, and is not as tightly managed by the CPU. It is free-floating region of memory and is larger than the stack allocation of memory. using the "malloc()" and "calloc()" which are built in c functions you can allocate memory to the heap and you are responsible for freeing it by using **free()** to de-allocate that memory once you don't need it any more this last step is important because the memory on the heap will still be set aside and won't be available to other processes that need it causing memory leaks.

Unlike the stack, the heap does not have size restrictions on variable size. The only thing that would limit the heap is the physical limitations of your computer. Heap memory is slightly slower to be read from and written to, because you have to to use pointers to access memory on the heap.

Unlike the stack, variables created on the heap are accessible by any function, anywhere in your program. Heap variables are essentially global in scope.

If you need to allocate a large block of memory for something like a struct or a large array and you need to keep that variable around for a good duration of the program to which must be accessed globally, then you should choose the heap for this purpose. If you need variables like arrays and structs that can change size dynamically such as arrays that can grow or shrink as needed, then you will likely need to allocate them on the heap, and use dynamic memory allocation functions like **malloc()**, **calloc()**, **realloc()** and **free()** to manage that memory manually.