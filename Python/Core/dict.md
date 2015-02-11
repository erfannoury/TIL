Python has built-in support for dictionary data structure. An structure which stores pairs of keys and values, where a single value corresponds to a key and keys are unique.
Also keys must be of immutable type, thus strings and tuples can be used as keys in dictionaries.

What special I learned today is how to delete a key-value pair from dictionary.
Suppose you have a key-value pair `<k,v>` in `d` which is an object of type `dict` in Python. To remove this pair from dictionary you could use this statement:

```python
del d[k]
```
