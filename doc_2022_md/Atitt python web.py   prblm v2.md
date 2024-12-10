Atitt python web.py   prblm

 GET /" - 405 Method Not Allowed

27.0.0.1:52822 - - [19/Mar/2013 20:44:18] "HTTP/1.1 GET /" - 405 Method Not Allowed


web.py cannot find controller class, you should either change urls.py:
or import index class in webstart.py

e. you should either map url directly to module_name.class_name or import class_name from module_name so class_name is available in global scope.


******* e: 'NoneType' object is not callable <class 'TypeError'>
### Error calling class <class 'fld.editf.editCls'>
D:\0src\acbo_api\dev\src\fld\editf.py : Traceback (most recent call last):
  File "D:\0src\acbo_api\dep\Windows\3.9\lib\web\application.py", line 612, in handle_class
  File "D:\0src\acbo_api\dev\src\fld\editf.py", line 19, in GET
    return render.editor()
TypeError: 'NoneType' object is not callable

应该是路径问题
       render=  web.template.frender(os.path.dirname(__file__)+"/editor.html"  )
        return render();



