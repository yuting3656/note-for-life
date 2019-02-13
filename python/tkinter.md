Disable Exit [x] , Alt + F4
=================

~~~python 
import tkinter

def disable_event():
    pass

root = Tk()
root.protocol("WM_DELETE_WINDOW", disable_event)
~~~
  
*reference:* `https://stackoverflow.com/questions/45467143/disable-exit-or-x-in-tkinter-window`

關機 / 重開 / 登出
======================

- 關機
~~~python
import os
os.system("shutdown -s")
~~~
~~~python
import subprocess
~~~
~~~python
def shutdown(self):
    subprocess.call(["shutdown", "-f", "-s", "-t", "60"])
~~~
~~~python 
    subprocess.call(["shutdown", "/s"])
~~~


- 重開
~~~python
def restart(self):
    subprocess.call(["shutdown", "-f", "-r", "-t", "60"])
~~~
~~~python
    subprocess.call(["shutdown", "/r"])
~~~

- 登出
~~~python 
    subprocess.call(["shutdown", "/l "])
~~~


*reference:* 
`https://www.daniweb.com/programming/software-development/threads/139335/logging-off-with-python`

*reference:* `https://stackoverflow.com/questions/14764126/how-to-make-a-python-script-which-can-logoff-shutdown-and-restart-a-computer`


跳到進入畫面
================================

~~~python
import ctypes
ctypes.windll.user32.LockWorkStation()
~~~

*reference:*
`https://stackoverflow.com/questions/20733441/lock-windows-workstation-using-python`

將窗放置 TaskBar
=================

~~~python
self.master.iconify()
~~~
