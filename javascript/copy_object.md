Object.assign()
=========




> The `Object.assign()` method is used to copy the values of all enumerable own properties from one or more source objects to a target object. It will return the target object.

~~~typescript
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget);
// expected output: Object { a: 1, b: 4, c: 5 }
~~~



add key/value pair to a JavaScript Object
=======

> link: https://stackoverflow.com/questions/1168807/how-can-i-add-a-key-value-pair-to-a-javascript-object

- 2017  Object.assign()
~~~ts
var obj = {key1: "value1", key2: "value2"};
Object.assign(obj, {key3: "value3"});

document.body.innerHTML = JSON.stringify(obj);
~~~

- 2018  object spread operator {...}
~~~ts
var obj = {key1: "value1", key2: "value2"};
var pair = {key3: "value3"};
obj = {...obj, ...pair};

document.body.innerHTML = JSON.stringify(obj);
~~~