Atitit 文件上传问题file upload prblm


为什么用php上传mp3文件就获取不到临时文件名 
为什么用php上传mp3文件就获取不到临时文件名echo$_FILES['userfile']['tmp_name']；这个语句没有输出东西。上传.doc文件都有。这是什么原因。请高手指点。我都改成的100M在php.ini里... 展开 
 我来答 
分享
举报 
1个回答 
#热议# 什么样的人容易遇上渣男？ 
laputa7 
2009-07-26 · TA获得超过268个赞 
关注 
php默认的上传文件大小限制是2M，在php.ini里可以修改，你传的MP3文件估计是超过2M了，没有传上去，所以取不到临时文件名 
那用echo $_FILES['userfile']['error']；看看文件上传错误消息 


name' => string 'IMG_20200822_164855.jpg' (length=23)
  'type' => string '' (length=0)
  'tmp_name' => string '' (length=0)
  'error' => int 1
  'size' => int 0


检查配置

 file_uploads = On

 upload_tmp_dir ="c:/wamp/tmp"

 upload_max_filesize = 20M

; Maximum number of files that can be uploaded via a single request
max_file_uploads = 20
