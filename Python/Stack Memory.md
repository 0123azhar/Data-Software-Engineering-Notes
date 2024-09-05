It is a region of RAM that functions as a stack data structure. It follows a Last-In-First-Out (LIFO) order.

Stack memory is used primarily for function calls and local variables within those functions. Specifically, stack stores:
1. **Function Call Frames**
    - Information about the function call, including the return address.
    - Local variables defined within the function.
    - Function parameters (arguments).
2. **Local Variables**
    - Variables defined within the scope of a function, including references to objects allocated on the heap.
3. **Return Address**
    - The address of the instruction to return to after the function call completes.
4. **Control Flow Information**
    - Information necessary to manage the control flow of the program, such as loop counters and conditional branches.