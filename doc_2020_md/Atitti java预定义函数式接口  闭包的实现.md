Atitti java预定义函数式接口  闭包的实现

 
java8中几个函数式接口的小例子
标签： JAVAjava8
2014-08-18 12:16 3559人阅读 评论(0) 收藏 举报
 分类：
 
java（124）  java8（1） 
版权声明：本文为博主原创文章，未经博主允许不得转载。
[java] view plain copy print?
// Function<T, R> -T作为输入，返回的R作为输出   
        Function<String,String> function = (x) -> {System.out.print(x+": ");return "Function";};  
        System.out.println(function.apply("hello world"));  
          
        //Predicate<T> -T作为输入，返回的boolean值作为输出   
        Predicate<String> pre = (x) ->{System.out.print(x);return false;};  
        System.out.println(": "+pre.test("hello World"));  
          
        //Consumer<T> - T作为输入，执行某种动作但没有返回值   
        Consumer<String> con = (x) -> {System.out.println(x);};  
        con.accept("hello world");  
          
        //Supplier<T> - 没有任何输入，返回T   
        Supplier<String> supp = () -> {return "Supplier";};  
        System.out.println(supp.get());  
          
        //BinaryOperator<T> -两个T作为输入，返回一个T作为输出，对于“reduce”操作很有用   
        BinaryOperator<String> bina = (x,y) ->{System.out.print(x+" "+y);return "BinaryOperator";};  
        System.out.println("  "+bina.apply("hello ","world"));  

