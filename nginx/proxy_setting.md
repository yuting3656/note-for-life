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


在同一　domain 下面放不同的 angualr apps
==================  

- link 

> `https://medium.com/@CristianSitov/delivering-multiple-angular2-apps-with-a-single-nginx-server-at-different-urls-55b42ca4c4ce`



~~~ngnix
		location /tmbc{
		   proxy_pass http://localhost:82;
		   include proxy_set_header.conf;
		   proxy_redirect off;
		}
		
		location /tmbc/csso {
		   proxy_pass http://localhost:83;
		   include proxy_set_header.conf;
		   proxy_redirect off;
		}


	server {
	    listen 81;
		server_name localhost;
		root htdoc/taitra;
		index index.html index.htm;
		port_in_redirect off;
	}


				
		location /tmbc/csso {
		   alias /var/www/html/tmbc/csso;
		   try_files $uri$args $uri$args/ /tmbc/csso/index.html;
		}
~~~
