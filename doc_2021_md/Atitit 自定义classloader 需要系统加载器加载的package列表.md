Atitit 自定义classloader 需要系统加载器加载的package列表



package com.wz.test;

import java.io.File;
import java.net.MalformedURLException;
import java.net.URL;
import java.net.URLClassLoader;
public class SimpleURLClassLoader extends URLClassLoader {
    //工程class类所在的路径
    public static String projectClassPath = "E:/IDE/work_place/ZJob-Note/bin/";
    //所有的测试的类都在同一个包下
    public static String packagePath = "testjvm/testclassloader/";
//    public SimpleURLClassLoader() {
//        //设置ClassLoader加载的路径
//        super(getMyURLs());
//    }
    public SimpleURLClassLoader(URL[] urls, ClassLoader object) {
		super(urls,object);
	}
 
    public Class load(String name) throws Exception{
        return loadClass(name);
    }
    public Class<?> loadClass(String name) throws ClassNotFoundException {
        return loadClass(name,false);
    }
    /**
     * 重写loadClass，不采用双亲委托机制("java."开头的类还是会由系统默认ClassLoader加载)
     */
    @Override
    public Class<?> loadClass(String name,boolean resolve) throws ClassNotFoundException {
        Class clazz = null;
        //查看HotSwapURLClassLoader实例缓存下，是否已经加载过class
 
        //如果类的包名为"java."开始，则有系统默认加载器AppClassLoader加载
        if(    name.startsWith("sun.reflect.") || name.startsWith("java.") || name.startsWith("javax.") ||  name.startsWith("org.xml.") ||  name.startsWith("org.w3c.") ) {
            try {
                //得到系统默认的加载cl，即AppClassLoader
                ClassLoader system = ClassLoader.getSystemClassLoader();
                clazz = system.loadClass(name);
                if (clazz != null) {
                    if (resolve)
                        resolveClass(clazz);
                    return (clazz);
                }
                
                //else    super.findClass(name);
                
            } catch (ClassNotFoundException e) {
                // Ignore
            	e.printStackTrace();
            }
        }   
        
       
        return  super.findClass(name);
    } 
    
   
}
