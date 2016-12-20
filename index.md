---
layout: fullscreensplash
splash_links:
  - url: "#test-link"
    btn_label: "Resume"
    btn_class: "btn--inverse"

  - url: "#test-link"
    btn_label: "LinkedIn"
    btn_class: "btn--inverse"

  - url: "#test-link"
    btn_label: "Github"
    btn_class: "btn--inverse"
---
<div class="page__hero--overlay" 
	style=" background-image: url(assets/images/code.jpg); 
	height: 100vh; 
	margin-bottom: 0px;">
{% include feature_row id="splash_links" class="full" %}


## testing!

University class database implemented in PostgreSQL.
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