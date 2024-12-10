Atitit 词云 字符云 的艺术


http://echarts.baidu.com/echarts2/doc/example/wordCloud.html





 {
                name: "爱",
                value: 1155.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "我们",
                value: 967.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "爱情",
                value: 417.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "自己",
                value: 337.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "知道",
                value: 332.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "永远",
                value: 297.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "如果",
                value: 288.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "爱你",
                value: 287.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "快乐",
                value: 245.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "情",
                value: 244.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "所有",
                value: 223.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "曾经",
                value: 222.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "一起",
                value: 215.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "眼泪",
                value: 213.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "幸福",
                value: 212.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "梦",
                value: 210.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "寂寞",
                value: 200.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "不要",
                value: 199.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "心里",
                value: 199.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "是否",
                value: 194.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "这样",
                value: 191.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "和你",
                value: 189.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "不会",
                value: 182.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "真的",
                value: 182.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "爱我",
                value: 178.0,
                itemStyle: createRandomItemStyle()
            }               ,  {
                name: "为何",
                value: 173.0,
                itemStyle: createRandomItemStyle()
            }         


/FulltxtLucenePrj/src/com/attilax/visual/chartcloud.java

package com.attilax.visual;

import java.io.File;
import java.io.IOException;
import java.util.LinkedHashMap;
import java.util.List;
import java.util.Map;
import java.util.function.Consumer;

import org.apache.commons.io.FileUtils;
import org.apache.poi.xssf.usermodel.XSSFCell;
import org.apache.poi.xssf.usermodel.XSSFRow;
import org.apache.poi.xssf.usermodel.XSSFSheet;

import com.attilax.collection.mapBuilder;
import com.attilax.io.BreakException;
import com.google.common.base.Joiner;
import com.google.common.collect.Lists;

import officefile.excelUtil;
import officefile.excelUtil2007ver;

public class chartcloud {

	public static void main(String[] args) throws IOException {
		String tmp = "C:\\0wkspc\\FulltxtLucenePrj\\src\\com\\attilax\\visual\\baiduWordcloudJsontmplt.txt";
		String t = FileUtils.readFileToString(new File(tmp));

		String filePath = "C:\\Users\\attilax\\Documents\\lyricsWords4.txt700song.xlsx";
		// excelUtil2007ver.trave_2007fmt(filePath, "coreword", new
		// Consumer<Object>() {
		//
		// @Override
		// public void accept(Object mx) {
		// Map m=(Map) mx;
		// XSSFCell cell =(XSSFCell) m.get("cell");
		// int rowindex=Integer.parseInt(m.get("rowIndex").toString());
		// int cellIndex=Integer.parseInt(m.get("cellIndex").toString());
		// if(rowindex>300)
		// throw new BreakException();
		// String colval = cell.getStringCellValue();
		//
		// }
		// });
		List<String> li = Lists.newArrayList();
		XSSFSheet sheet = excelUtil2007ver.getsheet(filePath, "coreword");
		for (int rowNum = 0; rowNum <= sheet.getLastRowNum(); rowNum++) {
			if (rowNum > 250)
				break;
			XSSFRow row_cur = sheet.getRow(rowNum);
			Map<Integer, Object> row_map = new LinkedHashMap<Integer, Object>();
			if (row_cur == null)
				continue;
			for (int cellNum_index = row_cur.getFirstCellNum(); cellNum_index < row_cur
					.getLastCellNum(); cellNum_index++) {
				XSSFCell cell = row_cur.getCell(cellNum_index);

				if (cellNum_index == 0)
					row_map.put(cellNum_index, cell.getStringCellValue());
				if (cellNum_index == 1)
					row_map.put(cellNum_index, cell.getNumericCellValue());

			} // trave row finish

			try {
				String t2 = t.replaceAll("@word@", row_map.get(0).toString()).replaceAll("@val@",
						row_map.get(1).toString());
				li.add(t2);
			} catch (Exception e) {
				// TODO: handle exception
			}

		} // trave tab finish

		System.out.println(Joiner.on(",").join(li));
		// String t_word=FileUtils.readFileToString(new File(word));

	}

}

