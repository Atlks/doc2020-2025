Atitit xml xpath以及mybatis xml mapper脱机解析




	String xpath = "/update";
		// jdom
		SAXBuilder sb = new SAXBuilder();
		org.jdom.Document doc = sb.build(xmlf);
	 
		Element root = (Element) doc.getRootElement();
		
	
 parseStt(String id, Element root)
	private static String parseStt(String id, Element root) throws Exception {
		String pathFltById = "/mapper/*[@id='{0}']";
	//	pathFltById = MessageFormat.format(pathFltById, id );
		pathFltById=pathFltById.replaceAll("\\{0\\}", id);
		Object sql = XPath.selectNodes(root, pathFltById);
		Element stt = (Element) XPath.selectSingleNode(root, pathFltById);
		List li = stt.getContent();
	//	System.out.println();
		return parseSttContestList(li, root);
	}
parseSttContestList(List li, Element root)
	private static String parseSttContestList(List li, Element root) throws Exception {

		List li_rzt = (List) li.stream().map(o -> {
			if (o instanceof Text) {
				return ((Text) o).getValue();
			}
			if (o instanceof Element) {
				Element o2 = (Element) o;
				if (o2.getName() == "include") {
					String refid = o2.getAttribute("refid").getValue();
					return ParseInclude(refid, root);
				}
			}
//			  return 0;
			return "";

		}).collect(Collectors.toList());
		return Joiner.on(" ").join(li_rzt);
	}
ParseInclude(String refid, Element root) 
	private static Object ParseInclude(String refid, Element root) {
		try {
			// MessageFormat.format("我是{0}，我来自{1}", "中国人", "中国");
			String pathFltById = "/mapper/sql[@id='{0}']/text()";
			pathFltById=pathFltById.replaceAll("\\{0\\}", refid);
		//	pathFltById = MessageFormat.format(pathFltById, refid, "中国");
			//msg fomt cant use in xpath...bcz single quore is missed..
			Text sql;

			sql = (Text) XPath.selectSingleNode(root, pathFltById);
			return sql.getValue();
		} catch (JDOMException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
			throw new RuntimeException(e);
		}

	}

