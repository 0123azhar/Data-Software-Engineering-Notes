functions that take other functions as inputs or return functions as outputs.
mainly used with lambda function. map, filter etc. 

#### Map
```python
numbers = [1, 2, 3, 4, 5] 
double = list(map(lambda i : i * 2, numbers))
#double = [map(lambda i : i * 2, numbers)] # this returns memory address
print(double)
```
#### Filter
```python
numbers = [1, 2, 3, 4, 5] 
even = filter( lambda i: (i % 2) == 0, numbers)
# filter returns an iterator
print(list(even))
```
#### Reduce
```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]
result = reduce(lambda i, j: i + j, numbers) 
print(result)

greatest = reduce(lambda i,j: i if i > j else j, numbers)
print(greatest)
```
