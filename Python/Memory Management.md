## Key concepts:
### **[[Memory Allocation]]**
- **Static Allocation**: Memory allocated at ==compile time== for ==fixed-size== objects.
- **Dynamic Allocation**: Memory allocated at ==runtime== for ==variable-sized== objects. Python uses a dynamic memory allocation strategy for certain objects like list as it is mutable.
### **[[Reference Counting]]**
object metadata
### **[[Garbage Collection]]**
Generational method and cyclic method
### **[[Memory Pools]]**
for small and frequently created and destroyed objects
### **[[Heap Memory]]**
   - **Heap Management**: Large objects are allocated on the heap, which is managed by the operating system's memory allocator.
   - **Object Caching**: Python caches small objects to avoid the overhead of frequent allocations and deallocations.
### **[[Stack Memory]]**
   - **Stack Allocation**: Memory for function calls and local variables is allocated on the stack. Each function call creates a new ==stack frame==, which is destroyed when the function returns.
### **Memory Leaks**
   - A memory leak in occurs when memory that is no longer needed is not released or reclaimed, causing ==excessive memory usage== and potential performance degradation. Properly managing references and understanding the lifecycle of objects helps prevent memory leaks.
### **Manual Memory Management**
   - **Explicit Deallocation**: While Python’s garbage collector handles most memory management, developers can use the ==`del` statement== to explicitly delete objects and reduce reference counts.
   - **Context Managers**: Using context managers (==`with` statements==) ensures that resources are properly cleaned up after use.
### **Weak References**
   - **Weak References**: The `weakref` module allows the creation of weak references to objects. These references do not increase the reference count, preventing certain types of memory leaks.
`import weakref`

`class MyClass:`
    `pass`

`obj = MyClass()`
`r = weakref.ref(obj)`
`print(r())  # Prints the object`
`del obj`
`print(r())  # Prints None since the object is no longer available`
