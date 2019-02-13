判斷數字是不是 nan
======================

*Checks if the float x is a NaN (not a number). NaNs are part of the IEEE 754 standards. Operation like but not limited to inf * 0, inf / inf or any operation involving a NaN, e.g. nan * 1, return a NaN.
New in version 2.6.*

~~~python
import math
x=float('nan')
math.isnan(x)
True
 
~~~
