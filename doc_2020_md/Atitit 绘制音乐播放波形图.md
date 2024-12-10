Atitit 绘制音乐播放波形图

Matplotlib
Matplotlib 是Python中类似 MATLAB 的绘图工具，熟悉 MATLAB 也可以很快的上手 Matplotlib

绘图显示
绘制声音波形
Librosa有显示声音波形函数waveplot( )：

# thie file encode is utf8
#djddd    C:\Users\Administrator\AppData\Local\Programs\Python\Python37\python.exe  D:\00wkspc\bpm.py
import librosa
import numpy as np
import numpy as np
import librosa.display



yy ,sr = librosa.load('D:\\00000\\不仅仅是喜欢_孙语赛_不仅仅是喜欢.mp3', sr=None)


#pip install matplotlib   Matplotlib 是 Python 的绘图库。 
# plot a wavform
import matplotlib.pyplot as plt
fig = plt.figure()
librosa.display.waveplot(yy, sr)
plt.title('Beat wavform')
plt.show()


(9+条消息)Python--Matplotlib（基本用法） - 苦作舟的人呐 - CSDN博客(9+条消息)Python--Matplotlib（基本用法） - 苦作舟的人呐 - CSDN博客
(9+条消息)音频处理库—librosa的安装与使用 - z小白的博客 - CSDN博客.html
