CSV write 
===========

~~~python
From this link

Modes: Description

r: Opens a file for reading only. The file pointer is placed at the beginning of the file. This is the default mode.
rb: Opens a file for reading only in binary format. The file pointer is placed at the beginning of the file. This is the default mode.
r+: Opens a file for both reading and writing. The file pointer will be at the beginning of the file.
rb+: Opens a file for both reading and writing in binary format. The file pointer will be at the beginning of the file.
w: Opens a file for writing only. Overwrites the file if the file exists. If the file does not exist, creates a new file for writing.
wb: Opens a file for writing only in binary format. Overwrites the file if the file exists. If the file does not exist, creates a new file for writing.
w+: Opens a file for both writing and reading. Overwrites the existing file if the file exists. If the file does not exist, creates a new file for reading and writing.
wb+: Opens a file for both writing and reading in binary format. Overwrites the existing file if the file exists. If the file does not exist, creates a new file for reading and writing.
a: Opens a file for appending. The file pointer is at the end of the file if the file exists. That is, the file is in the append mode. If the file does not exist, it creates a new file for writing.
ab: Opens a file for appending in binary format. The file pointer is at the end of the file if the file exists. That is, the file is in the append mode. If the file does not exist, it creates a new file for writing.
a+: Opens a file for both appending and reading. The file pointer is at the end of the file if the file exists. The file opens in the append mode. If the file does not exist, it creates a new file for reading and writing.
ab+: Opens a file for both appending and reading in binary format. The file pointer is at the end of the file if the file exists. The file opens in the append mode. If the file does not exist, it creates a new file for reading and writing.
~~~





csv writer 
=================

~~~python 

with open("C:\\Users\\Yuting\\Desktop\\ly_db\\custom_pon_7.csv", mode="w", newline='\n') as write_csv_file:
    wr = csv.writer(write_csv_file, dialect='excel', delimiter=',', lineterminator='\n')
    # , quoting=csv.QUOTE_ALL

    # wr.writerow(result_list)
    for i in range(len(result_list)):
        value = [result_list[i]]
        wr.writerow(value)

~~~