Python lists store multiple items in a single, ordered, mutable variable using square brackets `[]`. They're one of Python's core data structures, allowing duplicates and mixed data types.

## Creating Lists

Use `[]` for empty or direct lists, or `list()` constructor from iterables like strings or tuples.

```python
# Basic list
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4.5]
mixed = [1, "hello", True]

# Empty list
empty = []
empty2 = list()

# From string or tuple
chars = list("Python")  # ['P', 'y', 't', 'h', 'o', 'n']
nums_tuple = list((10, 20, 30))

```

Output: `fruits` prints `['apple', 'banana', 'cherry']`.[](https://www.w3schools.com/python/python_lists.asp)

## Accessing Elements

Lists are zero-indexed; use `index` for single items, slicing `[start:end]` for ranges.

```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])      # apple (first item)
print(fruits[-1])     # cherry (last item)
print(fruits[1:3])    # ['banana', 'cherry']
print(fruits[::2])    # ['apple', 'cherry'] (every second item)
```
