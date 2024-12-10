Atitit 封装的艺术     

规范是不暴露特有的api

比如遍历excel
List<Map> li = Lists.newArrayList();
		String filePath = "C:\\Users\\attilax\\Documents\\lyricsWords4.txt700song.xlsx";
  

	excelUtil2007ver.trave_2007fmt(filePath, "coreword", new Consumer<CellAti>() {

			@Override
			public void accept(CellAti CellAti1) {

				if (CellAti1.rowIndex > 300)
					throw new BreakException();
				Map<Integer, Object> row_map = getLiIdex(CellAti1.rowIndex, li);

				row_map.put(CellAti1.cellIndex, CellAti1.val);
				// String colval = cell.getStringCellValue();

			}
		});


方便理解，提升可读性


Atitit 提升可读性  数据结构特殊化专用api  比较通用的对象

不够通用的对象还是使用map吧不然类库过多了，工作量过大

