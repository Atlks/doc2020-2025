Atitit 热部署 与配置管理



Db分布式配置也不错。。。

，我们当然对它也非常的熟悉，想想配置一般都通过哪几种形式存在？
硬编码
配置文件
DB 配置表
相比“硬编码”的形式，它解决了第二个问题，持久化了配置。但是，另外两个问题并没有解决，运维成本依旧还是很高的。
配置动态变更，可以是通过类似“硬编码”暴露管理接口的方式，这时，代码中会多一步持久化新配置到文件的逻辑。或者，简单粗暴点，直接登录机器上去修改配置文件，再重启应用，让配置生效。当然，你也可以在代码中增加一个定时任务，如每隔 10s 读取配置文件内容，让最新的配置能够及时在应用中生效，这样也就免去了重启应用这个“较重”的运维操作。
它相对于前两者，更进一步，将配置从应用中抽离出来，集中管理，能较大的降低运维成本。
那么，它能怎么解决动态更新配置的问题呢？据我所知，有两种方式。
其一，如同之前一样，通过暴露管理接口去解决，当然，也一样得增加持久化的逻辑，只不过，之前是写文件，现在是将最新配置写入数据库。不过，程序中还需要有定时从数据库读取最新配置的任务，这样，才能做到只需调用其中一台机器的管理配置接口，就能把最新的配置下发到整个应用集群所有的机器上，真正达到降低运维成本的目的。
其二，直接修改数据库，程序中通过定时任务从数据库读取最新的配置内容。
“DB 配置表”的形式解决了主要的问题，但是它不够优雅，带来了一些“累赘

主流配置中心对比：Spring Cloud Config、Apollo、Nacos

　　目前市面上用的比较多的配置中心有：Spring Cloud Config、Apollo、Nacos和Disconf等。

　　由于Disconf不再维护，下面主要对比一下Spring Cloud Config、Apollo和Nacos。

　　　　nacos 1.2.0版本已支持权限控制

从配置中心角度来看，性能方面Nacos的读写性能最高，Apollo次之，Spring Cloud Config依赖Git场景不适合开放的大规模自动化运维API。功能方面Apollo最为完善，nacos具有Apollo大部分配置管理功能，而Spring Cloud Config不带运维管理界面，需要自行开发。Nacos的一大优势是整合了注册中心、配置中心功能，部署和操作相比Apollo都要直观简单，因此它简化了架构复杂度，并减轻运维及部署工作。
Nacos抽象定义了Namespace、Group、Data ID的概念
Nacos 配置管理基础应用：
　　Nacos抽象定义了Namespace、Group、Data ID的概念，具体这几个概念代表什么，取决于我们把它们看成什么，这里推荐给大家一种用法，如下图：
　　　　
　　　　Namespace ：代表不同环境，如开发、测试、生产环境。
　　　　Group：代表某项目，如XX医疗项目、XX电商项目
　　　　DataId：每个项目下往往有若干个工程，每个配置集(DataId)是一个工程的主配置文件
　　获取配置集需要指定：
　　　　1、nacos服务地址，必须指定
　　　　2、namespace，如不指定默认public
　　　　3、group，如不指定默认 DEFAULT_GROUP
　　　　4、dataId，必须指定
Nacos 特性：
　　Nacos主要提供以下四大功能：

　　　　1. 服务发现与服务健康检查
　　　　　　Nacos使服务更容易注册，并通过DNS或HTTP接口发现其他服务，Nacos还提供服务的实时健康检查，以防止向不健康的主机或服务实例发送请求。
　　　　2. 动态配置管理
　　　　　　动态配置服务允许您在所有环境中以集中和动态的方式管理所有服务的配置。Nacos消除了在更新配置时重新部署应用程序，这使配置的更改更加高效和灵活。
　　　　3. 动态DNS服务
　　　　　　Nacos提供基于DNS 协议的服务发现能力，旨在支持异构语言的服务发现，支持将注册在Nacos上的服务以域名的方式暴露端点，让三方应用方便的查阅及发现。
　　　　4. 服务和元数据管理
　　　　　　Nacos 能让您从微服务平台建设的视角管理数据中心的所有服务及元数据，包括管理服务的描述、生命周期、服务的静态依赖分析、服务的健康状态、服务的流量管理、路由及安全策略。
acos客户端获取配置：

　　　　　　新增一个项目，引入依赖

    <dependencies>
        <dependency>
            <groupId>com.alibaba.nacos</groupId>
            <artifactId>nacos-client</artifactId>
            <version>1.1.1</version>
        </dependency>
    </dependencies>

　　　　　　获取外部化配置

public class SimpleDemoMain {
    public static void main(String[] args) throws NacosException {
        //nacos 地址
        String serverAddr = "127.0.0.1:8848";
        //Data Id
        String dataId = "nacos_simple_demo.yaml";
        //Group
        String group = "DEFAULT_GROUP";
        Properties properties = new Properties();
        properties.put("serverAddr", serverAddr);
        // properties.put("namespace", "xxx");
        ConfigService configService = NacosFactory.createConfigService(properties);
        //获取配置,String dataId, String group, long timeoutMs
        String content = configService.getConfig(dataId, group, 5000);
        System.out.println(content);
        // common:
        // config1: something    }
}


