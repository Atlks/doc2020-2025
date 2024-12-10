Atitit 上传文件（图片 视频 音乐 其他文件  流程


界面  multipart
<form action="http://localhost:8080/uppic" method="post" enctype="multipart/form-data" name="form1" id="form1">
  <label for="fileField">File:</label>
  <input type="file" name="file" id="file">
 
  <input type="submit" name="submit" id="submit" value="提交">
</form>

Action  指明提交路径
 enctype="multipart/form-data"    指明编码
文件选择控件    <input type="file"



Springboot的实现 接收文件MultipartHttpServletRequest 
MultipartHttpServletRequest multiReq


        //得到上传文件的steam
	        FileInputStream fsInputStream=(FileInputStream) multiReq.getFile("file").getInputStream();  
	        
	        //设置输出文件output stream
	        FileOutputStream fileOutputStream = new FileOutputStream(new File("d://upload999.jpg"));
	        
	        //从上传文件的steam  copy  到  输出文件output 
			StreamUtils.copy(fsInputStream, fileOutputStream); 
			
			//关闭流
			fileOutputStream.close();



