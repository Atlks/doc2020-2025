Atitit 简化不使用spring的方法  

性能优化 启动速度优化，全部static 尽可能。。不要动态建立对象。。太慢

类库冲突法。。使用其子类混淆
  <dependency>
      <groupId>org.aspectj</groupId>
      <artifactId>aspectjweaver</artifactId>
      <version>1.8.9</version>
    </dependency>
    
版本冲突法 使用多个spr子类
混乱的cfg xml文件等。。
使用加密安全的db串。。。不标准对加密法
多个启动类和启动文件  扫描不同对path
