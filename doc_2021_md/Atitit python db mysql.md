Atitit python db mysql

C:\Users\ATI\OneDrive\prjs hsu6\spdrPy\VisitMovie\spdrKk.py

 
#  pip install requests
 # pip install bs4
  #     pip install pymysql

  #end
#   pip install demjson
  

	
# 	    pip install etree
	#	pymysql
# 	 pip install  lxml
	 
# 		
import string
import urllib.request
from bs4 import BeautifulSoup
import hashlib
import pymysql
import requests
import sdk.mysql
import sdk.encry
import sdk.tools
import  sdk.httpclient
# try:
#     #raise 'someEx'
#     raise Exception("抛出一个异常")
# except Exception as e:
#     print(e)
#     print('eee')
print( '------------start')
var1=5
r=vars() 
print( vars() )
print( '------------end')
#sys.exit()



print (sdk.encry. get_md5('555'))

 # 使用cursor()方法获取操作游标 
db = pymysql.connect("182.16.50.115", "tom_akbar", "123456", "dev_kk_sport")
conn=db




    
#, 'lxml'
#raise 'aa'
 
##----------------get url 
url = "http://kkkq.com/live/"
html=sdk.httpclient.getUrl(url)
Soup = BeautifulSoup(html)
trs= Soup.select('tr') 





for tag_tr in trs:
    
    try:    
        #print(tag_tr)
        tds= tag_tr.select('td')
        mt_type=str(tds[1].string)
        #print(tds[1].string)   #saishimchen
        mt_time=str(tds[2].string)
        home_team=str(tds[3].string)
        直播状态=str(tds[4].string)
        away_team=str(tds[5].string)
       # print(str (saisiMeinchen) +str(time) +str( judui) +str( kadwi))
        
        
        
        # 执行sql语句
       
        
        md5= sdk.encry.get_md5(str (mt_type) +str(mt_time) +str( home_team) +str( away_team)   )    
        sdk.mysql. uniqueIdx("kk_mt_t", "md5key", md5,conn)        
        rel_sql = string.Template("INSERT INTO kk_mt_t(id, mt_type, mt_time, home_team,away_team,md5key,mt_status)values" \
                                "('$id','$mt_type','$mt_time','$home_team','$away_team','$md5','$直播状态')  " )                       
        ##replace  the def vals..beirs if use json mode,,must manual defi  cant auto by var
        rel_sql=rel_sql.safe_substitute(  vars())
        rel_sql=rel_sql.replace('$直播状态',直播状态)
        rel_sql= string.Template(rel_sql)              
        rel_sql=(  rel_sql.safe_substitute( { "id":sdk. tools.generate_id()} )   )
       
        print(rel_sql)
        cursor= sdk.mysql.exeSqlUpdt(rel_sql,conn)    
        print(cursor)  #print(cursor.rowcount)
        #sys.exit()
    except Exception as e:
        print( e)    

  
#print(Soup)
         # rel_sql = f"INSERT INTO kk_mt_t(id, mt_type, mt_time, home_team,away_team,md5key)values" \
        #                         "('{id}','@mt_type@','@mt_time@','@home_team@','@away_team@','@md5key@')  " 
 
 

 
 



import pymysql
def exeSqlQry(sql,conn):
    cursor = conn.cursor()
    # 执行SQL语句
    cursor.execute(sql)
    # 获取所有记录列表
    results = cursor.fetchall()
    return results

def exeSqlUpdt(sql,conn):
    cursor = conn.cursor()
    # 执行SQL语句
    cursor.execute(sql)
    # 获取所有记录列表
    # 提交到数据库执行
    conn.commit()
    return cursor

def uniqueIdx(tab, col, val,conn):
    

    sql = "select * from " + tab + " where " + col + "='" + val + "'";
    rzt = exeSqlQry( sql,conn)
    if ( len(rzt) > 0) :
        # ex = {};
        # ex.sql = sql
        # ex.name = 'uniqueEx';

        raise Exception("抛出一个异常uniqueEx:"+sql)

