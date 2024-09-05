adding extra functionality to a function/method without updating the actual function source code.
##### Example 1:
Original function
```python
def say_hello(): 
    return print("hello world!")
 
say_hello() 
```
Modifying the say_hello() without actually updating it
```python
def log_function(func): 
    def wrapper(): 
        print(f"calling function {func.__name__}") 
        return func() 
    return wrapper 
    
@log_function 
def say_hello(): 
    return print("hello world!")
 
say_hello() 
#o/p: calling faction say_hello 
#     hello world 
```

##### Example 2
```python
def math_two(x, y):
    added = x + y
    return added

print(math_two(6,4))
```

```python
def subtract(func):
    def wrapper(x, y):
        subtracted = x - y
        original_result = func(x, y)
        return subtracted, original_result
    return wrapper

@subtract
def math_two(x, y):  # original 3 lines
    added = x + y    # original 3 lines
    return added     # original 3 lines

print(math_two(6, 4))  # Output: (2, 10)
```