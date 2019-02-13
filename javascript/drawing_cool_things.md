很酷得畫畫
============================

~~~ javascript 
for (var line=1; line<60; line++) {
  for(var i=1;i < 29;i++) {
    var s = (Math.floor((Math.random()*2)%2)) ? "╱" : "╲";
    document.write(s);
  }
  document.writeln("<br>");
}

~~~


string remove quotes
===============

e.g. if the String is: "I am here" then I want to output only I am here.

~~~ javascript 
var someStr = 'He said "Hello, my name is Foo"';
console.log(someStr.replace(/['"]+/g, ''));
~~~

> *link:*  https://stackoverflow.com/questions/19156148/i-want-to-remove-double-quotes-from-a-string