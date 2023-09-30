# Spring

![image-20230402002011541](https://cdn.jsdelivr.net/gh/yzk656/image/202304020020574.png)

## 初识Spring

![image-20230402002731299](https://cdn.jsdelivr.net/gh/yzk656/image/202304020027368.png)

## Spring系统架构

![image-20230402003058817](https://cdn.jsdelivr.net/gh/yzk656/image/202304020030893.png)

![image-20230402003431291](https://cdn.jsdelivr.net/gh/yzk656/image/202304020034367.png)

![image-20230402003624543](https://cdn.jsdelivr.net/gh/yzk656/image/202304020036629.png)

## 核心概念

![image-20230402004059439](https://cdn.jsdelivr.net/gh/yzk656/image/202304020040506.png)

![image-20230402004555139](https://cdn.jsdelivr.net/gh/yzk656/image/202304020045229.png)

![image-20230402004717200](https://cdn.jsdelivr.net/gh/yzk656/image/202304020047239.png)

## IoC入门案例

![image-20230402101201818](https://cdn.jsdelivr.net/gh/yzk656/image/202304021012873.png)

![image-20230402104024425](https://cdn.jsdelivr.net/gh/yzk656/image/202304021040490.png)

![image-20230402104034572](https://cdn.jsdelivr.net/gh/yzk656/image/202304021040639.png)

![image-20230402104048957](https://cdn.jsdelivr.net/gh/yzk656/image/202304021040042.png)

![image-20230402104059143](https://cdn.jsdelivr.net/gh/yzk656/image/202304021040213.png)

## DI入门案例

![image-20230402104724459](https://cdn.jsdelivr.net/gh/yzk656/image/202304021047500.png)

![image-20230402105502083](https://cdn.jsdelivr.net/gh/yzk656/image/202304021055129.png)

![image-20230402105614223](https://cdn.jsdelivr.net/gh/yzk656/image/202304021056281.png)

![image-20230402105545884](https://cdn.jsdelivr.net/gh/yzk656/image/202304021055954.png)

![image-20230402105713343](https://cdn.jsdelivr.net/gh/yzk656/image/202304021057424.png)

## bean基础配置

![image-20230402105841944](https://cdn.jsdelivr.net/gh/yzk656/image/202304021058026.png)

![image-20230402110531501](https://cdn.jsdelivr.net/gh/yzk656/image/202304021105588.png)

容器给我们创建的bean是单例的，只有一个；如果想要非单例bean就需要配置scope属性

![image-20230402111013131](https://cdn.jsdelivr.net/gh/yzk656/image/202304021110183.png)

![image-20230402111020804](https://cdn.jsdelivr.net/gh/yzk656/image/202304021110863.png)

![image-20230402111637591](https://cdn.jsdelivr.net/gh/yzk656/image/202304021116632.png)

## bean实例化-构造方法

![image-20230402112644181](https://cdn.jsdelivr.net/gh/yzk656/image/202304021126254.png)

## bean实例化-静态工厂

![image-20230402113241203](https://cdn.jsdelivr.net/gh/yzk656/image/202304021132266.png)

## bean实例化-实例工厂与FactoryBean

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304021333838.png)

改良后

![image-20230402133819054](https://cdn.jsdelivr.net/gh/yzk656/image/202304021338121.png)

## bean的生命周期

有两种方式

第一种：

![image-20230402135120330](https://cdn.jsdelivr.net/gh/yzk656/image/202304021351398.png)

第二种：

![image-20230402135148917](https://cdn.jsdelivr.net/gh/yzk656/image/202304021351979.png)

![image-20230402135304520](https://cdn.jsdelivr.net/gh/yzk656/image/202304021353572.png)

![image-20230402135354812](https://cdn.jsdelivr.net/gh/yzk656/image/202304021353882.png)

手动是暴力，而注册不是。注册可以写在当前方法任意地方，而手动必须要要在执行service后再关闭，否则会提示容器已经关闭错误

## setter注入

![image-20230402150533903](https://cdn.jsdelivr.net/gh/yzk656/image/202304021505970.png)

对于引用数据类型

![image-20230402150759614](https://cdn.jsdelivr.net/gh/yzk656/image/202304021507682.png)

对于简单类型

![image-20230402151329414](https://cdn.jsdelivr.net/gh/yzk656/image/202304021513481.png)

## 构造器注入

![image-20230402212245323](https://cdn.jsdelivr.net/gh/yzk656/image/202304022122386.png)

对于引用类型

![image-20230402214205067](https://cdn.jsdelivr.net/gh/yzk656/image/202304022142134.png)

对于简单类型

![image-20230402214225217](https://cdn.jsdelivr.net/gh/yzk656/image/202304022142294.png)

![image-20230402214315666](https://cdn.jsdelivr.net/gh/yzk656/image/202304022143738.png)

![im88age-20230402214420546](https://cdn.jsdelivr.net/gh/yzk656/image/202304022144628.png)   

![image-20230402234526832](https://cdn.jsdelivr.net/gh/yzk656/image/202304022345892.png)

## 依赖自动装配

![image-20230402234728235](https://cdn.jsdelivr.net/gh/yzk656/image/202304022347300.png)

![image-20230402235315986](https://cdn.jsdelivr.net/gh/yzk656/image/202304022353055.png)

![image-20230402235453241](https://cdn.jsdelivr.net/gh/yzk656/image/202304022354323.png)

## 集合注入

![image-20230403001006286](https://cdn.jsdelivr.net/gh/yzk656/image/202304030010362.png)

![image-20230403001014442](https://cdn.jsdelivr.net/gh/yzk656/image/202304030010517.png)

![image-20230403001023320](https://cdn.jsdelivr.net/gh/yzk656/image/202304030010393.png)

![image-20230403001033731](https://cdn.jsdelivr.net/gh/yzk656/image/202304030010805.png)

![image-20230403001045737](https://cdn.jsdelivr.net/gh/yzk656/image/202304030010807.png)

![image-20230403001055147](https://cdn.jsdelivr.net/gh/yzk656/image/202304030010225.png)

## 案例-数据源对象管理

![image-20230403004543190](https://cdn.jsdelivr.net/gh/yzk656/image/202304030045312.png)

![image-20230403004645120](https://cdn.jsdelivr.net/gh/yzk656/image/202304030046202.png)

![image-20230403004627436](https://cdn.jsdelivr.net/gh/yzk656/image/202304030046497.png)

## 加载properties文件

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304031259609.png)

![image-20230403130623872](https://cdn.jsdelivr.net/gh/yzk656/image/202304031306917.png)

![image-20230403130756778](https://cdn.jsdelivr.net/gh/yzk656/image/202304031307812.png)

![image-20230403130830283](https://cdn.jsdelivr.net/gh/yzk656/image/202304031308377.png)

## 容器

![image-20230403131645887](https://cdn.jsdelivr.net/gh/yzk656/image/202304031316946.png)

![image-20230403131700279](https://cdn.jsdelivr.net/gh/yzk656/image/202304031317331.png)

对于方式三，要保证容器中只有这一个bean，否则会报错

![image-20230403132521321](https://cdn.jsdelivr.net/gh/yzk656/image/202304031325460.png)

![image-20230403132637494](https://cdn.jsdelivr.net/gh/yzk656/image/202304031326556.png)

![image-20230403132845779](https://cdn.jsdelivr.net/gh/yzk656/image/202304031328820.png)

也就是，只有创建bean时才会使用构造函数

## 核心容器总结

![image-20230403133259715](https://cdn.jsdelivr.net/gh/yzk656/image/202304031332773.png)

![image-20230403133613303](https://cdn.jsdelivr.net/gh/yzk656/image/202304031336383.png)

![image-20230403133603019](https://cdn.jsdelivr.net/gh/yzk656/image/202304031336120.png)

## 注解开发定义Bean

![image-20230403152459851](https://cdn.jsdelivr.net/gh/yzk656/image/202304031524906.png)

![image-20230403152543151](https://cdn.jsdelivr.net/gh/yzk656/image/202304031525201.png)

## 纯注解开发模式

![image-20230403184808303](https://cdn.jsdelivr.net/gh/yzk656/image/202304031848398.png)

![image-20230403184822629](https://cdn.jsdelivr.net/gh/yzk656/image/202304031848700.png)

![image-20230403184946763](https://cdn.jsdelivr.net/gh/yzk656/image/202304031849830.png)

## 注解开发bean作用与生命周期管理

![image-20230403190722612](https://cdn.jsdelivr.net/gh/yzk656/image/202304031907660.png)

![image-20230403190746315](https://cdn.jsdelivr.net/gh/yzk656/image/202304031907386.png)

## 注解开发依赖注入

![image-20230403192203528](https://cdn.jsdelivr.net/gh/yzk656/image/202304031922596.png)

![image-20230403192214941](https://cdn.jsdelivr.net/gh/yzk656/image/202304031922002.png)

![image-20230403192345468](https://cdn.jsdelivr.net/gh/yzk656/image/202304031923507.png)

![image-20230403192909841](https://cdn.jsdelivr.net/gh/yzk656/image/202304031929898.png)

## 注解开发管理第三方bean

![image-20230403194358102](https://cdn.jsdelivr.net/gh/yzk656/image/202304031943167.png)

![image-20230403194422448](https://cdn.jsdelivr.net/gh/yzk656/image/202304031944505.png)

![image-20230403194438966](https://cdn.jsdelivr.net/gh/yzk656/image/202304031944043.png)

![image-20230403194511347](https://cdn.jsdelivr.net/gh/yzk656/image/202304031945420.png)

## 注解开发实现为第三方bean注入资源

![image-20230403205824536](https://cdn.jsdelivr.net/gh/yzk656/image/202304032058603.png)

![image-20230403205833473](https://cdn.jsdelivr.net/gh/yzk656/image/202304032058531.png)

![image-20230403205918829](https://cdn.jsdelivr.net/gh/yzk656/image/202304032059878.png)

## 注解开发总结

XML配置与注解配置比较

![image-20230403210044392](https://cdn.jsdelivr.net/gh/yzk656/image/202304032100469.png)

## Spring整个MyBatis思路分析

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304042016971.png)

![image-20230404212322787](https://cdn.jsdelivr.net/gh/yzk656/image/202304042123877.png)

## SPring整合MyBatis

![image-20230404212822892](https://cdn.jsdelivr.net/gh/yzk656/image/202304042128935.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304052151130.png)

![image-20230405215241012](https://cdn.jsdelivr.net/gh/yzk656/image/202304052152081.png)

## Spring整合Junit

![image-20230405215755365](https://cdn.jsdelivr.net/gh/yzk656/image/202304052157419.png)

![image-20230405215814484](https://cdn.jsdelivr.net/gh/yzk656/image/202304052158540.png)

## AOP简介

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304052211972.png)

![image-20230405222554247](https://cdn.jsdelivr.net/gh/yzk656/image/202304052225354.png)

## AOP入门案例

![image-20230413130417178](https://cdn.jsdelivr.net/gh/yzk656/image/202304131304249.png)

![image-20230413161109378](https://cdn.jsdelivr.net/gh/yzk656/image/202304131611453.png)

![image-20230413161132400](https://cdn.jsdelivr.net/gh/yzk656/image/202304131611477.png)

![image-20230413161143521](https://cdn.jsdelivr.net/gh/yzk656/image/202304131611570.png)

![image-20230413161245120](https://cdn.jsdelivr.net/gh/yzk656/image/202304131612174.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304131613669.png)

![image-20230413161326290](https://cdn.jsdelivr.net/gh/yzk656/image/202304131613359.png)

![image-20230413161334689](https://cdn.jsdelivr.net/gh/yzk656/image/202304131613739.png)

## AOP工作流程

![image-20230413161547630](https://cdn.jsdelivr.net/gh/yzk656/image/202304131615699.png)

![image-20230413162019175](https://cdn.jsdelivr.net/gh/yzk656/image/202304131620240.png)

![image-20230413163313327](https://cdn.jsdelivr.net/gh/yzk656/image/202304131633376.png)

## AOP切入点表达式

![image-20230413163853734](https://cdn.jsdelivr.net/gh/yzk656/image/202304131638828.png)

![image-20230413164105784](https://cdn.jsdelivr.net/gh/yzk656/image/202304131641855.png)

加速开发

![image-20230413164336715](https://cdn.jsdelivr.net/gh/yzk656/image/202304131643791.png)

![image-20230413170338230](https://cdn.jsdelivr.net/gh/yzk656/image/202304131703317.png)

## AOP通知类型

![image-20230413180353418](https://cdn.jsdelivr.net/gh/yzk656/image/202304131803506.png)

![image-20230413180404282](https://cdn.jsdelivr.net/gh/yzk656/image/202304131804358.png)

![image-20230413180428026](https://cdn.jsdelivr.net/gh/yzk656/image/202304131804125.png)

![image-20230413180720274](https://cdn.jsdelivr.net/gh/yzk656/image/202304131807349.png)

![image-20230413180726040](https://cdn.jsdelivr.net/gh/yzk656/image/202304131807372.png)

## 案例-业务层接口执行效率

![image-20230413183027917](https://cdn.jsdelivr.net/gh/yzk656/image/202304131830993.png)

![image-20230413183051200](https://cdn.jsdelivr.net/gh/yzk656/image/202304131830276.png)

## AOP通知获取数据

![image-20230413183406808](https://cdn.jsdelivr.net/gh/yzk656/image/202304131834853.png)

![image-20230413201210153](https://cdn.jsdelivr.net/gh/yzk656/image/202304132012235.png)

![image-20230413201322697](https://cdn.jsdelivr.net/gh/yzk656/image/202304132013775.png)

![image-20230413201538617](https://cdn.jsdelivr.net/gh/yzk656/image/202304132015699.png)

![image-20230413211758160](https://cdn.jsdelivr.net/gh/yzk656/image/202304132117206.png)

## 百度网盘密码数据兼容处理

![image-20230413201850137](https://cdn.jsdelivr.net/gh/yzk656/image/202304132018223.png)

![image-20230413202810141](https://cdn.jsdelivr.net/gh/yzk656/image/202304132028221.png)

## AOP总结

![image-20230413202927653](https://cdn.jsdelivr.net/gh/yzk656/image/202304132029716.png)

![image-20230413203432373](https://cdn.jsdelivr.net/gh/yzk656/image/202304132034429.png)

![image-20230413203451788](https://cdn.jsdelivr.net/gh/yzk656/image/202304132034871.png)

![image-20230413203710402](https://cdn.jsdelivr.net/gh/yzk656/image/202304132037453.png)

![image-20230413203925144](https://cdn.jsdelivr.net/gh/yzk656/image/202304132039199.png)



## Spring事务简介

![image-20230420102809320](https://cdn.jsdelivr.net/gh/yzk656/image/202304201028420.png)

![image-20230420103331806](https://cdn.jsdelivr.net/gh/yzk656/image/202304201033897.png)

![image-20230420103519592](https://cdn.jsdelivr.net/gh/yzk656/image/202304201035653.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304201039720.png)

![image-20230420104009398](https://cdn.jsdelivr.net/gh/yzk656/image/202304201040465.png)

![image-20230420104313218](https://cdn.jsdelivr.net/gh/yzk656/image/202304201043304.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304201043225.png)

![image-20230420104412272](https://cdn.jsdelivr.net/gh/yzk656/image/202304201044341.png)

## Spring事务角色

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304201049175.png)

![image-20230420105235878](https://cdn.jsdelivr.net/gh/yzk656/image/202304201052944.png)

## Spring事务属性

![image-20230420105358481](https://cdn.jsdelivr.net/gh/yzk656/image/202304201053568.png)

IOException不属于运行异常，只有运行异常才会进行回滚，因此可以这样做

![image-20230420110752894](https://cdn.jsdelivr.net/gh/yzk656/image/202304201107963.png)

作案例，写日志

![image-20230420110733885](https://cdn.jsdelivr.net/gh/yzk656/image/202304201107967.png)

![image-20230420111050498](https://cdn.jsdelivr.net/gh/yzk656/image/202304201110560.png)

![image-20230420111315426](https://cdn.jsdelivr.net/gh/yzk656/image/202304201113479.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304201114039.png)



![image-20230420111807861](https://cdn.jsdelivr.net/gh/yzk656/image/202304201118917.png)

![image-20230420112049846](https://cdn.jsdelivr.net/gh/yzk656/image/202304201120943.png)

# SpringMVC

![image-20230414213431250](https://cdn.jsdelivr.net/gh/yzk656/image/202304142134290.png)

![image-20230414213415460](https://cdn.jsdelivr.net/gh/yzk656/image/202304142134536.png)

## SpringMVC简介

![image-20230415082451665](https://cdn.jsdelivr.net/gh/yzk656/image/202304150824765.png)

## SpringMVC入门案例

![image-20230415082813191](https://cdn.jsdelivr.net/gh/yzk656/image/202304150828270.png)

![image-20230415083129111](https://cdn.jsdelivr.net/gh/yzk656/image/202304150831177.png)

![image-20230415083230771](https://cdn.jsdelivr.net/gh/yzk656/image/202304150832833.png)

![image-20230415090359121](https://cdn.jsdelivr.net/gh/yzk656/image/202304150903215.png)

![image-20230416102117447](https://cdn.jsdelivr.net/gh/yzk656/image/202304161021524.png)

![image-20230416102134644](https://cdn.jsdelivr.net/gh/yzk656/image/202304161021705.png)

![image-20230416102147797](https://cdn.jsdelivr.net/gh/yzk656/image/202304161021864.png)

![image-20230416102338779](https://cdn.jsdelivr.net/gh/yzk656/image/202304161023848.png)

![image-20230416102348895](https://cdn.jsdelivr.net/gh/yzk656/image/202304161023978.png)

![image-20230416102410220](https://cdn.jsdelivr.net/gh/yzk656/image/202304161024285.png)

![image-20230416102417943](https://cdn.jsdelivr.net/gh/yzk656/image/202304161024016.png)

## 入门案例工作流程

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304161030612.png)

## bean加载控制

![image-20230416103331820](https://cdn.jsdelivr.net/gh/yzk656/image/202304161033869.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304161053979.png)

![image-20230416105432553](https://cdn.jsdelivr.net/gh/yzk656/image/202304161054635.png)

![image-20230416105523221](https://cdn.jsdelivr.net/gh/yzk656/image/202304161055302.png)

![image-20230416105807835](https://cdn.jsdelivr.net/gh/yzk656/image/202304161058909.png)

![image-20230419215357985](https://cdn.jsdelivr.net/gh/yzk656/image/202304192153048.png)

## 请求与响应

### 设置请求映射路径

![image-20230416111430101](https://cdn.jsdelivr.net/gh/yzk656/image/202304161114175.png)

### get请求与post请求发送普通参数

![image-20230416150250041](https://cdn.jsdelivr.net/gh/yzk656/image/202304161502195.png)

### 5种类型参数传递

![image-20230416150427309](https://cdn.jsdelivr.net/gh/yzk656/image/202304161504382.png)

![image-20230416151923550](https://cdn.jsdelivr.net/gh/yzk656/image/202304161519628.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304161520156.png)

![image-20230416152026183](https://cdn.jsdelivr.net/gh/yzk656/image/202304161520247.png)

==注意：==

如果传过来的参数是`json`格式的要添加`@requestbody`注解

![image-20230416152040259](https://cdn.jsdelivr.net/gh/yzk656/image/202304161520330.png)

![image-20230416152053056](https://cdn.jsdelivr.net/gh/yzk656/image/202304161520125.png)

![image-20230416152114117](https://cdn.jsdelivr.net/gh/yzk656/image/202304161521193.png)

### JSON数据请求参数

![image-20230416161454071](https://cdn.jsdelivr.net/gh/yzk656/image/202304161614115.png)

![image-20230416161506468](https://cdn.jsdelivr.net/gh/yzk656/image/202304161615520.png)

![image-20230416161516977](https://cdn.jsdelivr.net/gh/yzk656/image/202304161615044.png)

![image-20230416161534627](https://cdn.jsdelivr.net/gh/yzk656/image/202304161615685.png)

![image-20230416161650848](https://cdn.jsdelivr.net/gh/yzk656/image/202304161616911.png)

![image-20230416161728085](https://cdn.jsdelivr.net/gh/yzk656/image/202304161617137.png)

### 日期型参数传递

![image-20230416162627953](https://cdn.jsdelivr.net/gh/yzk656/image/202304161626028.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304161629512.png)

### 响应

![image-20230416163908014](https://cdn.jsdelivr.net/gh/yzk656/image/202304161639052.png)

![image-20230416163917673](https://cdn.jsdelivr.net/gh/yzk656/image/202305052140499.png)

![image-20230416163941422](https://cdn.jsdelivr.net/gh/yzk656/image/202304161639465.png)

![image-20230416163953127](https://cdn.jsdelivr.net/gh/yzk656/image/202304161639194.png)

![image-20230416164229638](https://cdn.jsdelivr.net/gh/yzk656/image/202304161642709.png)

> 这个之间的转换不是convertor来转换的，而是使用一个全新的接口,来自json坐标

![image-20230416164216450](https://cdn.jsdelivr.net/gh/yzk656/image/202304161642527.png)

## Rest风格

### Rest简介

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304192119660.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304192122415.png)

![image-20230419212727672](https://cdn.jsdelivr.net/gh/yzk656/image/202304192127720.png)

### RESTful入门案例

![image-20230419213343356](https://cdn.jsdelivr.net/gh/yzk656/image/202304192133443.png)

![image-20230419213355277](https://cdn.jsdelivr.net/gh/yzk656/image/202304192133340.png)

![image-20230419213420453](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230419213420453.png)

![image-20230419213436807](https://cdn.jsdelivr.net/gh/yzk656/image/202304192134891.png)

### RESTful快速开发

![image-20230420093900931](https://cdn.jsdelivr.net/gh/yzk656/image/202304200939010.png)

![image-20230420093842388](https://cdn.jsdelivr.net/gh/yzk656/image/202304200938474.png)

![image-20230420093927119](https://cdn.jsdelivr.net/gh/yzk656/image/202304200939217.png)



### 案例：基于RESTful页面数据交互（后台接口开发）

![image-20230419225326011](https://cdn.jsdelivr.net/gh/yzk656/image/202304192253109.png)

由于会被拦截，因此需要在配置层添加放行操作

![image-20230419225522597](https://cdn.jsdelivr.net/gh/yzk656/image/202304192255693.png)

![image-20230419225554185](https://cdn.jsdelivr.net/gh/yzk656/image/202304192255257.png)

## SSM整合

### 整合配置

![image-20230419225807950](https://cdn.jsdelivr.net/gh/yzk656/image/202304192258012.png)

![image-20230420005930741](https://cdn.jsdelivr.net/gh/yzk656/image/202304200059787.png)

![image-20230420005744739](https://cdn.jsdelivr.net/gh/yzk656/image/202304200057811.png)

![image-20230420012637236](https://cdn.jsdelivr.net/gh/yzk656/image/202304200126289.png)

![image-20230420012656854](https://cdn.jsdelivr.net/gh/yzk656/image/202304200126900.png)

![image-20230420012829433](https://cdn.jsdelivr.net/gh/yzk656/image/202304200128484.png)

### 功能模块开发

![image-20230420161020922](https://cdn.jsdelivr.net/gh/yzk656/image/202304201610039.png)

![image-20230420161120053](https://cdn.jsdelivr.net/gh/yzk656/image/202304201611133.png)

![image-20230420161143484](https://cdn.jsdelivr.net/gh/yzk656/image/202304201611558.png)

![image-20230420161150877](https://cdn.jsdelivr.net/gh/yzk656/image/202304201611956.png)

![image-20230420161223397](https://cdn.jsdelivr.net/gh/yzk656/image/202304201612474.png)

### 表现层与前端数据传输协议定义

![image-20230420162032800](https://cdn.jsdelivr.net/gh/yzk656/image/202304201620877.png)

### 表现层与前端数据传输协议实现

![image-20230420194043021](https://cdn.jsdelivr.net/gh/yzk656/image/202304201940124.png)

![image-20230420194051672](https://cdn.jsdelivr.net/gh/yzk656/image/202304201940758.png)

![image-20230420194127241](https://cdn.jsdelivr.net/gh/yzk656/image/202304201941329.png)

### 异常处理器

![image-20230420194412652](https://cdn.jsdelivr.net/gh/yzk656/image/202304201944726.png)



> 注意使用的AOP思想，不过已经被SpringMVC封装好了

![image-20230420195236536](https://cdn.jsdelivr.net/gh/yzk656/image/202304201952607.png)

![](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230420200753944.png)

![image-20230420200846462](https://cdn.jsdelivr.net/gh/yzk656/image/202304202008558.png)

![image-20230420200921760](https://cdn.jsdelivr.net/gh/yzk656/image/202304202009834.png)

### 项目异常处理

![image-20230420201154861](https://cdn.jsdelivr.net/gh/yzk656/image/202304202011943.png)

![image-20230420201313034](https://cdn.jsdelivr.net/gh/yzk656/image/202304202013120.png)

![image-20230420201405425](https://cdn.jsdelivr.net/gh/yzk656/image/202304202014500.png)

![image-20230420201543547](https://cdn.jsdelivr.net/gh/yzk656/image/202304202015621.png)

![image-20230420203702159](https://cdn.jsdelivr.net/gh/yzk656/image/202304202037216.png)

![image-20230420215758525](https://cdn.jsdelivr.net/gh/yzk656/image/202304202157613.png)

![image-20230420215806791](https://cdn.jsdelivr.net/gh/yzk656/image/202304202158881.png)

![image-20230420222210232](https://cdn.jsdelivr.net/gh/yzk656/image/202304202222314.png)

![image-20230420222356902](https://cdn.jsdelivr.net/gh/yzk656/image/202304202223979.png)

![image-20230420230208706](https://cdn.jsdelivr.net/gh/yzk656/image/202304202302810.png)

![image-20230420230228050](https://cdn.jsdelivr.net/gh/yzk656/image/202304202302127.png)

### 案例

![image-20230424234634889](https://cdn.jsdelivr.net/gh/yzk656/image/202304242346099.png)

## 拦截器

### 拦截器简介

![image-20230425110358750](https://cdn.jsdelivr.net/gh/yzk656/image/202304251103910.png)

![image-20230425110826724](https://cdn.jsdelivr.net/gh/yzk656/image/202304251108795.png)

### 拦截器入门案例

![image-20230425123856282](https://cdn.jsdelivr.net/gh/yzk656/image/202304251238382.png)

![image-20230425123905665](https://cdn.jsdelivr.net/gh/yzk656/image/202304251239747.png)

![image-20230425123913107](https://cdn.jsdelivr.net/gh/yzk656/image/202304251239197.png)

![image-20230425124338552](https://cdn.jsdelivr.net/gh/yzk656/image/202304251243651.png)

![image-20230425124652068](https://cdn.jsdelivr.net/gh/yzk656/image/202304251246157.png)

### 拦截器参数

![image-20230425130731023](https://cdn.jsdelivr.net/gh/yzk656/image/202304251307118.png)

![image-20230425130754497](https://cdn.jsdelivr.net/gh/yzk656/image/202304251307570.png)

### 拦截器链配置

![image-20230425131816793](https://cdn.jsdelivr.net/gh/yzk656/image/202304251318893.png)

![image-20230425132051726](https://cdn.jsdelivr.net/gh/yzk656/image/202304251321519.png)

# SpringBoot

## SpringBoot简介

### 入门案例

![image-20230427134423466](https://cdn.jsdelivr.net/gh/yzk656/image/202304271344563.png)

![image-20230427141514784](https://cdn.jsdelivr.net/gh/yzk656/image/202304271415877.png)

![image-20230427145435904](https://cdn.jsdelivr.net/gh/yzk656/image/202304271454987.png)

![image-20230427145454723](https://cdn.jsdelivr.net/gh/yzk656/image/202304271454807.png)

![image-20230427145501483](https://cdn.jsdelivr.net/gh/yzk656/image/202304271455612.png)

### SpringBoot工程官网创建方式

![image-20230427145641916](https://cdn.jsdelivr.net/gh/yzk656/image/202304271456036.png)

![image-20230427145649582](https://cdn.jsdelivr.net/gh/yzk656/image/202304271456661.png)

![image-20230427145804107](https://cdn.jsdelivr.net/gh/yzk656/image/202304271458194.png)

![image-20230427150149799](https://cdn.jsdelivr.net/gh/yzk656/image/202304271501877.png)

### SpringBoot项目快速启动

![image-20230427153408438](https://cdn.jsdelivr.net/gh/yzk656/image/202304271534520.png)

![image-20230427153421229](https://cdn.jsdelivr.net/gh/yzk656/image/202304271534289.png)

![image-20230427153427135](https://cdn.jsdelivr.net/gh/yzk656/image/202304271534186.png)

![image-20230427153436721](https://cdn.jsdelivr.net/gh/yzk656/image/202304271534798.png)

### 起步依赖

![image-20230427153726531](https://cdn.jsdelivr.net/gh/yzk656/image/202304271537601.png)

![image-20230427210228648](https://cdn.jsdelivr.net/gh/yzk656/image/202304272102800.png)

![image-20230427210328703](https://cdn.jsdelivr.net/gh/yzk656/image/202304272103894.png)

### 辅助功能值切换web服务器

![image-20230427210427580](https://cdn.jsdelivr.net/gh/yzk656/image/202304272104755.png)

![image-20230427210444605](https://cdn.jsdelivr.net/gh/yzk656/image/202304272104754.png)

![image-20230427211901554](https://cdn.jsdelivr.net/gh/yzk656/image/202304272119745.png)

## 基础配置

### 配置文件格式

![image-20230427212226999](https://cdn.jsdelivr.net/gh/yzk656/image/202304272122130.png)

![image-20230427213406870](https://cdn.jsdelivr.net/gh/yzk656/image/202304272134003.png)

![image-20230427213713575](https://cdn.jsdelivr.net/gh/yzk656/image/202304272137737.png)

### yaml格式

![image-20230427214238304](https://cdn.jsdelivr.net/gh/yzk656/image/202304272142438.png)

![image-20230427214255422](https://cdn.jsdelivr.net/gh/yzk656/image/202304272142565.png)

### yaml数据读取三种方式

![image-20230428000935486](https://cdn.jsdelivr.net/gh/yzk656/image/202304280009659.png)

![image-20230428000943732](https://cdn.jsdelivr.net/gh/yzk656/image/202304280009894.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304280012945.png)

![image-20230428001343935](https://cdn.jsdelivr.net/gh/yzk656/image/202304280013060.png)

### 多环境开发配置

![image-20230428001451333](https://cdn.jsdelivr.net/gh/yzk656/image/202304280014487.png)

![image-20230428004055468](https://cdn.jsdelivr.net/gh/yzk656/image/202304280040621.png)

![image-20230428004115425](https://cdn.jsdelivr.net/gh/yzk656/image/202304280041569.png)

![image-20230428004123538](https://cdn.jsdelivr.net/gh/yzk656/image/202304280041704.png)

### 多环境命令行启动参数设置

将编码更给为`UTF-8`

![image-20230428150249597](https://cdn.jsdelivr.net/gh/yzk656/image/202304281502674.png)

![image-20230428150548531](https://cdn.jsdelivr.net/gh/yzk656/image/202304281505633.png)

### 多环境开发兼容问题

![image-20230429132541014](https://cdn.jsdelivr.net/gh/yzk656/image/202304291325150.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304291326005.png)

![image-20230429132702307](https://cdn.jsdelivr.net/gh/yzk656/image/202304291327387.png)

![image-20230429132710799](https://cdn.jsdelivr.net/gh/yzk656/image/202304291327880.png)

![image-20230429132722499](https://cdn.jsdelivr.net/gh/yzk656/image/202304291327561.png)

### 配置文件分类

![image-20230429151413277](https://cdn.jsdelivr.net/gh/yzk656/image/202304291514501.png)

file指的是文件中，而classpath是指idea中的设置

## 整合第三方技术

### 整合JUnit

![image-20230429160934528](https://cdn.jsdelivr.net/gh/yzk656/image/202304291609697.png)

![image-20230429162759104](https://cdn.jsdelivr.net/gh/yzk656/image/202304291627245.png)

![image-20230429162811172](https://cdn.jsdelivr.net/gh/yzk656/image/202304291628327.png)

### springboot整合MyBatis

![image-20230429163251005](https://cdn.jsdelivr.net/gh/yzk656/image/202304291632136.png)

![image-20230429163339811](https://cdn.jsdelivr.net/gh/yzk656/image/202304291633983.png)

![image-20230429163431607](https://cdn.jsdelivr.net/gh/yzk656/image/202304291634764.png)

boot整合mybatis

![image-20230429172541542](https://cdn.jsdelivr.net/gh/yzk656/image/202304291725803.png)

![image-20230429172559139](https://cdn.jsdelivr.net/gh/yzk656/image/202304291725292.png)

![image-20230429172610398](https://cdn.jsdelivr.net/gh/yzk656/image/202304291726569.png)

![image-20230429172634682](https://cdn.jsdelivr.net/gh/yzk656/image/202304291726797.png)

因为`spring`中有映射，因此不需要写`mapper`，但是在`springboot`中取消了config设置，因此还需要吧`mapper`写上

![image-20230429172809744](https://cdn.jsdelivr.net/gh/yzk656/image/202304291728891.png)

### 基于SpringBoot实现SSM整合

![](https://cdn.jsdelivr.net/gh/yzk656/image/202304301336643.png)

# MyBatis Plus

## MyBatisPlus简介

### 入门案例

![image-20230430135941985](https://cdn.jsdelivr.net/gh/yzk656/image/202304301359110.png)

![image-20230430135956087](https://cdn.jsdelivr.net/gh/yzk656/image/202304301359212.png)

![image-20230501150207186](https://cdn.jsdelivr.net/gh/yzk656/image/202305011502528.png)

![image-20230501150232185](https://cdn.jsdelivr.net/gh/yzk656/image/202305011502334.png)

![image-20230501150221087](https://cdn.jsdelivr.net/gh/yzk656/image/202305011502258.png)

![image-20230501150309015](https://cdn.jsdelivr.net/gh/yzk656/image/202305011503170.png)

![image-20230501150322833](https://cdn.jsdelivr.net/gh/yzk656/image/202305011503023.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202305011504975.png)

![image-20230501150425898](https://cdn.jsdelivr.net/gh/yzk656/image/202305011504043.png)

### MyBatisplus简介

![image-20230501150818385](https://cdn.jsdelivr.net/gh/yzk656/image/202305011508520.png)

![image-20230501150942303](https://cdn.jsdelivr.net/gh/yzk656/image/202305011509447.png)

## 标准数据层开发

### 标准数据层CRUD功能

![image-20230501151407515](https://cdn.jsdelivr.net/gh/yzk656/image/202305011514725.png)

![image-20230501165655185](https://cdn.jsdelivr.net/gh/yzk656/image/202305011656372.png)

![image-20230501165729339](https://cdn.jsdelivr.net/gh/yzk656/image/202305011657501.png)

只有`data`注解的话是没无参和全参构造函数的

### 标准分页功能制作

![image-20230501235248250](https://cdn.jsdelivr.net/gh/yzk656/image/202305012352433.png)

![image-20230502000334540](https://cdn.jsdelivr.net/gh/yzk656/image/202305020003702.png)

![image-20230502000341208](https://cdn.jsdelivr.net/gh/yzk656/image/202305020003360.png)

![image-20230502000346948](https://cdn.jsdelivr.net/gh/yzk656/image/202305020003112.png)



## DQL编程控制

### 条件查询三种格式

![image-20230502000609856](https://cdn.jsdelivr.net/gh/yzk656/image/202305020006089.png)

```java
        /*方式1 按条件查询*/
/*        QueryWrapper wrapper=new QueryWrapper();
        wrapper.lt("age",10);
        List list = userDao.selectList(wrapper);
        System.out.println(list);*/


        /*方式2 lambda格式条件查询*/
/*        QueryWrapper<User> wrapper=new QueryWrapper();
        wrapper.lambda().lt(User::getAge,19);
        List list = userDao.selectList(wrapper);
        System.out.println(list);*/


        /*方式3 Lambda格式按条件查询*/
/*        LambdaQueryWrapper<User> lqw=new LambdaQueryWrapper<>();
        lqw.lt(User::getAge,19);
        List list = userDao.selectList(lqw);
        System.out.println(list);*/


        /*多条件查询*/
/*        LambdaQueryWrapper<User> lqw=new LambdaQueryWrapper<>();
        lqw.lt(User::getAge,30);
        lqw.gt(User::getAge,10);
        List list = userDao.selectList(lqw);
        System.out.println(list);*/

        /*链式编程*/
        LambdaQueryWrapper<User> lqw=new LambdaQueryWrapper<>();
        /*10-30之间*/
        /*lqw.lt(User::getAge,30).gt(User::getAge,10);*/
        /*小于10 或者 大于30*/
        lqw.lt(User::getAge,10).or().gt(User::getAge,30);
        List list = userDao.selectList(lqw);
        System.out.println(list);
```

![image-20230502003639334](https://cdn.jsdelivr.net/gh/yzk656/image/202305020036499.png)

![image-20230502003705079](https://cdn.jsdelivr.net/gh/yzk656/image/202305020037272.png)

![image-20230502003735795](https://cdn.jsdelivr.net/gh/yzk656/image/202305020037989.png)

### 条件查询 null 判定

![image-20230502003926112](https://cdn.jsdelivr.net/gh/yzk656/image/202305020039285.png)

```java
        /*模拟页面传递过来的查询数据*/
        UserQuery userQuery = new UserQuery();
//        userQuery.setAge(10);
        userQuery.setAge2(30);

        /*链式编程*/
        LambdaQueryWrapper<User> lqw=new LambdaQueryWrapper<>();
        /*先判定第一个参数是否为true，如果为true连接当前条件*/
        lqw.lt(null!=userQuery.getAge2(),User::getAge,userQuery.getAge2());
        lqw.lt(null!=userQuery.getAge(),User::getAge,userQuery.getAge());
        List list = userDao.selectList(lqw);
        System.out.println(list);
```



![image-20230502005748535](https://cdn.jsdelivr.net/gh/yzk656/image/202305020057705.png)

![image-20230502005822781](https://cdn.jsdelivr.net/gh/yzk656/image/202305020058965.png)

### 查询投影

```java
        /*查询投影*/
        QueryWrapper<User> queryWrapper=new QueryWrapper<>();
        queryWrapper.select("count(*) as count");
        queryWrapper.groupBy("tel");
        List<Map<String, Object>> maps = userDao.selectMaps(queryWrapper);
        System.out.println(maps);
```



![image-20230502011006628](https://cdn.jsdelivr.net/gh/yzk656/image/202305020110805.png)

### 查询条件设置

![image-20230502011256001](https://cdn.jsdelivr.net/gh/yzk656/image/202305020112146.png)

```java
//        模糊查询
        LambdaQueryWrapper<User> lambdaQueryWrapper=new LambdaQueryWrapper<>();
        lambdaQueryWrapper.likeLeft(User::getName,"t");
        List<User> list = userDao.selectList(lambdaQueryWrapper);
        System.out.println(list);
```

对于`likeLeft`是`%t`左边是百分号

![image-20230502143858908](https://cdn.jsdelivr.net/gh/yzk656/image/202305021438012.png)

![image-20230502143929821](https://cdn.jsdelivr.net/gh/yzk656/image/202305021439903.png)

![image-20230502143938765](https://cdn.jsdelivr.net/gh/yzk656/image/202305021439819.png)

### 映射匹配兼容性

![image-20230502144232815](https://cdn.jsdelivr.net/gh/yzk656/image/202305021442877.png)

![image-20230502144242638](https://cdn.jsdelivr.net/gh/yzk656/image/202305021442699.png)

![image-20230502144248900](https://cdn.jsdelivr.net/gh/yzk656/image/202305021442961.png)

![image-20230502144401295](https://cdn.jsdelivr.net/gh/yzk656/image/202305021444384.png)

![image-20230502144414009](https://cdn.jsdelivr.net/gh/yzk656/image/202305021444073.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202305021445550.png)

![image-20230502144547689](https://cdn.jsdelivr.net/gh/yzk656/image/202305021445764.png)

![image-20230502144631191](https://cdn.jsdelivr.net/gh/yzk656/image/202305021446265.png)

![image-20230502144655522](https://cdn.jsdelivr.net/gh/yzk656/image/202305021446577.png)

## DML编程控制

### id生成策略

![image-20230502145816008](https://cdn.jsdelivr.net/gh/yzk656/image/202305021458056.png)

![image-20230502145833219](https://cdn.jsdelivr.net/gh/yzk656/image/202305021458283.png)

![image-20230502151206712](https://cdn.jsdelivr.net/gh/yzk656/image/202305021512787.png)

![image-20230502151550521](https://cdn.jsdelivr.net/gh/yzk656/image/202305021515600.png)

![image-20230502151603993](https://cdn.jsdelivr.net/gh/yzk656/image/202305021516042.png)

### 多数据操作（删除和查询）

![image-20230502155451559](https://cdn.jsdelivr.net/gh/yzk656/image/202305021554620.png)

### 逻辑删除

![image-20230502155520433](https://cdn.jsdelivr.net/gh/yzk656/image/202305021555491.png)

![image-20230502161247897](https://cdn.jsdelivr.net/gh/yzk656/image/202305021612947.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202305021612045.png)

![image-20230502161335901](https://cdn.jsdelivr.net/gh/yzk656/image/202305021613986.png)

### 乐观锁

就是不让同一个数据能够同时修改两次

![image-20230502164751398](https://cdn.jsdelivr.net/gh/yzk656/image/202305021647441.png)

![image-20230502165040490](https://cdn.jsdelivr.net/gh/yzk656/image/202305021650549.png)

![image-20230502165046537](https://cdn.jsdelivr.net/gh/yzk656/image/202305021650589.png)

![image-20230502165057813](https://cdn.jsdelivr.net/gh/yzk656/image/202305021650891.png)

![image-20230502165143910](https://cdn.jsdelivr.net/gh/yzk656/image/202305021651988.png)

## 快速开发

### 代码生成器

![](https://cdn.jsdelivr.net/gh/yzk656/image/202305021658868.png)

![image-20230502170128909](https://cdn.jsdelivr.net/gh/yzk656/image/202305021701984.png)

![image-20230502170136094](https://cdn.jsdelivr.net/gh/yzk656/image/202305021701182.png)

![image-20230502170143702](https://cdn.jsdelivr.net/gh/yzk656/image/202305021701737.png)

![image-20230502210356959](https://cdn.jsdelivr.net/gh/yzk656/image/202305022103155.png)

![image-20230502210408462](https://cdn.jsdelivr.net/gh/yzk656/image/202305022104524.png)

![image-20230502210431888](https://cdn.jsdelivr.net/gh/yzk656/image/202305022104991.png)

![image-20230502210439396](https://cdn.jsdelivr.net/gh/yzk656/image/202305022104488.png)

![image-20230502210450991](https://cdn.jsdelivr.net/gh/yzk656/image/202305022104092.png)
