```python
items = ["Roger", 1, "Syd", True]
print("Roger" in items) # True

print(items[0]) # "Roger"
print(items[1]) # 1
print(items[3]) # True
```
index
```python
print(items.index("Roger")) # 0
print(items.index("Syd")  )   # 2
```
slicing
```python
print(items[-1] ) # True
print(items[0:2]) # ["Roger", 1]
print(items[2:] ) # ["Syd", True]
```
length
```python
items = ["Roger", 1, "Syd", True]
len(items) #4
items.append("Test")```
extend
```python
items = ["Roger", 1, "Syd", True]
items.extend(["Test"])
```

```python
items = ["Roger", 1, "Syd", True]
items.extend(["Test1", "Test2"]) 
```
remove and concatenate with +
```python
items = ["Roger", 1, "Syd", True]
items += ["This"]
items.remove("This")
items += ["Test1", "Test2"]
```
insert
```python
items = ["Roger", 1, "Syd", True]
items.insert(1, "Test")
```

```python
items = ["Roger", 1, "Syd", True]
items[1:2] = ["Test1", "Test2"]
print(items)
```
sort
```python
num = [1, 9,4,4]
print(sorted(num)) # won't change the original 
print(num)
num.sort()
print(num)
```

append
list_test.append[]

del
```
del list_test[2]

```
