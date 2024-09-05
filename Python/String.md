[[slicing]]

Commonly used methods
1. upper 
2. len
3. find
4. index
5. isnumeric
6. isalpha
7. isalnum
8. replace
9. split

all available methods
```python
x = 'this is a string'
methods = [i for i in dir(x) if not i.startswith('__') and not i.endswith('__')]

methods.sort()

for i in methods:
	print(i)
```



