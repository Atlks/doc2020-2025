Phpcgi use  FastCGI 


NGINX 可以通过 FastCGI 守护进程与 Windows 上的 PHP 交互，该守护进程随 PHP 一起提供：php-cgi.exe。您需要在NGINX配置文件中运行和使用。启动后，将在命令提示符窗口中继续侦听连接。要隐藏该窗口，请使用小型实用程序RunHiddenConsolephp-cgi.exe -b 127.0.0.1:<port>fastcgi_pass 127.0.0.1:<port>;php-cgi.exe


启动一个端口，，，然后使用socket链接


Php应该作为参数传递进去


生成 FastCGI 进程
与 Apache 或 Lighttpd 不同，NGINX 不会自动生成 FCGI 进程。您必须单独启动它们。事实上，FCGI 很像代理。有几种方法可以启动 FCGI 程序，但幸运的是 PHP5 会根据您在PHP_FCGI_CHILDREN环境变量中设置的数量自动生成。因此，我们只需手动运行，或创建一个初始化脚本，如下所示：php -b 127.0.0.1:9000
#!/bin/bash



将 NGINX 连接到正在运行的 FastCGI 进程
现在 FCGI 进程正在运行，我们必须告诉 NGINX 通过 FCGI 协议将请求代理到它：



fastCgi 是什么
fastCgi 是用来提高 CGI 程序性能的。
那么 CGI 程序的性能问题在哪呢？”PHP 解析器会解析 php.ini 文件，初始化执行环境”，就是这里了。标准的 CGI 对每个请求都会执行这些步骤，所以处理每个请求的时间会比较长。
那么 fastCgi 是怎么做的呢？首先，fastCgi 会先启一个 master，解析配置文件，初始化执行环境，然后再启动多个 worker。当请求过来时，master 会传递给一个 worker，然后立即可以接受下一个请求。这样就避免了重复的劳动，效率自然是高。而且当 worker 不够用时，master 可以根据配置预先启动几个 worker 等着；当然空闲 worker 太多时，也会停掉一些，这样就提高了性能，也节约了资源。这就是 fastCgi 对进程的管理。



PHP-FPM 是什么
PHP-FPM 是一个实现了 FastCgi 的程序，被 PHP 官方收录。
PHP 的解释器是 php-cgi，它只是个 CGI 程序，只能解析请求，返回结果，不会进程管理。所以就出现了一些能够调度 php-cgi 进程的程序，比如说由 lighthttpd 分离出来的 spawn-fcgi。
PHP-FPM 也是这么个东西，在长时间的发展后，逐渐得到了大家的认可，也越来越流行。


FastCGI
FastCGI像是一个常驻(long-live)型的CGI，它可以一直执行着，只要激活后，不会每次都要花费时间去fork一次（这是CGI最为人诟病的fork-and-execute 模式）。它还支持分布式的运算，即 FastCGI 程序可以在网站服务器以外的主机上执行并且接受来自其它网站服务器来的请求。
FastCGI是语言无关的、可伸缩架构的CGI开放扩展，其主要行为是将CGI解释器进程保持在内存中并因此获得较高的性能。众所周知，CGI解释器的反复加载是CGI性能低下的主要原因，如果CGI解释器保持在内存中并接受FastCGI进程管理器调度，则可以提供良好的性能、伸缩性、Fail- Over特性等等。
FASTCGI是和HTTP协议类似的概念。无非就是规定了在同一个TCP连接里怎么同时传多个HTTP连接。这实际上导致了个问题，有个HTTP连接传个大文件不肯让出FASTCGI连接，在同一个FASTCGI连接里的其他HTTP连接就傻了。所以Lighttpd? 引入了 X-SENDFILE 。

PHP-CGI
PHP-CGI是PHP自带的FastCGI管理器。
PHP-CGI的不足：
php-cgi变更php.ini配置后需重启php-cgi才能让新的php-ini生效，不可以平滑重启。
直接杀死php-cgi进程，php就不能运行了。(PHP-FPM和Spawn-FCGI就没有这个问题，守护进程会平滑从新生成新的子进程。）
php-cgi是php提供给web serve也就是http前端服务器的cgi协议接口程序，当每次接到http前端服务器的请求都会开启一个php-cgi进程进行处理，而且开启的php-cgi的过程中会先要重载配置，数据结构以及初始化运行环境，如果更新了php配置，那么就需要重启php-cgi才能生效，例如phpstudy就是这种情况。


例如平滑过渡配置更改，普通的php-cgi在每次更改配置后，需要重新启动才能初始化新的配置，而php-fpm是不需要，php-fpm分将新的连接发送给新的子程序php-cgi，这个时候加载的是新的配置，而原先正在运行的php-cgi还是使用的原先的配置，等到这个连接后下一次连接的时候会使用新的配置初始化，这就是平滑过渡。


应用实现上的最大的区别是，FastCGI 应用实现模块中会有一个常驻服务进程。一个 CGI 应用的典型实现是，每次响应一个 Web 服务器发送过来的请求时，都会创建和初始化一个新的处理进程，使用这个进程来产生此请求对应的响应数据，最后在处理结束之后，关闭此进程。FastCGI 应用的初始化要比 CGI/1.1 的简化很多，其进程是固定常驻的，不需要管理生命周期，不需要初始化标准输入输出流 stdin、stdout、stderr，也不需要读取大量的环境变量。此初始化的核心部分是监听一个 socket（套接字），通过这个 socket 来接收 Web 服务器发来的请求。

当应用进程从当前监听的 socket 中成功建立了一个新的连接后，就会使用一个简单的 FastCGI 协议来与 Web 服务器进行通信。这个协议的设计支持了两种特性：第一个特性是，可以让多个 HTTP 请求使用同一个连接进行数据交互，这样应用的实现就可以采用事件驱动编程模型或者多线程编程模型；第二个特性是，同一个请求的多个数据流的传输可以复用同一个连接，这样 FastCGI 应用在输出响应数据时，就可以把 stdout、stderr 两个数据流的数据通过同一个连接发送给 Web 服务器，不用像 CGI/1.1 应用那样必须使用两个连接才行。


