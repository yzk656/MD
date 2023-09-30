在进行跳转到服务器

**消息** 实例化Servlet类[com.yzk.Servlets.addServlet]异常

![image-20230227092105048](https://cdn.jsdelivr.net/gh/yzk656/image/202302270921139.png)

解决办法：

![image-20230227092329931](https://cdn.jsdelivr.net/gh/yzk656/image/202302270923977.png)





## Cannot invoke "java.sql.Connection.prepareStatement(String, int)" because "this.conn" is null

> 忘记将mysql驱动连接池的jar包导入进来
>
> 一个项目可以由很多模快组成，如果你是在模块中新建的lib（mysql连接驱动），则不会报错；
>
> 但是如果是在项目中添加的lib，需要将lib添加为库，同时因为模块需要依赖他，因此需要在==项目结构上添加依赖==，同时，==问题==哪里应该也会报错，因此要进行更新工件

![image-20230227142942097](https://cdn.jsdelivr.net/gh/yzk656/image/202302271429173.png)

![image-20230227143033946](https://cdn.jsdelivr.net/gh/yzk656/image/202302271430992.png)

![image-20230227143104125](https://cdn.jsdelivr.net/gh/yzk656/image/202302271431165.png)

![image-20230227145402568](https://cdn.jsdelivr.net/gh/yzk656/image/202302271454615.png)

==老师讲解：==

https://www.bilibili.com/video/BV18R4y1M7Mt/?p=22&spm_id_from=pageDriver&vd_source=2b44df7de02d967d7dc69478401443b4

![image-20230227145452749](https://cdn.jsdelivr.net/gh/yzk656/image/202302271454806.png)





## 运行配置停止之前未连接应用程序服务器，原因: 无法在 localhost:1099 处 ping

解决办法：删除Tomcat配置，进行重新配置



## Cannot access defaults field of Properties

![image-20230312183454957](https://cdn.jsdelivr.net/gh/yzk656/image/202303121834994.png)

```java
在pom.xml文件中加入


<build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-war-plugin</artifactId>
                <version>3.3.1</version>
            </plugin>
        </plugins>
    </build>
```

## IDEA配置Tomcat成功运行自动打开网页找不到此localhost解放方案之一

解决办法：

在配置时，点部署Deployment，然后+号，下面划重点，**下面的根目录一条斜杠即可**

![image-20230317131723061](https://cdn.jsdelivr.net/gh/yzk656/image/202303171317109.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210619232407103.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1hXeERTSg==,size_16,color_FFFFFF,t_70)

## 启动tomcat7:run服务器出现BUILD SUCCESS解决办法

https://blog.csdn.net/qq_36833593/article/details/108541960

![image-20230318153208639](https://cdn.jsdelivr.net/gh/yzk656/image/202303181532693.png)



## pom.xml报错 expected START_TAG or END_TAG not TEXT (position: TEXT seen ... ``\n\n ＜d...

![image-20230319163717465](https://cdn.jsdelivr.net/gh/yzk656/image/202303191637509.png)

## HTTP Status 500 - Unable to compile class for JSP:

==解决办法==

tomcat版本过低，可以使用tomcat10版本

![image-20230322155044214](https://cdn.jsdelivr.net/gh/yzk656/image/202303221550286.png)

## 在学习servlet时为什么要导入jsp-api.jar和servlet-api.jar

 [maven](https://so.csdn.net/so/search?q=maven&spm=1001.2101.3001.7020)构建的web项目如果要使用HttpServletRequest或者PageContext等servlet或者jsp的api时，需要引入servlet-api和jsp-api,

## java修改操作出错：could not retrieve transation read-only status server

==解决办法==

升级mysql-connector驱动

最初的

![image-20230323164315673](https://cdn.jsdelivr.net/gh/yzk656/image/202303231643711.png)

更改后

```xml
<!--mysql-->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.28</version>
</dependency>
```

