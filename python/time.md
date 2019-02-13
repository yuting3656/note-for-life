時間的用法
===================
- 抓現在的時間 轉成 string
~~~python 
"{:%Y/%m/%d %H:%M:%S}".format(datetime.datetime.now())
~~~

- 從現在時間算起 抓 XXX 分鐘後的時間
~~~python
now = datetime.datetime.now()
now_plus_xxx =  now + datetime.timdelta(minutes = XXX)
~~~
