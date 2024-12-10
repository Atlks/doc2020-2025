Atitit   org.springframework.beans.factory.NoSuchBeanDefinitionException: No qualifying bean of type

可能是因为增加了日志aop cfg cause...if no its ok...



类库冲突法。。使用其子类混淆
  <dependency>
      <groupId>org.aspectj</groupId>
      <artifactId>aspectjweaver</artifactId>
      <version>1.8.9</version>
    </dependency>


也可能xmx不够了，所以加载不来

如果是俩个对话，会提示应该加载single，但是find 2..
