加入 server 寫法
=========================


~~~
server {
    listen {port};
    server_name {name};
    root {doc/location};
    index index.html index.htm;
    port_in_redirect off; 
}
~~~

- port_in_redirec : 會把 port 隱藏