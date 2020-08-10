---
layout: post
title: Coding with EAFP mindset in python
tags:
  - Python
  - Programming-principle
---
### EAFP principle (Easier to Ask for Forgiveness than it is to get Permission)
The EAFP is a common principle/coding style used by the python community.
It is a style in which the attributes or keys are assumed to be present and if the assumption is false, it is catched and handled in an exception. `try/except` play a great role in this style. This is opposed to LBYL style(Look Before You Leap) where the programmer needs to carefully evaluate the conditions before doing something. 

Example: 

(LBYL style):
```python
from os import path

if path.isfile('hello.txt'):
    data = open('hello.txt')
else:
    print('file does not exist')
```

(EAFP style):
```python
try:
    data = open('hello.txt')
except FileNotFoundError:
    print('file does not exist')
```

### Advantages
* Cleaner code
* Code is faster when running in the happy path. This is because the conditional checks are avoided before doing someting.
* A try/except block is extremely efficient if no exceptions are raised. [how fast are exceptions](https://docs.python.org/3/faq/design.html#id11)

Also to be noted:
While most of the times the EAFP style might be the way to go, Sometimes it is not.

[https://docs.python.org/3.4/glossary.html](https://docs.python.org/3.4/glossary.html)