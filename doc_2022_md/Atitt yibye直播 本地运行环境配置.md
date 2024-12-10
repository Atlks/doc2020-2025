Atitt yibye直播 本地运行环境配置

Debug cfg open
Index.php  debug=1
数据库  
D:\src_nml\live\data\config\database.php	

Create local db ,,import sql file 2m


Redis cfg
D:\src_nml\live\app\app.php


Nginx cfg


erver {

		listen 80;

		server_name  stream.com localhost;
		root D:\src_nml\live\public;
		index index.php index.html index.htm;
		access_log  nzsp1.log ;
		location ~ \.php$ {
			try_files $uri /index.php =404;
			fastcgi_pass 127.0.0.1:9000;
			fastcgi_index index.php;
			fastcgi_buffers 16 16k;
			fastcgi_buffer_size 32k;
			fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
			fastcgi_read_timeout 600;
			include fastcgi_params;
			autoindex on;
			autoindex_exact_size on;
		}
		 location / {
            if (!-e $request_filename) {
                rewrite ^/index.php(.*)$ /index.php?s=$1 last;
                rewrite ^/admin.php(.*)$ /admin.php?s=$1 last;
				rewrite ^/admin21hxc.php(.*)$ /admin21hxc.php?s=$1 last;
                rewrite ^/api.php(.*)$ /api.php?s=$1 last;
				 rewrite ^([0-9]+)$ /home/show/index?roomnum=$1 last;
                rewrite ^(.*)$ /index.php?s=$1 last;
                break;
            }
        }
	}
