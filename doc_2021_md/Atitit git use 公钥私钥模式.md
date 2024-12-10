Atitit git use 公钥私钥模式

Git命令行
C:\Program Files\Git\usr\bin\ssh-keygen.exe
C:\Windows\System32\OpenSSH\ssh-keygen.exe

要创建 SSH 密钥，请键入ssh-keygen -t rsa -C "your_email@example.com". 这将创建id_rsa和id_rsa.pub文件。

生成公司要，默认这个目录。。
C:\Users\ati\.ssh

公钥粘贴到ssh key在gitlab中。。

但是使用
C:\wamp\www\nzsp1_cms>git push git@git.xsitehub.com:hank/nzsp1.git
还是提示不行。。


使用gitgui试试totogit
Setting>git>remote设置git地址和putty key。。但提示说加载干菜生成的key不能load。。。

尝试使用totogit下面的putty生成key

这下私钥可以加载了，但还是不能连接。。

git push git@git.xsitehub.com:hank/nzsp1.git
git@git.xsitehub.com: Permission denied (publickey,gssapi-keyex,gssapi-with-mic).



Idea git
通过totogit去除http git，只保留ssh git，此时貌似起作用了。。
设置公钥私钥。
