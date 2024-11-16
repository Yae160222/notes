### Shallow copy:
1. It **creates a new object** but *** doesn't create new objects for the elements*** in the object.
2. Example:
```python
list1 = ["hello", (1,2,3,45), {1,2,3,4}]
list2 = list1.copy()
# Here the interpreter creates new object named list2 but does't create new instance of tuple and set present in the list1.
list2.add(5)
print(list1)
# ["hello", (1,2,3,4,5), {1,2,3,4,5}] 5 is addition of 5 in list2 is also reflected in list 1
```