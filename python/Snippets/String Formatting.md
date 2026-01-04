---
aliases: [Python strings]
---
## Date formats
```python
import datetime
event = datetime.datetime.now()
print(event.strftime('%d %b %Y %H:%M:%S'))
print(event.strftime('%d/%B/%Y'))
print(event.strftime('%d/%m/%Y'))
```
## Format a float with 2 decimal places
tag: [#format, #float]
```python
value = 3.1412
print(f'{value:.2f}')
```
## Format an integer with leading zeros
tag: [#format, #leading-zeros, #LFZ]
```python
value = 23
print(f'{value:04d}')
```
## Left justify a string in a field
tag: [#format, #left justify]
```python
text = 'The quick brown fox'
print('         1         2         3         4')
print('1234567890123456789012345678901234567890')
print(f'{text:<30}'+'aaa')
```
## Pad out a string with trailing .'s
tag: [#format, #ltrailing-dots]
```python
output = f'{customer:.<25} {balance:.2f}'
```