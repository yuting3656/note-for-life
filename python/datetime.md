converting string to datetime 
================

~~~python
from datetime import datetime
from dateutil.parser import parse
war_start = '2011-01-03'
datetime.strptime(war_start, '%Y-%m-%d')
~~~
 - datetime.datetime(2011, 1, 3, 0, 0)

*reference:* `https://chrisalbon.com/python/basics/strings_to_datetime/`