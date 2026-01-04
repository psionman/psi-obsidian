---
aliases: [Python dictionaries]
---
(see ~/projects/scratch/sort-dicts/main.py)
##  Sort a simple dict
```python
DICT = {'a': 3, 'b': 2, 'd': 4, 'c': 1,}
```
### Sort by key
tag: [#sort-by-key]
```python
dict(sorted(DICT.items()))
```
### List of sorted keys
```python
sorted(DICT.keys())
```
```bash
{'a': 3, 'b': 2, 'c': 1, 'd': 4}
```
### Sort by  values
tag: [#sort-by-values]
```python
dict(sorted(DICT.items(), key=lambda item: item[1]))
```
```bash
{'c': 1, 'b': 2, 'a': 3, 'd': 4}
```
```bash
['a', 'b', 'c', 'd']
```
### List of sorted values
```python
sorted(DICT.values())
```
```bash
[1, 2, 3, 4]
```
### Sorted items
```python
sorted(DICT.items())
```
```bash
[('a', 3), ('b', 2), ('c', 1), ('d', 4)]
```
## Sort a dict of objects
```python
class Foo():
    def __init__(self, name, value) -> None:
        self.name = name
        self.value = value
    def __repr__(self):
        return f'({self.name}, {self.value})'
FOOS = {
    'y': Foo('a', 3),
    'x': Foo('g', 1),
    'z': Foo('d', 2)
}
```
### Sort by keys
```python
dict(sorted(FOOS.items()))
```
```bash
{'x': (Foo: g, 1), 'y': (Foo: a, 3), 'z': (Foo: d, 2)}
```
### Sort by attribute
tag: [#sort-by-attrubute]
```python
sorted(FOOS.items(), key=lambda item: item[1].name)
```
or ...
```python
    def value_getter(item):
        return item[1].name
    sorted(FOOS.items(), key=value_getter)
```
```bash
[('y', (Foo: a, 3)), ('z', (Foo: d, 2)), ('x', (Foo: g, 1))]
```
## Remove an item from a dict
tag: #remove-item
```python
HAND_TYPE_NAMES = {
    1: 'use_stages',
    0: 'use_random',
    2: 'use_import',
}
HAND_TYPE_NAMES.pop(1)
print(HAND_TYPE_NAMES)
```