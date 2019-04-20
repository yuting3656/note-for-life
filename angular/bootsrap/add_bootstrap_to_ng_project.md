# Add Bootstrap to Angular project

- link: https://loiane.com/2017/08/how-to-add-bootstrap-to-an-angular-cli-project/

## 1. CLI
~~~
> npm install bootstrap
~~~

## 2. importing  css
1. config: `angulbooar.json`
~~~ typeScript
"styles": [
  "node_modules/bootstrap/dist/css/bootstrap.min.css",
  "styles.scss"
]
~~~
2. import directly in src/style.css or src/style.scss

~~~css
@import '~bootstrap/dist/css/bootstrap.min.css';
~~~

## 3. ngx-bootstrap

~~~
> npm install ngx-bootstrap --save
~~~
or
~~~
> npm install bootstrap ngx-bootstrap --save
~~~