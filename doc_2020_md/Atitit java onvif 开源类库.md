Atitit java onvif 开源类库 getProfiles getStreamUri

1. ONVIF Java Library by Milgo	1
1.1. https://github.com/milg0/onvif-java-lib	4
1.2. getProfiles  respones file	4
1.3. getStreamUri:rtsp://192.168.31.144:10554/tcp/av0_0	4
1.4. Code---	5

ONVIF Java Library by Milgo
Non-Profit, Analytics, Security
The ONVIF Java library by Milgo aims to be the first library to interact with the API features related to standardize communication between IP-based security products. ONVIF stands for open network video interface forum. ONVIF API is targeted to installers, system integrators, architects, engineers, and end users.
nvifDevice nvt = new OnvifDevice("192.168.0.20", "admin", "password");
nvt.getDevices(); // Basic methods for configuration and information
nvt.getMedia(); // Methods to get media information like stream or screenshot URIs or to change your video encoder configuration
nvt.getImaging(); // A few functions to change your image settings, really just for your image settings!
nvt.getPtz(); // Functionality to move your camera (if supported!)
Our first goal is to get a snapshot URI of our camera (not every must support this, but most NVT should do). So we will work on with our media methods and there are some methods to achieve our goal. Don't get irritated by the fact that there are methods to get snapshot- and screenshot-URIs, they return the same and have just different names.
getDefaultSnapshotUri() : String
getSnapshotUri(profileToken : String) : String


You can get your device profiles with the initial devices.
OnvifDevice nvt = new OnvifDevice("192.168.0.20", "admin", "password");
List<Profile> profiles = nvt.getDevices().getProfiles();


snapshot URI.
import java.net.ConnectException;
import java.util.List;

import javax.xml.soap.SOAPException;

import org.onvif.ver10.schema.Profile;

import de.onvif.soap.OnvifDevice;

public class OnvifTest {
   public static void main(String[] args) {
      try {
         OnvifDevice nvt = new OnvifDevice("192.168.0.20", "admin", "password");
         List<Profile> profiles = nvt.getDevices().getProfiles();
         String profileToken = profiles.get(0).getToken();
         System.out.println("Snapshot URI: "+nvt.getMedia().getSnapshotUri(profileToken));
      }
      catch (ConnectException e) {
         System.err.println("Could not connect to NVT.");
      }
      catch (SOAPException e) {
         e.printStackTrace();
      }
   }
}
https://github.com/milg0/onvif-java-lib
getProfiles  respones file


getStreamUri:rtsp://192.168.31.144:10554/tcp/av0_0


Request SOAP Message (GetStreamUri): <env:Envelope xmlns:env="http://www.w3.org/2003/05/soap-envelope" xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"><env:Header><wsse:Security><wsse:UsernameToken><wsse:Username/><wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordDigest">K3vtv2ZkAdcl0DFdQz/cjBsPcU8=</wsse:Password><wsse:Nonce EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">MTQ4MzgwMzUyMw==</wsse:Nonce><wsu:Created>2016-12-21T15:04:00Z</wsu:Created></wsse:UsernameToken></wsse:Security></env:Header><env:Body><ns2:GetStreamUri xmlns:ns10="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns11="http://www.onvif.org/ver10/schema" xmlns:ns2="http://www.onvif.org/ver10/media/wsdl" xmlns:ns3="http://www.w3.org/2005/08/addressing" xmlns:ns4="http://docs.oasis-open.org/wsn/b-2" xmlns:ns5="http://docs.oasis-open.org/wsrf/bf-2" xmlns:ns6="http://docs.oasis-open.org/wsrf/rp-2" xmlns:ns7="http://docs.oasis-open.org/wsn/t-1" xmlns:ns8="http://www.w3.org/2004/08/xop/include" xmlns:xmime="http://www.w3.org/2005/05/xmlmime"><ns2:StreamSetup/><ns2:ProfileToken>PROFILE_000</ns2:ProfileToken></ns2:GetStreamUri></env:Body></env:Envelope>
Response SOAP Message (GetStreamUriResponse): <?xml version="1.0" encoding="UTF-8"?><s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:e="http://www.w3.org/2003/05/soap-encoding" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:wsa="http://www.w3.org/2005/08/addressing" xmlns:xmime="http://www.w3.org/2005/05/xmlmime" xmlns:tns1="http://www.onvif.org/ver10/topics" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xop="http://www.w3.org/2004/08/xop/include" xmlns:tt="http://www.onvif.org/ver10/schema" xmlns:wsnt="http://docs.oasis-open.org/wsn/b-2" xmlns:wstop="http://docs.oasis-open.org/wsn/t-1" xmlns:tds="http://www.onvif.org/ver10/device/wsdl" xmlns:trt="http://www.onvif.org/ver10/media/wsdl" xmlns:tev="http://www.onvif.org/ver10/events/wsdl" xmlns:tptz="http://www.onvif.org/ver20/ptz/wsdl" xmlns:timg="http://www.onvif.org/ver20/imaging/wsdl" xmlns:ter="http://www.onvif.org/ver10/error" ><s:Body><trt:GetStreamUriResponse><trt:MediaUri><tt:Uri>rtsp://192.168.31.144:10554/tcp/av0_0</tt:Uri><tt:InvalidAfterConnect>false</tt:InvalidAfterConnect><tt:InvalidAfterReboot>false</tt:InvalidAfterReboot><tt:Timeout>PT60S</tt:Timeout></trt:MediaUri></trt:GetStreamUriResponse></s:Body></s:Envelope>
getStreamUri:rtsp://192.168.31.144:10554/tcp/av0_0







Code---
package com.attilax.video;

/**
 * @author attilax
 *2016年12月21日 下午10:38:11
 */
import java.io.IOException;
import java.net.ConnectException;
import java.util.List;

import javax.xml.soap.SOAPException;

import org.onvif.ver10.media.wsdl.GetStreamUri;
import org.onvif.ver10.media.wsdl.GetStreamUriResponse;
import org.onvif.ver10.schema.Profile;
import org.onvif.ver10.schema.StreamSetup;
import org.onvif.ver10.schema.Transport;

import de.onvif.soap.OnvifDevice;

public class OnvifTest {
	public static void main(String[] args) {
		// org.apache.commons.codec.binary.Base64
		// org.apache.commons.codec.binary.Base64
		try {
			// OnvifDevice nvt = new OnvifDevice("192.168.0.20", "admin",
			// "password");
			OnvifDevice nvt = new OnvifDevice("192.168.31.144:10080", "", "");
			List<Profile> profiles = nvt.getDevices().getProfiles();
			for (Profile profile : profiles) {
				// String profileToken = profiles.get(0).getToken();
				System.out.println(profile);
			}

			// System.out.println("Snapshot URI: "+nvt.getMedia().getSnapshotUri(profileToken));
			String profileToken = profiles.get(0).getToken();  //PROFILE_000
			StreamSetup streamSetup = new StreamSetup();
			String getStreamUri = nvt.getMedia().getStreamUri(profileToken, streamSetup);
			System.out.println("getStreamUri:" + getStreamUri);
		} catch (ConnectException e) {
			System.err.println("Could not connect to NVT.");
		} catch (SOAPException e) {
			e.printStackTrace();
		}
	}


作者:: 绰号:老哇的爪子claw of Eagle 偶像破坏者Iconoclast image-smasher
捕鸟王"Bird Catcher 王中之王King of Kings 虔诚者Pious 宗教信仰捍卫者 Defender Of the Faith. 卡拉卡拉红斗篷 Caracalla red cloak
简称：： Emir Attilax Akbar 埃米尔 阿提拉克斯 阿克巴
全名：：Emir Attilax Akbar bin Mahmud bin  attila bin Solomon bin adam Al Rapanui 埃米尔 阿提拉克斯 阿克巴 本 马哈茂德 本 阿提拉 本 所罗门 本亚当  阿尔 拉帕努伊
常用名：atl（ail），  EMAIL:1466519819@qq.com


头衔：uke总部o2o负责人，全球网格化项目创始人，
uke宗教与文化融合事务部部长， uke宗教改革委员会副主席
，Uke部落首席大酋长，
uke制度与重大会议委员会委员长，uke保安部首席大队长,uke制度检查委员会副会长，
奶牛科技cto ，uke 首席cto 
uke波利尼西亚区大区连锁负责人，克尔格伦群岛区连锁负责人，莱恩群岛区连锁负责人，uke汤加王国区域负责人。布维岛和南乔治亚和南桑威奇群岛大区连锁负责人 
 Uke软件标准化协会理事长理事长 uke终身教育学校副校长 
Uke 数据库与存储标准化协会副会长 uke出版社编辑总编
Uke医院方面的创始人

转载请注明来源：attilax的专栏  ?http://blog.csdn.net/attilax
--Atiend

