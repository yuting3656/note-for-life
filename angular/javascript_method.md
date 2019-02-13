在陣列中刪除特定位置資料
=================

> array1.splice(i, 1)

~~~javascript
var array1 = [5, 12, 8, 130, 44];

// fun 找出第一個大於數字13的number
function findFirstLargeNumber(element) {
  return element > 13;
}

// 用 javascript findIndex的方法來查找 
// Array.findIndex()
console.log(array1.findIndex(findFirstLargeNumber));

// 列印出來跟你說 第一個數字大於13的number 
i = array1.findIndex(findFirstLargeNumber)
console.log(i)

// 用splice(i, 1)的方法把他殺掉!
array1.splice(i, 1)


console.log(array1)
~~~


Array.prototype.findIndex()
=============

- 