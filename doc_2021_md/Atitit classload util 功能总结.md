Atitit classload util 功能总结


建立自己对classloader

	List li_libdir=Lists.newArrayList();
			li_libdir.add("D:\\libs_junbo");
			String classpath = "D:\\apiJubo\\api\\common\\target\\classes";
			List li_classDir=Lists.newArrayList();
			li_classDir.add(classpath);
			URLClassLoader myClassLoader = getURLClassLoader(li_libdir,li_classDir);
		


	private static URLClassLoader getURLClassLoader(List<String> li_libdir, List<String> li_classDir) {
		
		List<URL> li_urls=Lists.newArrayList();
		 for (String libpath : li_libdir) {
			 File file_directory = new File(libpath);

			 

				File[] fileNames =file_directory.listFiles();

			//	URL urls[] = new URL[fileNames.length];

				for (int i = 0; i < fileNames.length; i++) {

					try {
						li_urls.add(fileNames[i].toURL());
					} catch (MalformedURLException e) {
						// TODO Auto-generated catch block
						e.printStackTrace();
					}

				}

				
		}
		 for (String clsD : li_classDir) {
			 
			 try {
				li_urls.add(new File(clsD).toURL());
			} catch (MalformedURLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			 
		 }
		 
		 
		 URL[] urls=li_urls.toArray(new URL[li_urls.size()])  ;
		URLClassLoader	loader = new URLClassLoader(urls,null);

			return loader;
	//	return null;
	}

动态新增jar或者classdir 加载
New urlclassloader,父亲loader指向上一级的。。。

从jar或者class目录 load class
public static Class<?> loadClass(String name, ClassLoader classLoader, boolean isInitialized) 
cn.hutool.core.util.ClassLoaderUtil.loadClass(jarOrDir, name)

