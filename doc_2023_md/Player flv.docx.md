Player flv


flv.js 是一个HTML5 Flash视频(FLV)播放器，它通过纯JavaScript编写，没有使用 Flash。它的工作原理是 Flv.js 在 JavaScript 中流式解析 flv 文件流，并实时转封装为 fmp4 ，通过 Media Source Extensions 喂给浏览器。 
它依赖于媒体源扩展 MSE ( Media Source Extensions ） 来工作。它来自 Bilibili 开发和开源。



遇到不能自动播放的情况 原因是包含声音，在没有用户产生交互的情况下是不能自动播放的。 解决方法：给video标签加入<video muted></video> 静音即可
