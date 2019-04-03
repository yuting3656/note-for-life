imoprt 
==============

- link 

    > `https://stackoverflow.com/questions/4142151/how-to-import-the-class-within-the-same-directory-or-sub-directory`


- example 

~~~text
bin/
    main.py
    classes/
        user.py
        dir.py
~~~

~~~python
# python 2
from classes.user import User
from classes.dir import Dir
# python 
from .user import User
from .dir import Dir
~~~