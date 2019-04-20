tap 練習
========

> If you are using as a pipeable operator, do is known as tap!

~~~ts
const source = of(1, 2, 3, 4, 5);
//transparently log values from source with 'do'
const example = source.pipe(
  tap(val => console.log(`BEFORE MAP: ${val}`)),
  map(val => val + 10),
  tap(val => console.log(`AFTER MAP: ${val}`))
);
~~~