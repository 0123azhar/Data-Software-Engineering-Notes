Dictionary key must be unique, and values can be duplicates

*.get*
999 default value is optional. Returns 999 if key is not found
```python
x = {'abc' : 123}
print(x.get('abc', 999)) 
```

*.pop*
returns last inserted value

*.popitem*
returns last inserted key, value pair

return keys, values
```python
list(x.keys())
list(x.values())
```

add new key
```python
x["new_key_abc"] = new_value_xyz
```

delete key and value pair
```python
del x["new_key_abc"]
```

