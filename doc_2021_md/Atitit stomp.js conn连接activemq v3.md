Atitit stomp.js conn连接activemq  

activemq  启动，已经默认开启了stomp ws的接口。。地址是

url='ws://localhost:61614/stomp';



Js 客户端代码
C:\Users\u\OneDrive\桌面\hsim prj  index.php
<Script src="https://cdnjs.cloudflare.com/ajax/libs/stomp.js/2.3.3/stomp.js" ></script>

<script>
//  alert()
console.log("-start");
<!--TO 创建socket连接 并订阅相关频道-->
 
//if port err,so err can show..
url='ws://localhost:61614/stomp';
  stompClient = Stomp.client(url);
 
stompClient.debug= function(str) {
    // append the debug log to a #debug div somewhere in the page using JQuery:
     console.log("--debg:"+str);
  };;
 stompClient.heartbeat.outgoing = 20000;

stompClient.connect({}, function (frame) {
       // 相当于连接 ws://localhost:8080/gs-guide-websocket/041/hk5tax0r/websocket hk5tax0r就是sessionid
		console.log("正在连接");
		console.log(frame);
		//订阅通用私聊频道 群组也通过这里实现
		// must use /topic/xxxName mode  tsai nen conn...only  xxxName cant uswe..
		stompClient.subscribe('/topic/foo.bar', function (greeting) {
			  console.log("-------------receive..."+greeting);
			}
		   );
		   
		 
		  
		//订阅用户上线下线的公共频道
		stompClient.subscribe('/topic/userlist', function (greeting) {
			
		});
	},function errorCallBack (error) {
		// 连接失败时（服务器响应 ERROR 帧）的回调方法
	      console.log(error);
	}

);   //end conn
</script>


注意的问题，，activemq stomp启动的时候，显示端口61613..
但事迹ws端口61614.。。再配置文件C:\apache-activemq-5.16.0\conf\activemq.xml里面
指明了词端口


     <transportConnectors>
            <!-- DOS protection, limit concurrent connections to 1000 and frame size to 100MB -->
            <transportConnector name="openwire" uri="tcp://0.0.0.0:61616?maximumConnections=1000&amp;wireFormat.maxFrameSize=104857600"/>
            <transportConnector name="amqp" uri="amqp://0.0.0.0:5672?maximumConnections=1000&amp;wireFormat.maxFrameSize=104857600"/>
            <transportConnector name="stomp" uri="stomp://0.0.0.0:61613?maximumConnections=1000&amp;wireFormat.maxFrameSize=104857600"/>
            <transportConnector name="mqtt" uri="mqtt://0.0.0.0:1883?maximumConnections=1000&amp;wireFormat.maxFrameSize=104857600"/>
            <transportConnector name="ws" uri="ws://0.0.0.0:61614?maximumConnections=1000&amp;wireFormat.maxFrameSize=104857600"/>
        </transportConnectors>



连接mq主题偶可以再admin管理界面看到消费者数量
但是只能使用/topic/xxxx的模式连接主题，，不能直接使用xxx真是麻烦。。。
因为stomp.js的订阅api没有区分队列和订阅，所以要在url里面指定

(Object) subscribe(destination, callback, headers = {})
Note: The library will generate an unique ID if there is none provided in the headers. To use your own ID, pass it using the headers argument
Subscribe to a STOMP Broker location. The return value is an Object with unsubscribe method.
var subscription = client.subscribe("/queue/test", callback);


Stomp.js api 文档

https://stomp-js.github.io/stomp-websocket/codo/class/Client.html#subscribe-dynamic

启动php web服务器

C:\Users\u\OneDrive\桌面\hsim prj\php web server.txt.bat
C:\Program1\bin\php\php7.1.9\php.exe -S localhost:8080 -t "C:\Users\u\OneDrive\桌面\hsim prj"
