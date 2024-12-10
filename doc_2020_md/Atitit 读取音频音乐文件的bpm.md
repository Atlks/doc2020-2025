Atitit 读取音频音乐文件的bpm


Librosa是一个用于音频、音乐分析、处理的python工具包，
一些常见的时频处理、特征提取、绘制声音图形等功能应有尽有，功能十分强大。本文主要介绍librosa的安装与使用方法。
Librosa大概总共50M

\bpm.py
# thie file encode is utf8
#djddd    C:\Users\Administrator\AppData\Local\Programs\Python\Python37\python.exe  D:\00wkspc\bpm.py
import librosa
import numpy as np

yy ,sr = librosa.load('D:\\00000\\不仅仅是喜欢_孙语赛_不仅仅是喜欢.mp3')
onset_env = librosa.onset.onset_strength(yy, sr=sr, hop_length=512, aggregate=np.median)
tempo, _ = librosa.beat.beat_track(onset_envelope=onset_env, sr=sr)
print(tempo) 
#tempo就是你们要的bpm
#sr is samp rate 

Echo

C:\Users\Administrator>C:\Users\Administrator\AppData\Local\Programs\Python\Python37\python.exe  D:\00wkspc\bpm.py
112.34714673913044

Code desc

import librosa
import numpy as np
yy ,sr = librosa.load('xx.mp3')
onset_env = librosa.onset.onset_strength(y, sr=sr, hop_length=512, aggregate=np.median)
tempo, _ = librosa.beat.beat_track(onset_envelope=onset_env, sr=sr)
tempo就是你们要的bpm



>>> # Load a wav file
>>> y, sr = librosa.load('./beat.wav')
>>> y
array([  0.00000000e+00,   0.00000000e+00,   0.00000000e+00, ...,
         8.12290182e-06,   1.34394732e-05,   0.00000000e+00], dtype=float32)
>>> sr
22050
Librosa默认的采样率是22050，如果需要读取原始采样率，需要设定参数sr=None:
--------------------- 
 可见，'beat.wav'的原始采样率为44100。如果需要重采样，只需要将采样率参数sr设定为你需要的值：



ref
(9+条消息)音频处理库—librosa的安装与使用 - z小白的博客 - CSDN博客.html
