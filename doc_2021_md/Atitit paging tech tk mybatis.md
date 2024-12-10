Atitit paging tech tk mybatis

		//Page{count=true, pageNum=1, pageSize=10, startRow=0, endRow=10, total=0, pages=0, countSignal=true, orderBy='null', orderByOnly=false, reasonable=false, pageSizeZero=false}
	
    // trans ret data fmt
function responseHandlerRetDataFmt(res){

    return {"rows":res.list,"total":res.total};  


     
}

public Object ajaxBudanList(HttpServletRequest req, HttpServletResponse res ) {
		
		   res.setHeader("Access-Control-Allow-Origin", "*");
	//	List selectAll = eos.selectAll();
		Example example = new Example(ErrorOrder.class);
		//where
		if(StringUtils.isNotBlank(req.getParameter("searchText")))
			example.createCriteria().andLike("orderNumber",  req.getParameter("searchText"));
		
		
		example.setOrderByClause("operation_Time desc");
		
	//	example.s
		//searchText
		// 分页
		try {
			 PageHelper.startPage(Integer.parseInt(  req.getParameter("pageIndex")), Integer.parseInt(req.getParameter("pageSize"))); // 每次查询20条
		} catch (Exception e) {
			PageHelper.startPage(   1,99); // 每次查询20条
		}
       
//		Map m=Maps.newHashMap();m.put("pk", 111);
//		List li=Lists.newArrayList();li.add(m);
//		li.add(new HashMap() {{
//		this.put("pk", 222);
//		}});
//		li.add(new HashMap() {{
//			this.put("pk", 33);
//			}});
//		li.add(new HashMap() {{
//			this.put("pk", 44);
//			}});
//		 
//		return li;
	//	Page<E>
	 List selectByExample = eos.selectByExample(example);
	 Page p=(Page) selectByExample;
	return  p.toPageInfo();
	}
