Atitit springboot 上传与下载总结

上传

	@RequestMapping(value = "/up", method = RequestMethod.POST)
	public void testUploadFile2(@RequestParam MultipartFile file, @RequestParam String saveDir) throws IOException {
      //保存文件
		file.transferTo(new File(saveDir + "\\" + file.getOriginalFilename()));

	}


下载

    
    function down()
    {
    	window.location="http://localhost:8080/down?saveDir="+document.getElementById("saveDir").value;
    }

	@RequestMapping("/down")
	public void home(@RequestParam String saveDir, HttpServletResponse response) throws IOException {
		File dir = new File(saveDir);
		File[] fs = dir.listFiles();
		Random rand = new Random();
		int i = rand.nextInt(fs.length - 1); // 生成0-100以内的随机数
		File f = fs[i];	 
		response.setContentType("application/octet-stream");		 
		response.addHeader("Content-Disposition", "attachment;fileName=" + f.getName());// 设置文件名
		// 输出到下载刘
		IOUtils.copy(new FileInputStream(f), response.getOutputStream());
		response.flushBuffer();

	}
