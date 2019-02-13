Run certain code every n seconds
================================

~~~python
import threading 
    
    def xxx():
    threading.Timer(5.0,xxx).start() # 5.0 seconds
    print("Yo ~")

xxx()    
~~~

*reference:* `https://stackoverflow.com/questions/3393612/run-certain-code-every-n-seconds`


Run a function with an indepent thread
=================================

~~~python
import threading
   
   def xxx():
       print("hi ")

thread_run = threading.Thread(target=xxx, args=[])
thread_run.start()
~~~
