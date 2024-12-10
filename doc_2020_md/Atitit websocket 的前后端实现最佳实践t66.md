Atitit websocket 的前后端实现最佳实践t66


技术选型
Tomcat和spring类型的太麻烦。。使用mina也麻烦。。使用Java-WebSocket这个jar来实现最简单了。。
1.首先，在pom.xml引入如下jar包。Java-WebSocket-1.3.0.jar 
101kb

<!-- websocket -->
        <dependency>
            <groupId>org.java-websocket</groupId>
            <artifactId>Java-WebSocket</artifactId>
            <version>1.3.0</version>
        </dependency>


后端WsServer
/bookmarksHtmlEverythingIndexPrj/src/awebsocket/WsServer.java

package awebsocket;

 

import java.net.InetSocketAddress;

import org.java_websocket.WebSocket;
import org.java_websocket.WebSocketImpl;
import org.java_websocket.handshake.ClientHandshake;
import org.java_websocket.server.WebSocketServer;

public class WsServer extends WebSocketServer {
	
	 public static void main(String args[]){
	        WebSocketImpl.DEBUG = true;
	        int port = 8887; // 端口
	        WsServer WsServer1 = new WsServer(port);
	        WsServer1.start();
	        System.out.println("--");
	    }
    public WsServer(int port) {
        super(new InetSocketAddress(port));
    }

    public WsServer(InetSocketAddress address) {
        super(address);
    }

    @Override
    public void onOpen(WebSocket conn, ClientHandshake handshake) {
        // ws连接的时候触发的代码，onOpen中我们不做任何操作

    }

    @Override
    public void onClose(WebSocket conn, int code, String reason, boolean remote) {
        //断开连接时候触发代码
       // userLeave(conn);
        System.out.println(reason);
    }

    @Override
    public void onMessage(WebSocket conn, String message) {
        System.out.println(message);
  conn.send(" onmessage getmsg :"+message);
        if(null != message &&message.startsWith("online")){
            String userName=message.replaceFirst("online", message);//用户名
            userJoin(conn,userName);//用户加入
        }else if(null != message && message.startsWith("offline")){
            userLeave(conn);
        }

    }

    @Override
    public void onError(WebSocket conn, Exception ex) {
        //错误时候触发的代码
        System.out.println("on error");
        ex.printStackTrace();
    }
    /**
     * 去除掉失效的websocket链接
     * @param conn
     */
    private void userLeave(WebSocket conn){
    //    WsPool.removeUser(conn);
    }
    /**
     * 将websocket加入用户池
     * @param conn
     * @param userName
     */
    private void userJoin(WebSocket conn,String userName){
     //   WsPool.addUser(userName, conn);
    }

}

在线测试古巨基
http://www.blue-zero.com/WebSocket/



websocket在线测试.html
java中websocket的应用 - xdxxdx - 博客园.html
