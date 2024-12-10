Atitit 结构化日志输出

package com.kok.sport.utils;

import java.io.IOException;
import java.util.logging.ConsoleHandler;
import java.util.logging.Handler;
import java.util.logging.Level;

import org.apache.logging.log4j.LogManager;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class Logt {
	static Logger logger2 = LoggerFactory.getLogger(Logt.class);
	static org.apache.logging.log4j.Logger logger = LogManager.getLogger(Logt.class);
	  public static java.util.logging.Logger log = java.util.logging.Logger.getLogger(Logt.class.toString());
	  
	  static
		{
			Handler FileHandler1 = null;
			try {
				FileHandler1 = new java.util.logging.FileHandler("LOG_FILELOG_FILE.log");
				FileHandler1.setLevel(Level.FINEST);
				log.addHandler(FileHandler1);
			} catch (SecurityException | IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
					//new ConsoleHandler();
			
		}

	public static void main(String[] args) {
		logger.info("ttt");
		logger.info("---");
		log.info("fff");
	}

}

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE log SYSTEM "logger.dtd">
<log>
<record>
  <date>2020-04-03T11:09:21</date>
  <millis>1585883361058</millis>
  <sequence>0</sequence>
  <logger>class com.kok.sport.utils.Logt</logger>
  <level>INFO</level>
  <class>com.kok.sport.utils.Logt</class>
  <method>main</method>
  <thread>1</thread>
  <message>fff</message>
</record>
</log>

