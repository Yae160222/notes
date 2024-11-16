## Choice Statements:
### if statements:
```python
if x == 0:
	print("x is zero")
elif x > 0:
	print("x is positive")
else:
	print("x is negative")
```
### match statements(`switch in java`):
1. They are similar to **Switch** in Java.
2. **`case _`** acts as a `default` case.
```python
def fun(x):
	match x:
		case 1:
			return "one"
		case _ if x>0:
			return "positive"
		case _ if x<0:
			return "negative"
		case 0: # no need to use == operator
			return "zero"
		case _: #default case for match
			return "x is not an number"
```
3. They support [[unpacking assignments]] , [[sequence patterns]], [[mapping patterns]], [[identity comparisons]] for comparison.

## loop Statements:
### for statement:
1. **Syntax**:
```
for x in data_structure:
	# code
else:
	# code
```
2. **else** block is optional and it ***executes after the for loop ends***.
3. **Example**:
```python
map = {"ram": 1, "pam": -2, "zam": 22}
for name, age in map.items():
	if age < 0:
		del map[name]
```
### while:
1. Syntax:
```
while condition:
	#code
else:
	#code
```
2. **else** block executes if the ***condition in while block is not satisfied***.
### range(start, end, step):
1. The **end** parameter is ***must*** and the **rest** are ***optional***.
2. The **end** parameter is ***not inclusive***.
3. The default value for **start** is ***0***.
4. The default value for **step** is ***1***.
```pyhton
range(1,100,1) # 1,2,3,4,...,98,99
range(1, 100, 2) # 1,3,5,7,...,97,99
range(100, 1, -1) # 100,99,98,...3,2
range(100) # 0,1,2,3,4...,98,99
```
### break:
It is used to break the loop.
### continue:
It is used to skip the current iteration and continue the loop.
### pass:
This statement does nothing.
```python
while True:
	pass
class Class1:
	pass
def fun():
	pass
```
### NOTE:
`The loop terminated using` **break** `will not go to `**ELSE**` block`
## Functions:

### declaration:
```python
def fun(x):
	if(x%2 == 0):
		return True
```

NOTE: 
1. A function return **None** if ***no return statement*** is specified.
2. **Default arguments are supported**.

### function arguments:
```python
def fun(name, age, roll_no):
	# ***** key-word or positional

def fun(name, age, roll_no, /): 
	# ***** only Positional

def fun (*, name ,age , roll_no): 
	# ***** only key-word

```

### function parameters:
```python
# ***** tuple as a parameter
def fun(items, *args):
    print(f"Items: {items}")
    print(f"Args: {args}")

# ***** dictonary as a parameter
def fun1(*, items=None, **kwargs):
    print(f"Items: {items}")
    print(f"Kwargs: {kwargs}")

# Function calling
fun('raiden', 1, 2, 3, 55, 6.6)
fun1(items=1, client=1, shop=2, trip=3)
```

### lambdas:
```python
# SYNTAX
	# lambda parameters: expression
	
add_ten = lambda x: x+10
print(add_ten(5)) # output 15
```

### function annotations:
1. They represent the expected and return data types of the function.
```python
def f(ham: str, eggs: str = 'eggs') -> str:
    print("Annotations:", f.__annotations__)    # Print the annotations dictionary of the function
    return ham + ' and ' + eggs

result = f(42)

print(result)
# Output:
#Annotations: {'ham': <class 'str'>, 'eggs': <class 'str'>, 'return': <class 'str'>} 42 and eggs
```

### Unpacking arguments:
```python
# unpacking list or tuple
args = [0,10,2]
for i in range(*args):
	print(i)

# unpacking dict
def parrot(voltage, state='a stiff', action='voom'):
	print("-- This parrot wouldn't", action, end=' ')
	print("if you put", voltage, "volts through it.", end=' ')
    print("E's", state, "!")
d = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
parrot(**d)
```