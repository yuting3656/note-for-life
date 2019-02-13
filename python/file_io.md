下載 zip 檔 存到電腦裡面
================================

~~~python 
import requests

url="https://oa.hyweb.com.tw/hyoa/downloadid=26c2c62595a3bf1641ea79b0aa93136d"

r = requests.get(url)
 
z = zipfile.ZipFile(io.BytesIO(r.content))
~~~




刪除檔案~~~
=====================================

~~~python 
import shutil

shutil.rmtree('FILE_NAME')

~~~

路徑位置
=================================
~~~python

~~~





