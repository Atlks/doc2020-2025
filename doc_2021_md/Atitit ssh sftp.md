Atitit ssh sftp  


  

import java.io.File;
import java.io.FileInputStream;
import java.util.Map;
import java.util.concurrent.TimeUnit;

import com.google.common.collect.Maps;
import com.jcraft.jsch.JSchException;
import com.jcraft.jsch.SftpProgressMonitor;

public class SSHHelperTest2 {

 /**
  * @param args
  * @throws Exception
  */
 public static void main(String[] args) throws Exception {

  String linux_password = " ";
  // 使用目标服务器机上的用户名和密码登陆
  SSHHelper helper = new SSHHelper("10.0.1.15", 22, "root", linux_password);
  String command = "rm /data/api/WEB-INF/classes/application/web/controller/SscController.class00";
 System.out.println(helper.sendCmd(command)); 
 //command = "rm /data/api/WEB-INF/classes/application/web/controller/SscController.class00";
 //
 String remoteDir="/data/api/WEB-INF/classes/application/web/controller";
 System.out.println(helper.uploadLocalFileToRemote("D:\\SYSTEM\\api\\target\\classes\\application\\web\\controller\\SscController.class", remoteDir));
 
 command=" export  JAVA_HOME=/usr/jdk1.7 ; sh /data/tomcat7-api/bin/startup.sh";
 System.out.println(helper.sendCmd(command,3000)); 
 TimeUnit.SECONDS.sleep(3);
 System.out.println("f");
 //command=" sh /data/tomcat7-api/bin/startup.sh";
 //System.out.println(helper.sendCmd(command));
 }


deadlockchk0118.rar
