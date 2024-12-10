Atitit gwa改造之 nginx配置https 实录



Pwa改造webwork必须要https

需要证书，自签名证书来自 node   openssl-self-signed-certificate


说要用工具生成openssl 生成单第二部就不行。。

C:\Program Files\Git\usr\bin\openssl genrsa -des3 -passout pass:x -out ssl.pass.key 2048
openssl rsa -passin pass:x -in ssl.pass.key -out ssl.key
openssl req -new -key ssl.key -out ssl.csr
openssl x509 -req -days 365 -in ssl.csr -signkey ssl.key -out ssl.crt


C:\Users\ati\OneDrive\prjs hsu6\spdjs\node_modules\openssl-self-signed-certificate

直接配置https 但是403权限问题 使用root设置根目录
所以使用转发模式，转发到80端口，，反向代理配置 proxy_pass

    # HTTPS server
    #
   server {
		   listen       443 ssl;
			server_name  localhost;
			ssl_certificate      cert.pem;
			ssl_certificate_key  key.pem;
			ssl_session_cache    shared:SSL:10m;
			ssl_session_timeout  50m;
			ssl_ciphers  HIGH:!aNULL:!MD5;
			ssl_prefer_server_ciphers  on;
		#	rewrite ^(.*) http://$server_name:81$1  ;
		  location / {
			  proxy_pass http://localhost:81; # 配置反向代理的ip地址和端口号 【注：url地址需加上http:// 或 https://】
		 
		  }
	}
	

cd D:\phpstudy_pro\Extensions\Nginx1.15.11
d:
start D:\phpstudy_pro\Extensions\Nginx1.15.11\nginx.exe
start C:\wamp\bin\php\php5.6.31\php-cgi.exe -b 127.0.0.1:9003 -c  C:\wamp\bin\php\php5.6.31\phpForApache.ini
