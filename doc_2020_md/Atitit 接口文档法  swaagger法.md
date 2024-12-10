Atitit 接口文档法  swaagger法

Javadoc法

(9+条消息)swagger2常用注解说明 - 兴国-为梦想而战 - CSDN博客.html

首先需要在pom.xml进行增加我们需要Swagger2所需要的依赖。
    <!-- Swagger 接口文档 -->
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger2</artifactId>
            <version>2.9.2</version>
        </dependency>
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger-ui</artifactId>
            <version>2.9.2</version>
        </dependency>
--------------------- 
接下来需要在 Application中进行声明@EnableSwagger2如图1.1 

图1.1

图1.2
代码如下:
8
9
10
11
12
13
14
15
16
17
18
19
20
声明配置内容的配置 如图1.2   swagger cfg file


@Configuration
public class Swagger {

    @Bean
    public Docket controllerApi() {
        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(new ApiInfoBuilder()
                        .title("xx公司_xx项目_接口文档")
                        .description("描述内容")
//                        .contact("候帅")
                        .version("2.0.0")
                        .build())
                .select()
                .apis(RequestHandlerSelectors.basePackage("controller所在的包"))
                .paths(PathSelectors.any())
                .build();
    }


}
1
2
3
4
5
6
7

进行代码配置
运行api ui
 在编写完后，我们进行运行我们的项目后可以访问http://localhost:8088/swagger-ui.html 进行访问Swagger2的相关内容

问题：：显示不出来方法
必须要配置@api在类上，才能显示出类来然后是方法


ref
(9+条消息)Swagger2--Springboot使用 - 细心程度决定你的成败 - CSDN博客.html
