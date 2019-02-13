桌面管控程式 續借logic
=======================
1. 在提示警告視窗跑出來前一分鐘，會主動問Agent，能不能預約!

    ~~~python 
    def ask_agent_renewaL():
    def create_ask_agent_renewal_thread():
    ~~~

- > 可以：
    ~~~python
    self.global_infor.renewal_access_available = True
    ~~~
- > 不可以：
    ~~~python
    self.global_infor.renewal_access_available = False
    ~~~
- > exception:
    ~~~python
    self.global_infor.renewal_access_available = False
    ~~~

2. 在可以預約的狀況下，提示警告視窗跑出來，伴隨著續借Button。(因為 `self.global_infor.renewal_access_available = True`，所以Button跑得出來！)

3. 使用者 click 續借 Button 觸發續借 def
   ~~~python
   def url_renewal_function():
   ~~~