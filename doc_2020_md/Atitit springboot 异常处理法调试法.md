Atitit springboot 异常处理法调试法

默认不显示具体错误
1、返回错误页面配置（不推荐
如果此时配置有错误页，那么这个时候错误会统一跳转到 500 所在的路径上进行错误的显示，但是如果说现在希望能够显示 出错误更加详细的内容呢？

//@ControllerAdvice// 作为一个控制层的切面处理@RestControllerAdvice




 所以这个时候可以单独定义一个页面进行错误的信息显示处理，而这个页面，可以定义在“src/main/view/templates/error.html”， 这个页面里面要求可以输出一些信息；

@ControllerAdvicepublic class GlobalExceptionHandler {
    @ExceptionHandler(Exception.class) // 所有的异常都是Exception子类
    public ModelAndView defaultErrorHandler(HttpServletRequest request, Exception e) { // 出现异常之后会跳转到此方法
        ModelAndView mav = new ModelAndView("error"); // 设置跳转路径
        mav.addObject("exception", e); // 将异常对象传递过去
        mav.addObject("url", request.getRequestURL()); // 获得请求的路径
        return mav;
    }
}

2、返回Rest错误信息（推荐

package cn.study.microboot.advice;
import javax.servlet.http.HttpServletRequest;
import org.springframework.web.bind.annotation.ExceptionHandler;import org.springframework.web.bind.annotation.RestControllerAdvice;
//@ControllerAdvice// 作为一个控制层的切面处理@RestControllerAdvicepublic class GlobalExceptionHandler {
    public static final String DEFAULT_ERROR_VIEW = "error"; // 定义错误显示页，error.html
    @ExceptionHandler(Exception.class) // 所有的异常都是Exception子类
    public Object defaultErrorHandler(HttpServletRequest request,Exception e) {
        class ErrorInfo {
     ErrorInfo info = new ErrorInfo() ;
        info.setCode(100);     // 标记一个错误信息类型        info.setMessage(e.getMessage());
        info.setUrl(request.getRequestURL().toString());
        return info ;
    }


springboot系列六、springboot配置错误页面及全局异常 - 小人物的奋斗 - 博客园.html
