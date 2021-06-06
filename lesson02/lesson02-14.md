## Garbage Collection

#### Materials
 - Assembled circuit from the Primitive/Non-Primitive Data example

#### Instructions
 - In Thonny, click View - Variables
 - Using the REPL, type the following commands:
```
import gc
gc.collect()
gc.mem_alloc()
gc.mem_free()

# primitive data
x = 12
gc.mem_free()
y = x
gc.mem_free()
del x
gc.mem_free()
gc.collect()
gc.mem_free()
del y
gc.collect()
gc.mem_free()
```
 - Using the REPL, type the following commands:
```
# non-primitive data
a = {'name': 'jeff'} # ref count = 1
b = a # ref count = 2
gc.mem_free()
del a # ref count = 1
gc.mem_free()
del b # ref count = 0
gc.mem_free()
gc.collect()
gc.mem_free()
```
