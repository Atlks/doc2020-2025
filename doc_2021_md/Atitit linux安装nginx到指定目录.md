Atitit linux安装nginx到指定目录

可以指定安装nginx目录位置。。Configure 的时候指定其位置。。
这样可以安装多个nginx，方便将其容器化

安装依赖

yum install gcc
yum install pcre-devel
yum install zlib zlib-devel
yum install openssl openssl-devel
1
2
3
4
//一键安装上面四个依赖

yum -y install gcc zlib zlib-devel pcre-devel openssl openssl-devel
1

 
————————————————
 

解压nginx的tar包

Wget  http://nginx.org/download/nginx-1.21.1.tar.gz
tar -zxvf nginx-1.21.1.tar.gz
cd nginx-1.21.1


./configure --prefix=/home/ec2-user/nginxdir
make && make install


Nginx常用命令
//启动命令
/home/ec2-user/nginxdir/sbin/nginx
sudo /home/ec2-user/nginxdir/sbin/nginx

安装路径下的/home/work/your nginx/nginx-port/sbin目录下：./nginx
//停止命令
安装路径下的/home/work/your nginx/nginx-port/sbin目录下：./nginx -s stop
或者 : nginx -s quit
//重启命令
安装路径下的/home/work/your nginx/nginx-port/sbin目录下：./nginx -s reload
————————————————
 
