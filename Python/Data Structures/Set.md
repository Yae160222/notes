### Initialization:
```python
set1 = {'apple', 'apple', 'banana'}
# set1 {'apple', 'bannana'}

set2 = set('abracadabra')
# set2 {'a', 'r', 'b', 'c', 'b'}

set3 = {x for x in 'abracadabra' if x not in 'abc}
# set3 {'r', 'd'}
```
NOTE: to initialize an **empty set** we need to declare it using `set()`

### operations:
#### a-b:
1. ***letters in a but not in b***.
#### a | b:
1. ***letters in a or b or both***.
#### a & b:
1. ***letters in a and b****.
#### a ^ b:
1. ***letters in a or b but not in both.***
### membership operators:
```python
print('a' in set1)
```

### methods:

#### .add(x): None
```python
set1 = {1,2,3,4,5}
print(set1.add(6)) # None
print(set1.add(4)) # None
print(set1) # {1,2,3,4,5,6}
```

#### .remove(x) : None




