Bot gui输入中文


Robotjs 和pyautogui 都不支持


所以一种方法是使用剪贴板赋值法，一种是调用输入法模式。。
还有一种调用autoit模式更加简单
.2 连续输入
typewrite方式一：传入字符串，不支持中文字符，因为函数无法知道输入法需要什么按键才能得到中文字符

python


复制代码

pyautogui.typewrite('hello, PyAutoGUI!\n')


