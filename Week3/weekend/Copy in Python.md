## Copy in Python

In `Python`, we can make two types of `copies` of objects in Python:

- `A shallow copy` - constructs a new compound object (an object that contains other objects, like lists or class instances) and then inserts references into it to the objects found in the original.
- `A deep copy` - constructs a new compound object and then, recursively, inserts copies into it of the objects found in the original.

Things will get clearer after completing the following tutorial.

Instruction

Follow the [**Python Shallow Copy and Deep Copy** tutorial](https://www.programiz.com/python-programming/shallow-deep-copy) to discover how different types of copies work. This time you don't need to use your own Jupyter Notebook - just write and run code in the interactive shell on the page.

Note

Shallow copy is not possible for immutable objects like integers or tuples. In that case

```python
a = 1
b = a
a += 1
print(a)
2
print(b)
1
```