tag: #django-models
```python
from django.db import models
import json

class User(models.Model):
	username = models.CharField(max_length=32)
	logged_in = models.BooleanField(default=False)
	last_activity = models.DateField(null=True)
	archive = models.TextField(blank=True, default=json.dumps([]))
	board_number = models.IntegerField(default=0)

    def __str__(self):
        return f'User({self.username} logged in: {self.logged_in})'
```
