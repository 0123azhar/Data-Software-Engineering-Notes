read
```python
with open('path/to/file.txt', r) as f:
	text = f.read()

print(text)
```
write
```python
text = 'this is a sample text'

with open('path/to/file.txt', w) as f:
	f.write(text)
```
`f.readlines()` returns list of lines
r, r+, w, w+, a, a+