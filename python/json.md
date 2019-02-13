json 轉換
==================
~~~python 
 self.file = self.req.read()
                # 直接用 byte (print)寫出來
                print(self.file)
                # 將資料編寫成 json　字串 －－＞ json.dumps(XXX)

                # rep 原本就是json檔 直接decode (從byte轉成字形)
                self.json_file = self.file.decode('utf-8')
            #  將剛剛加入的 json 編寫成 python 資料結構　 －－＞ json.loads(XXX)
            self.dic_json_file = json.loads(self.json_file)
~~~


讀 txt 檔案 轉 json
==========================
~~~ python 
file = open('{}/hyweb_version.txt'.format(cwd), 'r')
json_file = json.load(file)
~~~