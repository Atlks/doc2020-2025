/JavaRobotGui/src/pkgs/WinManager.java
package pkgs;

import com.sun.jna.platform.win32.User32;
import com.sun.jna.platform.win32.WinDef.HWND;
import com.sun.jna.platform.win32.WinUser;

public class WinManager {
	// final User32 user32 = User32.INSTANCE;

	public static void main(String[] args) {

		while (true) {
			System.out.println("---in");
			HWND hwnd = User32.INSTANCE.FindWindow(null, "软件授权");
			if (hwnd != null)
			{
			 	User32.INSTANCE.CloseWindow(hwnd);
			 
				User32.INSTANCE.DestroyWindow(hwnd);
			}
				
				//User32.INSTANCE.CloseWindow(hwnd);
			else {
				System.out.println("---f");
				return;
			}

		}

	}

	static HWND FindWindow() {

		HWND hwnd = User32.INSTANCE.FindWindow(null, "软件授权");
		// if (unitFrameWnd == null) {
		// unitFrameWnd = hwnd;
		// }
		return hwnd;
	}

	/*
	 * 
	 * 
	 * 通过网上搜索 FindWindow 的用法，其函数原型： HWND FindWindow ( LPCTSTR lpClassName,
	 * LPCTSTR lpWindowName );
	 * 
	 */

}

