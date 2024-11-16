## Methods

### .append(x):
1. It adds an items at the end of the list.
2. `a.append(x) == a[len(a):] = [x]`
```python
list.append(x)
```
### .extend(iterable):
1. It is used to append all the items in the `iterable data structure` to the list.
2. `list.append == list[len(list):] = iterable`
```python
list.extend(set("Hello World"))
# append a set of unique characters to the list
```
### .insert(index, x):
1. It is used to insert the given value at the given index of the list.
```python
list.insert(2,"hello")
```
### .remove(x):
1. It ***removes only one*** item with same value which is the ***first item*** matching the given value.
2. It raises **ValueError** if there isn't any item matching the given value
```python
list.remove("hello")
```
### .pop([i]):
1. It ***removes and returns*** the item at the given position.
2. If **not specified** it ***removes the last element.***
3. It raises **IndexError** if there isn't any element at the specified position.
```python
list.pop(1)
list.pop()
```
### .clear():
1. It removes all the elements in the list
2. `list.clear == del list[:]`
```python 
list.clear()
```
### .index(x, `start,end`):
1. It is used to return the index of the first occurence of the given Element.
2. The start and end parameters are optional they define the range in which the serach must be performed.
3. It raises ValueError is there isn't any value.
```python
list.index("hello", 0,5)
# it returns the index of the first occuring element within the range
list.index("hello")
# it returns the index of the first occuring element within the whole list
```
### .count(x):
1. It returns the frequency of the 'x' in the list.
```python
list.count(x)
```
### .sort(`*`, key=None, reverse=False):
1. It takes in a **key** specifying the ***comparision condition***.
2. And reverse parameter indicating to ***sort it in reverse*** order of the.
```python
list.sort(key = len, reverse = True)
# sorts the list based on the size of the elements
list.sort()
# sort the elements lexcially
```
### .reverse():
1. It reverses the list.
### .copy():
1. It creates a [[shallow copy]] of the list.
## List as Queue:
### import:
```python
from collections import dequeue
```
### implementation:
#### syntax:
```
queue = dequeue([initialize the list])
```



