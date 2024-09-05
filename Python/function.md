
```python
def add_two_numbers(a,b):
	result = a+b
	return result # return clause is optional

x = 5
y = 4
sum = add_two_numbers(x,y)
print(sum)
```
#### Variable length arguments
```python
def foo(*args):
	for i in args:
		print(i)
		
foo(1,2,3)
foo('a','b','c')
```
#### Keyword arguments

```python
def foo(**kwargs):
	for i,j in kwargs.items():
		print(i,j)
		
foo(a=1, b=2, c=3)
```
#### Global keyword
without global
```python
name = 'azhar'

def change_name(x):
	name = x
	return name

print(name) # azhar
print(change_name('buzzer')) # buzzer
print(name) # azhar
```
with global
```python
name = 'azhar'

def change_name(x):
	global name
	name = x
	return name

print(name) # azhar
print(change_name('buzzer')) # buzzer
print(name) # buzzer
```
#### Recursion
```python
def factorial(n):
    # Base case: if n is 1, return 1
    if n == 1:
        return 1
    else:
        # Recursive case: n * factorial of (n-1)
        return n * factorial(n - 1)

# Example usage
print(factorial(5))  # Output will be 120 (5 * 4 * 3 * 2 * 1)
```