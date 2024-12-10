Atitit linux gui远程vncserver


yum install vnc vnc-server
sudo yum install firefox
sudo yum install xrdp vnc4serve
运行 vncpasswd，配置密码，密码至少6个字符，至多8个字符

vncserver :1
vncserver -kill :1

sudo yum  install gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal

程序安装与配置运行
linode 有一篇详尽的文章：Install VNC on Ubuntu 16.04。
ubuntu
安装 vnc4server，sudo apt-get install vnc4server
运行 vncpasswd，配置密码，密码至少6个字符，至多8个字符
运行 vnc4server :1，启动 vnc server。可通过 vnc4server -kill :1 关闭 vnc server。
windows
chrome 安装 vnc viewer 插件
通过 ip:5901 远程登陆，默认使用 x-terminal-emulator & x-window-manager 界面。





## open port  5901
iptables -I INPUT -p tcp --dport 8888 -j ACCEPT
iptables -I INPUT -p tcp --dport 5202 -j ACCEPT
iptables -I INPUT -p tcp --dport 5202 -j ACCEPT
iptables -I INPUT -p tcp --dport 5901 -j ACCEPT
 

notd ok blow..
iptables -A INPUT -p tcp --dport 5202 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 5202 -j ACCEPT

iptables -A INPUT -p tcp --dport 5901 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 5901 -j ACCEPT
