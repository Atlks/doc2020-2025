Atitit 架构之功能扩展性 流程引擎  决策引擎 规则引擎  业务脚本引擎

场景的扩展性需求

动态规则、表达式高精度计算、复杂布尔运算、自定义函数和操作生成等需求而设计的。

工作流引擎比较

脚本引擎php python sql js 

Dsl引擎 
xml 

表达式语言(EL expression language)
语法大量简化（比如去掉显示类、方法、变量声明，异常处理，逻辑跳转循环等等），只支持简单的数学公式、对象方法成员变量调用， 就
脚本引擎  嵌入式语言， dsl
我们通常是指一种小的嵌入式语言，它位于模板内并生成文本输出或文档。例如，Freemarker和Velocity通常被称为脚本引擎


Java Script Engine
Java 脚本引擎可以将脚本嵌入Java代码中，可以自定义和扩展Java应用程序，自JDK1.6被引入，基于Rhino引擎，JDK1.8后使用Nashorn引擎，支持ECMAScript 5，但后期还可能会换。
脚本引擎包位于javax.script中，各个类名及描述如下


使用脚本实现Java接口
@Testpublic void runnableImpl() throws Exception{
    ScriptEngineManager manager = new ScriptEngineManager();
    ScriptEngine engine = manager.getEngineByName("JavaScript");

    // String里定义一段JavaScript代码脚本
    String script = "function run() { print('run called'); }";
    // 执行这个脚本
    engine.eval(script);

    // 从脚本引擎中获取Runnable接口对象（实例）. 该接口方法由具有相匹配名称的脚本函数实现。
    Invocable inv = (Invocable) engine;
    // 在上面的脚本中，我们已经实现了Runnable接口的run()方法
    Runnable runnable = inv.getInterface(Runnable.class);

    // 启动一个线程运行上面的实现了runnable接口的script脚本
    Thread thread = new Thread(runnable);
    thread.start();
    Thread.sleep(1000);
}
Java 脚本引擎入门 - 阿提说说 - OSCHINA - 中文开源技术交流社区

