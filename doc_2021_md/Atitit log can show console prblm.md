Atitit log can show console prblm

Use

Logback不能直接指定。。Log4j可以指定。。
java.util.logging.Logger


public class junitt {
	
	//private static Logger LOG2 = LoggerFactory.getLogger("oneInfo");
	static  org.slf4j.Logger logger2_slf4j = LoggerFactory.getLogger(Object.class);
	static   Logger logger_log4j = LogManager.getLogger("myLogger");  
	private static final Log log = LogFactory.getLog(HKlhcTest2.class);
 	private static org.apache.logging.log4j.Logger logger_log4j2 = org.apache.logging.log4j.LogManager.getLogger(junitt.class);
	static java.util.logging.Logger logr_javalog=java.util.logging.Logger.getLogger("LoggingDemo");
	public static void main(String[] args) {
		 
		logger_log4j2.info("log2j222 v2");
	//	org.apache.logging.log4j.LogManager
		logr_javalog.info("---------javalog");
		logger2_slf4j.info("logger2_slf4j");logger_log4j.info( "logger_log4j:");
	}
