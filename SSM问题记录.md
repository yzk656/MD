## java.lang.IllegalArgumentException: Unsupported class file major version 63

​	at

![image-20230413132303720](https://cdn.jsdelivr.net/gh/yzk656/image/202304131323767.png)

>  解决办法

![image-20230413132322448](https://cdn.jsdelivr.net/gh/yzk656/image/202304131323488.png)

# 数据库主从复制

最开始，我是想把虚拟机中的`mysql`作为主库`master`，自己的服务器中的`mysql`作为从库`slave`,但是无论如何都无法连接上，同时我发现一个问题就是虚拟机突然无法连接外网，我以为是这个问题，导致从库不能连接上主库呢

1. 解决虚拟机无法上网问题
   最初我打算使用静态代理的，修改的是ens33网关配置

   ```java
   TYPE=Ethernet
   PROXY_METHOD=none
   BROWSER_ONLY=no
   BOOTPROTO=dhcp
   DEFROUTE=yes
   IPV4_FAILURE_FATAL=no
   IPV6INIT=yes
   IPV6_AUTOCONF=yes
   IPV6_DEFROUTE=yes
   IPV6_FAILURE_FATAL=no
   IPV6_ADDR_GEN_MODE=stable-privacy
   NAME=ens33
   UUID=b7e9cd81-0df2-4b38-96bb-72d33cfb8ea0
   DEVICE=ens33
   ONBOOT=yes
   ```

   这里先配一个图，一遍理解连接外网的流程：

   ![image-20230624135151211](https://cdn.jsdelivr.net/gh/yzk656/image/202306241351492.png)

   ==但是按照他这种方式我并没有连接成功，但是我朋友能够连接成功，于是我按照他的配置进行了修改，请注意看下面第二图片，勾选了DHCP自动配置==

   ![image-20230624135422917](https://cdn.jsdelivr.net/gh/yzk656/image/202306241354503.png)

   ![image-20230624135444047](https://cdn.jsdelivr.net/gh/yzk656/image/202306241354432.png)

   ![image-20230624135540848](https://cdn.jsdelivr.net/gh/yzk656/image/202306241355189.png)

   ![image-20230624135556857](https://cdn.jsdelivr.net/gh/yzk656/image/202306241355238.png)

   > 总结：
   >
   > 1. 我按照他这个配置，进行了修改，同时修改了ens33网络配置文件，但是进行重启网络服务后`IP`地址竟然失败了，然后我就想着安装LINUX图形界面去里面看一下，安装完成后显示有网络连接，但是`ifconfig`并没有找到`IP`地址
   >
   > 2. 于是我就`重启电脑(主机)`再进行查询就能够查询到`IP`地址了
   >
   >  	3. 接下来验证`DHCP`的作用：我后来把ens33文件删除后，仍然能够查询到`IP`地址.通过实验证明，如果勾选`DHCP`选项，ens33应该就不会发挥作用了
   >  	4. `重启解决一切`

2. 解决了虚拟机连接外网问题后，接下来解决两个数据库进行连接

   > 我当时以为是防火墙问题（之前我已经把相应的3306端口已经打开了），关=关闭防火墙后还是无法连接
   >
   >  
   >
   > 我于是右新建了一个虚拟机，不再使用自己的服务器作为从库`slave`了。令人震惊的是使用虚拟机竟然可以连接，难道不是同一网段下不能够连接成功吗？
   >
   >  
   >
   > 这次错误就这样莫名其妙解决了！！！