

Atitit 得到mybatis 实际 sql

1.1. 使用mybatis工具提供的，只能出现问号一大堆不行	1
1.2. 配置log 打印sql依然不行，里面有问号。。	4
1.3. 配置pgsdql sql日志只能抓取到navicate的不能mybatis的。。	4
1.4. 使用序列化保存的map调用mybatis，然后解析参数，替换ok	4

使用mybatis工具提供的，只能出现问号一大堆不行

     String sql = this.getSqlSession().getConfiguration().getMappedStatement("CliSchemeDefine.adviceSousuo_kucui").getBoundSql(map).getSql();
      logger.info(sql);	


  public List adviceSousuo_kucui(HashMap map) throws Exception
    {
    //	SqlSessionFactory.getConfiguration()
      String sql = this.getSqlSession().getConfiguration().getMappedStatement("CliSchemeDefine.adviceSousuo_kucui").getBoundSql(map).getSql();
      logger.info(sql);	
      return this.queryFo



14:10:25.821 [main] DEBUG java.sql.PreparedStatement - ==>  Executing: with kbmbbj as ( select a.BBY01,a.BCK01A,a.BCK01B from BBJ1 a where ? = '0' and a.BCK01A = ? and exists(select *from baz1 b where b.BCK01 = a.BCK01B and ? = (b.ACF01 & ?) ) ) SELECT distinct e.BDA01, e.BDA02, f.AAS02, a.BBX01, a.BDO01, d.BBY04 as BBX04, a.BBX05 , d.BBY05||case when bag16='' then '('||bag16||')' else '' end BBY05 , a.BDG02 , (COALESCE(b.BAP02,'')||'、'||COALESCE(c.BAG11,'')||'、'|| case when COALESCE(f2.BHJ01,0)=0 then '' else f2.BHJ02 end) as NBBX13 , d.BBY06, d.BBE02, d.BBY01, c.BAG27 , CASE WHEN ?=1 THEN c.BDG02A ELSE c.BDG02B END AS NUnit , case when ?='2' then GetDrugPrice(h1.BCK01 , d.BBY01 , ? , ?) else CASE WHEN ?=1 THEN d.BBY25*c.BAG05 ELSE d.BBY25*c.BAG07 END end AS Price , CASE WHEN ? = 1 THEN COALESCE(h1.LSQty,0)/c.BAG05 ELSE COALESCE(h1.LSQty,0)/c.BAG07 END AS amount ,h2.BCK03, f1.BCG02,d.BBY29 ,f.AAS07,COALESCE(h1.BCK01,0) BCK01,d.BBY44,c.bag03,c.bag05 FROM BBX1 a JOIN BBT1 b ON a.BBX01 = b.BBX01 JOIN BAG1 c ON b.BBX01 = c.BBX01 JOIN BBY1 d ON c.BBY01 = d.BBY01 JOIN BDA1 e ON a.BDA01 = e.BDA01 JOIN kbmbbj h ON d.BBY01 = h.BBY01 left JOIN V_DPK6 h1 ON h.BBY01 = h1.BBY01 AND h.BCK01B = h1.BCK01 and ? = (h1.ACF01 & ?) left join BCK1 h2 on h2.BCK01 = h1.BCK01 LEFT JOIN AAS1 f ON f.AAS01 = d.AAS01 left join BCG1 f1 on f1.BCG01 = d.BCG01 left join BHJ1 f2 on f2.BHJ01 = b.BBT08 WHERE ? ='0' and ((? = '1') or (? <> '1' and ((? <>1 and COALESCE(h1.LSQty,0)>0) or ?=1))) and ? = (d.ACF01 & ?) And a.BDA01<'4' And d.BBY31 > now() AND e.BEH01=? and h2.corporationid = ? and (d.BBY04 LIKE ? OR d.BBY44 LIKE ? OR (EXISTS(SELECT g.* FROM BDK1 g WHERE g.BBX01 = a.BBX01 AND (g.BDK03 LIKE ? OR g.ABBRP LIKE ? OR g.ABBRW LIKE ?)))) and (d.bdn01!='3' or (d.bdn01='3' and h1.bck01=?)) UNION ALL SELECT e.BDA01, e.BDA02, f.AAS02, a.BBX01, a.BDO01, d.BBY04 as BBX04, a.BBX05 , d.BBY05||case when bag16>'' then '('||bag16||')' else '' end BBY05, a.BDG02 , (COALESCE(b.BAP02,'')||'、'||COALESCE(c.BAG11,'')||'、'|| case when COALESCE(f2.BHJ01,0)=0 then '' else f2.BHJ02 end) as NBBX13 , d.BBY06, d.BBE02, d.BBY01, c.BAG27 , CASE WHEN ?=1 THEN c.BDG02A ELSE c.BDG02B END AS NUnit , case when ?='2' then GetDrugPrice(h1.BCK01 , d.BBY01 , ? , ?) else CASE WHEN ?=1 THEN d.BBY25*c.BAG05 ELSE d.BBY25*c.BAG07 END end AS Price , CASE WHEN ? = 1 THEN COALESCE(h1.LSQty,0)/c.BAG05 ELSE COALESCE(h1.LSQty,0)/c.BAG07 END AS amount ,case when COALESCE(h1.BCK01,0)=0 then '' else h2.BCK03 end BCK03, f1.BCG02,d.BBY29 ,f.AAS07,COALESCE(h1.BCK01,0) BCK01,d.BBY44 ,c.bag03,c.bag05 FROM BBX1 a JOIN BBT1 b ON a.BBX01 = b.BBX01 JOIN BAG1 c ON b.BBX01 = c.BBX01 JOIN BBY1 d ON c.BBY01 = d.BBY01 and d.ACF01 in (1,3) AND a.BDA01<'4' And d.BBY31 > now() and (d.BBY04 LIKE ? OR d.BBY44 LIKE ? OR (EXISTS(SELECT g.* FROM BDK1 g WHERE g.BBX01 = a.BBX01 AND (g.BDK03 LIKE ? OR g.ABBRP LIKE ? OR g.ABBRW LIKE ?)))) JOIN BDA1 e ON a.BDA01 = e.BDA01 AND e.BEH01=? left JOIN V_DPK6 h1 ON h1.BBY01 = d.BBY01 and (? <> '3' or (? = '3' and h1.BCK01=0)) and ((? = '1') or (? <> '1' and ((? <>1 and COALESCE(h1.LSQty,0)>0) or ?=1))) and (d.bdn01!='3' or (d.bdn01='3' and h1.bck01=?)) left join BCK1 h2 on h2.BCK01 = h1.BCK01 and h2.corporationid = ? LEFT JOIN AAS1 f ON f.AAS01 = d.AAS01 left join BCG1 f1 on f1.BCG01 = d.BCG01 left join BHJ1 f2 on f2.BHJ01 = b.BBT08 WHERE ? <> '0' union all SELECT distinct e.BDA01, e.BDA02, f.AAS02, a.BBX01, a.BDO01, d.BBY04 as BBX04, d.BBY05 BBX05, d.BBY05 , a.BDG02, '' NBBX13, d.BBY06, d.BBE02, d.BBY01, 0 BAG27, d.BBY08 NUnit ,case when ?='2' then GetBBY1Price(d.BBY01,?) else d.BBY25 end price , g.lsqty AS amount,'' BCK03, h.BCG02,d.BBY29,f.AAS07,0 ,d.BBY44,1,1 FROM BBX1 a JOIN BCT1 c ON c.BBX01 = a.BBX01 and c.BCT33 = 1 JOIN BBY1 d ON d.BBY01 = c.BBY01 and d.ACF01 in (1,3) AND d.BBY31 > now() and (c.bct40=1 or c.bct40 is null) and (d.BBY04 LIKE ? OR d.BBY44 LIKE ? OR (EXISTS(SELECT g.* FROM BCL1 g WHERE g.BBY01 = d.BBY01 AND (g.BCL03 LIKE ? OR g.ABBRP LIKE ? OR g.ABBRW LIKE ?)))) JOIN BDA1 e ON e.BDA01 = a.BDA01 and e.BEH01=? AND e.BDA01 in ('4','M') LEFT JOIN AAS1 f ON f.AAS01 = d.AAS01 left join BCG1 h on h.BCG01 = d.BCG01 join v_mdk6 g on d.bby01 = g.bby01 and g.lsqty>0 and g.acf01 in (1,3) join blo1 k on k.bby01 = g.bby01 and k.bck01a= ? and k.bck01b = g.bck01 left join bck1 m on m.bck01 = k.bck01b and m.corporationid = ? union all SELECT distinct e.BDA01, e.BDA02, f.AAS02, a.BBX01, a.BDO01, d.BBY04 as BBX04, d.BBY05 BBX05, d.BBY05 , a.BDG02, '' NBBX13, d.BBY06, d.BBE02, d.BBY01, 0 BAG27, d.BBY08 NUnit ,case when ?='2' then GetBBY1Price(d.BBY01,?) else d.BBY25 end price , 1 AS amount,'' BCK03, h.BCG02,d.BBY29,f.AAS07,0 bck01,d.BBY44,1,1 FROM BBX1 a JOIN BCT1 c ON c.BBX01 = a.BBX01 and c.BCT33 = 1 and (c.bct40=0) JOIN BBY1 d ON d.BBY01 = c.BBY01 and d.ACF01 in (1,3) AND d.BBY31 > now() and (d.BBY04 LIKE ? OR d.BBY44 LIKE ? OR (EXISTS(SELECT g.* FROM BCL1 g WHERE g.BBY01 = d.BBY01 AND (g.BCL03 LIKE ? OR g.ABBRP LIKE ? OR g.ABBRW LIKE ?)))) JOIN BDA1 e ON e.BDA01 = a.BDA01 AND e.BEH01=? AND e.BDA01 in ('4','M') LEFT JOIN AAS1 f ON f.AAS01 = d.AAS01 left join BCG1 h on h.BCG01 = d.BCG01 join blo1 k on k.bby01 = d.bby01 left join bck1 m on m.bck01 = k.bck01b and K.bck01a = ?::int and m.corporationid = ? UNION ALL SELECT e.BDA01,e.BDA02,f.AAS02 ,a.BBX01,a.BDO01,a.BBX04,a.BBX05,a.BBX05,a.BDG02 ,CASE WHEN a.BDA01 IN ('8','9') THEN a.BBX06 WHEN a.BDA01 = 'T' THEN a1.AAF02 WHEN a.BDA01 = 'E' THEN a2.BBC02 WHEN a.BDA01 = 'L' THEN a3.AAV02 WHEN a.BDA01 = 'S' THEN a4.ACH02 WHEN a.BDA01 = 'A' THEN a5.ACI02 WHEN a.BDA01 = 'N' THEN a6.AAG02 WHEN a.BDA01 = 'Z' THEN a7.AAP02 ELSE NULL END NBBX13 ,a.BBX06, NULL AS BBE02,a.BBX01,a.BBX12,a.BDG02 AS NUnit ,case when ?='2' then GetBBX1Price(a.BBX01,?) else vb.Price end price,NULL ,'','' ,a.BBX29 ,f.AAS07,0,A.BBX36,1,1 FROM BBX1 a JOIN BDA1 e ON a.BDA01 = e.BDA01 AND e.BEH01=? LEFT JOIN V_BDU vb ON a.BBX01 = vb.BBX01 LEFT JOIN AAS1 f ON f.AAS01 = a.AAS01 LEFT JOIN AAF1 a1 ON a.BDA01='T' AND a.BBX13=a1.AAF01 LEFT JOIN BBC1 a2 ON a.BDA01='E' AND a.BBX13=a2.BBC01 LEFT JOIN AAV1 a3 ON a.BDA01='L' AND a.BBX13=a3.AAV01 LEFT JOIN ACH1 a4 ON a.BDA01='S' AND a.bbx13=a4.ACH01 LEFT JOIN ACI1 a5 ON a.BDA01='A' AND cast(a.BBX01 as varchar)=a5.ACI01 LEFT JOIN AAP1 a7 ON a.BDA01='Z' AND a.BBX13=a7.AAP01 LEFT JOIN AAG1 a6 ON a.BDA01='N' AND a.BBX13=cast(a6.AAG01 as varchar(10)) WHERE a.BDA01 >'7' and a.BDA01 <> 'M' and ((a.BBX11 =1)or(a.BBX11 = 0 and a.BBX12 in (1,3,4))) AND a.BBX09 IN (0,?) And a.BBX25 > now() and ((a.BBX30 = 0)or(a.BBX30 = 1 and exists(select * from BIP1 c2 where c2.BBX01 = a.BBX01 and c2.BCK01 = ?))) and ((a.BBX46 = 0)or(a.BBX46 = 1 and exists(select * from BMP1 c3 where c3.BBX01 = a.BBX01 and c3.BDP02 = ?))) AND ((a.BDA01 <> '9')OR((a.BDA01='9') AND ((a.BBX15=0 and a.BCE01 = ?) or a.BBX15=2 or (a.BBX15=1 and exists(select c.* from BAR1 c where a.BBX01=c.BBX01 and c.BCK01 =?))))) AND ? = (a.ACF01 & ?) and (a.BBX04 LIKE ? OR a.bbx36 LIKE ? OR (EXISTS(SELECT g.* FROM BDK1 g WHERE g.BBX01 = a.BBX01 AND (g.BDK03 LIKE ? OR g.ABBRP LIKE ? OR g.ABBRW LIKE ?)))) limit 10 offset ? 
14:10:25.822 [main] DEBUG java.sql.PreparedStatement - ==> Parameters: null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null
0

配置log 打印sql依然不行，里面有问号。。

配置pgsdql sql日志只能抓取到navicate的不能mybatis的。。

使用序列化保存的map调用mybatis，然后解析参数，替换ok

package com.cnhis.cloudhealth;

import java.io.File;
import java.io.IOException;
import java.util.Map;
import java.util.Set;

import org.apache.commons.io.FileUtils;

import com.alibaba.fastjson.JSON;
import com.alibaba.fastjson.JSONObject;
 
import com.google.common.collect.Maps;
@SuppressWarnings("all")
public class MybatisUtil {

	public static void main(String[] args) throws IOException {
		String t1="#{11}";
		System.out.println(t1.replace("#{", "aa"));System.out.println(t1.replace("{", "aa"));
		   String sqlid="C:\\qsql\\t.txt";
		   String t=FileUtils.readFileToString(new File(sqlid));
		   String params="{aParam60=0, beh01=1, bbx09=1, vaf58=0, abc02=普通, sqltext=%葡萄糖%, aParamno=0, yiyuanId=-5, bce01=1, acf01=1, aParam1=0, bdp02=自费, offset=0, bckyf=0, bck01=14, aParam106=1}";
		   params="{aParam60=0, beh01=null, bbx09=1, vaf58=0, abc02=普通, sqltext=%葡萄糖%, aParamno=0, yiyuanId=-5, bce01=1, acf01=1, aParam1=0, bdp02=自费, offset=0, bckyf=0, bck01=108, aParam106=1}";
	//	   Map<String,Object> m=getM(params);
		   
		   Map<String,Object> m=(Map) serilizeUtil.serizGetObjFromFile("c:\\logs\\adviceSousuo_kucui_map_8080f6ab-35b1-440f-b1b5-8c1b0ea2de32");
		   
		//   JSONObject jo=JSON.parseObject(params);
		   // Set<Map.Entry<K, V>>
   for (Map.Entry  entry : m.entrySet()) {
	   String key = (String) entry.getKey();
	   key=key.trim();
	System.out.println(key + ":" + entry.getValue());
       
    
	t=  t.replaceAll("\\#\\{"+key+"\\}", getValueByTypeinSql(entry.getValue()));
   }
   System.out.println(t);
   
	}


	private static String getValueByTypeinSql(Object value) {
		if(value.getClass()==String.class)
		return  "'"+value.toString()+"'";
		if(value.getClass()==Integer.class)
		return value.toString();
		throw new RuntimeException("getValueByTypeinSql:: value not jude type");
	}


	private static Map getM(String params) {
		Map m=Maps.newConcurrentMap();
		params=params.substring(1,params.length()-1);  //de start end one char ..openclose char
		String[] entry_arr=params.split(",");
		for (String e : entry_arr) {
			String[] kva=e.split("=");
			
			m.put(kva[0], kva[1]);
		}
		return m;
	}

}


应用程序获取Mybatis中配置的执行SQL - CSDN博客.html
(5 封私信 _ 45 条消息)如何在mybatis中调试查看生成的sql语句？ - 知乎.html
