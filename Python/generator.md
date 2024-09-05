use yield instead of return. generators produces values one at a time, only when iterated over.
Generators are useful when we want to produce a large sequence of values, but we don't want to store all of them in memory at once.
```python
def gen(x): 
	for i in range(x): 
		yield i 
	
foo = gen(5)

print('next: ', next(foo))

for i in foo:
	print(i)
```