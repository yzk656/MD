​	

# JDBC

## 第一节课

![image-20221106102231001](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221106102231001.png)

![image-20221106103358103](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221106103358103.png)

## 第一天

![image-20221127234413444](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221127234413444.png)

![image-20221127234942719](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221127234942719.png)

![image-20221127235550802](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221127235550802.png)

![image-20221127235722578](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221127235722578.png)

![image-20221128000202388](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221128000202388.png)

![image-20221128000259332](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221128000259332.png)

1. ascll：只占一个字节

	gbk：字母数字占一个字节，汉字占两个字节

	utf-8：字母数字占一个字节，汉字占三个字节（110xxxxx 10xxxxxx 10xxxxxx）

2. 一致

3. 不会，因为很多字符集都兼容了ascll码

![image-20221128000911916](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221128000911916.png)

![image-20221128001139804](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221128001139804.png)

![image-20221128001325782](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221128001325782.png)

![image-20221128001520914](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221128001520914.png)

![image-20221128001550390](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221128001550390.png)

# Servlet

## 2023-02-03

![image-20230203161932288](https://cdn.jsdelivr.net/gh/yzk656/image/202302031619354.png)

![image-20230203163422451](https://cdn.jsdelivr.net/gh/yzk656/image/202302031634518.png)

![image-20230203163722848](https://cdn.jsdelivr.net/gh/yzk656/image/202302031637903.png)

![image-20230203165840355](https://cdn.jsdelivr.net/gh/yzk656/image/202302031658390.png)

![image-20230203165917593](https://cdn.jsdelivr.net/gh/yzk656/image/202302031659616.png)

## 2023-02-04

![image-20230204121347016](https://cdn.jsdelivr.net/gh/yzk656/image/202302041213088.png)

![image-20230204121430003](https://cdn.jsdelivr.net/gh/yzk656/image/202302041214033.png)

![image-20230204170908413](https://cdn.jsdelivr.net/gh/yzk656/image/202302041709504.png)

![image-20230204171242274](https://cdn.jsdelivr.net/gh/yzk656/image/202302041712304.png)

![image-20230204171521459](https://cdn.jsdelivr.net/gh/yzk656/image/202302041715490.png)

![image-20230204173459294](https://cdn.jsdelivr.net/gh/yzk656/image/202302041734335.png)

![image-20230204181854481](https://cdn.jsdelivr.net/gh/yzk656/image/202302041818542.png)

![image-20230204181954627](https://cdn.jsdelivr.net/gh/yzk656/image/202302041819689.png)

![image-20230204182044183](https://cdn.jsdelivr.net/gh/yzk656/image/202302041820232.png)

![image-20230204191605363](https://cdn.jsdelivr.net/gh/yzk656/image/202302041916406.png)

![image-20230204191816652](https://cdn.jsdelivr.net/gh/yzk656/image/202302041918705.png)

![image-20230204191826164](https://cdn.jsdelivr.net/gh/yzk656/image/202302041918211.png)

## 2023-02-05

![image-20230204214536283](https://cdn.jsdelivr.net/gh/yzk656/image/202302042145328.png)

![image-20230204214636950](https://cdn.jsdelivr.net/gh/yzk656/image/202302042146019.png)

```js
//service方法会自动判断是 Get 还是 Post 请求



package com.yzk.servlet;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

@WebServlet("/ser04")
public class servlet04 extends HttpServlet {
//    @Override
//    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
//        System.out.println("service ...");
//    }

    /**
     * Get 请求调用
     * @param req
     * @param resp
     * @throws ServletException
     * @throws IOException
     */
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("Get 请求");
    }

    /**
     * Post 请求调用
     * @param req
     * @param resp
     * @throws ServletException
     * @throws IOException
     */
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("Post 请求");
        /*调用 Get 请求*/
        doGet(req, resp);
    }
}
```

![image-20230205122445341](https://cdn.jsdelivr.net/gh/yzk656/image/202302051224460.png)

![image-20230205122801173](https://cdn.jsdelivr.net/gh/yzk656/image/202302051228225.png)

![image-20230205124402292](https://cdn.jsdelivr.net/gh/yzk656/image/202302051244335.png)

![image-20230205124412640](https://cdn.jsdelivr.net/gh/yzk656/image/202302051244683.png)

![image-20230205124607018](https://cdn.jsdelivr.net/gh/yzk656/image/202302051246052.png)

```java
package com.yzk.servlet;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * @ClassName: servlet05
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/5 12:31
 */

@WebServlet("/ser05")
public class servlet05 extends HttpServlet {

    /**
     * 就绪/服务方法（处理请求数据）
     * 系统方法，服务器自动调用
     * 当有请求到达 Servlet 容器时，就会调用该方法（可以被多次调用）
     * @param req
     * @param resp
     * @throws ServletException
     * @throws IOException
     */
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("servlet 被调用了");
    }

    /**
     * 销毁方法
     * 系统方法，服务器自动调用
     * 当服务器关闭或应用程序停止时，调用该方法
     * 方法只会执行一次
     */
    @Override
    public void destroy() {
        System.out.println("servlet 被销毁了");
    }

    /**
     * 初始化方法
     * 系统方法，服务器自动调用
     * 当请求到达 Servlet 容器时，Servlet容器会自动判断该 Servlet 对象是否存在，如果不存在，则创建实例并初始化
     * 方法只会执行一次
     * @throws ServletException
     */
    @Override
    public void init() throws ServletException {
        System.out.println("servlet 被创建了");
    }
}
```

![image-20230205124658577](https://cdn.jsdelivr.net/gh/yzk656/image/202302051246622.png)

![image-20230205125029327](https://cdn.jsdelivr.net/gh/yzk656/image/202302051250390.png)

![image-20230205145355908](https://cdn.jsdelivr.net/gh/yzk656/image/202302051453014.png)

```java
package com.yzk.servlet;


import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * @ClassName: servlet01
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/5 14:00
 */
@WebServlet("/ser01")
public class servlet01 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /*常用方法*/
        /*获取请求头的完整路径 （从http开始，到“？”前面结束）*/
        String url = req.getRequestURL().toString();
        System.out.println(url);
        /*获取请求时的部分路径 （从项目的站点开始，到 ？ 前面结束）*/
        String uri = req.getRequestURI();
        System.out.println(uri);
        /*获取请求时的参数字符串 （从 ？ 后面开始，到最后的字符串）*/
        String queryString = req.getQueryString();
        System.out.println(queryString);
        /*获取请求方式 （Get和Post）*/
        String method = req.getMethod();
        System.out.println(method);
        /*获取当前协议版本 （Http/1.1）*/
        String protocol=req.getProtocol();
        System.out.println(protocol);
        /*获取项目的站点名 （项目对外访问路径）*/
        String webapp=req.getContextPath();
        System.out.println(webapp);


        /*获取指定名称的参数值*/
        String uname=req.getParameter("uname");
        String upwd=req.getParameter("upwd");

        System.out.println(uname+" "+upwd);

        /*获取指定名称参数的所有参数值，返回字符串数组（用于复选框传值）*/
        String[] hobbys=req.getParameterValues("hobby");
        /*判断数组是否为空*/
        if(hobbys!=null&&hobbys.length>0){
            for(String hobby:hobbys){
                System.out.println(hobby);
            }
        }
    }
}
```

![image-20230205151838317](https://cdn.jsdelivr.net/gh/yzk656/image/202302051518371.png)

==Tomcat10.1.x发布，告别中文乱码==

目前post请求中文乱码也已经没了

![image-20230205163019615](https://cdn.jsdelivr.net/gh/yzk656/image/202302051630674.png)

```java
package com.yzk.servlet;

/**
 * @ClassName: servlet03
 * @Description: 请求转发跳转
 * @Author: 杨振坤
 * @date: 2023/2/5 16:33
 */

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * 可以让请求从服务端跳转到客户端（或跳转到指定的 Servlet）
 * 这个是服务端行为
 *
 * 特点：
 *  1. 服务端行为
 *  2. 地址栏不变
 *  3. 从始至终只有一个请求
 *  4. req数据可以共享
 */
@WebServlet("/ser03")
public class servlet03 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /*接收客户端请求参数*/
        String uname = req.getParameter("uname");
        System.out.println("servlet03 " + uname);

        /*请求转发跳转Servlet04*/
//        req.getRequestDispatcher("ser04").forward(req, resp);

        /*请求转发跳转到 jsp 页面*/
//        req.getRequestDispatcher("login.jsp").forward(req,resp);
        /*请求转发跳转到 HTML 页面*/
        req.getRequestDispatcher("login.html").forward(req,resp);
    }
}
```

![image-20230205165249870](https://cdn.jsdelivr.net/gh/yzk656/image/202302051652908.png)

```java
package com.yzk.servlet;

/**
 * @ClassName: servlet03
 * @Description: request作用域
 * @Author: 杨振坤
 * @date: 2023/2/5 16:33
 */

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;
import java.util.ArrayList;
import java.util.List;


@WebServlet("/ser05")
public class servlet05 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("servlet05。。。 ");

        /*设置域对象内容*/
        req.setAttribute("name", "admin");
        req.setAttribute("age", 20);
        List<String> list = new ArrayList<>();
        list.add("aaa");
        list.add("bbb");
        req.setAttribute("list", list);

        /*进行请求转发*/
//        req.getRequestDispatcher("ser06").forward(req,resp);
        req.getRequestDispatcher("index.jsp").forward(req,resp);
    }
}

```



jsp

```jsp
<%@ page import="java.util.List" %>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>$Title$</title>
</head>
<body>
<h2>index页面</h2>
<%--如果要在jsp中写 Java 代码，需要写在脚本段中<%%>--%>
<%
    /*获取域对象内容*/
    String name=request.getAttribute("name").toString();
    Integer age=(Integer) request.getAttribute("age");
    List<String> list=(List<String>) request.getAttribute("list");
    System.out.println(name);
    System.out.println(age);
    System.out.println(list);
%>
</body>
</html>

```

![image-20230205194838464](https://cdn.jsdelivr.net/gh/yzk656/image/202302051948537.png)

![image-20230205213050745](https://cdn.jsdelivr.net/gh/yzk656/image/202302052130792.png)

```java
package com.yzk.servlet1;

/**
 * @ClassName: servlet01
 * @Description: Response
 * @Author: 杨振坤
 * @date: 2023/2/5 21:34
 */

import jakarta.servlet.ServletException;
import jakarta.servlet.ServletOutputStream;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;
import java.io.PrintWriter;

/**
 * 响应数据
 *  getWriter()         字符输出流【输出字符串】
 *  getOutputStream（）  字节输出流【输出一切数据】
 *  两种流不能同时使用，否则会报错
 */
@WebServlet("/ser001")
public class servlet01 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
/*        *//*获取字符输出流*//*
        PrintWriter writer=resp.getWriter();
        *//*输出数据*//*
        writer.write("hello");*/

        /*获取字节输出流*/
        ServletOutputStream out=resp.getOutputStream();
        out.write("hi".getBytes());
    }
}
```

![image-20230205221208103](https://cdn.jsdelivr.net/gh/yzk656/image/202302052212174.png)

```java
package com.yzk.servlet1;

/**
 * @ClassName: servlet01
 * @Description: 乱码问题
 * @Author: 杨振坤
 * @date: 2023/2/5 21:34
 */

import jakarta.servlet.ServletException;
import jakarta.servlet.ServletOutputStream;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.*;

/**
 * 字符响应流
 * 乱码解决
 * 1. 设置服务端编码格式、
 * 2. 设置客户端编码格式
 * 总结：设置客户端和服务端编码格式都支持中文，且保持一致
 */
@WebServlet("/ser002")
public class servlet02 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
//        /*设置服务端的编码格式*/
//        resp.setCharacterEncoding("UTF-8");
//        /*设置客户端编码格式*/
//        resp.setHeader("content-type", "text/html;charset=UTF-8");

        /*简洁模式*/
        resp.setContentType("text/html;charset=UTF-8");

        //*获取字符输出流*//
        PrintWriter writer = resp.getWriter();
        //*输出数据*//
        writer.write("<h2>你好</h2>");
    }
}
```

![image-20230205223514590](https://cdn.jsdelivr.net/gh/yzk656/image/202302052235658.png)

```java
package com.yzk.servlet1;

/*
 * @ClassName: servlet01
 * @Description: Response
 * @Author: 杨振坤
 * @date: 2023/2/5 21:34
 */

import jakarta.servlet.ServletException;
import jakarta.servlet.ServletOutputStream;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * 字节响应数据
 * 乱码解决
 * 1. 设置服务端编码格式、
 * 2. 设置客户端编码格式
 * 总结：设置客户端和服务端编码格式都支持中文，且保持一致
 * */
@WebServlet("/ser003")
public class servlet03 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /*简洁模式*/
        resp.setContentType("text/html;charset=UTF-8");
        /*获取字节输出流*/
        ServletOutputStream out=resp.getOutputStream();
        out.write("<h2>你好</h2>".getBytes("UTF-8"));
    }
}
```

![image-20230205223913662](https://cdn.jsdelivr.net/gh/yzk656/image/202302052239715.png)

```java
package com.yzk.servlet1;

/*
 * @ClassName: servlet01
 * @Description: 重定向
 * @Author: 杨振坤
 * @date: 2023/2/5 21:34
 */

import jakarta.servlet.ServletException;
import jakarta.servlet.ServletOutputStream;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * 1. 服务端指导，客户端行为
 * 2. 存在两次请求
 * 3. 地址栏会发生改变
 * 4. request对象不共享
 * */
@WebServlet("/ser004")
public class servlet04 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("servlet004");

        /*接收参数*/
        String uname=req.getParameter("uname");
        System.out.println("ser004 "+uname);

        /*重定向跳转到ser005*/
        resp.sendRedirect("ser005");
    }
}

```

```java
package com.yzk.servlet1;

/*
 * @ClassName: servlet01
 * @Description: 重定向
 * @Author: 杨振坤
 * @date: 2023/2/5 21:34
 */

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

@WebServlet("/ser005")
public class servlet05 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {

        /*接收参数*/
        String uname=req.getParameter("uname");
        System.out.println("ser005 "+uname);/*接收不到*/

        System.out.println("servlet005");
    }
}
```

![image-20230205225123865](https://cdn.jsdelivr.net/gh/yzk656/image/202302052251921.png)

![image-20230205230013572](https://cdn.jsdelivr.net/gh/yzk656/image/202302052300607.png)

总结：重定向可以跨域，请求转发不能。

​			请求转发只能访问当前项目下的资源

## 2023-02-06

![image-20230206092233007](https://cdn.jsdelivr.net/gh/yzk656/image/202302060922082.png)

![image-20230206115346097](https://cdn.jsdelivr.net/gh/yzk656/image/202302061153188.png)

```java
package com.yzk.servlet;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.Cookie;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * @ClassName: cookie01
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/6 11:56
 */

@WebServlet("/cook01")
public class cookie01 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /*Cookie的创建*/
        Cookie cookie=new Cookie("name","admin");
        /*发送（响应）Cookie*/
        resp.addCookie(cookie);
    }
}
```

![image-20230206120654375](https://cdn.jsdelivr.net/gh/yzk656/image/202302061215039.png)

```java
package com.yzk.servlet;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.Cookie;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * @ClassName: cookie01
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/6 11:56
 */

/**
 * cookie 的获取
 * 返回的是数组
 */
@WebServlet("/cook02")
public class cookie02 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        Cookie[] cookies = req.getCookies();
        /*判断cookie是否为空*/
        if (cookies != null && cookies.length > 0) {
            for(Cookie cookie:cookies){
                /*获取cookie的名称和值*/
                String name=cookie.getName();
                String value=cookie.getValue();
                System.out.println(name+" "+value);
            }
        }
    }
}

```

注意：cookie里面的内容是放在浏览器里面的，和你服务器是否关闭没有关系【默认是关闭浏览器后失效】

![image-20230206122048939](https://cdn.jsdelivr.net/gh/yzk656/image/202302061220010.png)

不同域名是无法*共享*浏览器端本地信息，包括*cookies*

```java
package com.yzk.servlet;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.Cookie;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * @ClassName: cookie01
 * @Description: cookie到期时间
 * @Author: 杨振坤
 * @date: 2023/2/6 11:56
 */

/**
 * cookie 的获取
 * 返回的是数组
 */
@WebServlet("/cook03")
public class cookie03 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        Cookie cookie=new Cookie("name","admin");
        cookie.setMaxAge(-1);
        resp.addCookie(cookie);

        Cookie cookie2=new Cookie("name1","admin1");
        cookie2.setMaxAge(30);
        resp.addCookie(cookie2);

        Cookie cookie3=new Cookie("name3","admin3");
        cookie3.setMaxAge(0);
        resp.addCookie(cookie3);
    }
}
```

![image-20230206160240314](https://cdn.jsdelivr.net/gh/yzk656/image/202302061602394.png)

![image-20230206160410416](https://cdn.jsdelivr.net/gh/yzk656/image/202302061604457.png)

```java
package com.yzk.servlet;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.Cookie;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;
import java.net.URLDecoder;
import java.net.URLEncoder;

/**
 * @ClassName: cookie01
 * @Description: cookie注意点
 * @Author: 杨振坤
 * @date: 2023/2/6 11:56
 */

/**
 * 大小有限，4kb左右
 */
@WebServlet("/cook04")
public class cookie04 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /*cookie不能存中文，非要存的话，需要进行转化*/
        String name="姓名";
        String value="张三";

        name=URLEncoder.encode(name);
        value=URLEncoder.encode(value);

        Cookie cookie = new Cookie(name,value);
        resp.addCookie(cookie);

        Cookie[] cookies = req.getCookies();
        if (cookies != null) {
            for (Cookie cookie1 : cookies) {
                /*解码*/
                System.out.println(URLDecoder.decode(cookie1.getName()));
                System.out.println(URLDecoder.decode(cookie1.getValue()));
            }
        }

        /*出现同名cookie对象，则会进行覆盖*/
        Cookie cookie1=new Cookie("name","zhangsan");
        resp.addCookie(cookie1);
    }
}
```

![image-20230206184538869](https://cdn.jsdelivr.net/gh/yzk656/image/202302061845962.png)

![image-20230206184756251](https://cdn.jsdelivr.net/gh/yzk656/image/202302061847304.png)

![image-20230206191144226](https://cdn.jsdelivr.net/gh/yzk656/image/202302061911270.png)

![image-20230206191354540](https://cdn.jsdelivr.net/gh/yzk656/image/202302061913615.png)

![image-20230206211415421](https://cdn.jsdelivr.net/gh/yzk656/image/202302062114469.png)

```java
package com.yzk.session;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import jakarta.servlet.http.HttpSession;

import java.io.IOException;

/**
 * @ClassName: Session01
 * @Description: Session对象
 * @Author: 杨振坤
 * @date: 2023/2/6 21:05
 */
@WebServlet("/ss01")
public class Session01 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /*获取Session对象*/
        HttpSession session = req.getSession();

        /*获取Session的对话标识符*/
        String id = session.getId();
        System.out.println(id);
        /*获取Session的创建时间*/
        System.out.println(session.getCreationTime());
        /*获取最后一次访问时间*/
        System.out.println(session.getLastAccessedTime());
        /*判断是否是新的session对象*/
        System.out.println(session.isNew());
    }
}
```

![image-20230206211436504](https://cdn.jsdelivr.net/gh/yzk656/image/202302062114573.png)

![image-20230206212221077](https://cdn.jsdelivr.net/gh/yzk656/image/202302062122140.png)

```java
package com.yzk.session;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import jakarta.servlet.http.HttpSession;

import java.io.IOException;

/**
 * @ClassName: Session01
 * @Description: Session域对象
 * @Author: 杨振坤
 * @date: 2023/2/6 21:05
 */

/**
 * 请求转发只使用 1 次请求，可以保留数据，因此使用请求转发方法
 * 请求转发
 *      一次请求
 *      request作用域有效
 *      Session作用域有效
 * 重定向
 *      两次请求
 *      request作用域无效
 *      Session作用域有效
 */
@WebServlet("/ss02")
public class Session02 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /*获取Session对象*/
        HttpSession session = req.getSession();

        /*设置Session域对象*/
        session.setAttribute("uname", "admin");
        session.setAttribute("upwd", "123456");

        /*移除Session域对象*/
        session.removeAttribute("upwd");

        /*request域对象*/
        req.setAttribute("name", "zhangsan");
        req.setAttribute("pwd", "123");


        /*请求转发*/
//        req.getRequestDispatcher("index.jsp").forward(req, resp);

        /*重定向跳转*/
        resp.sendRedirect("index.jsp");
    }
}
```

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>$Title$</title>
</head>
<body>
<%
    /*获取Session域对象*/
    String uname = (String) request.getSession().getAttribute("uname");
    String upwd = (String) request.getSession().getAttribute("upwd");

    /*获取request域对象*/
    String name = (String) request.getAttribute("name");
    String pwd = (String) request.getAttribute("pwd");

    out.print(uname+" "+upwd);
    out.print(name+" "+pwd);
%>
</body>
</html>
```

![image-20230206214540163](https://cdn.jsdelivr.net/gh/yzk656/image/202302062145220.png)

![image-20230206224057399](https://cdn.jsdelivr.net/gh/yzk656/image/202302062240457.png)

![image-20230206224613337](https://cdn.jsdelivr.net/gh/yzk656/image/202302062246382.png)

![image-20230206224915397](https://cdn.jsdelivr.net/gh/yzk656/image/202302062249443.png)

![image-20230206225022592](https://cdn.jsdelivr.net/gh/yzk656/image/202302062250638.png)

## 2023-02-07

![image-20230207171535157](https://cdn.jsdelivr.net/gh/yzk656/image/202302071715264.png)

![image-20230207173023875](https://cdn.jsdelivr.net/gh/yzk656/image/202302071730940.png)

```java
package com.yzk.ServletContext;

import jakarta.servlet.ServletContext;
import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * @ClassName: Servlet01
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/7 17:30
 */

@WebServlet("/servletContext01")
public class Servlet01 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /*通过Request对象获取*/
        ServletContext servletContext = req.getServletContext();

        /*通过Session对象获取*/
        ServletContext servletContext1 = req.getSession().getServletContext();

        /*通过ServletConfig对象获取*/
        ServletContext servletContext2 = getServletConfig().getServletContext();

        /*直接获取*/
        ServletContext servletContext3 = getServletContext();

        /*常用方法*/
        /*1、获取当前服务器的版本信息*/
        String serverInfo = req.getServletContext().getServerInfo();
        System.out.println(serverInfo);
        /*2、获取项目的真实路径*/
        String realPath = req.getServletContext().getRealPath("/");
        System.out.println(realPath);
    }
}

```

![image-20230207174952355](https://cdn.jsdelivr.net/gh/yzk656/image/202302071749428.png)

![image-20230207202623466](https://cdn.jsdelivr.net/gh/yzk656/image/202302072026562.png)

![image-20230207204938244](https://cdn.jsdelivr.net/gh/yzk656/image/202302072049316.png)

![image-20230207205149182](https://cdn.jsdelivr.net/gh/yzk656/image/202302072051275.png)

```java
package com.yzk.UploadServlet;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.MultipartConfig;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import jakarta.servlet.http.Part;

import java.io.IOException;

/**
 * @ClassName: UploadServlet
 * @Description: 文件上传
 * @Author: 杨振坤
 * @date: 2023/2/7 20:53
 */

@WebServlet("/UploadServlet")
/**
 *如果是文件上传，一定要加该注解
 */
@MultipartConfig
public class UploadServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("文件上传。。。");
        /*设置请求的编码格式*/
        req.setCharacterEncoding("UTF-8");

        /*获取普通表项（获取参数）*/
        String uname = req.getParameter("uname");
        System.out.println(uname);
        /*获取Part对象（Servlet将multipart/form-data的Post请求封装成Part对象）*/
        Part part = req.getPart("my_file");
        /*通过Part对象得到上传的文件名*/
        String filename = part.getSubmittedFileName();
        System.out.println(filename);
        /*得到文件的存放路径*/
        String filepath = req.getServletContext().getRealPath("/");
        System.out.println("文件的存放路径:"+filepath);
        /*上传文件到指定目录*/
        part.write(filepath + "/" + filename);
    }
}
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>文件上传</title>
</head>
<body>
<!--文件上传
    1. 准备表单
    2. 设置表单提交类型为Post请求 method=“post”
    3. 设置表单为文件上传地址 enctype="multipart/form-data"
    4. 设置文件提交地址
    5. 准备表单元素
        1. 普通表单项 type=“text”；
        2. 文件项 type=“file”
    6. 设置表单元素的name值（表单提交一定要设置表单元素的name属性值，否则后台无法接收数据）
-->

<form action="UploadServlet" method="post" enctype="multipart/form-data">
    姓名：<input type="text" name="uname"><br>
    文件：<input type="file" name="my_file"><br>
    <!--button默认类型是提交表单，type=submit-->
    <button>提交</button>
</form>
</body>
</html>
```

![image-20230207222104010](https://cdn.jsdelivr.net/gh/yzk656/image/202302072221089.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>文件下载</title>
</head>
<body>
<!--
    超链接下载
        当使用超链接时，如果遇到浏览器能够识别的资源，则会显示内容
        如果遇到浏览器不能识别的资源，则会进行下载
    download属性
        通过download属性规定浏览器进行下载
-->

<!--浏览器能够识别的资源-->
<a href="download/新建文本文档.txt">文本文件</a>
<a href="download/复杂度.png">图片文件</a>
<!--浏览器不能识别的资源-->
<a href="download/《TCP-IP详解卷1：协议》.zip">压缩文件</a>
<hr>
<a href="download/新建文本文档.txt"download="">文本文件</a>
<a href="download/复杂度.png" download="百度.png">图片文件</a>

</body>
</html>
```

==注意：==浏览器要想访问项目内的文件夹，需要在进行部署【不加/sc04也得到正常的结果】

![image-20230207230857309](https://cdn.jsdelivr.net/gh/yzk656/image/202302072308354.png)

![image-20230207231233733](https://cdn.jsdelivr.net/gh/yzk656/image/202302072312823.png)

![image-20230207231831419](https://cdn.jsdelivr.net/gh/yzk656/image/202302072318497.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>文件下载</title>
</head>
<body>
<!--
    超链接下载
        当使用超链接时，如果遇到浏览器能够识别的资源，则会显示内容
        如果遇到浏览器不能识别的资源，则会进行下载
    download属性
        通过download属性规定浏览器进行下载
-->

<!--浏览器能够识别的资源-->
<a href="download/新建文本文档.txt">文本文件</a>
<a href="download/复杂度.png">图片文件</a>
<!--浏览器不能识别的资源-->
<a href="download/《TCP-IP详解卷1：协议》.zip">压缩文件</a>
<hr>
<a href="download/新建文本文档.txt"download="">文本文件</a>
<a href="download/复杂度.png" download="百度.png">图片文件</a>

<hr>
<form action="downloadServlet2">
    文件名：<input type="text" name="filename" placeholder="请输入要下载的文件名">
    <button>下载</button>
</form>

</body>
</html>
```

```java
package com.yzk.UploadServlet;

import jakarta.servlet.Servlet;
import jakarta.servlet.ServletException;
import jakarta.servlet.ServletOutputStream;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;

/**
 * @ClassName: DownloadServlet2
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/7 23:23
 */
@WebServlet("/downloadServlet2")
public class DownloadServlet2 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("文件正在下载");

        /*设置请求的编码格式*/
        req.setCharacterEncoding("UTF-8");
        resp.setContentType("text/html;charset=UTF-8");
        /*获取参数（得到要下载的名字）*/
        String filename = req.getParameter("filename");
        /*参数的非空判断*/
        if (filename == null || filename.trim().equals("")) {
            resp.getWriter().write("请输入要下载的文件名");
            resp.getWriter().close();
            return;
        }

        /*得到图片存放的路径*/
        String path = req.getServletContext().getRealPath("/download/");
        /*通过路径得到file路径*/
        File file = new File(path + filename);
        /*判断文件对象是否存在并且是否是一个标准文件*/
        if (file.exists() && file.isFile()) {
            /*设置响应类型（浏览器无法使用某种方式或者激活某个程序来处理的 MIME 类型）*/
            resp.setContentType("application/x-msdownload");
            /*设置响应头*/
            resp.setHeader("Content-Disposition", "attachment;filename=" + filename);
            /*得到文件的输入流*/
            InputStream in = new FileInputStream(file);
            /*得到字节输出流*/
            ServletOutputStream out = resp.getOutputStream();
            /*定义byte数组*/
            byte[] bytes = new byte[1024];
            /*定义长度*/
            int len = 0;
            /*循环输出*/
            while ((len = in.read()) != -1) {
                /*输出*/
                out.write(bytes,0,len);
            }
            /*关闭资源*/
            out.close();
            in.close();
        } else {
            resp.getWriter().write("文件不存在，请重试！！！");
            resp.getWriter().close();
            return;
        }
    }
}
```

# JSP

## 2022-02-08

![image-20230208130023014](https://cdn.jsdelivr.net/gh/yzk656/image/202302081300115.png)

![image-20230208130419061](https://cdn.jsdelivr.net/gh/yzk656/image/202302081304138.png)

![image-20230208130638735](https://cdn.jsdelivr.net/gh/yzk656/image/202302081306792.png)

![image-20230208133159153](https://cdn.jsdelivr.net/gh/yzk656/image/202302081331221.png)

![image-20230208134814458](https://cdn.jsdelivr.net/gh/yzk656/image/202302081348513.png)

![image-20230208192240471](https://cdn.jsdelivr.net/gh/yzk656/image/202302081922557.png)

```java
<%--
  Created by IntelliJ IDEA.
  User: 27939
  Date: 2023/2/8
  Time: 19:24
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>脚本小程序</title>
</head>
<body>
<%--第一种：Java代码，可以写Java代码，定义局部变量。编写语句--%>
<%
    String str="111";
    System.out.println(str);
    out.write(str);

    /*输出全局变量*/
    out.write("全局变量："+num);
%>
<%--第二种：生命区局变量、方法、类等--%>
<%!
    int num=10;
%>
<%--第三种：输出表达式，可以输出变量或字面量--%>
<%=
    str
%>

</body>
</html>
```

![image-20230208205427210](https://cdn.jsdelivr.net/gh/yzk656/image/202302082054282.png)

![image-20230208205721630](https://cdn.jsdelivr.net/gh/yzk656/image/202302082057696.png)

![image-20230208224233268](https://cdn.jsdelivr.net/gh/yzk656/image/202302082242450.png)

```jsp
<%--
  Created by IntelliJ IDEA.
  User: 27939
  Date: 2023/2/8
  Time: 21:00
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>include静态包含</title>
</head>
<body>

<%@include file="04-header.jsp" %>
<h2>主题内容</h2>
<%@include file="04-footer.jsp" %>

</body>
</html>

```

```java
<%--
  Created by IntelliJ IDEA.
  User: 27939
  Date: 2023/2/8
  Time: 21:00
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>底部信息</title>
</head>
<body>
<h2>底部内容</h2>
</body>
</html>
```

```java
<%--
  Created by IntelliJ IDEA.
  User: 27939
  Date: 2023/2/8
  Time: 21:00
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>头部信息</title>
</head>
<body>

<h2>头部内容</h2>

</body>
</html>
```

![image-20230208224355262](https://cdn.jsdelivr.net/gh/yzk656/image/202302082243316.png)

![image-20230208225418830](https://cdn.jsdelivr.net/gh/yzk656/image/202302082254878.png)

![image-20230208230302030](https://cdn.jsdelivr.net/gh/yzk656/image/202302082303074.png)

```jsp
<%--
  Created by IntelliJ IDEA.
  User: 27939
  Date: 2023/2/8
  Time: 22:44
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>include动态包含</title>
</head>
<body>
<%--相当于方法的调用
        可以有同名变量
        jsp标签中间是添加参数的，如果不添加参数，空格都不能添加
--%>

<%
    int a = 1;
%>
<%
    String str = "123456";
    String url = "04-footer.jsp";
%>


<jsp:include page="04-header.jsp"></jsp:include>
<h2>主题内容</h2>
<%--注意：注释两旁的也算空格，因此jsp标签里面不能写注释
    page也能通过变量定义
--%>
<jsp:include page="<%=url%>">
    <jsp:param name="uname" value="admin"></jsp:param>
    <jsp:param name="upwd" value="<%=str%>"></jsp:param>
</jsp:include>
</body>
</html>
```

```jsp
<%--
  Created by IntelliJ IDEA.
  User: 27939
  Date: 2023/2/8
  Time: 21:00
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>底部信息</title>
</head>
<body>
<h2>底部内容</h2>

<%--获取参数--%>
<%
    int a = 10;
    String uname = request.getParameter("uname");
    String pwd = request.getParameter("upwd");
    out.print(uname + " " + pwd);
%>

</body>
</html>
```

![image-20230208231306244](https://cdn.jsdelivr.net/gh/yzk656/image/202302082313313.png)

![image-20230208232029337](https://cdn.jsdelivr.net/gh/yzk656/image/202302082320394.png)



![image-20230208233719532](https://cdn.jsdelivr.net/gh/yzk656/image/202302082337577.png)

![image-20230208233701343](https://cdn.jsdelivr.net/gh/yzk656/image/202302082337395.png)

```jsp
<%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/8
  Time: 23:23
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%
    /*设置Page范围内的域对象*/
    pageContext.setAttribute("name1","zhangsan");

    /*设置request范围内的域对象*/
    request.setAttribute("name2","lisi");

    /*设置session范围内的域对象*/
    session.setAttribute("name3","yzk");

    /*设置application范围内的域对象*/
    application.setAttribute("name4","zhaosi");

%>


<%--    /*jsp中服务端跳转*/--%>
<%--<jsp:forward page="06-JSP的四大域对象02.jsp"></jsp:forward>--%>

    <%--服务端跳转是通过超链接实现--%>
<a href="06-JSP的四大域对象02.jsp">跳转</a>
</body>
</html>
```

```jsp
<%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/8
  Time: 23:23
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%
    /*获取域对象的值*/
    /*page范围*/
    out.print("page范围" + pageContext.getAttribute("name1")+"<br>");
    out.print("request范围" + request.getAttribute("name2")+"<br>");
    out.print("session范围" + session.getAttribute("name3")+"<br>");
    out.print("application范围" + application.getAttribute("name4")+"<br>");
%>
</body>
</html>
```

## 2023-02-09

简单的登录功能

```jsp
<%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/9
  Time: 21:15
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<form action="login_servlet" method="post">
    姓名：<input type="text" name="uname"><br>
    密码：<input type="password" name="upwd"><br>
    <button>登录</button>
    <span style="color: red;font-size: 12px"><%=request.getAttribute("msg")%></span>
</form>
</body>
</html>
```

```java
package com.yzk.controller;

import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

import java.io.IOException;

/**
 * @ClassName: Login_servlet
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/9 21:18
 */

@WebServlet("/login_servlet")
public class LoginServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /*设置客户端的编码格式*/
        req.setCharacterEncoding("UTF-8");

        /*接收客户端传递的参数*/
        String uname = req.getParameter("uname");
        String upwd = req.getParameter("upwd");

        /*判断参数是否为空*/
        if (uname == null || uname.trim().equals("")) {
            req.setAttribute("msg", "用户姓名不能为空");
            req.getRequestDispatcher("login.jsp").forward(req, resp);
            return;
        }
        if (upwd == null || upwd.trim().equals("")) {
            req.setAttribute("msg", "用户密码不能为空");
            req.getRequestDispatcher("login.jsp").forward(req, resp);
            return;
        }

        /*判断账号，密码是否正确*/
        if (!uname.equals("admin") || !upwd.equals("admin")) {
            req.setAttribute("msg","登录失败");
            req.getRequestDispatcher("login.jsp").forward(req,resp);
            return;
        }

        /*登录成功*/
        /*设置登录信息到Session作用域*/
        req.getSession().setAttribute("uname",uname);
        resp.sendRedirect("index.jsp");
    }
}
```

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>$Title$</title>
</head>
<body>
    <h2>欢迎<%=session.getAttribute("uname")%>登录</h2>
</body>
</html>
```

![image-20230209214406139](https://cdn.jsdelivr.net/gh/yzk656/image/202302092144282.png)

解决显示`null`值的情况

![image-20230209220910370](https://cdn.jsdelivr.net/gh/yzk656/image/202302092209418.png)

![image-20230209221036011](https://cdn.jsdelivr.net/gh/yzk656/image/202302092210060.png)

```jsp
<%@ page import="com.yzk.session.Session01" %><%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/9
  Time: 22:17
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%--
    EL表达式一般操作的是域对象，不能操作局部变量
    EL表达式获取对象的值为空，默认显示空字符串
    EL表达式默认从小到大范围去找，找到即可，如果四个对象（page、request、session、application）都没找到，就显示空字符串
    获取指定范围内的域对象：<br>
        ${sessionScope.uname}
--%>
<%
    pageContext.setAttribute("uname","yzk1");
    request.setAttribute("uname","yzk2");
    session.setAttribute("uname","yzk3");
    application.setAttribute("uname","yzk4");

    /*定义局部变量*/
    String str="123";
%>

<%--获取数据--%>
获取局部变量：${str}<br>
获取域对象：${uname}<br>

获取指定范围内的域对象：<br>
${sessionScope.uname}


</body>
</html>

```

![image-20230209222929119](https://cdn.jsdelivr.net/gh/yzk656/image/202302092229163.png)

![image-20230209223204898](https://cdn.jsdelivr.net/gh/yzk656/image/202302092232972.png)

![image-20230209223220284](https://cdn.jsdelivr.net/gh/yzk656/image/202302092232356.png)

![image-20230209223254503](https://cdn.jsdelivr.net/gh/yzk656/image/202302092232545.png)

![image-20230209223311810](https://cdn.jsdelivr.net/gh/yzk656/image/202302092233862.png)

![image-20230209223323322](https://cdn.jsdelivr.net/gh/yzk656/image/202302092233375.png)

![image-20230210003722433](https://cdn.jsdelivr.net/gh/yzk656/image/202302100037523.png)

```jsp
<%@ page import="java.util.List" %>
<%@ page import="java.util.ArrayList" %>
<%@ page import="java.util.Map" %>
<%@ page import="java.util.HashMap" %>
<%@ page import="com.yzk.po.User" %><%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/9
  Time: 22:48
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%
    /*list*/
    List<String> list=new ArrayList<>();
    list.add("aaa");
    list.add("bbb");
    list.add("ccc");
    request.setAttribute("list",list);

    /*map*/
    Map map=new HashMap();
    map.put("aaa","1111");
    map.put("bbb","2222");
    map.put("ccc","3333");
    request.setAttribute("map",map);

    /*JavaBean*/
    User user=new User();
    user.setUser_id(1);
    user.setUname("yzk");
    user.setUpwd("123456");
    request.setAttribute("user",user);

%>

获取list
${list.size()}<br>
${list.get(1)};<br>

获取Map
${map.aaa}<br>
${map["aaa"]}<br>

获取JavaBean
${user.uname}<br>
${user.getUname()}

</body>
</html>

```

```java
package com.yzk.po;

/**
 * @ClassName: User
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/10 0:27
 */
public class User {
    private Integer user_id;
    private String uname;
    private String upwd;

    public User() {
    }

    public User(Integer user_id, String uname, String upwd) {
        this.user_id = user_id;
        this.uname = uname;
        this.upwd = upwd;
    }

    public Integer getUser_id() {
        return user_id;
    }

    public void setUser_id(Integer user_id) {
        this.user_id = user_id;
    }

    public String getUname() {
        return uname;
    }

    public void setUname(String uname) {
        this.uname = uname;
    }

    public String getUpwd() {
        return upwd;
    }

    public void setUpwd(String upwd) {
        this.upwd = upwd;
    }
}

```

## 2023-02-10

![image-20230210094909728](https://cdn.jsdelivr.net/gh/yzk656/image/202302100949797.png)

![image-20230210101832778](https://cdn.jsdelivr.net/gh/yzk656/image/202302101018854.png)

![image-20230210101913154](https://cdn.jsdelivr.net/gh/yzk656/image/202302101019219.png)

![image-20230210101934327](https://cdn.jsdelivr.net/gh/yzk656/image/202302101019383.png)

```jsp
<%@ page import="java.util.List" %>
<%@ page import="java.util.ArrayList" %>
<%@ page import="java.util.HashMap" %>
<%@ page import="java.util.Map" %>
<%@ page import="com.yzk.po.User" %><%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/10
  Time: 9:58
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%--
    对于字符串、List、Map空对象看为null
    对于JavaBean 空构造函数不算null
--%>
<%
    /*字符串*/
    request.setAttribute("str1","aaa");
    request.setAttribute("str2","");
    request.setAttribute("str3",null);

    /*List*/
    List list1=new ArrayList();
    List list2=null;
    List list3=new ArrayList();
    list1.add(1);
    request.setAttribute("list1",list1);
    request.setAttribute("list2",list2);
    request.setAttribute("list3",list3);

    /*Map*/
    Map map1=null;
    Map map2=new HashMap();
    Map map3=new HashMap();
    map3.put(1,2);
    request.setAttribute("map1",map1);
    request.setAttribute("map2",map2);
    request.setAttribute("map3",map3);

    /*JavaBean*/
    User user1=null;
    User user2=new User();
    User user3=new User();
    user3.setUser_id(1);
    request.setAttribute("user1",user1);
    request.setAttribute("user2",user2);
    request.setAttribute("user3",user3);
%>
字符串 <br>
${empty str}<br>
${empty str1}<br>
${empty str2}<br>
${empty str3}<br>

<hr>

List <br>
${empty list1}<br>
${empty list2}<br>
${empty list3}<br>

<hr>

Map <br>
${empty map1}<br>
${empty map2}<br>
${empty map3}<br>

<hr>

JavaBean <br>
${empty user1}<br>
${empty user2}<br>
${empty user3}<br>

</body>
</html>
```

# JSTL

## 2023-02-10

![image-20230210102209396](https://cdn.jsdelivr.net/gh/yzk656/image/202302101022466.png)

![image-20230210102841831](https://cdn.jsdelivr.net/gh/yzk656/image/202302101028892.png)

==注意==：在运行JSTL时，报错

```jsp
org.apache.jasper.JasperException: java.lang.ClassNotFoundException: org.apache.jsp._01_002dJSTL的使用_jsp
```

https://blog.csdn.net/qq_27130163/article/details/115665919

![image-20230210212410848](https://cdn.jsdelivr.net/gh/yzk656/image/202302102124928.png)

![image-20230210212423280](https://cdn.jsdelivr.net/gh/yzk656/image/202302102124315.png)

```jsp
<%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/10
  Time: 10:34
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%--通过 taglib 标签引入所需要的标签库--%>
<%@taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%--
    JSTL的使用
        1. 下载JSTL所需要的jar包（standaard.jar 和 jstl.jar）
        2. 在项目的web目录下的web—INF中新建lib目录，将jar包拷贝进去
        3. 选择目录结构 ，将jar包添加为依赖，
--%>
<c:if test="${1==1}">
    Hello JSTL
</c:if>
</body>
</html>
```

![image-20230210212523614](https://cdn.jsdelivr.net/gh/yzk656/image/202302102125698.png)

```jsp
<%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/10
  Time: 22:42
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%--
    常用属性
        test：操作的是域对象，接收返回结果是boolean类型的值(必要属性)
        var：限域变量名（存放在作用域的变量名），用来接收判断结果的值（可选属性）
        scope：限域变量名的范围(page\request\session\application)（可选属性）

        获取结果时 超过指定范围，就获取不到了
--%>
<%
    /*设置数据*/
    request.setAttribute("num", 10);
%>

<c:if test="${num>0}">
    数值大于0
</c:if>

<c:if test="${num>100}" var="flag" scope="request">
</c:if>
${flag}---${sessionScope.flag}--${requestScope.flag}

</body>
</html>
```

![image-20230211002827123](https://cdn.jsdelivr.net/gh/yzk656/image/202302110028193.png)

![image-20230211003725293](https://cdn.jsdelivr.net/gh/yzk656/image/202302110037351.png)

![image-20230211003834679](https://cdn.jsdelivr.net/gh/yzk656/image/202302110038738.png)

![image-20230211004055981](https://cdn.jsdelivr.net/gh/yzk656/image/202302110040028.png)

```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/11
  Time: 0:29
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>

<%
    request.setAttribute("score",80);
%>

<c:choose>
    <c:when test="${score<60}">
        小渣渣
    </c:when>
    <c:when test="${score==60}">
        及格
    </c:when>
    <c:when test="${score>60&&score<=80}">
        良好
    </c:when>
    <c:otherwise>
        大神
    </c:otherwise>
</c:choose>

</body>
</html>
```

![image-20230211004225784](https://cdn.jsdelivr.net/gh/yzk656/image/202302110042859.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202302110043065.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202302110043288.png)

```jsp
<%@ page import="java.util.List" %>
<%@ page import="java.util.ArrayList" %><%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/11
  Time: 0:48
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<c:forEach var="i" begin="1" end="10" step="2">
    ${i}
</c:forEach>

<%
    List<String> list=new ArrayList<>();
    for(int i=1;i<=10;i++){
        list.add("A:"+i);
    }
    pageContext.setAttribute("list",list);
%>

<c:forEach items="${list}" var="i">
    ${i}
</c:forEach>
</body>
</html>
```

![image-20230211010858010](https://cdn.jsdelivr.net/gh/yzk656/image/202302110108090.png)

![image-20230211010934559](https://cdn.jsdelivr.net/gh/yzk656/image/202302110109613.png)

![image-20230211013429417](https://cdn.jsdelivr.net/gh/yzk656/image/202302110134487.png)

![image-20230211013654545](https://cdn.jsdelivr.net/gh/yzk656/image/202302110136623.png)

```jsp
<%--
  Created by IntelliJ IDEA.
  User: 杨振坤
  Date: 2023/2/11
  Time: 1:37
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%--
    如果只是用于一次输出，则不用设置var属性，他会自动输出
    但是如果设置了value属性，想要获取值，就必须使用var属性
    默认类型是Number
--%>


<fmt:formatNumber value="10" type="number" var="num"></fmt:formatNumber>
${num}
<fmt:formatNumber value="10" type="percent"></fmt:formatNumber>
<fmt:formatNumber value="10" type="currency"></fmt:formatNumber>

<%--设置时区--%>
<fmt:setLocale value="en_US"></fmt:setLocale>
<fmt:formatNumber value="10" type="currency"></fmt:formatNumber>


</body>
</html>
```

![image-20230211014946108](https://cdn.jsdelivr.net/gh/yzk656/image/202302110149184.png)

![image-20230211020036853](https://cdn.jsdelivr.net/gh/yzk656/image/202302110200943.png)

```jsp
<%--格式化日期--%>
<%
    request.setAttribute("my_date",new Date());
%>
<fmt:formatDate value="${my_date}"/> <br>
<fmt:formatDate value="${my_date}" type="date"/><br>
<fmt:formatDate value="${my_date}" type="time"/><br>
<fmt:formatDate value="${my_date}" type="both"/><br>
<fmt:formatDate value="${my_date}" type="both" dateStyle="full"/><br>
<fmt:formatDate value="${my_date}" type="both" dateStyle="short"/><br>
<fmt:formatDate value="${my_date}" pattern="yyyy-MM-dd"/><br>
```

![image-20230211020204665](https://cdn.jsdelivr.net/gh/yzk656/image/202302110202740.png)

![image-20230211021000738](https://cdn.jsdelivr.net/gh/yzk656/image/202302110210787.png)

![image-20230211021338735](https://cdn.jsdelivr.net/gh/yzk656/image/202302110213812.png)

```jsp
<%--<fmt:setLocale value="zh_CN"/>--%>
<fmt:parseNumber value="100"/><br>
<fmt:parseNumber value="100" type="number"/><br>
<fmt:parseNumber value="100%" type="percent"/><br>
<fmt:parseNumber value="$100.00" type="currency"/><br>

下面这个注释为解决，上面那个使用中文￥也未解决
<%--<fmt:parseDate value="2:21:10 AM" type="date"/><br>--%>
<fmt:parseDate value="2020/01/16" pattern="yyyy/MM/dd"/><br>
```

## 2023-02-12

![image-20230212110949579](https://cdn.jsdelivr.net/gh/yzk656/image/202302121109679.png)

# 尚硅谷Servlet

## review

![image-20230227150610784](https://cdn.jsdelivr.net/gh/yzk656/image/202302271506858.png)

![image-20230227150854441](https://cdn.jsdelivr.net/gh/yzk656/image/202302271508528.png)

mapping：映射

![image-20230227190419372](https://cdn.jsdelivr.net/gh/yzk656/image/202302271904416.png)

## Servlet处理请求参数中文乱码问题

![image-20230227193719191](https://cdn.jsdelivr.net/gh/yzk656/image/202302271937239.png)

## Servlet继承关系以及Service方法

![image-20230227224448417](https://cdn.jsdelivr.net/gh/yzk656/image/202302272244539.png)

![image-20230227224508511](https://cdn.jsdelivr.net/gh/yzk656/image/202302272245553.png)

![image-20230227224716488](https://cdn.jsdelivr.net/gh/yzk656/image/202302272247529.png)

![image-20230227230314827](https://cdn.jsdelivr.net/gh/yzk656/image/202302272303881.png)

总结：如果我们没有成功重写对应的方法，就会自动调用父类里面的 do 方法，就会产生 405 错误

## Servlet的生命周期

![image-20230301000144245](https://cdn.jsdelivr.net/gh/yzk656/image/202303010001349.png)

==500错误：==内部服务器错误

![image-20230301001227340](https://cdn.jsdelivr.net/gh/yzk656/image/202303010012395.png)

![image-20230301001703708](https://cdn.jsdelivr.net/gh/yzk656/image/202303010017759.png)

## HTTP协议

![image-20230301143758728](https://cdn.jsdelivr.net/gh/yzk656/image/202303011437856.png)



![image-20230301143910083](https://cdn.jsdelivr.net/gh/yzk656/image/202303011439168.png)

![image-20230301144422631](https://cdn.jsdelivr.net/gh/yzk656/image/202303011444700.png)

## Session会话跟踪技术

![image-20230301152159952](https://cdn.jsdelivr.net/gh/yzk656/image/202303011522031.png)

![image-20230301213020322](https://cdn.jsdelivr.net/gh/yzk656/image/202303012130441.png)

![image-20230301213348079](https://cdn.jsdelivr.net/gh/yzk656/image/202303012133139.png)

![image-20230301215750746](https://cdn.jsdelivr.net/gh/yzk656/image/202303012157797.png)

## Session保存作用域

![image-20230301222941527](https://cdn.jsdelivr.net/gh/yzk656/image/202303012229584.png) 

![image-20230301224346533](https://cdn.jsdelivr.net/gh/yzk656/image/202303012243597.png)

## 服务器端转发和客户端重定向

![image-20230302192857583](https://cdn.jsdelivr.net/gh/yzk656/image/202303021928745.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303021944459.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303021946853.png)

状态码：302代表冲重定向

## Thymleaf快速入门

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303022014632.png)

![image-20230304153522148](https://cdn.jsdelivr.net/gh/yzk656/image/202303041535247.png)

## Thymeleaf渲染index页面

![image-20230304160754135](https://cdn.jsdelivr.net/gh/yzk656/image/202303041607213.png)

![image-20230304160804724](https://cdn.jsdelivr.net/gh/yzk656/image/202303041608794.png)

![image-20230304161202493](https://cdn.jsdelivr.net/gh/yzk656/image/202303041612568.png)

![image-20230304162933121](https://cdn.jsdelivr.net/gh/yzk656/image/202303041629182.png)

## thymeleaf—review

1. Post提交方式下的设置编码，防止中文乱码

2. request.setCharacterEncoding("UTF-8");

3. get提交方式，tomcat8开始，编码不需要设置

   ![image-20230306152637233](https://cdn.jsdelivr.net/gh/yzk656/image/202303061526379.png)

4. Servlet继承关系以及生命周期

   ​	Servlet接口：init（）、service（）、destory（）

![image-20230307001826185](https://cdn.jsdelivr.net/gh/yzk656/image/202303070018308.png)

![image-20230307002204758](https://cdn.jsdelivr.net/gh/yzk656/image/202303070022816.png)

![image-20230308210234668](https://cdn.jsdelivr.net/gh/yzk656/image/202303082102761.png)

![image-20230308210244666](https://cdn.jsdelivr.net/gh/yzk656/image/202303082102741.png)

![image-20230308210319478](https://cdn.jsdelivr.net/gh/yzk656/image/202303082103550.png)

![image-20230308210651564](https://cdn.jsdelivr.net/gh/yzk656/image/202303082106640.png)

![image-20230308210824707](https://cdn.jsdelivr.net/gh/yzk656/image/202303082108765.png)

==Thymeleaf是面向Web和独立环境的现代服务器端Java模板引擎==

![image-20230308211223276](https://cdn.jsdelivr.net/gh/yzk656/image/202303082112351.png)

## Servlet保存作用域



![image-20230308211832959](https://cdn.jsdelivr.net/gh/yzk656/image/202303082118031.png)

![image-20230308212336994](https://cdn.jsdelivr.net/gh/yzk656/image/202303082123062.png)

==客户端的理解：==

> 不一定。两个不同的链接可能代表着同一个客户端，也可能代表着不同的客户端，这取决于链接的来源和目的。比如，如果您在同一个浏览器中打开两个不同的网页，那么这两个网页都是属于同一个客户端的。但是，如果您在不同的设备或浏览器中打开两个不同的网页，那么这两个网页就是属于不同的客户端的

==不同的设备或浏览器中打开两个相同的网页，那么这两个网页就是属于不同的客户端的吗？==

> 是的，不同的设备或浏览器中打开两个相同的网页，那么这两个网页就是属于不同的客户端的。因为每个客户端都有自己的IP地址和用户代理等信息，服务器可以根据这些信息来区分不同的客户端。

![image-20230308213230492](https://cdn.jsdelivr.net/gh/yzk656/image/202303082132567.png)

![image-20230308214225084](https://cdn.jsdelivr.net/gh/yzk656/image/202303082142151.png)

![image-20230308214410919](https://cdn.jsdelivr.net/gh/yzk656/image/202303082144994.png)

==总结==

![image-20230308214837189](https://cdn.jsdelivr.net/gh/yzk656/image/202303082148248.png)

## Servlet路径问题

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303091246859.png)

![image-20230309124843456](https://cdn.jsdelivr.net/gh/yzk656/image/202303091248489.png)

![image-20230309125334334](https://cdn.jsdelivr.net/gh/yzk656/image/202303091253377.png)

> [您好，这是必应。th:href是一个链接表达式，用于在Thymeleaf模板中创建URL](https://www.thymeleaf.org/doc/articles/standardurlsyntax.html)[1](https://www.thymeleaf.org/doc/articles/standardurlsyntax.html)[。它的意思是“超文本引用”，它指定了链接的目标地址](https://www.pcmag.com/encyclopedia/term/href)[2](https://www.pcmag.com/encyclopedia/term/href)[3](https://www.semrush.com/blog/ahref-link/)[4](https://blog.hubspot.com/website/html-a-href)[。例如，th:href="@{http://www.example.com}"表示一个指向http://www.example.com的绝对URL](https://www.thymeleaf.org/doc/articles/standardurlsyntax.html)[1](https://www.thymeleaf.org/doc/articles/standardurlsyntax.html)。
>
>  
>
> [如果大括号中没有内容，那么th:href会使用当前页面的URL作为链接的目标地址](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html)[1](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html)[。这可以用于创建相对于当前页面的URL](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html)[1](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html)[。例如，th:href="@{}“表示当前页面的URL，th:href=”@{/login}"表示当前页面所在目录下的login页面](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html)[1](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html)
>
>  
>
> 所说的页面指的就是当前 HTML 页面

## 编辑和修改特定库存信息

```jsp
<!-- <td><a th:text="${fruit.fname}" th:href="@{'/edit.do?fid='+${fruit.fid}}">苹果</a></td> -->
<!--加上一个@{}：就是代表基于根目录查找edit.do文件-->
<!--如果是字符串+变量 则'字符串'+${变量} -->
<!--对于URL中的参数，也可以不写问号，写一个小括号，变量之间通过 逗号 隔开，不过获取变量还是通过 ${} 来获取-->
<td><a th:text="${fruit.fname}" th:href="@{/edit.do(fid=${fruit.fid})}">苹果</a></td>
```

![image-20230310000516080](https://cdn.jsdelivr.net/gh/yzk656/image/202303100005135.png)

> 接口中的方法都要实现吗
>
> 接口中的方 法是否都要实现取决于实现接口的类是否是抽象类。如果是非抽象类，则必须实现接口中的所有方法；如果是抽象类，则可以不实现接口中的所有方法，但是子类化该抽象类时必须实现缺少的方法。
>
>  
>
> 什么是子类化该抽象类
>
> [子类化该抽象类是指用一个子类来继承抽象父类](https://blog.csdn.net/Birdmotianlun/article/details/107949952)[1](https://blog.csdn.net/Birdmotianlun/article/details/107949952)[。子类必须覆盖重写抽象父类当中所有的抽象方法，否则该子类也要声明为抽象类](https://blog.csdn.net/Birdmotianlun/article/details/107949952)[1](https://blog.csdn.net/Birdmotianlun/article/details/107949952)[2](https://blog.csdn.net/qq_44718582/article/details/105720639)。

## 状态码

200：正常

404：找不到资源

405：请求方式不支持

500：服务器内部错误

# Maven

## Maven概述

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303121502099.png)

![image-20230312150527760](https://cdn.jsdelivr.net/gh/yzk656/image/202303121505819.png)

![image-20230312150756111](https://cdn.jsdelivr.net/gh/yzk656/image/202303121507175.png)

## Maven简介

![image-20230312155556998](https://cdn.jsdelivr.net/gh/yzk656/image/202303121555086.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303121603560.png)

## Maven安装&配置及使用

具体安装步骤：







![image-20230312160416456](https://cdn.jsdelivr.net/gh/yzk656/image/202303121604518.png)

![image-20230312162346164](https://cdn.jsdelivr.net/gh/yzk656/image/202303121623205.png)

编译： mvn compile

清理产生文件：mvn clean

将 Java项目 打包成 jar包： mvn package

执行测试代码：mvn test

将打包成的 jar 包安装到本地仓库：mvn install

![image-20230312172344385](https://cdn.jsdelivr.net/gh/yzk656/image/202303121723450.png)

![image-20230312172646430](https://cdn.jsdelivr.net/gh/yzk656/image/202303121726487.png)

## idea配置Maven

![image-20230312172744894](https://cdn.jsdelivr.net/gh/yzk656/image/202303121727972.png)

![image-20230312173111903](https://cdn.jsdelivr.net/gh/yzk656/image/202303121731963.png)

![image-20230312174457538](https://cdn.jsdelivr.net/gh/yzk656/image/202303121744622.png)

![image-20230312174418012](https://cdn.jsdelivr.net/gh/yzk656/image/202303121744102.png)

## 依赖管理&依赖范围

 ![image-20230312175049022](https://cdn.jsdelivr.net/gh/yzk656/image/202303121750083.png)

![image-20230312181809995](https://cdn.jsdelivr.net/gh/yzk656/image/202303121818062.png)

![image-20230312182013790](https://cdn.jsdelivr.net/gh/yzk656/image/202303121820856.png)

![image-20230312202736594](https://cdn.jsdelivr.net/gh/yzk656/image/202303122027662.png)



# MyBatis

## MyBatis简介

![image-20230312203755819](https://cdn.jsdelivr.net/gh/yzk656/image/202303122037902.png)

![image-20230312205003122](https://cdn.jsdelivr.net/gh/yzk656/image/202303122050173.png)

![image-20230312211220289](https://cdn.jsdelivr.net/gh/yzk656/image/202303122112349.png)

![image-20230312211904867](https://cdn.jsdelivr.net/gh/yzk656/image/202303122119992.png)

![image-20230312212215364](https://cdn.jsdelivr.net/gh/yzk656/image/202303122122507.png)

## MyBatis快速入门

![image-20230312212629279](https://cdn.jsdelivr.net/gh/yzk656/image/202303122126377.png)

<img src="https://cdn.jsdelivr.net/gh/yzk656/image/202303130011243.png" alt="image-20230313001128171" style="zoom:150%;" />

![image-20230313001143273](https://cdn.jsdelivr.net/gh/yzk656/image/202303130011330.png)

> 对于mybatis的文件结构
>
>  
>
> SqlSessionFactory
>
> ​		数据库连接信息
>
> ​		mappers：数据库映射文件
>
>  
>
> 对于数据映射文件一般是以要操作的表的名字进行命名
>
> ​	如操作User表：UserMapper.xml
>
> ​	Mapper：映射
>
>  
>
> sql语句是写在这个映射文件

## Mapper代理开发

![image-20230313152003477](https://cdn.jsdelivr.net/gh/yzk656/image/202303131520576.png)

![image-20230313152039258](https://cdn.jsdelivr.net/gh/yzk656/image/202303131520351.png)

==全限定类名是指类名的全称，包括包路径，用点隔开，例如java.lang.String 。全限定类名可以唯一地标识一个类，避免与其他同名的类混淆==

==如果您使用mapper接口方式开发整合，那么namespace写的是mapper接口的类名，例如com.example.mapper.UserMapper。==

> 根据搜索结果，mapper接口和mapper文件的关联是通过namespace属性来实现的。namespace属性必须指定为mapper接口的全限定类名，这样mybatis就能根据接口方法的名称和xml文件中的id来匹配对应的sql语句
>
>  
>
> ```
> /*UserMapper.class是一个接口的类对象，它定义了一些方法，例如getRole，insertUser等。*/
> ```
>
>  
>
> 注意：
>
> 整个流程：获取sqlSession=》获取接口的代理对象（通过接口获取）=》找到接口后就找到了同级的XML文件=》然后执行方法，就能找到接口中的抽象方法（这个抽象方法也就是xml文件的SQL语句的ID）=》也就能找到对应的SQL语句并执行



> 当 进行加载SQL映射文件时，由于可能以后会出现多个XML映射文件，为了简化，可以使用包扫描的方式
>
>  
>
> ```
>         <!--加载sql映射文件-->
> <!--        <mapper resource="com/itheima/mapper/UserMapper.xml"/>-->
> 
>         <!--Mapper代理方式：使用包扫描-->
>         <!--会将所有XML文件加载到接口的目录下-->
>         <package name="com.itheima.mapper"/>
> ```



![image-20230313152453014](https://cdn.jsdelivr.net/gh/yzk656/image/202303131524068.png)

![image-20230313182858932](https://cdn.jsdelivr.net/gh/yzk656/image/202303131828979.png)

![image-20230313182958222](https://cdn.jsdelivr.net/gh/yzk656/image/202303131829258.png)

编译后的文件：

![image-20230313183028150](https://cdn.jsdelivr.net/gh/yzk656/image/202303131830196.png)

## MyBatis核心配置文件

![image-20230313221542164](https://cdn.jsdelivr.net/gh/yzk656/image/202303132215328.png)

![image-20230313222201353](https://cdn.jsdelivr.net/gh/yzk656/image/202303132222449.png)

## MyBatis案例-环境准备

![image-20230313222421985](https://cdn.jsdelivr.net/gh/yzk656/image/202303132224099.png)

![image-20230313222726089](https://cdn.jsdelivr.net/gh/yzk656/image/202303132227182.png)

## 查询所有&结果映射

![image-20230313225135539](https://cdn.jsdelivr.net/gh/yzk656/image/202303132251631.png)

==结局Mybatis的XML文件在写SQL语句时没有提示==

![image-20230314002727755](https://cdn.jsdelivr.net/gh/yzk656/image/202303140027817.png)

![image-20230314004449677](https://cdn.jsdelivr.net/gh/yzk656/image/202303140044762.png)

```XML
    <!--
        数据库表的字段名称 和 实体类的属性名称 不一样，则不能自动封装数据
            起别名：对不一样的列名，让别名和实体类的属性名一样
                缺点：每次查询都要定义一次别名
                解决办法：使用SQL片段
                    确定：不灵活
                引出新的解决方案：ResultMap
                    1. 定义<resultMap>标签
                    2. 在<select>标签中，使用ResultMap属性替换ResultType属性
    -->
    <!--
        SQL片段
    -->
<!--    <sql id="brand_column">
        id,brand_name as brandName,company_name as companyName,ordered,description,status
    </sql>
    <select id="selectAll" resultType="com.itheima.pojo.Brand">
        select <include refid="brand_column"/>
            from tb_brand;
    </select>-->

    <!--
        id:唯一标识
        type：映射类型，支持别名
    -->
    <resultMap id="brandResultMap" type="com.itheima.pojo.Brand">
        <!--
            id：完成主键字段的映射
            result：完成一般字段的映射
                column：数据库中表的列名
                property：Java程序中的属性名
        -->
        <result column="brand_name" property="brandName"/>
        <result column="company_name" property="companyName"/>
    </resultMap>

    <!--注意看此时的ResultType=>ResultMap-->
    <select id="selectAll" resultMap="brandResultMap">
        select *
        from tb_brand;
    </select>
```

## 查询-查看详情

![image-20230314103623014](https://cdn.jsdelivr.net/gh/yzk656/image/202303141036082.png)

==关于${}和#{}==

> 那么什么情况下必须使用${}呢？
>
>  
>
> [一般来说，什么情况下必须使用${}呢？就是当我们需要拼接的变量上不能带单引号时，就必须使用${}](https://www.cnblogs.com/bear7/p/13696911.html)[1](https://bing.com/search?q=Mybatis什么情况下必须使用%24{})[2](https://www.cnblogs.com/bear7/p/13696911.html)[。例如，如果你的SQL语句中需要动态指定表名或者排序字段，那么就必须使用${}，因为这些地方不能用预编译的占位符](https://blog.csdn.net/Ahuuua/article/details/113352377)[3](https://blog.csdn.net/Ahuuua/article/details/113352377)。例如：
>
> ```sql
> select * from ${tableName} order by ${sortField}
> ```
>
> 
>
> 为什么表名和排序字段不能用占位符代替 ?
>
>  
>
> 表名和排序字段不能用占位符代替的原因是，占位符只能替换值，而不能替换表名或字段名。如果使用占位符，那么SQL语句会被预编译，占位符的两边会自动加上单引号。这样就会导致SQL语句无法执行，因为表名和字段名不能用单引号引起来。您可以理解为，占位符是用来传递参数的，而不是用来拼接SQL语句的。
>
>  
>
> 比如，如果是使用 = 可以使用${} 来进行传递参数：
>
> ```sql
> select * from tb_brand where id=#{id};
> ```
>
>  
>
> 但是如果是单个不是赋值的，就必须使用替换值，也就是拼接，使有 ${}
>
> 否则就会出现下面情况
>
> ```sql
> select * from ? order by ?
> ```
>
>  这样的SQL语句是无法执行的，因为表名和排序字段不能用占位符代替。
>
> 
>
> 注意事项：
>
> [一般来说，什么情况下必须使用${}呢？就是当我们需要拼接的变量上不能带单引号时，就必须使用${}例如，如果你的SQL语句中需要动态指定表名或者排序字段，那么就必须使用${}，因为这些地方不能用预编译的占位符。例如：
>
> ```sql
> select * from ${tableName} order by ${sortField}
> ```

![image-20230314111708805](https://cdn.jsdelivr.net/gh/yzk656/image/202303141117875.png)

```xml
    <!--通过ID进行查看详情-->
    <!--
        参数占位符
            1. #{}:会将其替换成 ？，为了防止SQL注入
            2. ${}：拼接SQL，会存在SQL注入问题
        使用时机：
            参数传递过程：#{}
            表名或者列名不固定的情况下使用${}
        特殊字符处理
            1. 转义字符
                小于号：&lt;
            2. CDATA区
                小于： <![CDATA[
                         <
                      ]]>

    -->
<!--    <select id="selectById" resultMap="brandResultMap">
        select * from tb_brand where id=#{id};
    </select>-->
    <select id="selectById" resultMap="brandResultMap">
        select * from tb_brand where id <![CDATA[
            <
        ]]> #{id};
    </select>
```

## 查询-条件查询

![image-20230314111906163](https://cdn.jsdelivr.net/gh/yzk656/image/202303141119251.png)

![image-20230314111914593](https://cdn.jsdelivr.net/gh/yzk656/image/202303141119658.png)



![image-20230314111922075](https://cdn.jsdelivr.net/gh/yzk656/image/202303141119149.png)

![image-20230314132057831](https://cdn.jsdelivr.net/gh/yzk656/image/202303141320914.png)

```java
    /**
     * 条件查询：
     *    参数接收
     *      1. 散装参数（如果有多个参数时，需要使用@Param("SQL参数占位符名称")）
     *      2. 对象参数(对象属性名称要和参数占位符名称一致)
     *      3. Map集合参数
     *
     * @param status
     * @param companyName
     * @param brandName
     * @return
     */
//    List<Brand> selectByCondition(@Param("status")int status,@Param("companyName")String companyName,@Param("brandName")String brandName);
//    List<Brand> selectByCondition(Brand brand);
    List<Brand> selectByCondition(Map map);
```



```Java
        /*接收参数*/
        int status = 1;
        String companyName = "华为";
        String brandName = "华为";

        /*由于SQL语句采用的是模糊查询（like），因此要进行处理参数*/
        companyName = "%" + companyName + "%";
        brandName = "%" + brandName + "%";

        /*封装成对象*/
        Brand brand = new Brand();
        brand.setStatus(status);
        brand.setBrandName(brandName);
        brand.setCompanyName(companyName);

        /*封装成Map集合*/
        Map map = new HashMap();
        map.put("status", status);
        map.put("companyName", companyName);
        map.put("brandName", brandName);


        /*1. 获取SQLSessionFactory对象*/
        String resource = "mybatis-config.xml";
        InputStream inputStream = getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);

        /*2. 获取SQLSess对象*/
        SqlSession sqlSession = sqlSessionFactory.openSession();

        /*3.获取Mapper接口的代理对象*/
        BrandMapper mapper = sqlSession.getMapper(BrandMapper.class);

        /*4. 执行方法*/
//        List<Brand> brands=mapper.selectByCondition(status,companyName,brandName);
//        List<Brand> brands = mapper.selectByCondition(brand);
        List<Brand> brands=mapper.selectByCondition(map);
        System.out.println(brands);
        sqlSession.close();
```

## 动态条件查询

前因：必须输入三个选择值，而不能根据一个选择值进行查询

![image-20230314132607162](https://cdn.jsdelivr.net/gh/yzk656/image/202303141326213.png)

![image-20230314132459852](https://cdn.jsdelivr.net/gh/yzk656/image/202303141324899.png)

解决办法：

![image-20230314132700397](https://cdn.jsdelivr.net/gh/yzk656/image/202303141327462.png)

```XML
    <!--
        动态条件查询
            if:条件判断
                test：逻辑判断
            问题：
                and会报错
            解决：
                使用恒等式（1=1）
                <where>标签 替换 where【第一个判断开头也不同写 and ，正常写就行】
    -->
    <select id="selectByCondition" resultMap="brandResultMap">
        select *
        from tb_brand
        <where>
            <if test="status != null">
                status=#{status}
            </if>
            <if test="companyName !=null and companyName !=''">
                and company_name like #{companyName}
            </if>
            <if test="brandName !=null and brand_name !=''">
                and brand_name like #{brandName};
            </if>
        </where>
    </select>
```



![image-20230314144348889](https://cdn.jsdelivr.net/gh/yzk656/image/202303141443944.png)

![image-20230314144628012](https://cdn.jsdelivr.net/gh/yzk656/image/202303141446085.png)

![image-20230314144723405](https://cdn.jsdelivr.net/gh/yzk656/image/202303141447459.png)

```xml
    <!--
        单条件动态查询
            使用where标签，就可以不用写otherwise了，因为如果你的where标签如果有问题，就会帮你自动解决
    -->
    <select id="selectByConditionSingle" resultMap="brandResultMap">
        select *
        from tb_brand
        <where>
            <choose><!--相当于switch-->
                <when test="status != null"><!--相当于case-->
                    status=#{status}
                </when>
                <when test="companyName !=null and companyName !=''">
                    company_name like #{companyName}
                </when>
                <when test="brandName !=null and brand_name !=''">
                    brand_name like #{brandName};
                </when>
                <otherwise>
                    1=1
                </otherwise>
            </choose>
        </where>
    </select>
```

## 添加&&修改功能

![image-20230314151157234](https://cdn.jsdelivr.net/gh/yzk656/image/202303141511302.png)

> 使用mybatis进行数据库操作时，为什么还要提交事务?
>
>  
>
> 使用mybatis进行数据库操作时，为什么还要提交事务呢？这是因为mybatis的事务控制方式其本质也是JDBC的setAutoCommit()方法来设置事务提交的方式的[1](https://blog.csdn.net/weixin_44547914/article/details/109166504)[2](https://cloud.tencent.com/developer/article/1589662)[3](https://blog.csdn.net/m0_67402774/article/details/123990337)。如果不手动提交事务，那么对数据库的增删改操作可能不会生效[4](https://blog.csdn.net/kangshihang1998/article/details/118637542)[5](https://zhuanlan.zhihu.com/p/133807626)。
>
> 你可以通过在获取sqlsession对象时传入一个布尔值参数来设置是否自动提交事务[3](https://blog.csdn.net/m0_67402774/article/details/123990337)。例如：
>
> ```java
> SqlSession session = sqlSessionFactory.openSession(true); //自动提交
> ```
>
> [或者在执行完增删改操作后调用sqlsession对象的commit()方法来手动提交事务](https://blog.csdn.net/kangshihang1998/article/details/118637542)[4](https://blog.csdn.net/kangshihang1998/article/details/118637542)。例如：
>
> ```java
> session.insert("insertUser", user);
> session.commit(); //手动提交
> ```
>
> 希望这能回答你的问题。

![image-20230314190239090](https://cdn.jsdelivr.net/gh/yzk656/image/202303141902197.png)

![image-20230314190903181](https://cdn.jsdelivr.net/gh/yzk656/image/202303141909236.png)

> mybatis中useGeneratedKeys属性是干嘛的?
>
> useGeneratedKeys属性是Mybatis的一个配置参数，它只对insert语句有效，用于获取数据库自动生成的主键
>
>  
>
> 为什么要使用这个属性？
>
> 使用这个属性的目的是为了在插入数据后，能够获取数据库自动生成的主键值
>
> 
>
> 那mybatis中的keyProperty属性是干嘛的?
>
> keyProperty属性是用来指定存放主键值的属性名。如果你在插入数据时使用了一个实体类对象，那么keyProperty就是实体类中的属性名

![image-20230314191428362](https://cdn.jsdelivr.net/gh/yzk656/image/202303141914426.png)

![image-20230314192307843](https://cdn.jsdelivr.net/gh/yzk656/image/202303141923928.png)

## 删除功能

![image-20230314195930046](https://cdn.jsdelivr.net/gh/yzk656/image/202303141959106.png)

![image-20230314200525828](https://cdn.jsdelivr.net/gh/yzk656/image/202303142005898.png)

## 参数传递

![image-20230314220841036](https://cdn.jsdelivr.net/gh/yzk656/image/202303142208118.png)

![image-20230314221632749](https://cdn.jsdelivr.net/gh/yzk656/image/202303142216821.png)

![image-20230314221706149](https://cdn.jsdelivr.net/gh/yzk656/image/202303142217199.png)

![image-20230314221733928](https://cdn.jsdelivr.net/gh/yzk656/image/202303142217983.png)



![image-20230314222203202](https://cdn.jsdelivr.net/gh/yzk656/image/202303142222257.png)

![image-20230314222530650](https://cdn.jsdelivr.net/gh/yzk656/image/202303142225724.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303142230768.png)

注意看，对于普通类型和map类型是可以直接

==总结：==

![image-20230314223033942](https://cdn.jsdelivr.net/gh/yzk656/image/202303142230029.png)

![image-20230314224503203](https://cdn.jsdelivr.net/gh/yzk656/image/202303142245269.png)

## 注解开发

![image-20230314224552243](https://cdn.jsdelivr.net/gh/yzk656/image/202303142245318.png)

> 在进行业务开发时，mybatis操作数据时应该使用xml配置还是注解?
>
> 
>
> [mybatis操作数据时使用xml配置还是注解，主要取决于您的具体需求和场景。一般来说，xml配置和注解有以下几点区别](https://blog.csdn.net/qq_43116031/article/details/129436046)[1](https://blog.csdn.net/qq_43116031/article/details/129436046)[2](https://blog.csdn.net/qq_68500904/article/details/124292259)[3](https://blog.csdn.net/jiatai_/article/details/97613804)[4](https://www.cnblogs.com/binbingg/p/13796239.html):
>
> - xml配置可以更灵活地编写和修改SQL语句，不需要重新编译和部署代码，也可以动态生成SQL语句。
> - 注解可以简化配置文件的编写，适合简单的数据处理，可读性高，但是不方便动态生成SQL语句。
>
> 您可以根据您的项目规模、复杂度、性能等因素来选择合适的方式。

## 参数注解何时使用

我理解你的困惑。让我为你解释一下在 MyBatis 中何时需要使用 `@Param` 注解以及何时不需要。

在 MyBatis 中，大部分情况下，你不需要使用 `@Param` 注解，特别是当你的方法只有一个参数时。MyBatis 会根据参数的类型自动进行参数映射，无需额外的注解。例如：

```java
public interface UserMapper {
    User getUserById(int id);
}
```

在上述例子中，`getUserById` 方法只有一个参数，即 `int id`，无需使用 `@Param` 注解。

然而，当你的方法有多个参数，且这些参数类型相同（或者 MyBatis 无法自动判断参数名称）时，你可能需要使用 `@Param` 注解来为参数指定名称，以便在 Mapper XML 文件中引用这些参数。例如：

```java
public interface UserMapper {
    List<User> getUsersByIdAndName(@Param("id") int id, @Param("age") int age);
}
```

在上述例子中，由于存在两个 `int` 类型的参数，MyBatis 可能无法自动判断它们的名称，所以我们使用 `@Param` 注解来指定参数的名称。

总结：

1. 单参数方法：不需要 `@Param` 注解。
2. 多参数方法且参数类型不同：不需要 `@Param` 注解。
3. 多参数方法且参数类型相同：使用 `@Param` 注解来明确指定参数的名称，以便在 Mapper XML 文件中引用。

记住，`@Param` 注解的目的是为了在方法参数较复杂或有歧义的情况下，明确告诉 MyBatis 如何将参数映射到 SQL 查询中。



## 那不同的数据类型指的是哪些

在 MyBatis 中，当方法参数的类型不同时，MyBatis 可以根据参数的名称自动映射参数值到 SQL 语句中的占位符，无需使用 `@Param` 注解。然而，当方法参数的类型相同或存在歧义时，就可能需要使用 `@Param` 注解来明确指定参数的名称。

不同的数据类型指的是 Java 中的不同数据类型，例如：

1. 基本数据类型（`int`, `double`, `float`, `boolean`, 等）
2. 包装类（`Integer`, `Double`, `Float`, `Boolean`, 等）
3. 字符串（`String`）
4. 自定义类（例如，`User`, `Product` 等）
5. 集合类型（`List`, `Set`, `Map` 等）

当方法参数包含上述不同的数据类型，并且没有歧义时，MyBatis 通常可以正确地进行参数映射。例如：

```java
public interface UserMapper {
    User getUserById(int id);
    List<User> getUsersByRoleAndStatus(String role, boolean isActive);
    List<User> getUsersByCriteria(Map<String, Object> criteria);
}
```

在上述例子中，`getUserById` 方法的参数类型是基本数据类型，`getUsersByRoleAndStatus` 方法的参数包括基本数据类型和布尔型，`getUsersByCriteria` 方法的参数是一个 `Map`。

在这些方法中，MyBatis 可以根据参数的名称自动映射参数值，无需使用 `@Param` 注解。

然而，当方法参数类型相同或存在歧义时，例如有多个参数类型都是相同的基本数据类型，或者参数类型是一个自定义类而不是基本数据类型或字符串，此时可能需要使用 `@Param` 注解来明确指定参数的名称，以确保正确的参数映射。



# 黑马Servlet

## Maven安装Tomcat插件

![image-20230315153949433](https://cdn.jsdelivr.net/gh/yzk656/image/202303151539543.png)

## Servlet快速入门

![image-20230315160121551](https://cdn.jsdelivr.net/gh/yzk656/image/202303151601623.png)

provided
provided适合在编译和测试的环境，他和compile很接近，但是provide仅仅需要在编译和测试阶段，同样provide将不会被打包到lib目录下。

==注意：==

这里的servlet要配置成provided，因为打包成war后Tomcat中的servlet会与这个依赖产生冲突。而如果使用provided，则只会在编译和测试时生效，并不会打包进war包

## Servlet执行流程和生命周期

![image-20230315161246338](https://cdn.jsdelivr.net/gh/yzk656/image/202303151612425.png)

![image-20230315161837241](https://cdn.jsdelivr.net/gh/yzk656/image/202303151618324.png)

## Servlet方法介绍&体系结构

![image-20230315162545802](https://cdn.jsdelivr.net/gh/yzk656/image/202303151625867.png)

![image-20230315163735209](https://cdn.jsdelivr.net/gh/yzk656/image/202303151637292.png)

## URLPattern配置

![image-20230315185406613](https://cdn.jsdelivr.net/gh/yzk656/image/202303151854697.png)

![image-20230315185834072](https://cdn.jsdelivr.net/gh/yzk656/image/202303151858139.png)

![image-20230315191447737](https://cdn.jsdelivr.net/gh/yzk656/image/202303151914785.png)



![image-20230315191426795](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230315191435418.png)

==注意：==

当路径同时满足精确匹配和目录匹配，精确匹配的优先级更高

注意拓展名的路径不用加  `/` 

`/*` 的优先级高于 `/`

默认的匹配路径是可以访问静态资源的（HTML），如果更改匹配格式为 `/` 则不能访问静态资源了

## XML配置Servlet

![image-20230315191531591](https://cdn.jsdelivr.net/gh/yzk656/image/202303151915655.png)

```xml
    <servlet>
        <!--这个servlet-name只是为了和mapping对应所起的名字-->
        <servlet-name>servlet01</servlet-name>
        <!--这个是缩写的Servlet服务的类名-->
        <servlet-class>servlet01</servlet-class>
    </servlet>
    <!--创建Servlet映射-->
    <servlet-mapping>
        <!--对应XML文件的servlet-name的名字-->
        <servlet-name>servlet01</servlet-name>
        <!--这个是以后指定的访问地址-->
        <url-pattern>/01</url-pattern>
    </servlet-mapping>
```

## Request和Response介绍&Request继承体系

![image-20230315192426903](https://cdn.jsdelivr.net/gh/yzk656/image/202303151924989.png)

![image-20230316001643466](https://cdn.jsdelivr.net/gh/yzk656/image/202303160016547.png)

## Request获取请求数据-请求行&请求头&请求体

![image-20230316002609979](https://cdn.jsdelivr.net/gh/yzk656/image/202303160026037.png)

![image-20230316002750935](https://cdn.jsdelivr.net/gh/yzk656/image/202303160027979.png)

## Request通用方式获取请求参数

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303160039900.png)

	## idea模板创建Servlet

![image-20230316083549726](https://cdn.jsdelivr.net/gh/yzk656/image/202303160835826.png)

## 请求参数中文乱码-Post解决方案

![image-20230316085924258](https://cdn.jsdelivr.net/gh/yzk656/image/202303160859308.png)

## Request请求转发

![image-20230316090316313](https://cdn.jsdelivr.net/gh/yzk656/image/202303160903371.png)

![image-20230316090639568](https://cdn.jsdelivr.net/gh/yzk656/image/202303160906616.png)

![image-20230316090907867](https://cdn.jsdelivr.net/gh/yzk656/image/202303160909912.png)

## Response设置响应数据功能&完成重定向

![image-20230316091509436](https://cdn.jsdelivr.net/gh/yzk656/image/202303160915515.png)

![image-20230316094733921](https://cdn.jsdelivr.net/gh/yzk656/image/202303160947977.png)

![image-20230316095226356](https://cdn.jsdelivr.net/gh/yzk656/image/202303160952414.png)

![image-20230316095254558](https://cdn.jsdelivr.net/gh/yzk656/image/202303160952597.png)

## 资源路径问题

![image-20230316100031914](https://cdn.jsdelivr.net/gh/yzk656/image/202303161000996.png)

## Response响应字符&字节数据

![image-20230316100510102](https://cdn.jsdelivr.net/gh/yzk656/image/202303161005145.png)

想要显示HTML

![image-20230316101139567](https://cdn.jsdelivr.net/gh/yzk656/image/202303161011620.png)

出现中文乱码

setContentType不仅可以设置头的编码，也可以设置流的编码，因此要写在流（getWriter（））的前面

![image-20230316101549096](https://cdn.jsdelivr.net/gh/yzk656/image/202303161015145.png)

==字节数据==

![image-20230316104351632](https://cdn.jsdelivr.net/gh/yzk656/image/202303161043676.png)

![image-20230316110126537](https://cdn.jsdelivr.net/gh/yzk656/image/202303161101578.png)

![image-20230316105453048](https://cdn.jsdelivr.net/gh/yzk656/image/202303161054099.png)

有点麻烦，可以采用阿帕奇的依赖：

![image-20230316105922818](https://cdn.jsdelivr.net/gh/yzk656/image/202303161059862.png)

![image-20230316105954069](https://cdn.jsdelivr.net/gh/yzk656/image/202303161059114.png)

## 封装前台传过来的JavaBean

1. 先安装所对应jar包

   ![image-20230418111942310](https://cdn.jsdelivr.net/gh/yzk656/image/202304181119675.png)

2. 使用方法

3. ```java
           /*获取表单数据*/
           User user=new User();
           try {
               BeanUtils.populate(user,request.getParameterMap());
           } catch (Exception e) {
               throw new RuntimeException(e);
           }
   ```



# 案例

## 用户登录-准备环境&代码实现

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303162043410.png)

![image-20230316204430124](https://cdn.jsdelivr.net/gh/yzk656/image/202303162044177.png)

```XML
<!--由于是XML文件，所以 & 符号要使用&amp;来进行替换-->
<property name="url" value="jdbc:mysql:///db1?useSSL=false&amp;useServerPrepStmts=true"/>
```

> mybatis 在进行查询时为什么多个参数要加上@parm?
>
>  
>
> [Mybatis在进行查询时，如果方法有多个参数，需要使用@Param注解来指定参数的名称，否则会报错](https://blog.csdn.net/neusoft2016/article/details/110818507)[1](https://blog.csdn.net/neusoft2016/article/details/110818507)[2](https://blog.csdn.net/Joash_Wu/article/details/122024251)[。这是因为Mybatis默认会将方法的参数封装成一个Map对象，其中key为param1,param2,…，value为参数的值](https://blog.csdn.net/Mrqiang9001/article/details/79520436)[3](https://blog.csdn.net/Mrqiang9001/article/details/79520436)[。如果不使用@Param注解来指定key的名称，那么在XML文件中就无法通过#{paramName}来引用参数的值](https://blog.csdn.net/Mrqiang9001/article/details/79520436)[3](https://blog.csdn.net/Mrqiang9001/article/details/79520436)。
>
> 例如，如果方法定义如下：
>
> ```java
> List<Device> getDeviceListTest (String deviceId,String deviceName);
> ```
>
> 那么在XML文件中就需要写成：
>
> ```xml
> <select id="getDeviceListTest" resultType="Device">
>     select * from device where device_id=#{param1} and device_name=#{param2}
> </select>
> ```
>
> 而如果使用了@Param注解来指定参数的名称，如下：
>
> ```java
> List<Device> getDeviceListTest (@Param("deviceId") String deviceId,@Param("deviceName") String deviceName);
> ```
>
> 那么在XML文件中就可以写成：
>
> ```xml
> <select id="getDeviceListTest" resultType="Device">
>     select * from device where device_id=#{deviceId} and device_name=#{deviceName}
> </select>
> ```
>
> 这样可以提高代码的可读性和维护性[1](https://blog.csdn.net/neusoft2016/article/details/110818507)[3](https://blog.csdn.net/Mrqiang9001/article/details/79520436)。

## 用户注册

![image-20230317151845491](https://cdn.jsdelivr.net/gh/yzk656/image/202303171518581.png)

## SqlSessionFactory工具类提取

![image-20230317203755923](https://cdn.jsdelivr.net/gh/yzk656/image/202303172037994.png)

注意：静态方法只会执行一次

![image-20230317205222642](https://cdn.jsdelivr.net/gh/yzk656/image/202303172052704.png)

```Java
/*sqlSession是不能抽取到工具类中的，因为一个Session就相当于一个数据库连接*/
SqlSession sqlSession = sqlSessionFactory.openSession(true);
```

# JSP

## JSP概述&快速入门&原理

![image-20230317224233175](https://cdn.jsdelivr.net/gh/yzk656/image/202303172242242.png)

![image-20230318093905065](https://cdn.jsdelivr.net/gh/yzk656/image/202303180939147.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303181043234.png)

![image-20230318104156530](https://cdn.jsdelivr.net/gh/yzk656/image/202303181041593.png)

## JSP脚本

![image-20230318104523172](https://cdn.jsdelivr.net/gh/yzk656/image/202303181045232.png)

![image-20230318104734195](https://cdn.jsdelivr.net/gh/yzk656/image/202303181047256.png)

## JSP缺点

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303181538608.png)

## EL表达式

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303181558973.png)

![image-20230318155755438](https://cdn.jsdelivr.net/gh/yzk656/image/202303181557499.png)

## JSTL-if&foreach

![image-20230318163623951](https://cdn.jsdelivr.net/gh/yzk656/image/202303181636026.png)

![image-20230318163632490](https://cdn.jsdelivr.net/gh/yzk656/image/202303181636554.png)

![image-20230318164457512](https://cdn.jsdelivr.net/gh/yzk656/image/202303181644585.png)

![image-20230318165303320](https://cdn.jsdelivr.net/gh/yzk656/image/202303181653359.png)

![image-20230318165452338](https://cdn.jsdelivr.net/gh/yzk656/image/202303181654387.png)

![image-20230318165608421](https://cdn.jsdelivr.net/gh/yzk656/image/202303181656469.png)

## MVC和三层架构

![image-20230319002154958](https://cdn.jsdelivr.net/gh/yzk656/image/202303190021018.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303190020381.png)

![image-20230319002318581](https://cdn.jsdelivr.net/gh/yzk656/image/202303190023642.png)

## JSP隐式对象和EL隐式对象比较

> JSP隐式对象

| **名称**    | **类型**                               | **描述**                                    |
| ----------- | -------------------------------------- | ------------------------------------------- |
| out         | javax.servlet.jspJspWriter             | 用于页面输出                                |
| request     | javax.servlet.http.HttpServletRequest  | 得到用户请求信息                            |
| response    | javax.servlet.http.HttpServletResponse | 服务器向客户端的回应信息                    |
| config      | javax.servlet.ServletConfig            | 服务器配置，可以取得初始化参数              |
| session     | javax.servlet.http.HttpSession         | 用来保存用户的信息                          |
| application | javax.servlet.ServletContext           | 所有用户的共享信息                          |
| page        | java.lang.Object                       | 指当前页面转换后的Servlet类的实例           |
| pageContext | javax.servlet.jsp.PageContext          | JSP的页面容器                               |
| exception   | java.lang.Throwable                    | 表示JSP页面所发生的异常，在错误页中才起作用 |



> **EL**隐式对象

| **隐式对象名称** | **描**    **述**                                             |
| ---------------- | ------------------------------------------------------------ |
| pageContext      | 对应于JSP页面中的pageContext对象                             |
| pageScope        | 代表page域中用于保存属性的Map对象                            |
| requestScope     | 代表request域中用于保存属性的Map对象                         |
| sessionScope     | 代表session域中用于保存属性的Map对象                         |
| applicationScope | 代表application域中用于保存属性的Map对象                     |
| param            | 表示一个保存了所有请求参数的Map对象                          |
| paramValues      | 表示一个保存了所有请求参数的Map对象，它对于某个请求参数，返回的是一个String类型数组 |
| header           | 表示一个保存了所有http请求头字段的Map对象                    |
| headerValues     | 表示一个保存了所有http请求头字段的Map对象，返回String类型数组 |
| cookie           | 用于获取使用者的cookie值，cookie的类型是Map                  |
| initParam        | 表示一个保存了所有Web应用初始化参数的Map对象                 |

1. 在上表列举的隐式对象中，pageContext可以获取其他10个隐式对象，pageScope、requestScope、sessionScope、applicationScope是用于获取指定域的隐式对象；param和paramValues是用于获取请求参数的隐式对象，header和headerValues是用于获取HTTP请求消息头的隐式对象；cookie是用于获取Cookie信息的隐式对象；initParam是用于获取Web应用初始化信息的隐式对象。

> 为了获取JSP页面的隐式对象，可以使用EL中的pageContext隐式对象。pageContext隐式对象用法示例代码如下：

```java
${pageContext.response.characterEncoding}
```



# 案例



## 准备环境

![image-20230319002430245](https://cdn.jsdelivr.net/gh/yzk656/image/202303190024304.png)

![image-20230319002438851](https://cdn.jsdelivr.net/gh/yzk656/image/202303190024899.png)

## 查询所有

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303190833426.png)

![image-20230319101237914](https://cdn.jsdelivr.net/gh/yzk656/image/202303191012981.png)

![image-20230319115432586](https://cdn.jsdelivr.net/gh/yzk656/image/202303191154650.png)

## 添加

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303191418631.png)

![image-20230319143740636](https://cdn.jsdelivr.net/gh/yzk656/image/202303191437690.png)

==报500-错误==

解决办法：更新mybatis、java-connector

![image-20230319161240932](https://cdn.jsdelivr.net/gh/yzk656/image/202303191612022.png)

![image-20230319161316873](https://cdn.jsdelivr.net/gh/yzk656/image/202303191613930.png)

## 修改-回显数据

![image-20230319161857861](https://cdn.jsdelivr.net/gh/yzk656/image/202303191618934.png)

![image-20230319162631422](https://cdn.jsdelivr.net/gh/yzk656/image/202303191626504.png)

## 修改数据

![image-20230319183024630](https://cdn.jsdelivr.net/gh/yzk656/image/202303191830722.png)

项目完成

项目地址：==E:\Code\workspace\brand-demo==

# 会话跟踪技术

## 会话跟踪技术概述

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303200000721.png)

## Cookie-基本使用

![image-20230320000941006](https://cdn.jsdelivr.net/gh/yzk656/image/202303200009104.png)

## Cookie原理&细节

![image-20230320001535928](https://cdn.jsdelivr.net/gh/yzk656/image/202303200015987.png)

![image-20230320002300346](https://cdn.jsdelivr.net/gh/yzk656/image/202303200023394.png)

![image-20230320002633193](https://cdn.jsdelivr.net/gh/yzk656/image/202303200026269.png)

![image-20230320002706349](https://cdn.jsdelivr.net/gh/yzk656/image/202303200027397.png)

![image-20230320002647501](https://cdn.jsdelivr.net/gh/yzk656/image/202303200026551.png)

## Session的基本使用

![image-20230320002943835](https://cdn.jsdelivr.net/gh/yzk656/image/202303200029910.png)

![image-20230320003102202](https://cdn.jsdelivr.net/gh/yzk656/image/202303200031252.png)

![image-20230320003009949](https://cdn.jsdelivr.net/gh/yzk656/image/202303200030004.png)

## Session原理&细节

![image-20230320003703921](https://cdn.jsdelivr.net/gh/yzk656/image/202303200037993.png)



![image-20230320004813211](https://cdn.jsdelivr.net/gh/yzk656/image/202303200048696.png)

![image-20230320004709629](https://cdn.jsdelivr.net/gh/yzk656/image/202303200047687.png)

## 小结

![image-20230320005215083](https://cdn.jsdelivr.net/gh/yzk656/image/202303200052153.png)

# 案例

## 需求说明

![image-20230320131228911](https://cdn.jsdelivr.net/gh/yzk656/image/202303201312998.png)

## 用户登录

![image-20230320144927715](https://cdn.jsdelivr.net/gh/yzk656/image/202303201449797.png)

![image-20230320151637342](https://cdn.jsdelivr.net/gh/yzk656/image/202303201516404.png)

![image-20230320183856950](https://cdn.jsdelivr.net/gh/yzk656/image/202303201838012.png)

![image-20230320183909435](https://cdn.jsdelivr.net/gh/yzk656/image/202303201839495.png)

## 记住用户

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303201919890.png)

```java
/*3. 判断用户是否为null*/
if (user != null) {
    /*判断用户是否勾选记住我*/
    /*为了防止空指针异常，可以吧字符串放在前面*/
    if ("1".equals(remember)) {
        
    }
```

![image-20230320212914801](https://cdn.jsdelivr.net/gh/yzk656/image/202303202129856.png)

![image-20230320211736304](https://cdn.jsdelivr.net/gh/yzk656/image/202303202117362.png)

![image-20230320211708294](https://cdn.jsdelivr.net/gh/yzk656/image/202303202117375.png)

![image-20230320213044978](https://cdn.jsdelivr.net/gh/yzk656/image/202303202130063.png)

![image-20230320213509563](https://cdn.jsdelivr.net/gh/yzk656/image/202303202135605.png)

## 用户注册

![image-20230320213557284](https://cdn.jsdelivr.net/gh/yzk656/image/202303202135368.png)

![image-20230320213719181](https://cdn.jsdelivr.net/gh/yzk656/image/202303202137258.png)

## 验证码-展示与校验

![image-20230321003802555](https://cdn.jsdelivr.net/gh/yzk656/image/202303210038632.png)

![image-20230321010245026](https://cdn.jsdelivr.net/gh/yzk656/image/202303210102092.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303210107031.png)

# Filter

## 概述&快速入门&执行流程

![image-20230321143422867](https://cdn.jsdelivr.net/gh/yzk656/image/202303211434976.png)

![image-20230321150114093](https://cdn.jsdelivr.net/gh/yzk656/image/202303211501187.png)

![image-20230321150312812](https://cdn.jsdelivr.net/gh/yzk656/image/202303211503893.png)

## 拦截路径配置&过滤链

![image-20230321200801642](https://cdn.jsdelivr.net/gh/yzk656/image/202303212008720.png)

![image-20230322162341205](https://cdn.jsdelivr.net/gh/yzk656/image/202303221623290.png)

==过滤顺序==

![image-20230322162719290](https://cdn.jsdelivr.net/gh/yzk656/image/202303221627350.png)

## 案例

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303221641566.png)

```tcl
        /**
         * 总结：
         *  1. 如果是访问注册或者登录接口就直接放行
         *  2. 如果不是访问登录或者注册，在进行判断是否登录过
         */
```

# Listener

![image-20230322165808599](https://cdn.jsdelivr.net/gh/yzk656/image/202303221658709.png)

![image-20230322170536598](https://cdn.jsdelivr.net/gh/yzk656/image/202303221705653.png)

![image-20230322175309495](https://cdn.jsdelivr.net/gh/yzk656/image/202303221753560.png)

# AJAX

## 概述

![image-20230322221510628](https://cdn.jsdelivr.net/gh/yzk656/image/202303222215735.png)

![image-20230322221600799](https://cdn.jsdelivr.net/gh/yzk656/image/202303222216855.png)

## AJAX-快速入门

![image-20230322222346192](https://cdn.jsdelivr.net/gh/yzk656/image/202303222223281.png)

type：xhr代表异步

## 案例-验证用户是否存在

![image-20230322230354625](https://cdn.jsdelivr.net/gh/yzk656/image/202303222303714.png)

## Axios异步框架

![image-20230323094111042](https://cdn.jsdelivr.net/gh/yzk656/image/202303230941116.png)

![image-20230323094205101](https://cdn.jsdelivr.net/gh/yzk656/image/202303230942173.png)

![image-20230323100948092](https://cdn.jsdelivr.net/gh/yzk656/image/202303231009171.png)

![image-20230323110130807](https://cdn.jsdelivr.net/gh/yzk656/image/202303231101872.png)

## JSON

![image-20230323110425567](https://cdn.jsdelivr.net/gh/yzk656/image/202303231104635.png)

![image-20230323111200876](https://cdn.jsdelivr.net/gh/yzk656/image/202303231112929.png)

## JSON数据和JAVA对象转换

![image-20230323111141850](https://cdn.jsdelivr.net/gh/yzk656/image/202303231111923.png)

![image-20230323111344067](https://cdn.jsdelivr.net/gh/yzk656/image/202303231113157.png)

```xml
        <!--JSON对象和JAVA对象转换：fastjson-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>1.2.62</version>
        </dependency>
```

## 案例-查询所有

![image-20230323115454675](https://cdn.jsdelivr.net/gh/yzk656/image/202303231154750.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303231156443.png)

## 案例-新增品牌

![image-20230323155000064](https://cdn.jsdelivr.net/gh/yzk656/image/202303231605709.png)

![image-20230323160654118](https://cdn.jsdelivr.net/gh/yzk656/image/202303231606187.png)

==获取POST方式提交过来的JSON数据==

![image-20230326151251873](https://cdn.jsdelivr.net/gh/yzk656/image/202303261512965.png)

# Vue

## Vue概述&快速入门

![image-20230324192055800](https://cdn.jsdelivr.net/gh/yzk656/image/202303241920898.png)

![image-20230324220028432](https://cdn.jsdelivr.net/gh/yzk656/image/202303242200507.png)

![image-20230324221205797](https://cdn.jsdelivr.net/gh/yzk656/image/202303242212865.png)

## Vue常见指令&生命周期

![image-20230324224928957](https://cdn.jsdelivr.net/gh/yzk656/image/202303242249042.png)

![image-20230324230231215](https://cdn.jsdelivr.net/gh/yzk656/image/202303242302283.png)

![image-20230325092720713](https://cdn.jsdelivr.net/gh/yzk656/image/202303250927795.png)

![image-20230325093326446](https://cdn.jsdelivr.net/gh/yzk656/image/202303250933518.png)

![image-20230325101529208](https://cdn.jsdelivr.net/gh/yzk656/image/202303251015269.png)

![image-20230325103306424](https://cdn.jsdelivr.net/gh/yzk656/image/202303251033463.png)

​		<template> 标签定义在页面加载时隐藏的一些内容，该标签中的内容可以稍后使用 JavaScript 呈现。

​		如果您有一些需要重复使用的 HTML 代码，则可以使用 `<template>` 设置为公用的模板。

![image-20230325103650919](https://cdn.jsdelivr.net/gh/yzk656/image/202303251036967.png)

![image-20230325103723571](https://cdn.jsdelivr.net/gh/yzk656/image/202303251037626.png)

![image-20230325104431219](https://cdn.jsdelivr.net/gh/yzk656/image/202303251044297.png)

![image-20230325104507724](https://cdn.jsdelivr.net/gh/yzk656/image/202303251045804.png)

![image-20230419225221106](https://cdn.jsdelivr.net/gh/yzk656/image/202304192252227.png)

## 案例

![image-20230325104917878](https://cdn.jsdelivr.net/gh/yzk656/image/202303251049963.png)

==注意==

对象在封装json时，会调用所有的get方法，顺序是get后的按照字母自然排序，所以即时没有statusStr属性，在转换的json中也有status

brand.statusStr会自动调用getStatusStr方法

![image-20230325145412505](https://cdn.jsdelivr.net/gh/yzk656/image/202303251454648.png)

# Element

![image-20230325153459683](https://cdn.jsdelivr.net/gh/yzk656/image/202303251534810.png)

## Element概述&快速入门&布局

![image-20230325154130009](https://cdn.jsdelivr.net/gh/yzk656/image/202303251541142.png)

 ![image-20230325160841811](https://cdn.jsdelivr.net/gh/yzk656/image/202303251608922.png)

## Element常用组件-表格

![image-20230325163912421](https://cdn.jsdelivr.net/gh/yzk656/image/202303251639538.png)

## Element常用组件-表单

https://element.eleme.cn/#/zh-CN/component/form、

## Element常用组件-对话框和表单

https://element.eleme.cn/#/zh-CN/component/dialog

## Element常用组件-分页工具条

# 综合案例

## 环境搭建

![image-20230326103019029](https://cdn.jsdelivr.net/gh/yzk656/image/202303261030100.png)

![image-20230326103048244](https://cdn.jsdelivr.net/gh/yzk656/image/202303261030296.png)

## 查询所有-后台&前台

![image-20230326104506977](https://cdn.jsdelivr.net/gh/yzk656/image/202303261045060.png)

## 新增品牌-前台和后端

![image-20230326142159124](https://cdn.jsdelivr.net/gh/yzk656/image/202303261421218.png)

==添加数据后是乱码==

[在XML文件中，&符号是一个特殊字符，它用于表示实体引用。如果您想在XML文件中使用&符号，必须使用实体引用&来代替。这是因为XML文件中的一些字符具有特殊含义，例如<和>，如果您想在XML文件中使用这些字符，则必须使用实体引用<和>来代替。](https://blog.csdn.net/qq_38878740/article/details/98869780)[1](https://blog.csdn.net/qq_38878740/article/details/98869780)[2](https://blog.csdn.net/Pruett/article/details/78350948)

![image-20230326154925364](https://cdn.jsdelivr.net/gh/yzk656/image/202303261549416.png)

![image-20230326154719019](https://cdn.jsdelivr.net/gh/yzk656/image/202303261547086.png)

## Servlet代码优化

![image-20230326164940611](https://cdn.jsdelivr.net/gh/yzk656/image/202303261649723.png)

![image-20230326170149822](https://cdn.jsdelivr.net/gh/yzk656/image/202303261701891.png)

![image-20230326171719114](https://cdn.jsdelivr.net/gh/yzk656/image/202303261717176.png)

![image-20230326171821388](https://cdn.jsdelivr.net/gh/yzk656/image/202303261718449.png)


## 批量删除-后端&前端

![image-20230327204322910](https://cdn.jsdelivr.net/gh/yzk656/image/202303282141983.png)

## 分页查询-分析

![](https://cdn.jsdelivr.net/gh/yzk656/image/202303272326846.png)

![image-20230327233436766](https://cdn.jsdelivr.net/gh/yzk656/image/202303272334854.png)

## 分页查询-后端&前端

![image-20230329190548235](https://cdn.jsdelivr.net/gh/yzk656/image/202303291905384.png)

## 条件查询-后台

![image-20230329195945203](https://cdn.jsdelivr.net/gh/yzk656/image/202303291959306.png)

==注意==

![image-20230330213428282](https://cdn.jsdelivr.net/gh/yzk656/image/202303302134441.png)

![image-20230330213454671](https://cdn.jsdelivr.net/gh/yzk656/image/202303302134781.png)

这里就算没有statusStr属性也没事，因为到时候会给句status去找到获取方法，但是一定要保证`statusStr`的首字母要小写

![image-20230331235454943](https://cdn.jsdelivr.net/gh/yzk656/image/202303312354142.png)

## 修改和删除功能

![image-20230401095414058](https://cdn.jsdelivr.net/gh/yzk656/image/202304010954201.png)

在进行删除和修改时，如果遇到使用相同组件产生冲突时，只需要更改响应名称

![image-20230401095600043](https://cdn.jsdelivr.net/gh/yzk656/image/202304010956101.png)

点击按钮时获取对应行数据，可以使用scope

![image-20230401095809597](https://cdn.jsdelivr.net/gh/yzk656/image/202304010958651.png)

​	在修改时，一个是回显，一个是修改

# 总结

1. mybatis使数据库连接更加方便
2. servlet用于创建服务器程序
3. JSP是前端页面可以动态接收参数
4. Filter是到达服务器的请求得到过滤
5. AJAX能够在不刷新页面的情况与服务器进行交互
6. Vue使JS的操作更加简化，以及数据的动态绑定
7. Element一款使用vue实现的组件库



