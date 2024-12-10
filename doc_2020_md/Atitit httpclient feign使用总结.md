Atitit httpclient feign使用总结RestTemplate  

Httpclient重要的功能
重试与超时
RedirectExec执行器的默认策略是，在接收到重定向错误码301与307时会继续访问重定向的地址
所以，HttpClient有默认的执行器RetryExec，其默认的重试策略是DefaultHttpRequestRetryHandler。



HttpClient有默认的执行器RetryExec
关于RetryExec执行器的执行过程，做一个阶段小结：
  RetryExec在执行http请求的时候使用的是底层的基础代码MainClientExec，并记录了发送次数
  当发生IOException的时候，判断是否要重试
  　　首先是根据重试策略DefaultHttpRequestRetryHandler判断，如果可以重试就继续
　　　　 判断当前request是否还可以再次发起
　　如果重试策略判断不可以重试了，就抛相应异常并退出
通过构造器可以看到，默认的重试策略是：
重试3次
如果请求被成功发送过，就不再重试了
InterruptedIOException、UnknownHostException、ConnectException、SSLException，发生这4中异常不重试
关于默认的重试策略，做一个阶段小结：
如果重试超过3次，则不再重试
几种特殊异常及其子类，不进行重试
同一个请求在异步任务重已经被终止，则不进行重试
幂等的方法可以进行重试，比如Get
如果请求没有发送成功，可以进行重试。
五、重试策略对业务的影响 
5.1 我们的业务重试了吗？
  对于我们的场景应用中的get与post，可以总结为：
只有发生IOExecetion时才会发生重试
InterruptedIOException、UnknownHostException、ConnectException、SSLException，发生这4中异常不重试
get方法可以重试3次，post方法在socket对应的输出流没有被write并flush成功时可以重试3次。
首先分析下不重试的异常：
InterruptedIOException，线程中断异常
UnknownHostException，找不到对应host
ConnectException，找到了host但是建立连接失败。
SSLException，https认证异常
  另外，我们还经常会提到两种超时，连接超时与读超时：
java.net.SocketTimeoutException: Read timed out
java.net.SocketTimeoutException: connect timed out
  这两种超时都是SocketTimeoutException，继承自InterruptedIOException，属于上面的第1种线程中断异常，不会进行重试。
七、本文总结
通过本文分析，可以得知HttpClient默认是有重试机制的，其重试策略是：
  1.只有发生IOExecetion时才会发生重试
  2.InterruptedIOException、UnknownHostException、ConnectException、SSLException，发生这4中异常不重试
  3.get方法可以重试3次，post方法在socket对应的输出流没有被write并flush成功时可以重试3次。
  4.读/写超时不进行重试
  5.socket传输中被重置或关闭会进行重试
  6.以及一些其他的IOException，暂时分析不出来。


来的时候掉接口需要三次重试，由于对httpclient不是很了解。只能在for循环里面对异常经常处理并重新调接口。后来做http服务端的时候，有次debug偶然发现客户端调一次请求，服务端会跳多次debug，后来查阅资料发现httpclient有重试机制。
            今天做了个通天塔接口重试的需求，便想起来了httpclient的重试机制。
   查了很久资料，也测试了很多次。后来终于成功了。是通过设置httpclient 的retryHandler来实现。
不多说废话，直接贴代码，如下：

/**


     * @param isPooled 是否使用连接池


     */


    public static CloseableHttpClient getClient(boolean isPooled) {


        HttpRequestRetryHandler handler = new HttpRequestRetryHandler() {






Feign RestTemplate  
					package commxx;

					import java.net.URI;
					import java.net.URISyntaxException;

					import feign.Client;
					import feign.Feign;
					import feign.RequestLine;
					import feign.Retryer;
					import feign.Target;
					import feign.codec.Encoder;
					import feign.codec.Encoder.Default;
					import feign.codec.StringDecoder;

					public class FeignTest {

						public interface someItfs {

					 
							@RequestLine("GET")
							String getx(URI baseUri);
						}

						public static void main(String[] args) throws URISyntaxException {
							String url = "http://www.baidu.com/s?wd=ddd";  //ok..
							someItfs someItfs1 = Feign.builder()
									// .logger(new FeignInfoLogger()) // 自定义日志类，继承 feign.Logger
									// .logLevel(Logger.Level.BASIC)// 日志级别
									// Default(long period, long maxPeriod, int maxAttempts)
									.client(new Client.Default(null, null))// 默认 http
									.retryer(new Retryer.Default(5000, 5000, 1))// 5s超时，仅1次重试
								//	.encoder(Encoder)
								//	.decoder(new StringDecoder())
									.target(Target.EmptyTarget.create(someItfs.class));

					//		 String url = "http://localhost:9104/";
					//	       
							System.out.println(someItfs1.getx(new URI(url)));
						}

					}



RestTemplate  exchange  而不是getfor  postforxxx的优点

exchange

image
RestTempalte中定义很多重载的exchange()方法，如下
String|URL ：请求路径
HttpMethod：Http的动作，如Get、delete等
requestEntity()：在请求中发送资源，get可以为null
responseType（如果要获取状态码和header可使用ResponseEntity<T>）：返回数据的类型
Map/Object... ：填充Url的参数
exchange()利用HttpMethod这个参数，可以完成其他RestTemplate方法的工作，如上GET、POST、DELETE、PUT等。exchange()优于其他方法的点事它可以在发送给服务器的请求中加入头信息。


 (400条消息) HttpClient重试机制 --- 自定义HttpRequestRetryHandler（自定义 重试次数以及重试的时候业务处理）_u010800970的专栏-CSDN博客_httpclient 重试

