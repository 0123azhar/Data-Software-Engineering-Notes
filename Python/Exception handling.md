
```
try:
	# some lines of code
except <ERROR1>:
	# handler <ERROR1>
except <ERROR2>:
	# handler <ERROR2>
else:
	# no exceptions were raised, the code ran successfully
finally:
	# do something in any case
```


```python
def handle_division(): 
    try: 
        # Try to execute some potentially error-prone code 
        x = int(12)
        y = int(4)
        result = x / y 
    except ZeroDivisionError: 
        # Specific handling for zero division error 
        print("Error: You can't divide by zero!") 
    except ValueError: 
        # Handle the case where x, y are strings (non numeric strings)
        print("Error: Please enter valid integer numbers!") 
    else: 
        # Executes if the try block is successful 
        print(f"The result is {result}") 
    finally: 
        # Always executes, regardless of other blocks' outcomes 
        print("Execution complete whether an error occurred/not.") 
 
handle_division() 
```