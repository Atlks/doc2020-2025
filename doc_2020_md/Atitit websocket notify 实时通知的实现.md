Atitit websocket notify 实时通知的实现


主要思路  定时器循环，遍历每个conn，发送通知

utils/WsSrv.java


App启动调用


	public static void main(String args[]) {
		WebSocketImpl.DEBUG = true;
		int port = 5202; // 端口
		WsSrv WsServer1 = new WsSrv(port);
	 	WsServer1.start();
 
		
		System.out.println("--");
	}

加载定时时间事件
//   /bookmarksHtmlEverythingIndexPrj/src/awebsocket/WsServer.java
public class WsSrv extends WebSocketServer {
	static {
		timerEvent() ;
	}


public static void timerEvent() {
		System.out.println("timerEvent");
		Timer tmr = new Timer();
		tmr.schedule(new TimerTask() {

			@Override
			public void run() {
				try {
					System.out.println("timerEvent run");
					conns_li.forEach(new Consumer<WebSocket>() {

						@Override
						public void accept(WebSocket t) {
							try {
								LinkedHashMap<String, Object> m = Maps.newLinkedHashMap();
								m.put("from", " tlive_v");
								m.put("page", "1");
								m.put("pagesize", 3);
								MybatisMapper mybatisMapper1;
								if (SportApplication.context != null) {
									mybatisMapper1 = SportApplication.context.getBean(MybatisMapper.class);
									
								} else {
									mybatisMapper1=MybatisUtil.getMybatisMapper();
									
								}
								Object r = MybatisQueryUtil.queryPage(m, mybatisMapper1);

								t.send(JSON.toJSONString(r, true));
							} catch (Exception e) {
								e.printStackTrace();
							}
							

						}
					});

				} catch (Exception e) {
					e.printStackTrace();
				}
				
			}
		}, 1, 5000);

	}

Open 连接onClose事件 保持移除conn列表

	@Override
	public void onOpen(WebSocket conn, ClientHandshake handshake) {
		// ws连接的时候触发的代码，onOpen中我们不做任何操作
		conn.send("open ok..");
		if(!conns_li.contains(conn))
			conns_li.add(conn);
	}


	@Override
	public void onClose(WebSocket conn, int code, String reason, boolean remote) {
		// 断开连接时候触发代码
		// userLeave(conn);
		try {
			conns_li.remove(conn);
		} catch (Exception e) {
			e.printStackTrace();
		}
		
		System.out.println(reason);
	}
rf
Atitit websocket 使用大概总结
Atitit websocket 的前后端实现最佳实践t66
Websockt php.docx
