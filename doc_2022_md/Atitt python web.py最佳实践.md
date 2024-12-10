Atitt python web.py最佳实践

Url 与class 映射
必须要十个模块，不能直接单独的class，不然找不到控制器model

    #you yva
    #  
    from fld.editf import *
    tasksCls2.m()
   # exit()
    url2 = urls + ('/xxx', 'fld.editf.tasksCls2','/edit','fld.editf.editCls','/staticx/(.*)','fld.editf.staticxCls')
    print(url2)
    print("start server...")


获取url参水参数
 http://localhost:8080/edit?id=1

  web_ipt = web.input()
        print(web_ipt)
        print(web_ipt.id)
        print(type(web_ipt.id))
        sql='select * from  table_article where id='+str(int(web_ipt.id))

读取数据库
def query(db,sql):
    import sqlite3
    import os
    import sys

    # conn = sqlite3.connect('%s/../db_test')
    print(os.getcwd())
    print(sys.path[0])
    conn = sqlite3.connect(sys.path[0]+'/../db_test')
    #D:\0src\acbo_api\dev\src main scrpt  boot path

    print ("数据库打开成功")
    c = conn.cursor()
    print ("数据库打开成功")

    cursor = c.execute(sql)
    results = cursor.fetchall()
    # print(results)
    print('000000000000000000000000000')
    # for item in results:
    #     print(item)

    print(cursor)
    num_fields = len(cursor.description)
    field_names = [i[0] for i in cursor.description]
    
    print(field_names)
return results,field_names



  (results,field_names)=query('',sql)
        print(results[0])


输出到模板 ，输出变量


  render=  web.template.frender(os.path.dirname(__file__)+"/editor.html"  )
        tit=results[0][field_names.index('name')]
        art={};
        art['id']=results[0][field_names.index('id')]
        return render(results,field_names,tit,results[0][field_names.index('text_content')],art);


Htmlx
$def with (rs,flds,tit,con,art)

<p style="display:none">
    $rs
    $flds
    $art
</p>
<p>
    <input value="$tit" / >
    <p></p>
    <textarea name="content1" id="w3review" name="w3review" rows="25" cols="200">
        $con
        </textarea>
    
</p>

