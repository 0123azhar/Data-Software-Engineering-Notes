- Modules have to be imported.
- There is no straight forward way to list all the available builtin modules using code because some modules are very old and not organized as per current standards but have to be kept around for backward compatibility.

###  Commonly used builtin modules
#### math
- ceil, floor, factorial, gcd
```python
import math

print(math.ceil(20.22)) # 21
print(math.floor(20.22)) # 20
print(math.factorial(5)) # 120
print(math.gcd(20,25)) # 5
```
- sine, cosine, square root, etc.
#### random
```python
import random

print(random.choice(['a','b','c']))
print(random.sample(range(1,10),3))
print(random.random()) # any float
print(random.uniform(4,5)) # float b/w 4,5
print(random.randint(4,9)) # including 9
print(random.randrange(4,9)) # excluding 9
```
#### datetime
- For manipulating dates and times. 
```python
from datetime import date

print(date.today())
print(date.today().strftime('%Y%m%d'))
print(date(2024,1,23))
```
#### os
Provides a way of using operating system dependent functionality like reading or writing to the file system. 
```python
import os

print(os.getcwd())
print(os.system('ls'))
#os.chdir('/home')
#os.system('mkdit foo')
```
#### sys
- Access to system-specific parameters and functions. 
#### re
Provides regular expression matching operations 
#### logging
Essential for tracking events that happen when some software runs, which is critical for monitoring and troubleshooting data pipelines. 
#### collections
Offers additional data structures to store data, like `namedtuple`, `deque`, `Counter`, etc., which can be very handy in data processing tasks. 
#### itertools
Includes a set of fast, memory-efficient tools that are useful by themselves or in combination for complex data manipulations. 
#### venv
Automatically manages project packages and dependencies. 
#### unittest
for unittesting
#### [[multiprocessing]] 
#### [[asyncio]]
#### [[threading]]