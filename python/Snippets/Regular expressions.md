---
aliases: [Python regex]
---
NB *match* looks for match at the start of a string, *search* looks at the whole string
## Import
```python
import re
```
## Find all occurrences that match a pattern
```python
result = re.findall('[0-9]{4}', line)
```
returns a list of all strings that match. e.g. ['1234', '0000']
## Find value of a string that matches a pattern
```python
version = "__version__ = '0.0.1'"
version_re = r'[0-9]{1,}.[0-9]{1,}.[0-9]{1,}'
match = re.search(version_re, version)
my_version = match.group()
```
## Find text based on a pattern
E.g find table number in *bbo logo Table activity: Table:1*
```python
        table_re = r'\sTable:(\d+)'
        ...
            match = re.search(table_re, line)
            if match:
                table_no = match.group(1)
```
## Find position
```python
date_re = re.compile(r'[0-9]{6}')
for match in date_re.finditer('abc123456def':
    start = match.start()
```
## Assertion
```python
from psiutils._version import __version__
def test_version():
    version_re = r'^[0-9]{1,}.[0-9]{1,}.[0-9]{1,}$'
    assert re.match(version_re, __version__)
```