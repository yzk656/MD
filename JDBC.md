## mysql安装配置

![image-20221225204451424](https://cdn.jsdelivr.net/gh/yzk656/image/202212252044475.png)

![image-20221225204442232](https://cdn.jsdelivr.net/gh/yzk656/image/202212252044326.png)

![image-20221225204635981](https://cdn.jsdelivr.net/gh/yzk656/image/202212252046041.png)

![image-20221225204951360](https://cdn.jsdelivr.net/gh/yzk656/image/202212252049426.png)

![image-20221225205019492](https://cdn.jsdelivr.net/gh/yzk656/image/202212252050528.png)

````
[mysqld]
#设置3306端口号
port=3306
#设置MySQL的安装目录
basedir=E:\\SoftWare\mysql-8.0.30-winx64
#设置MySQL数据库的数据存放目录
datadir=E:\\SoftWare\mysql-8.0.30-winx64\data
#运行最大连接数
max_connections=200
#运行连接失败的次数。这也是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10
#服务端使用的字符集默认为utf-8
character-set-server=utf8
[mysql]
#客户端使用的字符集默认为utf8
default-character-set=utf8
[client]
#客户端默认端口号为3306
port=3306
````

![image-20221225205534594](https://cdn.jsdelivr.net/gh/yzk656/image/202212252055648.png)

![image-20221225210122576](https://cdn.jsdelivr.net/gh/yzk656/image/202212252101619.png)

![image-20221225210247428](https://cdn.jsdelivr.net/gh/yzk656/image/202212252102484.png)





出现报错

![image-20221225210728371](https://cdn.jsdelivr.net/gh/yzk656/image/202212252107398.png)

解决办法

![image-20221225210743339](https://cdn.jsdelivr.net/gh/yzk656/image/202212252107383.png)

```
[mysqld]
#设置3306端口号
port=3306
#设置MySQL的安装目录
basedir=E:\\SoftWare\mysql-8.0.30-winx64
#设置MySQL数据库的数据存放目录
datadir=E:\\SoftWare\mysql-8.0.30-winx64\data
#运行最大连接数
max_connections=200
#运行连接失败的次数。这也是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10
#服务端使用的字符集默认为utf-8
character-set-server=utf8
[mysql]
#客户端使用的字符集默认为utf8
default-character-set=utf8
[client]
#客户端默认端口号为3306
port=3306
```

![image-20221225210926952](https://cdn.jsdelivr.net/gh/yzk656/image/202212252109003.png)

```
E:\SoftWare\mysql-8.0.30-winx64\bin>net start mysql
MySQL 服务正在启动 .
MySQL 服务已经启动成功。
```

















## 第一天

![image-20221117142451441](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221117142451441.png)

![image-20221117145343059](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221117145343059.png)

![image-20221117145443594](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221117145443594.png)

![image-20221117145835925](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221117145835925.png)

![image-20221117152943299](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221117152943299.png)

![image-20221117154247077](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221117154247077.png)

![image-20221117154313852](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221117154313852.png)

![image-20221117155756983](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221117155756983.png)

![image-20221118002344452](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118002344452.png)

![image-20221118003305773](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118003305773.png)

![image-20221118005236976](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118005236976.png)

![image-20221118005429334](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118005429334.png)

![image-20221118012037616](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118012037616.png)

![image-20221118012501969](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118012501969.png)

![image-20221118012856446](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118012856446.png)

![image-20221118013833394](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118013833394.png)

![image-20221118014037299](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118014037299.png)

## 第二天

![image-20221118095552145](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118095640336.png)

![image-20221118100332562](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118100332562.png)

![image-20221118100555408](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221118100555408.png)

![image-20221119001339174](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119001339174.png)

快捷键ctrl+alt+T

![image-20221119004329616](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119004329616.png)

![image-20221119004714510](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119004714510.png)

![image-20221119012233130](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119012233130.png)

![image-20221119013745146](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119013745146.png)

![image-20221119013826284](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119013826284.png)

![image-20221119014638304](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119014638304.png)

![image-20221119015041295](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119015041295.png)

![image-20221119015827109](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119015827109.png)

![image-20221119015843060](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119015843060.png)

## 第三天

使用c3p0-0.9.5.5.bin（高版本）`就需要使用两个jar包`

![image-20221119115053229](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119115053229.png)

![image-20221119115111003](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119115111003.png)

![image-20221119171851272](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119171851272.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119191606005.png)

![image-20221119191849801](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119191849801.png)

![image-20221119193738057](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119193738057.png)

![image-20221119220757305](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119220757305.png)

![image-20221119221022122](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119221022122.png)

![image-20221119232441438](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221119232441438.png)

![image-20221120000135353](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221120000135353.png)

## 第四天

![image-20221120102938645](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221120102938645.png)

![image-20221120104720790](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221120104720790.png)

![image-20221120104801531](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221120104801531.png)

![image-20221120104818146](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221120104818146.png)

![image-20221120105050029](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221120105050029.png) 

![image-20221120105547881](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221120105547881.png)

![image-20221120160444483](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221120160444483.png)

![image-20221120173240195](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221120173240195.png)

## 知识梳理

在添加时间时不需要使用双引号

![image-20221201085741759](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221201085741759.png)

正确格式：

![image-20221201090743833](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221201090743833.png)

获取date【上面带时间，下面那个不带】

![image-20221201091948267](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221201091948267.png)

设置时间，java里面用的是java.util.date,为数据库设置时，用的是sql里面的date

![image-20221201092036797](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221201092036797.png)