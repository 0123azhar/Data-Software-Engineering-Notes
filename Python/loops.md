2024-08-24 03:35
# loops

for: use when end/stop condition is known
``` python
items = [1, 2, 3, 4]
for item in items:
	print(item)
```

while: use when end/stop condition is not unknown

```python
number = 1045
sum_of_digits = 0

while number > 0:
    digit = number % 10 # reminder
    print('digit=',digit)
    
    sum_of_digits += digit
    print('sum_of_digits=',sum_of_digits)
    
    number = number // 10 # quotient without decimel value
    print('number=',number)

print(f"The sum of digits is: {sum_of_digits}")
```

continue stops the current iteration
```python
items = [1, 2, 3, 4]
for item in items:
	if item == 2:
		continue
	print(item) # [1,3,4]
```
break stops the loop altogether
```python
items = [1, 2, 3, 4]
for item in items:
	if item == 2:
		break
	print(item) # 1
```

Pass:
Just a place holder in case there is no logic to write in ’if’ or function 