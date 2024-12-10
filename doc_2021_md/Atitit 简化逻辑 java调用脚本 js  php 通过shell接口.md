Atitit 简化逻辑 java调用脚本 js  php 通过shell接口


public class ShellUtil {

	public static void main(String[] args) throws Exception {
		
		echo("java111");
		
		echo(runJs("d:\\t.js"));   ;
		echo(runPhp("d:\\t.php"));   ;
		
		echo("java9999");

	}

	
	
	
	
	
	




	private static String runJs(String string) throws Exception {
Process process=	Runtime.getRuntime().exec("d:\\node13.exe " +string);
		
		int status = process.waitFor();
		
	return  InputStreamUtils.getContentsAsString(process.getInputStream())	;
	}
 










	private static String runPhp(String string) throws Exception {
		Process process=	Runtime.getRuntime().exec("C:\\xampp\\php\\php.exe " +string);
		
		int status = process.waitFor();
		
	return  InputStreamUtils.getContentsAsString(process.getInputStream())	;
	}

}
