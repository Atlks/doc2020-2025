Atitit 解决java程序内存泄漏  垃圾回收gc 功能

定时器太麻烦，  跑个线程国家简单
	new Thread(new Runnable() {
			
			@Override
			public void run() {
				try {
					Thread.sleep(9000);
				} catch (InterruptedException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
				Runtime.getRuntime().exit(0);
				
			}
		}).start();;
