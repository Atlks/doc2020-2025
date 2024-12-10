Atitit enhance readable topic--code block  代码块 可读性

原理，使用『『』』java初始化块，包裹在一个对象里面初始化


public static long toSecs(String time) {
		
		//convert hsm mode
		time=time.replaceAll("''", "S");
		time=time.replaceAll("'", "M");
		String t=time;
	    //
		Map m=new HashMap() {{ // parse time str fmt 
			int indexOfMill = t.indexOf("S");
			String timeNoMillsec=t.substring(0,indexOfMill+1);	
			if(indexOfMill==-1) //excpt
				timeNoMillsec=t;
			put("timeNoMillsec",timeNoMillsec);
			String mill=t.substring(indexOfMill+1);
			put("mill",timeNoMillsec);
			
		}};
	
		String timeNoMillsec="PT"+m.get("timeNoMillsec").toString();
		System.out.println(timeNoMillsec);
		//"P1DT1H10M10.5S"
		Duration fromChar1 = Duration.parse(timeNoMillsec);
		
		//process millsec
		try {
			
			fromChar1.plusMillis(Long.parseLong(m.get("mill").toString()));
		} catch (Exception e) {
			System.out.println(e);
		}
		
	 
		return fromChar1.getSeconds();
	}

