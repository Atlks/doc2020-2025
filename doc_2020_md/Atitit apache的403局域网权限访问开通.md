Atitit apache的403局域网权限访问开通


除了httpd cofn 文件名里面访问以外。。
还需要
在 C:\Program1\bin\apache\apache2.4.27\conf\extra\httpd-vhosts.conf

里面更改require loccalhost

   Require all granted
