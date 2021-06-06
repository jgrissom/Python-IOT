## Primitive/Non-Primitive Data

#### Materials
 - Assembled circuit from the Battery management example

#### Instructions
 - In Thonny, click View - Variables
 - Using the REPL, type the following commands:
```Python
# primitive data
x = 12
y = x # y stores its own copy of 12
x
y
x = 15
x
y

# non-primitive data
a = {'name': 'jeff'}
b = a # b stores a pointer to a
a
b
a['name'] = 'george'
a
b
```
