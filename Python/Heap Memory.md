Heap memory is used for dynamically allocated objects and has a more flexible allocation and deallocation mechanism. 

Specifically, heap memory stores:
1. **Objects**
    - Instances of classes created using the `class` keyword.
    - Built-in types like lists, dictionaries, [[Set]], [[Tuples]], strings, etc.
2. **Data Structures**
    - Complex data structures such as graphs, trees, and linked lists.
3. **Dynamic [[Memory Allocation]]**
    - Memory allocated at runtime using various Python operations (e.g., creating new lists, dictionaries, or instances of custom classes).
4. **Attributes of Objects**
    - Attributes (instance variables) of objects are stored within the objects themselves, which reside on the heap.
5. **[[Reference Counting]]**
    - Metadata for [[Garbage Collection]], including reference counts for each object.