
## class:
### creation:
```python

class MyClass:
	i = 123 # **** class variables
	def __init__(self, name):
		self.name = name # **** instance variable (unique to each instance)
	def fun1():
		return 'fun1'
```

NOTE:
1. You can pass external function references to a class methods.
```python
def fun(self, x, y):
	return min(x,y)
class MyClass:
	f = fun
```

### Inheritance:
```python
class MyClass(SuperClass1, SuperClass2, SuperClass3):
```
### Access modifiers:
```python
class MyClass:
	public_var = 'public'
	_protected_var = 'protected'
	__private_var = 'private'
```
The python interpreter changes the name of the 
`private_var` to  `MyClass_private_var `
this is called **Name Mangling .

### Iterators:
```python
class MyClass:
	def __init__(self, data):
		self.data = data
		self.index = 0
	def __iter__(self):
		return self
	def __next__(self):
		if(index == len(data)):
			raise StopIteration
		self.index = self.index - 1
		return self.data[self.index]
```

### generators:
1. It automatically creates `Iterator` and `next` functions.
```python
def reverse(data):
	for index in range(len(data)-1, -1, -1):
		yield data[index]
```
## data class:
```python
from dataclasses import dataclass

@dataclass
class Employee:
	name:str
	dept: str
	salary: int
```

