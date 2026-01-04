---
aliases: [Python miscellaneous]
---

Python scripts for system wide use are in: *projects/scripts*
## Run program with parameters
```python
if sys.argv[1] == 'cat':
    cat()
elif sys.argv[1] == 'dog':
    dog()
else:
    print('hello')
```

## Check string is numeric
tag: #numeric
```python
'37'.isnumeric())
```
is *True*
```python
'37.0'.isnumeric())
```
is *False*
## Exceptions
tag: #excptions
```python
try:
    x = 7 / z
except ZeroDivisionError:
    print('Cannot divide by zero')
except Exception as exception:
    print(exception.message)
else:
    print('no exception found')
finally:
    print('Always print this')
```
## Run a shell command
```python
os.system(command)
```
## Run a shell command and capture output
tag: #shell-command
```python
from subprocess import run
free = run('free', capture_output=True).stdout
print(free)
```
## Copy to clipboard
tag: #clipboard
```bash
pip install clipboard
```
```python
clipboard.copy("abc")
```
```python
# --- Get clipboard text ---
try:
	text = subprocess.check_output(GET_CMD, text=True, timeout=3).strip()
except Exception:
	text = ""
```
## pytest
```bash
pytest bridgeobjects/tests/test_contracts.py -v
```
```bash
pytest -v --cov-report=html --cov=.
```
```bash
pytest -v --cov-report=html --cov=. bridgeobjects/tests/test_hands.py
```
## Access a module in another folder
With the folder structure in the directory *bfgcardplay*:
```
.
├── src
│   ├── __init__.__py
│   ├── suggested_card.py
├── tests
│   ├── __init__.__py
│   ├── blitz.py
└── _version.py
```
in *blitz.py*
```python
from bfgcardplay.src.suggested_card import next_card
```
## Access sqlite3
```python
import sqlite3
def connect_db(db_name):
   connection = None
   try:
       connection = sqlite3.connect(db_name)
    #    print("Database connected successfully")
   except sqlite3.OperationalError as e:
       print(f"An Error has occurred: {e}")
   return connection
connection = connect_db(DATABASE_NAME)
cursor = connection.cursor()
command = f"SELECT * FROM {TABLE_NAME} WHERE name='{room_name}'"
# print(command)
cursor.execute(command)
xxx = cursor.fetchall()[0][10]
cursor.close()
```