Python lists store multiple items in a single, ordered, mutable variable using square brackets `[]`. They're one of Python's core data structures, allowing duplicates and mixed data types.

## Creating Lists

Use `[]` for empty or direct lists, or `list()` constructor from iterables like strings or tuples.

```python
# Basic list
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4.5]
mixed = [1, "hello", True]

# list type casting
nums_tuple = list((10, 20, 30))

```


Output: `fruits` prints `['apple', 'banana', 'cherry']`

## Accessing Elements

Lists are zero-indexed; use `index` for single items, slicing `[start:end]` for ranges.

```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])      # apple (first item)
print(fruits[1:3])    # ['banana', 'cherry']
print(fruits[1:])  
print(fruits[::-1])    # reverce
```




Python list methods are essential for manipulating lists efficiently, and here are basic ones with simple code examples.

## Update Elements

```python
fruits = ["apple", "banana"]
fruits[0]="letsgo"
print(fruits)  
```


## Add Elements

**append(x)**: Adds one item to the end.
```python
fruits = ["apple", "banana"]
fruits.append("cherry")
print(fruits)  # ['apple', 'banana', 'cherry'] []
```

**extend(iterable)**: Adds multiple items from an iterable.
```python
fruits = ["apple"]
fruits.extend(["banana", "cherry"])
print(fruits)  # ['apple', 'banana', 'cherry'] []

```

**insert(index, x)**: Inserts an item at a specific position.
```python
fruits = ["banana", "cherry"]
fruits.insert(0, "apple")
print(fruits)  # ['apple', 'banana', 'cherry'] []
```

## Remove Elements
**remove(x)**: Removes the first occurrence of an item.
```python
fruits = ["apple", "banana", "apple"]
fruits.remove("apple")
print(fruits)  # ['banana', 'apple'] []
```

**pop([index])**: Removes and returns an item (last by default).
```python
fruits = ["apple", "banana", "cherry"]
item = fruits.pop()
print(item)    # 'cherry'
print(fruits)  # ['apple', 'banana'] []
```

## Search and Count
**index(x)**: Returns the position of the first occurrence.
```python
fruits = ["apple", "banana", "cherry"]
pos = fruits.index("banana")
print(pos)  # 1 []
```

**count(x)**: Counts occurrences of an item.
```python
fruits = ["apple", "banana", "apple"]
print(fruits.count("apple"))  # 2 []
```
**search answer**
```python
fruits = ["apple", "banana", "apple"]
print("apple" in friuts)  # 2 []
```



## Modify Order
**sort()**: Sorts the list in place.
```python
numbers = [3, 1, 4]
numbers.sort()
print(numbers)  # [1, 3, 4] []
```

**reverse()**: Reverses the list order.
```python
fruits = ["apple", "banana"]
fruits.reverse()
print(fruits)  # ['banana', 'apple'] []

```



## Utility
**copy()**: Creates a shallow copy.
```python
original = [1, 2]
copy_list = original.copy()
print(copy_list)  # [1, 2] []
```

**clear()**: Empties the list.
```python
fruits = ["apple", "banana"]
fruits.clear()
print(fruits)  # [] []
```


