### initializing:
```python
dict1 = {}

dict2 = {'a':1, 'b':2}

dict3 = dict( [('a',1), ('b',2)] )

dict4 = {x:x**2 for x in range(0,4)}
```

### Iterating:
```python
# .items()
for k, v in dict1.items():
	print(k,v)
# only keys
for key in dict1:
	print(key)
# only values
for val in dict1.values():
	print(val)
```

### **NOTE**: 
**Dictionary `supports updation and assignment like ARRAY in c`

### methods:
#### `dict1['c'] = 3`
#### `.get(): value|None`
#### `.__contains__(key): bool`
#### `.pop(key): value`
#### `.clear(): None`