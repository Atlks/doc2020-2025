Atitit football biz parse doc 足球赛事业务文档


base



Football.Live.Match_list	足球赛程赛果
2	Football.Analysis.Match_detail	足球比赛详情	返回具体一场比赛的比赛环境、文字

Match_analysis	足球分析数据	
Match_lineup	足球比赛阵容
Match_detail_live	足球实时统计
.Match_live	足球即时比分

接口服务	接口名称	更多说明
1	Football.Analysis.Match_analysis	足球分析数据	返回数据多为历史数据，变化不频繁
2	Football.Analysis.Match_detail	足球比赛详情	返回具体一场比赛的比赛环境、文字直播、技术统计信息；
3	Football.Analysis.Match_lineup	足球比赛阵容	根据“赛程赛果接口”中“是否有阵容”字段来判断是否开启该比赛的阵容接口读取

接口服务	接口名称	更多说明
1	Football.Live.Match_detail_live	足球实时统计	返回最近240分钟内的比赛事件和技术统计数据
2	Football.Live.Match_list	足球赛程赛果	返回所请求日期（限制：前后30天）的全量赛程赛果数据，及赛程中比赛涉及到的球队及赛事信息；
3	Football.Live.Match_live	足球即时比分	返回实时变动的即时数据信息,无即时数据变动的比赛不返回




