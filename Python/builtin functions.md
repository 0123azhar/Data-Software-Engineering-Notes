2024-08-24 10:36
# builtin functions

These functions are globally available. We do not need to import them from any package or module
`len, round, abs etc.`

```python
import builtins, sys

print(sys.version)

# Get a list of all attributes in the builtins module
builtin_functions = [name for name in dir(builtins) if callable(getattr(builtins, name))]

builtin_functions.sort()

for i in builtin_functions:
	print(i)
```

- The list comprehension iterates over all attribute names in the `builtins` module.
- For each attribute name, `getattr(builtins, name)` retrieves the attribute.
- `callable(getattr(builtins, name))` checks if the attribute is a callable object (function or method).
- Only the names of callable attributes (functions) are included in the `builtin_functions` list.

All the builtin functions available in python version 3.12.4 
1. ArithmeticError
2. AssertionError
3. AttributeError
4. BaseException
5. BaseExceptionGroup
6. BlockingIOError
7. BrokenPipeError
8. BufferError
9. BytesWarning
10. ChildProcessError
11. ConnectionAbortedError
12. ConnectionError
13. ConnectionRefusedError
14. ConnectionResetError
15. DeprecationWarning
16. EOFError
17. EncodingWarning
18. EnvironmentError
19. Exception
20. ExceptionGroup
21. FileExistsError
22. FileNotFoundError
23. FloatingPointError
24. FutureWarning
25. GeneratorExit
26. IOError
27. ImportError
28. ImportWarning
29. IndentationError
30. IndexError
31. InterruptedError
32. IsADirectoryError
33. KeyError
34. KeyboardInterrupt
35. LookupError
36. MemoryError
37. ModuleNotFoundError
38. NameError
39. NotADirectoryError
40. NotImplementedError
41. OSError
42. OverflowError
43. PendingDeprecationWarning
44. PermissionError
45. ProcessLookupError
46. RecursionError
47. ReferenceError
48. ResourceWarning
49. RuntimeError
50. RuntimeWarning
51. StopAsyncIteration
52. StopIteration
53. SyntaxError
54. SyntaxWarning
55. SystemError
56. SystemExit
57. TabError
58. TimeoutError
59. TypeError
60. UnboundLocalError
61. UnicodeDecodeError
62. UnicodeEncodeError
63. UnicodeError
64. UnicodeTranslateError
65. UnicodeWarning
66. UserWarning
67. ValueError
68. Warning
69. ZeroDivisionError
70. `__build_class__`
71. `__import__`
72. `__loader__`
73. abs
74. aiter
75. all
76. anext
77. any
78. ascii
79. bin
80. bool
81. breakpoint
82. bytearray
83. bytes
84. callable
85. chr
86. classmethod
87. compile
88. complex
89. copyright
90. credits
91. delattr
92. dict
93. dir
94. divmod
95. enumerate
96. eval
97. exec
98. exit
99. filter
100. float
101. format
102. frozenset
103. getattr
104. globals
105. hasattr
106. hash
107. help
108. hex
109. id
110. input
111. int
112. isinstance
113. issubclass
114. iter
115. len
116. license
117. list
118. locals
119. map
120. max
121. memoryview
122. min
123. next
124. object
125. oct
126. open
127. ord
128. pow
129. print
130. property
131. quit
132. range
133. repr
134. reversed
135. round
136. set
137. setattr
138. slice
139. sorted
140. staticmethod
141. str
142. sum
143. super
144. tuple
145. type
146. vars
147. zip