```python
numbers = [1, 2, 3, 4, 5]
double = [i*2 for i in numbers]
print(double)
```
##### for and if
else clause is not allowed below
```python
my_list = [1,2,3,4,5,6,10]
print([x for x in my_list if x%2 == 0])
# [2, 4, 6, 10]
```
##### if else and for
else clause is compulsory below
```python
my_list = [1,2,3,4,5,6,10]
print([x if x%2 == 0 else '#' for x in my_list])
```