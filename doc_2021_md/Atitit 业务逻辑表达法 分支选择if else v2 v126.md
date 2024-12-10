Atitit 业务逻辑表达法 分支选择if else


管道命令法
·  顺序执行多条命令：command1;command2;command3;
简单的顺序指令可以通过 ;来实现
·  有条件的执行多条命令：which command1 && command2 || command3
&& : 如果前一条命令执行成功则执行下一条命令，如果command1执行成功（返回0）,则执行command2
|| :与&&命令相反，执行不成功时执行这个命令
管道命令
管道是一种通信机制，通常用于进程间的通信（也可通过socket进行网络通信），它表现出来的形式将前面每一个进程的输出（stdout）直接作为下一个进程的输入（stdin）。
管道命令使用|作为界定符号，管道命令与上面说的连续执行命令不一样。
Foreach逻辑

选取命令:cut.grep
cut:从某一行信息中取出某部分我们想要的信息。
cut -d '分隔字符' -f field // 用于分隔字符
cut -c 字符范围
[参数说明]
-d : 后面接分隔字符,通常与 -f 一起使用
-f : 根据-d 将信息分隔成数段，-f 后接数字 表示取出第几段
-c : 以字符为单位取出固定字符区间的信息


ps:cut在处理多空格相连的数据时，比较吃力。
grep:分析一行信息，如果其中有我们需要的信息，就将该行拿出来

排序命令：sort,wc,uniq
sort
uniq
uniq [-ic]
[参数]
-i ：忽略大小写的不同
-c ：进行计数
栗子5
使用 last 取出历史登录信息的账号，排序，去重[root@izuf6i29flb2df231kt91hz /]# last | cut -d ' ' -f 1 | sort | uniq -c
      1 
      7 reboot
     19 root
      1 wtmp
wc
wc [-lwm]
[参数]
-l ：仅列出行
-w ：仅列出多少字(英文单字)
-m ：多少字符


字符转换命令：tr,col,join,paste,expand
tr：用来删除一段信息当中的文字，或者进行文字信息得替换
tr [-ds] set
[参数]
-d : 删除信息当中的set1这个字符串
-s : 替换掉重复的字符
栗子8
将上一步生成的info 文件删除掉所有的 root
删除前[root@izuf6i29flb2df231kt91hz /]# cat info
root     pts/0        112.28.180.86    Thu May 10 18:01 - 18:12  (00:11)    
reboot   system boot  3.10.0-693.2.2.e Fri May 11 02:00 - 16:31 (51+14:30)  
 删除后[root@izuf6i29flb2df231kt91hz /]# cat info | tr -d 'root'  
     ps/0        112.28.180.86    Thu May 10 18:01 - 18:12  (00:11)    
eb   sysem b  3.10.0-693.2.2.e Fi May 11 02:00 - 16:31 (51+14:30)  

删除时并不是只删除连续的字符，reboot也被删除掉了root部分
除去dos文件留下来的^M符号
$ cat /root/passwd | tr -d '\r' > /root/passwd.linux^M可以用\r替代
col
col [-xb]
[参数]
-x ： 将tab键换成对等的空格键
-b : 在文字内有反斜杠(/)时，仅保留反斜杠最后接的那个字符

栗子9
将上图中的^I换成空格键[root@izuf6i29flb2df231kt91hz /]# cat info | col -x | cat -A | more
        root     pts/0        112.28.181.159   Sun Jul  1 14:28   still logged in$
col经常被用于将man page转存为纯文本文件
join:主要讲两个文件有相同数据的一行,相同字段放在前面
join [-ti12] file1 file2
[参数]
-t : join 默认以空格符分隔数据，并且对比第一个字段的数据 ,如果两个文件相同，则将两条数据连成一行
-i : 忽略大小写的差异
-1 : 说明第一个文件通过那个字段来进行分析
-2 : 说明第二个文件通过那个字段来分析
栗子10
将/etc/passwd 与  /etc/shadow 相关数据整合成一列[root@izuf6i29flb2df231kt91hz /]# head -3 /etc/passwd /etc/shadow==> /etc/passwd <==
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
==> /etc/shadow <==
root:$6$RNGEziM7$2e/EJd3hThS8TMqHSgDIfeDf7dJUG1dbJ0ik1goybGYmLGZL.sHNv1Ltb4.1HUksxTI0Cs3PJw5g/YirSImKg1:17643:0:99999:7:::
bin:*:17110:0:99999:7:::
daemon:*:17110:0:99999:7:::[root@izuf6i29flb2df231kt91hz /]# join -t ':' /etc/passwd /etc/shadow
root:x:0:0:root:/root:/bin/bash:$6$RNGEziM7$2e/EJd3hThS8TMqHSgDIfeDf7dJUG1dbJ0ik1goybGYmLGZL.sHNv1Ltb4.1HUksxTI0Cs3PJw5g/YirSImKg1:17643:0:99999:7:::
bin:x:1:1:bin:/bin:/sbin/nologin:*:17110:0:99999:7:::
daemon:x:2:2:daemon:/sbin:/sbin/nologin:*:17110:0:99999:7:::

将etc/passwd 按：分隔的第4个字段 与 etc/group的第3个字段 比较，如果相同，则将他两同行数据放在一起[root@izuf6i29flb2df231kt91hz /]# join -t ':' -1 4 /etc/passwd -2 3 /etc/group0:root:x:0:root:/root:/bin/bash:root:x:1:bin:x:1:bin:/bin:/sbin/nologin:bin:x:2:daemon:x:2:daemon:/sbin:/sbin/nologin:daemon:x:4:adm:x:3:adm:/var/adm:/sbin/nologin:adm:x:
join: /etc/passwd:6: is not sorted: sync:x:5:0:sync:/sbin:/bin/sync7:lp:x:4:lp:/var/spool/lpd:/sbin/nologin:lp:x:
paste:直接将两个文件两行贴在一起，中间以[tab]键隔开
paste [-d] file1 file2
[ 参数]
-d : 后面可以接分隔字符，默认以[tab]来分隔的
- : 如果file部分写成-，表示接受standard input数据的意思
栗子11[root@izuf6i29flb2df231kt91hz /]# paste info info2
    root     pts/0        112.28.181.159   Sun Jul  1 14:28   still logged in       root     pts/0        112.28.181.159   Sun Jul  1 14:28   still logged in   
root     pts/0        112.28.181.159   Sun Jul  1 14:24 - 14:27  (00:03)        root     pts/0        112.28.181.159   Sun Jul  1 14:24 - 14:27  (00:03)    
root     pts/0        112.28.181.159   Sun Jul  1 13:19 - 14:24  (01:04)        root     pts/0        112.28.181.159   Sun Jul  1 13:19 - 14:24  (01:04) 
*expand:把tab键转为空格键
expand [-t] file
[参数]
`` -t : 后面接数字，一般，一个tab可以用8个空格代替，可以自行定义代表几个空格
栗子12[root@izuf6i29flb2df231kt91hz /]# cat info | expand -3 info
   root     pts/0        112.28.181.159   Sun Jul  1 14:28   still logged in   
root     pts/0        112.28.181.159   Sun Jul  1 14:24 - 14:27  (00:03)    
root     pts/0        112.28.181.159   Sun Jul  1 13:19 - 14:24  (01:04)    
root     tty1                          Sun Jul  1 12:46   still logged in
切割命令：split
split：顾名思义，讲一个大文件依据文件大小或行数切割成为小文件
split [-bl] file prefix
[参数]
-b : 后面可接欲切割文件的大小，可加单位，例如b,k,m等
-l : 以行数来进行切割
PREFIX : 代表前导符，可作为切割文件的前导文字
Mysql 流程函数
流程函数也是很常用的一类函数，用户可以使用这类函数在 SQL 中实现条件选择。这样做能够提高查询效率。下表列出了这些流程函数
其他函数

 

