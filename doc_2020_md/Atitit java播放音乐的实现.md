Atitit java播放音乐的实现

感谢您能抽空阅读我的博客，在这里我会使用2种播放MP3格式音频的方法。第一种，使用JavaFX的javafx.scene.media.*包播放。第二种，使用第三方库进行播放，第三方库的下载地址点击打开链接。

/bookmarksHtmlEverythingIndexPrj/src/apkg/MySound.java

import javazoom.jl.decoder.*;
import javazoom.jl.player.*;

public class MySound extends Thread {

	 

	 public static void main(String[] args) throws Exception {
		String musicName="C:\\Users\\Administrator\\Music\\冷漠 - 一路向北.mp3";
			InputStream resourceAsStream =new FileInputStream(new File(musicName));
			new Player(resourceAsStream).play();
	}

	 


(9+条消息)java如何播放mp3格式音频文件，以及如何循环播放音频？ - yourlittlelemon的博客 - CSDN博客.html
