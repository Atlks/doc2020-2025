Atitit springboot 数据json数字返回字符串的解决   Json结构化调试


看起里条件应该是4种情况，，


 

Json结构化调试ff 返回体content-type json 

使用ff ，但是要返回体content-type非json 




SpringBoot解决返回体content-type非json 
2018.07.12 22:12 7339浏览 
最佳解决方案为自定义消息转换器。
首先，为什么要自定义消息转换器？所见即所得，原本的消息转换器并不能满足我们目前的需求。
在最近的项目中，使用了SpringBoot与FastJson构建项目，在我们返回时，使用 @ResponseBody的方法里，采用了fastjson里的JSON.toJSONString()方法返回我们需要的Json数据，而这种返回中，会有一个问题，在返回中@ResponseBody注解中的消息转换器会默认理解为String解析，在返回体中如下图，content-type为text/html。

因此我们解决想让我们的返回体中content-type为application/json。
针对于这个问题，有一种最暴力的解决方案，直接在@RequestMapping中添加produces属性，设置produces="application/json"直接使得返回体设置为json格式。
当然对于这种每个接口暴力解决的方案来说，对于每写一个接口都需要设置，因此增加我们写代码的重复性工作，因此需要一个一劳永逸的方式。
在@ResponseBody里默认有消息转换器，一般json转换使用的是JackJson进行转换的，而我们在项目中配置使用fastjson，因此需要修改消息转化器。
首先消息转化器中不只有json转换器，还有字符转换器等。
在我们的项目中可以自定义一个配置类，标注有@Configuration或者在@SpringBootApplication的启动配置类中添加下面代码，就增加了fastjson的消息转换器注入。
/**
 * fastjson消息转换器
 * @return
 */@Beanpublic HttpMessageConverters httpMessageConverters() {
    FastJsonHttpMessageConverter fastJsonHttpMessageConverter = new FastJsonHttpMessageConverter();    //添加fastJson的配置信息
    FastJsonConfig fastJsonConfig = new FastJsonConfig();
    fastJsonConfig.setSerializerFeatures(SerializerFeature.PrettyFormat);    //处理中文乱码问题
    List<MediaType> fastMediaTypes = new ArrayList<>();
    fastMediaTypes.add(MediaType.APPLICATION_JSON_UTF8);    //在convert中添加配置信息.   
    fastJsonHttpMessageConverter.setSupportedMediaTypes(fastMediaTypes);
    fastJsonHttpMessageConverter.setFastJsonConfig(fastJsonConfig);
    HttpMessageConverter<?> converter = fastJsonHttpMessageConverter;        return new HttpMessageConverters(converter);
}
当然需要注意，这种配置的方式必须在fastjson 1.2.44版本及之后才支持。在我们使用Maven构建项目是，需要添加fastjson的依赖。
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>fastjson</artifactId>
    <version>1.2.44</version></dependency>
使用这种配置后，可以在返回中去掉我们的json转化，并直接返回我们需要转化的实体，在消息转换器中会自动调用fastjson进行转json。

