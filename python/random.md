從一 list 隨機拿
============

- 連結

    > `https://machinelearningmastery.com/how-to-generate-random-numbers-in-python/`

- 例子


~~~python 
# choose a random element from a list
from random import seed
from random import choice
# seed random number generator
seed(1)
# prepare a sequence
sequence = [i for i in range(20)]
print(sequence)
# make choices from the sequence
for _ in range(5):
	selection = choice(sequence)
	print(selection)
~~~