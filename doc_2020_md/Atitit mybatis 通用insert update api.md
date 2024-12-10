Atitit mybatis 通用insert update api
Prj 

@SuppressWarnings("all")
public class MybatisAdvUtil {

  		String tabname = "football_odds_t";

		Map kv_frmNet = Maps.newLinkedHashMap();
		kv_frmNet.put("id", 11);
 		kv_frmNet.put("real_time_score", "vv");
		
		
		
		Map m_intoMybatis = getMap_intoMbts(conn, kv_frmNet, tabname);
		


		System.out.println(JSON.toJSONString(m_intoMybatis, true));
		System.out.println(conn.update(sttID, m_intoMybatis));



	public static Map getMap_intoMbts(SqlSession conn, Map kv_frmNet, String tabname) throws Exception {
		Map m_intoMybatis = Maps.newLinkedHashMap();
	
		m_intoMybatis.put("tab", tabname);
		m_intoMybatis.put("objFrmNet", kv_frmNet);

		m_intoMybatis.put("cols", getColsFrom_objFrmNet(kv_frmNet));
		String vals_spel_placehodler = "vals_spel_placehodler";
		m_intoMybatis.put(vals_spel_placehodler, getvals_spel_placehodler(m_intoMybatis.get("cols")));
		String val_warped_sqlValFmt = "val_warped_sqlValFmt";
		m_intoMybatis.put(val_warped_sqlValFmt, vals_warpedgene(tabname, kv_frmNet, conn));
		m_intoMybatis.put("vals", QlSpelUtil.parse(m_intoMybatis.get(vals_spel_placehodler).toString(),
				(Map) m_intoMybatis.get(val_warped_sqlValFmt)));
		return m_intoMybatis;
	}


	<update id="insert_into_tabs" parameterType="Map">
		insert into ${tab}( ${cols})values( ${vals})
	</update>


	@Insert(" insert into ${tab}( ${cols})values( ${vals}) ")
	public int insert(Map m);



{
	"tab":"football_odds_t",
	"objFrmNet":{
		"id":11,
		"match_id":12,
		"real_time_score":"vv",
		"create_time":"2020-04-06 06:19:01",
		"delete_flag":0
	},
	"cols":"id,match_id,real_time_score,create_time,delete_flag",
	"vals_spel_placehodler":"#{[id]},#{[match_id]},#{[real_time_score]},#{[create_time]},#{[delete_flag]}",
	"val_warped_sqlValFmt":{
		"create_time":"'2020-04-06 06:19:01'",
		"match_id":"12",
		"real_time_score":"'vv'",
		"id":"11",
		"delete_flag":"'0'"
	},
	"vals":"11,12,'vv','2020-04-06 06:19:01','0'"
}
==>  Preparing: insert into football_odds_t( id,match_id,real_time_score,create_time,delete_flag)values( 11,12,'vv','2020-04-06 06:19:01','0') 
==> Parameters: 
<==    Updates: 1
