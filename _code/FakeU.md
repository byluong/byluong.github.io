---
title: "ECS 165A: Databases"
---
## Here's some code:

```python
import psycopg2		# to access PostGreSQL db
import os
import sys

do3a = True
do3b = True
do3c = True
do3d = True
do3e = True
do3f = True
do3g = True


conn = psycopg2.connect(database="postgres", user=os.environ['USER'], port="5432")
cur = conn.cursor()
```