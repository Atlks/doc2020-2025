Atitit springboot fix 2


http://localhost:8081/hello/name11?t=jsonstr


package com.attilax.oplog.util;  
  
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.hibernate.validator.constraints.URL;
import org.springframework.boot.autoconfigure.EnableAutoConfiguration;  
import org.springframework.web.bind.annotation.PathVariable;  
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
@EnableAutoConfiguration  
public class RestUtil {  
      
    @RequestMapping("/")  
    String home() {  
        return "Hello World 22!";  
    }  
      
    @RequestMapping("/hello/{myName}")  
    String index(@PathVariable String myName,HttpServletRequest request,HttpServletResponse response) {  
        return "Hello "+myName+"!!!"+request.getParameter("t");  
    }  
}  


一、spring mvc的获取参数和传递参数 - CSDN博客.html
