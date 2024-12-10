Atitit springcloud的艺术 attilax总结

核心组件
核心部件 微服务的核心要素在于服务的发现、注册、路由、熔断、降级、分布式配置，

微服务的核心要素在于服务的发现、注册、路由、熔断、降级、分布式配置，基于上述几种必要条件对 Dubbo 和 Spring Cloud 做出对比。




点评：从整体架构上来看，二者模式接近，都需要服务提供方，注册中心，服务消费方

微服务架构核心要素 Dubbo 只是实现了服务治理，而 Spring Cloud


Dubbo 只是实现了服务治理，而 Spring Cloud 子项目分别覆盖了微服务架构下的众多部件，服务治理只是其中的一个方面。
Dubbo 提供了各种 Filter，对于上述中“无”的要素，可以通过扩展 Filter 来完善。例如：

分布式配置：可以使用淘宝的 diamond、百度的 disconf 来实现分布式配置管理。

服务跟踪：可以使用京东开源的 Hydra，或者扩展 Filter 用 Zippin 来做服务跟踪。

批量任务：可以使用当当开源的 Elastic-Job、tbschedule。
--------------------- 
 组件运行流程


Dubbo



下图中的每个组件都是需要部署在单独的服务器上，Gateway 用来接受前端请求、聚合服务，并批量调用后台原子服务。每个 Service 层和单独的 DB 交互。



Dubbo 组件运行流程



Dubbo 组件运行：

Gateway：前置网关，具体业务操作，Gateway 通过 Dubbo 提供的负载均衡机制自动完成。

Service：原子服务，只提供该业务相关的原子服务。

Zookeeper：原子服务注册到 ZK 上。



Spring Cloud 组件运行




Spring Cloud



Spring Cloud组件运行：

所有请求都统一通过 API 网关（Zuul）来访问内部服务。

网关接收到请求后，从注册中心（Eureka）获取可用服务。

由 Ribbon 进行均衡负载后，分发到后端的具体实例。

微服务之间通过 Feign 进行通信处理业务。



点评：业务部署方式相同，都需要前置一个网关来隔绝外部直接调用原子服务的风险。



Dubbo 需要自己开发一套 API 网关，而 Spring Cloud 则可以通过 Zuul 配置即可完成网关定制。使用方式上 Spring Cloud 略胜一筹。
--------------------- 
 具体组件

服务治理：Spring Cloud Eureka 39  注册中心

服务治理 39
Netflix Eureka 40
搭建服务注册中心 41
注册服务提供者 43
高可用注册中心 46
第4章　客户端负载均衡：Spring Cloud Ribbon 73
服务容错保护：Spring Cloud Hystrix 130
第6章　声明式服务调用：Spring Cloud Feign 199

快速入门 200
参数绑定 202
继承特性 205
Ribbon配置 209
全局配置 209

API网关服务：Spring Cloud Zuul 217

快速入门 219
构建网关 220
请求路由 221
请求过滤 223
路由详解 226
传统路由配置 226
服务路由配置 228
服务路由的默认规则 229
自定义路由映射规则 229
路径匹配 230
路由前缀 233
本地跳转 234
Cookie与头信息 235
第8章　分布式配置中心：Spring Cloud Config	267
快速入门	267
构建配置中心	268
配置规则详解	269
客户端配置映射	272


第9章　消息总线：Spring Cloud Bus	295
消息代理	295
RabbitMQ实现消息总线	296
基本概念	297
安装与使用	298
快速入门	302

第10章　消息驱动的微服务：Spring Cloud Stream	344
快速入门	344
核心概念	349
绑定器	350
发布-订阅模式	351
消费组	353
消息分区	354
使用详解	355
开启绑定功能	355
绑定消息通道	356
消息生产与消费	360
响应式编程	366
消费组与消息分区	368
消息类型	370
绑定器详解	373

第11章　分布式服务跟踪：Spring Cloud Sleuth	386  类似elk
快速入门	386
准备工作	386
实现跟踪	389
跟踪原理	390
抽样收集	392
与Logstash整合	394
与Zipkin整合	397
HTTP收集	398
消息中间件收集	402
收集原理	404
数据存储	414
API接口	417

《深入理解Spring Cloud与微服务构建》(方志朋)【简介_书评_在线阅读】 - 当当图书.html
* 1章　微服务简介	1
* 2章　Spring Cloud简介	14
第3章　构建微服务的准备	30
第4章　开发框架Spring Boot	43
第5章　服务注册和发现Eureka	66
第6章　负载均衡Ribbon	84
第7章　声明式调用Feign	101
第8章　熔断器Hystrix	115
第9章　路由网关Spring Cloud Zuul	126
* 10章　配置中心
* 11章　服务链路追踪
* 12章　微服务监控
* 13章　Spring Boot Security详解	174
* 14章　使用Spring Cloud OAuth2
* 15章　使用Spring Security OAuth2
* 16章　使用Spring Cloud构建微

《Spring Cloud微服务实战》(翟永超　著)【简介_书评_在线阅读】 - 当当图书.html
