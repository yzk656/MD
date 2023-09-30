# 认识微服务

![image-20230628010801045](https://cdn.jsdelivr.net/gh/yzk656/image/202306280108149.png)

![image-20230628012410514](https://cdn.jsdelivr.net/gh/yzk656/image/202306280124620.png)

![image-20230628012443635](https://cdn.jsdelivr.net/gh/yzk656/image/202306280124728.png)

![image-20230628012557093](https://cdn.jsdelivr.net/gh/yzk656/image/202306280125165.png)

![image-20230628012840361](https://cdn.jsdelivr.net/gh/yzk656/image/202306280128465.png)

![image-20230628012926764](https://cdn.jsdelivr.net/gh/yzk656/image/202306280129835.png)

# 第一天

## 认识微服务



![image-20230628013517549](https://cdn.jsdelivr.net/gh/yzk656/image/202306280135626.png)

![image-20230628013855256](https://cdn.jsdelivr.net/gh/yzk656/image/202306280138322.png)

![image-20230628013934071](https://cdn.jsdelivr.net/gh/yzk656/image/202306280139134.png)

![image-20230628014138898](https://cdn.jsdelivr.net/gh/yzk656/image/202306280141990.png)

![image-20230628014559100](https://cdn.jsdelivr.net/gh/yzk656/image/202306280145157.png)

![image-20230628014713945](https://cdn.jsdelivr.net/gh/yzk656/image/202306280147015.png)

![image-20230628231623053](https://cdn.jsdelivr.net/gh/yzk656/image/202306282316135.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202306282317319.png)

## 服务拆分及远程调用

![](https://cdn.jsdelivr.net/gh/yzk656/image/202306282324862.png)

![image-20230628233923809](https://cdn.jsdelivr.net/gh/yzk656/image/202306282339858.png)

![image-20230628234155717](https://cdn.jsdelivr.net/gh/yzk656/image/202306282341775.png)

![image-20230628234253260](https://cdn.jsdelivr.net/gh/yzk656/image/202306282342312.png)

![image-20230628235744635](https://cdn.jsdelivr.net/gh/yzk656/image/202306282357689.png)

![image-20230629103854328](https://cdn.jsdelivr.net/gh/yzk656/image/202306291038415.png)

![image-20230630225718488](https://cdn.jsdelivr.net/gh/yzk656/image/202306302257651.png)

![image-20230630225833626](https://cdn.jsdelivr.net/gh/yzk656/image/202306302258683.png)

## Eureka-提供者与消费者

![image-20230630230122888](https://cdn.jsdelivr.net/gh/yzk656/image/202306302301948.png)

![image-20230630230129515](https://cdn.jsdelivr.net/gh/yzk656/image/202306302301557.png)

一个服务既可以是提供者又可以是消费者，主要看是相对于谁而言

![image-20230630230233466](https://cdn.jsdelivr.net/gh/yzk656/image/202306302302509.png)

### Eureka注册中心

![image-20230630230523171](https://cdn.jsdelivr.net/gh/yzk656/image/202306302305234.png)

![image-20230630230754903](https://cdn.jsdelivr.net/gh/yzk656/image/202306302307991.png)

![image-20230630230848868](https://cdn.jsdelivr.net/gh/yzk656/image/202306302308921.png)

![image-20230630230857019](https://cdn.jsdelivr.net/gh/yzk656/image/202306302308082.png)

![image-20230630231000536](https://cdn.jsdelivr.net/gh/yzk656/image/202306302310606.png)

![image-20230630231006981](https://cdn.jsdelivr.net/gh/yzk656/image/202306302310056.png)

![image-20230630233339319](https://cdn.jsdelivr.net/gh/yzk656/image/202306302333370.png)

###  服务注册

![image-20230630233349058](https://cdn.jsdelivr.net/gh/yzk656/image/202306302333124.png)

![image-20230630234154340](https://cdn.jsdelivr.net/gh/yzk656/image/202306302341409.png)

![image-20230630234738168](https://cdn.jsdelivr.net/gh/yzk656/image/202306302347235.png)

![image-20230630234819991](https://cdn.jsdelivr.net/gh/yzk656/image/202306302348036.png)

### 服务发现

![image-20230630234837692](https://cdn.jsdelivr.net/gh/yzk656/image/202306302348761.png)

 

![image-20230630235646751](https://cdn.jsdelivr.net/gh/yzk656/image/202306302356820.png)

## Ribbon负载均衡原理

![image-20230630235853193](https://cdn.jsdelivr.net/gh/yzk656/image/202306302358254.png)

![image-20230701001558287](https://cdn.jsdelivr.net/gh/yzk656/image/202307010015363.png)

### 负载均衡策略

![image-20230701001711483](https://cdn.jsdelivr.net/gh/yzk656/image/202307010017567.png)

![image-20230701001723448](https://cdn.jsdelivr.net/gh/yzk656/image/202307010017545.png)

![image-20230701002258590](https://cdn.jsdelivr.net/gh/yzk656/image/202307010022657.png)

> 第一个是针对任意一个服务
>
> 第二个是针对指定服务

### 饥饿加载

![image-20230701002841394](https://cdn.jsdelivr.net/gh/yzk656/image/202307010028446.png)

![image-20230701003619635](https://cdn.jsdelivr.net/gh/yzk656/image/202307010036702.png)

## Nacos 认识和安装nacos

![image-20230701003804503](https://cdn.jsdelivr.net/gh/yzk656/image/202307010038559.png)

> 在Nacos的GitHub页面，提供有下载链接，可以下载编译好的Nacos服务端或者源代码：
>
> GitHub主页：https://github.com/alibaba/nacos
>
> GitHub的Release下载页：https://github.com/alibaba/nacos/releases

### 快速入门

![image-20230701005007853](https://cdn.jsdelivr.net/gh/yzk656/image/202307010050904.png)

![image-20230701005137728](https://cdn.jsdelivr.net/gh/yzk656/image/202307010051788.png)

父工程

```java
<dependency>
    <groupId>com.alibaba.cloud</groupId>
    <artifactId>spring-cloud-alibaba-dependencies</artifactId>
    <version>2.2.5.RELEASE</version>
    <type>pom</type>
    <scope>import</scope>
</dependency>
```

客户端

```java
<!-- nacos客户端依赖包 -->
<dependency>
    <groupId>com.alibaba.cloud</groupId>
    <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
</dependency>
```

![image-20230701010109764](https://cdn.jsdelivr.net/gh/yzk656/image/202307010101810.png)

![image-20230701141724405](https://cdn.jsdelivr.net/gh/yzk656/image/202307011417577.png)

![image-20230701141816749](https://cdn.jsdelivr.net/gh/yzk656/image/202307011418814.png)

![image-20230701142423611](https://cdn.jsdelivr.net/gh/yzk656/image/202307011424669.png)

![image-20230701142945225](https://cdn.jsdelivr.net/gh/yzk656/image/202307011429282.png)

### NacosRule负载均衡

![image-20230701143024119](https://cdn.jsdelivr.net/gh/yzk656/image/202307011430184.png)

 ![image-20230701143647109](https://cdn.jsdelivr.net/gh/yzk656/image/202307011436169.png)

![image-20230701144249259](https://cdn.jsdelivr.net/gh/yzk656/image/202307011442300.png)

### Nacos服务实例的权重设置

![image-20230701144446692](https://cdn.jsdelivr.net/gh/yzk656/image/202307011444753.png)

![image-20230701144911292](https://cdn.jsdelivr.net/gh/yzk656/image/202307011449340.png)

### Nacos环境隔离

![image-20230701145112863](https://cdn.jsdelivr.net/gh/yzk656/image/202307011451962.png)

![image-20230701145301250](https://cdn.jsdelivr.net/gh/yzk656/image/202307011453313.png)

![image-20230701145306647](https://cdn.jsdelivr.net/gh/yzk656/image/202307011453702.png)

![image-20230701145312662](https://cdn.jsdelivr.net/gh/yzk656/image/202307011453706.png)

![image-20230701145320034](https://cdn.jsdelivr.net/gh/yzk656/image/202307011453103.png)

![image-20230701145546731](https://cdn.jsdelivr.net/gh/yzk656/image/202307011455827.png)

![image-20230701145554994](https://cdn.jsdelivr.net/gh/yzk656/image/202307011455038.png)

### Nacos与Eureka对比

![image-20230701150140968](https://cdn.jsdelivr.net/gh/yzk656/image/202307011501026.png)

![image-20230701150151065](https://cdn.jsdelivr.net/gh/yzk656/image/202307011501104.png)

![image-20230701150839094](https://cdn.jsdelivr.net/gh/yzk656/image/202307011508161.png)

# 第二天

![image-20230701150923424](https://cdn.jsdelivr.net/gh/yzk656/image/202307011509457.png)

## Nacos

### Nacos配置管理

![image-20230701164826216](https://cdn.jsdelivr.net/gh/yzk656/image/202307011648276.png)

![image-20230701164832043](https://cdn.jsdelivr.net/gh/yzk656/image/202307011648111.png)

![image-20230701164842031](https://cdn.jsdelivr.net/gh/yzk656/image/202307011648088.png)

### 微服务配置拉取

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307011651772.png)

![image-20230701165135582](https://cdn.jsdelivr.net/gh/yzk656/image/202307011651650.png)

![image-20230701170537023](https://cdn.jsdelivr.net/gh/yzk656/image/202307011705082.png)

![image-20230701170545227](https://cdn.jsdelivr.net/gh/yzk656/image/202307011705273.png)

### 配置热更新

![image-20230701171512685](https://cdn.jsdelivr.net/gh/yzk656/image/202307011715749.png)

![image-20230701171748012](https://cdn.jsdelivr.net/gh/yzk656/image/202307011717058.png)

![image-20230701214527739](https://cdn.jsdelivr.net/gh/yzk656/image/202307012145808.png)

### 多环境配置共享

![image-20230701220522332](https://cdn.jsdelivr.net/gh/yzk656/image/202307012205403.png)

![image-20230701221258889](https://cdn.jsdelivr.net/gh/yzk656/image/202307012212916.png)

![image-20230701222404006](https://cdn.jsdelivr.net/gh/yzk656/image/202307012224049.png)

![image-20230701222412531](https://cdn.jsdelivr.net/gh/yzk656/image/202307012224582.png)

### Nacos集群搭建

![image-20230701222758057](https://cdn.jsdelivr.net/gh/yzk656/image/202307012227115.png)

![image-20230701222805383](https://cdn.jsdelivr.net/gh/yzk656/image/202307012228435.png)

![image-20230702011338537](https://cdn.jsdelivr.net/gh/yzk656/image/202307020113748.png)

```java
	upstream nacos-cluster {
		server 127.0.0.1:8845;
		server 127.0.0.1:8846;
		server 127.0.0.1:8847;
	}

	server {
		listen       80;
		server_name  localhost;

		location /nacos {
			proxy_pass http://nacos-cluster;
		}
	}
```

## Feign

![image-20230702012237816](https://cdn.jsdelivr.net/gh/yzk656/image/202307020122874.png)

![image-20230702012428569](https://cdn.jsdelivr.net/gh/yzk656/image/202307020124651.png)

![image-20230702012439933](https://cdn.jsdelivr.net/gh/yzk656/image/202307020124042.png)

![image-20230702012532328](https://cdn.jsdelivr.net/gh/yzk656/image/202307020125444.png)

![image-20230702012600902](https://cdn.jsdelivr.net/gh/yzk656/image/202307020126992.png)

```java
        <!--feign客户端依赖-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-openfeign</artifactId>
        </dependency>
```

![image-20230702014808180](https://cdn.jsdelivr.net/gh/yzk656/image/202307020148292.png)

![image-20230702014819681](https://cdn.jsdelivr.net/gh/yzk656/image/202307020148759.png)

### 自定义配置

![image-20230702105822939](https://cdn.jsdelivr.net/gh/yzk656/image/202307021058044.png)

![image-20230702111410425](https://cdn.jsdelivr.net/gh/yzk656/image/202307021114530.png)

![image-20230702111417570](https://cdn.jsdelivr.net/gh/yzk656/image/202307021114674.png)

![image-20230702112434039](https://cdn.jsdelivr.net/gh/yzk656/image/202307021124128.png)

### 性能优化

![image-20230702112656099](https://cdn.jsdelivr.net/gh/yzk656/image/202307021126171.png)

![image-20230702112704688](https://cdn.jsdelivr.net/gh/yzk656/image/202307021127796.png)

![image-20230702115058468](https://cdn.jsdelivr.net/gh/yzk656/image/202307021150557.png)

### 最佳实践分析

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307021156573.png)

![image-20230702115837482](https://cdn.jsdelivr.net/gh/yzk656/image/202307021158600.png)

![image-20230702115849057](https://cdn.jsdelivr.net/gh/yzk656/image/202307021158147.png)

### 实现最佳实践（方式2）

![image-20230702120031648](https://cdn.jsdelivr.net/gh/yzk656/image/202307021200736.png)

![image-20230702134354588](https://cdn.jsdelivr.net/gh/yzk656/image/202307021343692.png)

![image-20230702134656893](https://cdn.jsdelivr.net/gh/yzk656/image/202307021346971.png)

## Gateway

![image-20230702134849918](https://cdn.jsdelivr.net/gh/yzk656/image/202307021348983.png)

![image-20230702135212378](https://cdn.jsdelivr.net/gh/yzk656/image/202307021352510.png)

![image-20230702135302891](https://cdn.jsdelivr.net/gh/yzk656/image/202307021353970.png)

![image-20230702135319406](https://cdn.jsdelivr.net/gh/yzk656/image/202307021353476.png)

### 快速入门

![image-20230702135347318](https://cdn.jsdelivr.net/gh/yzk656/image/202307021353435.png)

![image-20230702140347912](https://cdn.jsdelivr.net/gh/yzk656/image/202307021403974.png)

![image-20230702141952304](https://cdn.jsdelivr.net/gh/yzk656/image/202307021419401.png)

![image-20230702142039515](https://cdn.jsdelivr.net/gh/yzk656/image/202307021420618.png)

### 路由断言工厂

![image-20230702142135438](https://cdn.jsdelivr.net/gh/yzk656/image/202307021421510.png)

![image-20230702142628298](https://cdn.jsdelivr.net/gh/yzk656/image/202307021426376.png)

![image-20230702142634858](https://cdn.jsdelivr.net/gh/yzk656/image/202307021426955.png)

![image-20230702143640532](https://cdn.jsdelivr.net/gh/yzk656/image/202307021436607.png)

### 路由的过滤器配置

![image-20230702143906451](https://cdn.jsdelivr.net/gh/yzk656/image/202307021439536.png)

![image-20230702144134112](https://cdn.jsdelivr.net/gh/yzk656/image/202307021441212.png)

> lb:负载均衡（Load Balancer（负载均衡器））

![image-20230702144754896](https://cdn.jsdelivr.net/gh/yzk656/image/202307021447996.png)

![image-20230702145040860](https://cdn.jsdelivr.net/gh/yzk656/image/202307021450952.png)

### 全局过滤器

![image-20230702145250815](https://cdn.jsdelivr.net/gh/yzk656/image/202307021452938.png)

![image-20230702145338572](https://cdn.jsdelivr.net/gh/yzk656/image/202307021453646.png)

![image-20230702162320002](https://cdn.jsdelivr.net/gh/yzk656/image/202307021623118.png)

![image-20230702162337651](https://cdn.jsdelivr.net/gh/yzk656/image/202307021623739.png)

### 过滤器链执行顺序

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307021628547.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307021659565.png)

![image-20230702170013352](https://cdn.jsdelivr.net/gh/yzk656/image/202307021700444.png)

### 网关的cors跨域配置

![image-20230702170317797](https://cdn.jsdelivr.net/gh/yzk656/image/202307021703871.png)

![image-20230702170324311](https://cdn.jsdelivr.net/gh/yzk656/image/202307021703412.png)

![image-20230702175446920](https://cdn.jsdelivr.net/gh/yzk656/image/202307021754014.png)

```java
npm install live-server -g
live-server --port=8090
```

# 第三天

## Docker

### 初始Docker

![image-20230709212816440](https://cdn.jsdelivr.net/gh/yzk656/image/202307092128518.png)



![image-20230709213103452](https://cdn.jsdelivr.net/gh/yzk656/image/202307092131564.png)

![image-20230709213124878](https://cdn.jsdelivr.net/gh/yzk656/image/202307092131007.png)

![image-20230709213504588](https://cdn.jsdelivr.net/gh/yzk656/image/202307092135653.png)

> 不同的系统应用就有不同库函数，但是都是同一种内核
>
> 因此可以把库函数进行打包，这样就不用调用当前平台的库函数了，就直接使用打包的库函数来调用系统内核

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307092139663.png)

![image-20230709214147940](https://cdn.jsdelivr.net/gh/yzk656/image/202307092141034.png)

![image-20230709214222503](https://cdn.jsdelivr.net/gh/yzk656/image/202307092142586.png)

![image-20230709214302335](https://cdn.jsdelivr.net/gh/yzk656/image/202307092143385.png)

![image-20230709214616054](https://cdn.jsdelivr.net/gh/yzk656/image/202307092146128.png)

![image-20230709214716665](https://cdn.jsdelivr.net/gh/yzk656/image/202307092147746.png)

![image-20230709214930774](https://cdn.jsdelivr.net/gh/yzk656/image/202307092149866.png)

![image-20230709215015174](https://cdn.jsdelivr.net/gh/yzk656/image/202307092150235.png)

![image-20230709215059190](https://cdn.jsdelivr.net/gh/yzk656/image/202307092150241.png)

### Docker基本操作

#### 镜像命令

![image-20230709221214949](https://cdn.jsdelivr.net/gh/yzk656/image/202307092212005.png)

![image-20230709221542552](https://cdn.jsdelivr.net/gh/yzk656/image/202307092215626.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307092222061.png)

![image-20230710103959779](https://cdn.jsdelivr.net/gh/yzk656/image/202307101039838.png)

![image-20230710103944483](https://cdn.jsdelivr.net/gh/yzk656/image/202307101039541.png)

![image-20230710104104633](https://cdn.jsdelivr.net/gh/yzk656/image/202307101041689.png)

![image-20230716114221714](https://cdn.jsdelivr.net/gh/yzk656/image/202307161142815.png)

> 启动Docker

```java
systemctl start docker  # 启动docker服务

systemctl stop docker  # 停止docker服务

systemctl restart docker  # 重启docker服务
```

#### 容器命令

![image-20230716121500748](https://cdn.jsdelivr.net/gh/yzk656/image/202307161215906.png)

> 解读：基于nginx镜像创建并运行一个容器，他的名字叫containerName，并将宿主机端口80：映射到容器80端口

![image-20230716122537274](https://cdn.jsdelivr.net/gh/yzk656/image/202307161225375.png)

![image-20230716122804130](https://cdn.jsdelivr.net/gh/yzk656/image/202307161228232.png)

> 如何关闭暂停任务

要关闭正在停止状态的任务，您可以使用以下步骤：

1. 查看任务状态：首先，使用`jobs`命令查看当前正在运行或停止的任务列表。这将显示任务的标识符（job ID）和状态信息。

2. 终止任务：根据任务的状态，使用适当的命令来终止任务。对于已停止的任务，您可以使用`kill`命令加上SIGTERM信号（或其他合适的信号）来终止任务。

   使用以下命令来终止任务：
   ```
   kill -SIGTERM %<job_id>
   ```
   其中，`<job_id>`是您要终止的任务的标识符。在您的情况下，任务的标识符为`1`，因此命令如下：
   ```
   kill -SIGTERM %1
   ```

   如果任务不响应，您也可以尝试使用SIGKILL信号强制终止任务：
   ```
   kill -SIGKILL %1
   ```

   上述命令将发送相应的信号给任务，使其终止。

注意：任务标识符（job ID）以百分号（%）开头。如果任务的标识符不是`1`，请相应地更改命令中的标识符。

希望这可以帮助您关闭已停止的任务！

![image-20230716123949903](https://cdn.jsdelivr.net/gh/yzk656/image/202307161239970.png)

```java
sed -i 's#Welcome to nginx#传智教育欢迎你#g' index.html
sed -i 's#<head>#<head><meta charset="utf-8">#g' index.html
```

![image-20230716153121126](https://cdn.jsdelivr.net/gh/yzk656/image/202307161531225.png)

![image-20230716153258576](https://cdn.jsdelivr.net/gh/yzk656/image/202307161532663.png)

![image-20230716153557043](https://cdn.jsdelivr.net/gh/yzk656/image/202307161535118.png)

> 如果你没有进行容器与宿主机进行端口映射，那么就不能修改然后进行端口映射了，但是可以保存数据然后再加载进来
>
> 但是没有找到加载办法

![image-20230716210447418](https://cdn.jsdelivr.net/gh/yzk656/image/202307162104506.png)

#### 数据卷

![image-20230717004343407](https://cdn.jsdelivr.net/gh/yzk656/image/202307170043482.png)

![image-20230717004730464](https://cdn.jsdelivr.net/gh/yzk656/image/202307170047545.png)

![image-20230717004818512](https://cdn.jsdelivr.net/gh/yzk656/image/202307170048568.png)

![image-20230717084507485](https://cdn.jsdelivr.net/gh/yzk656/image/202307170845551.png)

![image-20230717084538425](https://cdn.jsdelivr.net/gh/yzk656/image/202307170845483.png)

![image-20230717085033855](https://cdn.jsdelivr.net/gh/yzk656/image/202307170850919.png)

 ![image-20230717104322805](https://cdn.jsdelivr.net/gh/yzk656/image/202307171043902.png)

1. 如果html数据卷不存在，使用第一条指令可以自动创建数据卷并挂载

![image-20230717104452337](https://cdn.jsdelivr.net/gh/yzk656/image/202307171044398.png)

![image-20230717104804251](https://cdn.jsdelivr.net/gh/yzk656/image/202307171048338.png)

- 在床架mysql时显示端口已经被使用了，是因为我们这个虚拟机之前装过mysql，要想使用改端口，可以使用`service mysqld stop`停止mysql服务
- 然后运行创建mysql容器的命令`docker run --name mysql -e MYSQL_ROOT_PASSWORD=yzk -p 3306:3306 -v /tmp/mysql/conf/hmy.cnf:/etc/mysql/conf.d/hmy.cnf -v /tmp/mysql/data:/var/lib/mysql -d mysql:5.7.25`

![image-20230719134612056](https://cdn.jsdelivr.net/gh/yzk656/image/202307191346138.png)

![image-20230719134735743](https://cdn.jsdelivr.net/gh/yzk656/image/202307191347814.png)



### Dockerfile自定义镜像

![image-20230719140111605](https://cdn.jsdelivr.net/gh/yzk656/image/202307191401648.png)

![image-20230719140309672](https://cdn.jsdelivr.net/gh/yzk656/image/202307191403733.png)

![image-20230719140715226](https://cdn.jsdelivr.net/gh/yzk656/image/202307191407329.png)

![image-20230719140733985](https://cdn.jsdelivr.net/gh/yzk656/image/202307191407044.png)

![image-20230719141031128](https://cdn.jsdelivr.net/gh/yzk656/image/202307191410205.png)

![image-20230719141107880](https://cdn.jsdelivr.net/gh/yzk656/image/202307191411947.png)

![image-20230719142859108](https://cdn.jsdelivr.net/gh/yzk656/image/202307191428168.png)

![image-20230719142906470](https://cdn.jsdelivr.net/gh/yzk656/image/202307191429537.png)

![image-20230719150137190](https://cdn.jsdelivr.net/gh/yzk656/image/202307191501256.png)

1. 使用Dockerfile可以生成javaweb:2.0镜像这种，通过docker run --name web2.0 -p 8090:8090 -d javaweb:2.0运行该服务

### DockerCompose

![image-20230719171553553](https://cdn.jsdelivr.net/gh/yzk656/image/202307191715657.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307191754586.png)

![image-20230719175442629](https://cdn.jsdelivr.net/gh/yzk656/image/202307191754673.png)

Base自动补全命令：

```sh
# 补全命令
curl -L https://raw.githubusercontent.com/docker/compose/1.29.1/contrib/completion/bash/docker-compose > /etc/bash_completion.d/docker-compose
```

如果这里出现错误，需要修改自己的hosts文件：

```sh
echo "199.232.68.133 raw.githubusercontent.com" >> /etc/hosts
```

![image-20230719180754492](https://cdn.jsdelivr.net/gh/yzk656/image/202307191807561.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307192057938.png)

打包找不到feign-api的是因为 在父模块中的pom文件 没有管理feign-api模块 在modules中引入该模块 即可打包成功

### Docker镜像仓库

![image-20230719210206882](https://cdn.jsdelivr.net/gh/yzk656/image/202307192102935.png)

![image-20230719210213058](https://cdn.jsdelivr.net/gh/yzk656/image/202307192102118.png)

往里面写文件的时候，一定要按照老师的从主机里修改内容，我直接粘贴进去会报错

如果要是直接把yml文件内容通过shell粘贴进去，会发生报错，所以要用本地编辑器打开进行粘贴

![image-20230719215928461](https://cdn.jsdelivr.net/gh/yzk656/image/202307192159529.png)

 ![image-20230719220646703](https://cdn.jsdelivr.net/gh/yzk656/image/202307192206757.png)

![image-20230719220746369](https://cdn.jsdelivr.net/gh/yzk656/image/202307192207432.png)

## 注意：

### 如何设置docker开机自启动

要在Linux系统上设置Docker在系统开机时自动启动，通常需要启用Docker的系统服务。具体的步骤可能因Linux发行版而异，以下是一些常见的方法：

**对于使用systemd的系统（如Ubuntu 16.04+、CentOS 7+等）：**

1. 首先，确保Docker已经安装并配置好了。

2. 使用以下命令来启用Docker的systemd服务，并设置为开机自启动：

```bash
sudo systemctl enable docker
```

3. 然后，启动Docker服务：

```bash
sudo systemctl start docker
```

现在，Docker将在系统开机时自动启动。

**对于使用Upstart的系统（如Ubuntu 14.10及更早版本）：**

1. 启动Docker服务：

```bash
sudo service docker start
```

2. 使用以下命令将Docker添加到开机自启动项中：

```bash
sudo chkconfig docker on
```

**对于使用SysV init的系统（如CentOS 6及更早版本）：**

1. 启动Docker服务：

```bash
sudo service docker start
```

2. 使用以下命令将Docker添加到开机自启动项中：

```bash
sudo chkconfig docker on
```

根据你的Linux发行版和版本，上述命令可能会有所不同。请根据你的系统配置选择适当的方法，并确保在设置Docker开机自启动之后，Docker服务将在系统启动时自动运行。如果你使用的是较新的Linux版本，通常会使用systemd来管理服务。

# 第四天

![image-20230720080221730](https://cdn.jsdelivr.net/gh/yzk656/image/202307200802786.png)

## 初识MQ

### 同步调用

![image-20230720081116198](https://cdn.jsdelivr.net/gh/yzk656/image/202307200811286.png)

![image-20230720081230822](https://cdn.jsdelivr.net/gh/yzk656/image/202307200812903.png)

![image-20230720081241421](https://cdn.jsdelivr.net/gh/yzk656/image/202307200812475.png)

### 异步调用

![image-20230720081657621](https://cdn.jsdelivr.net/gh/yzk656/image/202307200816693.png)

![image-20230720081806875](https://cdn.jsdelivr.net/gh/yzk656/image/202307200818954.png)

![image-20230720081847510](https://cdn.jsdelivr.net/gh/yzk656/image/202307200818581.png)

![image-20230720082015322](https://cdn.jsdelivr.net/gh/yzk656/image/202307200820403.png)

![image-20230720082331185](https://cdn.jsdelivr.net/gh/yzk656/image/202307200823245.png)

### 什么是MQ

![image-20230720083017854](https://cdn.jsdelivr.net/gh/yzk656/image/202307200830919.png)

## RabbitMQ快速入门

![image-20230720083240892](https://cdn.jsdelivr.net/gh/yzk656/image/202307200832948.png)

![image-20230720102342605](https://cdn.jsdelivr.net/gh/yzk656/image/202307201023700.png)

![image-20230720102353540](https://cdn.jsdelivr.net/gh/yzk656/image/202307201023608.png)

![image-20230720103004692](https://cdn.jsdelivr.net/gh/yzk656/image/202307201030772.png)

![image-20230720103124860](https://cdn.jsdelivr.net/gh/yzk656/image/202307201031914.png)

![image-20230720115548086](https://cdn.jsdelivr.net/gh/yzk656/image/202307201155152.png)

![image-20230720115403201](https://cdn.jsdelivr.net/gh/yzk656/image/202307201154365.png)

- 对于消费者，采用的是回调机制，只有当消息来了，才会重写方法

![image-20230720115700716](https://cdn.jsdelivr.net/gh/yzk656/image/202307201157792.png)

## SpringAMQP

![image-20230720115809969](https://cdn.jsdelivr.net/gh/yzk656/image/202307201158017.png)

![image-20230720165502289](https://cdn.jsdelivr.net/gh/yzk656/image/202307201655433.png)

### 入门案例的消息推送

![image-20230720173852572](https://cdn.jsdelivr.net/gh/yzk656/image/202307201738728.png)

![image-20230720173921713](https://cdn.jsdelivr.net/gh/yzk656/image/202307201739774.png)

![image-20230720174013629](https://cdn.jsdelivr.net/gh/yzk656/image/202307201740718.png)

> RabbitMQ中虚拟主机的作用

在RabbitMQ中，虚拟主机（Virtual Host）是一个逻辑概念，它允许您在RabbitMQ服务器上创建多个独立的消息空间。每个虚拟主机都有自己的一组交换器（exchanges）、队列（queues）和绑定（bindings），它们是相互隔离的，就像是在RabbitMQ服务器上运行多个独立的消息代理一样。

虚拟主机的作用包括以下几个方面：

1. 逻辑隔离：虚拟主机允许在同一台RabbitMQ服务器上创建多个独立的消息空间，使得不同应用程序、不同业务或不同团队可以相互隔离地使用消息队列。这种隔离确保了消息的安全性和隐私性。

2. 权限控制：虚拟主机提供了一种机制来控制用户和应用程序对消息队列的访问权限。您可以为每个虚拟主机分配不同的用户和角色，并为它们设置不同的权限，从而实现精细的访问控制。

3. 系统资源隔离：由于每个虚拟主机都是相互隔离的，这意味着它们之间的消息处理不会相互影响。一个虚拟主机中的高负载或错误不会影响到其他虚拟主机，从而提高了系统的稳定性和可靠性。

4. 配置灵活性：通过使用虚拟主机，您可以根据应用程序或业务的需要，独立地配置交换器、队列、绑定和其他相关参数。这样，不同的应用程序可以根据自己的需求进行优化和调整，而不影响其他应用程序。

总结来说，虚拟主机在RabbitMQ中提供了逻辑隔离、权限控制、资源隔离和配置灵活性，使得RabbitMQ能够更好地满足不同应用程序之间的消息通信需求，并提供更好的可维护性和扩展性。



> 测试类为什么要加下面这些注解
>
> @RunWith(SpringRunner.class)
> @SpringBootTest

1. 加上这个是为了获得spring环境的上下文支持，不加可能会报错

在Java中，`@RunWith` 和 `@SpringBootTest` 是JUnit测试类中常见的两个注解，它们通常用于测试Spring应用程序的功能。这些注解的作用如下：

1. `@RunWith(SpringRunner.class)`: 这个注解告诉JUnit使用指定的运行器来运行测试类。在这里，`SpringRunner.class` 是Spring提供的一个特殊运行器，它与JUnit集成，使得在测试中可以使用Spring框架的功能。

2. `@SpringBootTest`: 这个注解用于指示当前测试是一个Spring Boot应用程序的集成测试。当使用该注解时，Spring Boot会加载完整的应用程序上下文，并根据类路径中的配置来配置应用程序。它会启动Spring Boot应用程序，并允许您在测试中使用注入的bean和其他Spring特性。

综合来看，这两个注解在Spring Boot的集成测试中起着关键作用：

- `@RunWith(SpringRunner.class)`：确保在测试中使用Spring提供的运行器，以便能够利用Spring的依赖注入等特性。
- `@SpringBootTest`：启动完整的Spring Boot应用程序，并允许您进行集成测试，包括测试Controller、Service等组件与它们之间的交互。

通过这些注解的结合，您可以编写更接近真实环境的集成测试，并确保Spring Boot应用程序在测试过程中的正确行为。



==注意点==

`在使用SpringAMQP之前要先创建好队列，他不在想原始那样在代码中创建了`

其实也不同，可以声明一个队列，将他放在容器中

![image-20230730111101118](https://cdn.jsdelivr.net/gh/yzk656/image/202307301111196.png)

![image-20230720183107454](https://cdn.jsdelivr.net/gh/yzk656/image/202307201831535.png)

### 入门案例的消息接收

![image-20230720183148379](https://cdn.jsdelivr.net/gh/yzk656/image/202307201831440.png)

![image-20230720183334163](https://cdn.jsdelivr.net/gh/yzk656/image/202307201833249.png)

![image-20230720192909270](https://cdn.jsdelivr.net/gh/yzk656/image/202307201929373.png)

### WorkQueue模型

![image-20230720205916314](https://cdn.jsdelivr.net/gh/yzk656/image/202307202059444.png)

![image-20230720205929064](https://cdn.jsdelivr.net/gh/yzk656/image/202307202059122.png)

![image-20230720230617428](https://cdn.jsdelivr.net/gh/yzk656/image/202307202306494.png)

`监听者和队列中的那条线就叫通道，预取的消息存放在通道中,进行预处理，慢的自然拿到的就少了`

![image-20230720230723518](https://cdn.jsdelivr.net/gh/yzk656/image/202307202307581.png)

### 发布、订阅模型

![image-20230720233834177](https://cdn.jsdelivr.net/gh/yzk656/image/202307202338266.png)

#### Fanout Exchange

![image-20230720235659639](https://cdn.jsdelivr.net/gh/yzk656/image/202307202356708.png)

![image-20230720235706046](https://cdn.jsdelivr.net/gh/yzk656/image/202307202357102.png)

![image-20230720235746378](https://cdn.jsdelivr.net/gh/yzk656/image/202307202357469.png)

![image-20230720235809302](https://cdn.jsdelivr.net/gh/yzk656/image/202307202358389.png)

![image-20230720235920007](https://cdn.jsdelivr.net/gh/yzk656/image/202307202359086.png)

![image-20230721001526854](https://cdn.jsdelivr.net/gh/yzk656/image/202307210015940.png)

![image-20230721001548195](https://cdn.jsdelivr.net/gh/yzk656/image/202307210015264.png)

![image-20230721001712878](https://cdn.jsdelivr.net/gh/yzk656/image/202307210017943.png)

#### Direct Exchange

![image-20230721064059736](https://cdn.jsdelivr.net/gh/yzk656/image/202307210640822.png)

![image-20230721064240980](https://cdn.jsdelivr.net/gh/yzk656/image/202307210642065.png)

![image-20230721064250063](https://cdn.jsdelivr.net/gh/yzk656/image/202307210642159.png)

![image-20230721070031249](https://cdn.jsdelivr.net/gh/yzk656/image/202307210700332.png)

![image-20230721070145672](https://cdn.jsdelivr.net/gh/yzk656/image/202307210701744.png)

#### Topic Exchange

![image-20230721070513317](https://cdn.jsdelivr.net/gh/yzk656/image/202307210705414.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307210706386.png)

![image-20230721073142141](https://cdn.jsdelivr.net/gh/yzk656/image/202307210731229.png)

![image-20230721073207403](https://cdn.jsdelivr.net/gh/yzk656/image/202307210732483.png)

- 在bingkey中支持通配符，在routekey中是以 . 分割

### 消息转换器

![image-20230721073925256](https://cdn.jsdelivr.net/gh/yzk656/image/202307210739343.png)

![image-20230721073958761](https://cdn.jsdelivr.net/gh/yzk656/image/202307210739843.png)

- 消息队列不仅可以直接在ui界面上直接生成，也可以在配置类中进行声明

![image-20230721075348927](https://cdn.jsdelivr.net/gh/yzk656/image/202307210753015.png)

![image-20230721075657505](https://cdn.jsdelivr.net/gh/yzk656/image/202307210757336.png)



# 第五天

## 分布式搜索

![image-20230721231930005](https://cdn.jsdelivr.net/gh/yzk656/image/202307212319095.png)

### 初识elasticsearch

![image-20230721232051687](https://cdn.jsdelivr.net/gh/yzk656/image/202307212320729.png)

![image-20230721232408674](https://cdn.jsdelivr.net/gh/yzk656/image/202307212324788.png)

![image-20230721232526096](https://cdn.jsdelivr.net/gh/yzk656/image/202307212325179.png)

![image-20230721232635145](https://cdn.jsdelivr.net/gh/yzk656/image/202307212326209.png)

![image-20230721232801097](https://cdn.jsdelivr.net/gh/yzk656/image/202307212328183.png)

![image-20230721232829931](https://cdn.jsdelivr.net/gh/yzk656/image/202307212328027.png)

![image-20230721233132532](https://cdn.jsdelivr.net/gh/yzk656/image/202307212331596.png)

![image-20230721233347575](https://cdn.jsdelivr.net/gh/yzk656/image/202307212333655.png)

![image-20230721234224484](https://cdn.jsdelivr.net/gh/yzk656/image/202307212342573.png)

![image-20230722111938174](https://cdn.jsdelivr.net/gh/yzk656/image/202307221119252.png)

#### elasticsearch与Mysql的区别

![image-20230722112036770](https://cdn.jsdelivr.net/gh/yzk656/image/202307221120847.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307221122122.png)

![image-20230722112321372](https://cdn.jsdelivr.net/gh/yzk656/image/202307221123442.png)

![image-20230722113026553](https://cdn.jsdelivr.net/gh/yzk656/image/202307221130618.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307221133086.png)

1. docker network create es-net，这句docker语句的作用

这条Docker语句的作用是在Docker中创建一个自定义的网络（Custom Bridge Network）并将其命名为 "es-net"。在Docker中，网络可以用来连接容器，使它们能够相互通信或与外部网络进行通信。

具体而言，`docker network create es-net` 这条命令会创建一个名为 "es-net" 的网络，该网络是一个自定义的桥接网络，用于连接Docker容器。通过将多个容器连接到同一个自定义网络，这些容器就可以通过网络进行通信，就好像它们在同一个局域网中一样。

使用自定义网络可以提供更好的隔离性和安全性，使容器能够更轻松地进行相互通信，并且可以更灵活地控制容器之间的连接和通信。通常情况下，可以在创建容器时通过指定 `--network` 参数来将容器连接到特定的网络，从而使容器成为该网络的一部分。

例如，如果你有一个运行Elasticsearch的容器和一个运行Kibana的容器，并且你希望它们可以相互通信，你可以使用以下命令来创建一个名为 "es-net" 的自定义网络，并将这两个容器连接到该网络：

```bash
docker network create es-net

docker run -d --name elasticsearch-container --network es-net elasticsearch:latest

docker run -d --name kibana-container --network es-net kibana:latest
```

这样，Elasticsearch容器和Kibana容器将能够通过 "es-net" 网络进行通信，而同时也与主机的网络隔离开来，提供了更好的容器管理和安全性。

#### 安装IK分词器

![image-20230722142737326](https://cdn.jsdelivr.net/gh/yzk656/image/202307221427445.png)

![image-20230722143102614](https://cdn.jsdelivr.net/gh/yzk656/image/202307221431660.png)

#### IK分词器的拓展和停用词典

![image-20230722144746770](https://cdn.jsdelivr.net/gh/yzk656/image/202307221447837.png)

![image-20230722144752334](https://cdn.jsdelivr.net/gh/yzk656/image/202307221447406.png)

![image-20230722144820613](https://cdn.jsdelivr.net/gh/yzk656/image/202307221448693.png)

![image-20230722145548305](https://cdn.jsdelivr.net/gh/yzk656/image/202307221455369.png)

### 索引库操作

![image-20230722145616911](https://cdn.jsdelivr.net/gh/yzk656/image/202307221456965.png)

![image-20230722175621632](https://cdn.jsdelivr.net/gh/yzk656/image/202307221756748.png)

![image-20230722175713169](https://cdn.jsdelivr.net/gh/yzk656/image/202307221757232.png)

#### 创建索引表

![image-20230722175938816](https://cdn.jsdelivr.net/gh/yzk656/image/202307221759897.png)

```java

PUT /heima
{
  "mappings": {
    "properties": {
      "info": {
        "type": "text",
        "analyzer": "ik_smart"
      },
      "email": {
        "type": "keyword",
        "index": false
      },
      "name": {
        "type": "object",
        "properties": {
          "firstName": {
            "type": "keyword"
          },
          "lastName": {
            "type": "keyword"
          }
        }
      }
    }
  }
}
```

#### 查询、删除、修改索引库

![image-20230725124008469](https://cdn.jsdelivr.net/gh/yzk656/image/202307251240641.png)

![image-20230725124225265](https://cdn.jsdelivr.net/gh/yzk656/image/202307251242328.png)

![image-20230725130637040](https://cdn.jsdelivr.net/gh/yzk656/image/202307251306110.png)

### 文档操作

![image-20230725130838986](https://cdn.jsdelivr.net/gh/yzk656/image/202307251308053.png)

![image-20230725131152576](https://cdn.jsdelivr.net/gh/yzk656/image/202307251311636.png)

![image-20230725131556373](https://cdn.jsdelivr.net/gh/yzk656/image/202307251315433.png)

![image-20230725131752791](https://cdn.jsdelivr.net/gh/yzk656/image/202307251317849.png)

![image-20230725132041459](https://cdn.jsdelivr.net/gh/yzk656/image/202307251320534.png)

### RestClient操作索引库

![image-20230725165930463](https://cdn.jsdelivr.net/gh/yzk656/image/202307251659864.png)

![image-20230725190956018](https://cdn.jsdelivr.net/gh/yzk656/image/202307251909165.png)

![image-20230725191051245](https://cdn.jsdelivr.net/gh/yzk656/image/202307251910386.png)

![image-20230725192407975](https://cdn.jsdelivr.net/gh/yzk656/image/202307251924027.png)

![image-20230726113011746](https://cdn.jsdelivr.net/gh/yzk656/image/202307261130841.png)

> 如果版本号被<artifactId>spring-boot-starter-parent</artifactId>管理了
>
> 可以在<properties>里指定版本号
>
> ```java
> <properties>
>     <java.version>1.8</java.version>
>     <elasticsearch.version>7.12.1</elasticsearch.version>
> </properties>
> ```

==@BeforeEach注解的作用==

`@BeforeEach` 是 JUnit 5（JUnit Jupiter）测试框架中的一个注解，它的作用是指定在每个测试方法运行之前执行的操作。

在 JUnit 4 中，我们使用 `@Before` 注解来实现相同的功能。而在 JUnit 5 中，这一功能被拆分为两个注解：`@BeforeEach` 和 `@AfterEach`。其中，`@BeforeEach` 用于在每个测试方法运行之前执行一段代码，而 `@AfterEach` 则用于在每个测试方法运行之后执行一段代码。

使用 `@BeforeEach` 注解时，可以将一些测试准备工作放在被注解的方法中，这样每次执行测试方法前都会先执行这些准备工作。这对于初始化测试数据、创建对象实例等操作非常有用，可以保证每个测试方法在相同的环境下运行，提高测试的可靠性和一致性。

以下是一个使用 `@BeforeEach` 的简单示例：

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

public class MyTest {

    @BeforeEach
    void setUp() {
        // 在每个测试方法运行之前执行的操作
        // 可以进行测试数据的初始化、对象的创建等准备工作
        System.out.println("Before each test: Setting up...");
    }

    @Test
    void test1() {
        // 测试方法1
        System.out.println("Test 1");
    }

    @Test
    void test2() {
        // 测试方法2
        System.out.println("Test 2");
    }
}
```

在上面的示例中，`@BeforeEach` 注解用于标记 `setUp()` 方法，在每个测试方法运行之前会先执行该方法。因此，在运行测试方法 `test1()` 和 `test2()` 之前，都会先执行 `setUp()` 方法，并打印 "Before each test: Setting up..."。

![image-20230726115554963](https://cdn.jsdelivr.net/gh/yzk656/image/202307261155117.png)

![image-20230726123841713](https://cdn.jsdelivr.net/gh/yzk656/image/202307261238814.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307261242404.png)

### RestClient操作文档

![image-20230726125148062](https://cdn.jsdelivr.net/gh/yzk656/image/202307261251125.png)

![image-20230726125204717](https://cdn.jsdelivr.net/gh/yzk656/image/202307261252808.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307261253564.png)

![image-20230726170717928](https://cdn.jsdelivr.net/gh/yzk656/image/202307261707071.png)

![image-20230726171738960](https://cdn.jsdelivr.net/gh/yzk656/image/202307261717054.png)

![image-20230726172750118](https://cdn.jsdelivr.net/gh/yzk656/image/202307261727180.png)

![image-20230726172843204](https://cdn.jsdelivr.net/gh/yzk656/image/202307261728272.png)

![image-20230726173157234](https://cdn.jsdelivr.net/gh/yzk656/image/202307261731321.png)

```java
    @Test
    void testBulkDocument() throws IOException {
        //获取数据
        List<Hotel> list = iHotelService.list();

        BulkRequest request = new BulkRequest();
        //转换成文档类型
        for (Hotel hotel : list) {
            HotelDoc hotelDoc = new HotelDoc(hotel);
            request.add(new IndexRequest("hotel")
                    .id(hotelDoc.getId().toString())
                    .source(JSON.toJSONString(hotelDoc),XContentType.JSON));
        }
        restHighLevelClient.bulk(request,RequestOptions.DEFAULT);
    }
```

==restclient与DSL的关系是什么==

RestClient和DSL（Domain-Specific Language）是两个不同的概念，但它们在Elasticsearch中是相关的，因为它们通常一起使用来与Elasticsearch集群进行通信和执行查询。

1. **RestClient**:
   - RestClient是一个用于与Elasticsearch集群进行通信的客户端库，它是一个轻量级的HTTP客户端，用于通过RESTful API与Elasticsearch进行交互。
   - 通过RestClient，您可以直接发送HTTP请求（GET、PUT、POST、DELETE等）来与Elasticsearch执行各种操作，如索引文档、执行查询、管理索引和集群等。
   - RestClient提供了一种简单的方式来与Elasticsearch进行通信，是一个跨语言、跨平台的解决方案。

2. **DSL（Domain-Specific Language）**:
   - DSL查询语法是Elasticsearch中用于构建复杂查询的特定领域语言。它允许用户以一种结构化的方式定义查询条件，以在Elasticsearch中执行搜索操作。
   - 使用DSL查询语法，您可以以JSON格式表示查询和过滤器，以灵活和精确的方式构建查询，满足不同场景下的搜索需求。

**关系**：
RestClient和DSL通常一起使用，特别是在编写应用程序与Elasticsearch集群进行交互时。通过RestClient，您可以发送HTTP请求到Elasticsearch，其中请求的请求体通常包含使用DSL查询语法构建的查询条件。这样，您可以将查询条件作为JSON格式的数据传递给Elasticsearch，然后由Elasticsearch执行查询并返回结果。

示例（使用Python的`requests`库作为RestClient）：

```python
import requests

# 示例：向Elasticsearch发送DSL查询请求
response = requests.get('http://localhost:9200/index_name/_search', json={
    "query": {
        "match": {
            "field": "value"
        }
    }
})

# 处理响应
if response.status_code == 200:
    result = response.json()
    # 处理结果
else:
    print("请求失败:", response.status_code, response.text)
```

在上述示例中，我们使用RestClient发送了一个DSL查询，其中查询条件使用了DSL的语法来指定匹配字段`field`中包含`value`的文档。当然，实际使用中，您可以根据具体需求构建更复杂的DSL查询，并使用RestClient将其发送给Elasticsearch。

总结：RestClient是用于与Elasticsearch进行通信的客户端库，而DSL查询语法是用于构建复杂查询的特定领域语言。RestClient通常用来发送包含DSL查询的HTTP请求，以便执行查询操作并获取结果。



# 第六天

## DSL查询语法

![image-20230726185236833](https://cdn.jsdelivr.net/gh/yzk656/image/202307261852931.png)

```java
PUT /hotel
{
  "mappings": {
    "properties": {
      "id": {
        "type": "keyword"
      },
      "name": {
        "type": "text",
        "analyzer": "ik_max_word",
        "copy_to": "{all}"
      },
      "address": {
        "type": "keyword",
        "index": false
      },
      "price": {
        "type": "integer"
      },
      "score": {
        "type": "integer"
      },
      "brand": {
        "type": "keyword",
        "copy_to": "{all}"
      },
      "city": {
        "type": "keyword"
      },
      "startName": {
        "type": "keyword"
      },
      "bussiness": {
        "type": "keyword",
        "copy_to": "{all}"
      },
      "location": {
        "type": "geo_point"
      },
      "pic": {
        "type": "keyword",
        "index": false
      },
      "all": {
        "type": "text",
        "analyzer": "ik_max_word"
      }
    }
  }
}
```



![](https://cdn.jsdelivr.net/gh/yzk656/image/202307270058140.png)

![image-20230727005922876](https://cdn.jsdelivr.net/gh/yzk656/image/202307270059952.png)

![image-20230727090132644](https://cdn.jsdelivr.net/gh/yzk656/image/202307270901767.png)

### 全文检索查询

![image-20230727090246957](https://cdn.jsdelivr.net/gh/yzk656/image/202307270902040.png)

![image-20230727113251236](https://cdn.jsdelivr.net/gh/yzk656/image/202307271132375.png)

### 精确查询

![image-20230727114308743](https://cdn.jsdelivr.net/gh/yzk656/image/202307271143846.png)

![image-20230727114331014](https://cdn.jsdelivr.net/gh/yzk656/image/202307271143088.png)

![image-20230727135441096](https://cdn.jsdelivr.net/gh/yzk656/image/202307271354218.png)

![image-20230727145239839](https://cdn.jsdelivr.net/gh/yzk656/image/202307271452918.png)



### 地理查询

![image-20230727145348403](https://cdn.jsdelivr.net/gh/yzk656/image/202307271453510.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307271455244.png)

![image-20230727145656246](https://cdn.jsdelivr.net/gh/yzk656/image/202307271456400.png)

```java
GET /hotel/_search
{
  "query": {
    "geo_distance": {
      "distance": "15km",
      "location": "31.21,121.5"
    }
  }
}
```

### 相关性算分

![image-20230727150451030](https://cdn.jsdelivr.net/gh/yzk656/image/202307271504124.png)

![image-20230727150839001](https://cdn.jsdelivr.net/gh/yzk656/image/202307271508073.png)

![image-20230727150855700](https://cdn.jsdelivr.net/gh/yzk656/image/202307271508755.png)

### Function Score Query

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307271519868.png)

![image-20230727151914013](https://cdn.jsdelivr.net/gh/yzk656/image/202307271519106.png)

![image-20230727161121671](https://cdn.jsdelivr.net/gh/yzk656/image/202307271611780.png)

### Boolean Query

![image-20230727161929323](https://cdn.jsdelivr.net/gh/yzk656/image/202307271619402.png)

![image-20230727175432603](https://cdn.jsdelivr.net/gh/yzk656/image/202307271754670.png)

## 搜索结果处理

![image-20230727183036406](https://cdn.jsdelivr.net/gh/yzk656/image/202307271830514.png)

![image-20230727183724357](https://cdn.jsdelivr.net/gh/yzk656/image/202307271837488.png)

```java
GET /hotel/_search
{
  "query": {
    "match_all": {}
  },
  "sort": [
    {
      "score": {
        "order": "desc"
      },
      "price": {
        "order": "asc"
      }
    }
  ]
}
```



### 分页

![image-20230727183913572](https://cdn.jsdelivr.net/gh/yzk656/image/202307271839638.png)

```java
GET /hotel/_search
{
  "query": {
    "match_all": {}
  },
  "sort": [
    {
      "price": {
        "order": "asc"
      }
    }
  ],
  "from": 0,
  "size": 10
}
```

![image-20230727185035256](https://cdn.jsdelivr.net/gh/yzk656/image/202307271850347.png)

![image-20230727192958962](https://cdn.jsdelivr.net/gh/yzk656/image/202307271929014.png)

![image-20230727195901609](https://cdn.jsdelivr.net/gh/yzk656/image/202307271959684.png)

### 高亮

![image-20230727224214964](https://cdn.jsdelivr.net/gh/yzk656/image/202307272242128.png)

```java
GET /hotel/_search
{
  "query": {
    "match": {
      "brand": "如家"
    }
  },
  "highlight": {
    "fields": {
      "brand": {
        "require_field_match": "false"
      }
    }
  }
}
```

![image-20230727225147235](https://cdn.jsdelivr.net/gh/yzk656/image/202307272251332.png)

## RestClient查询文档

![image-20230727225229247](https://cdn.jsdelivr.net/gh/yzk656/image/202307272252302.png)

![image-20230727225345559](https://cdn.jsdelivr.net/gh/yzk656/image/202307272253626.png)

![image-20230727230344078](https://cdn.jsdelivr.net/gh/yzk656/image/202307272303171.png)

```java
    @Test
    void testMatchAll() throws IOException {
        //准备request
        SearchRequest request = new SearchRequest("hotel");
        //准备DSL
        request.source().query(QueryBuilders.matchAllQuery());
        //发送请求
        SearchResponse search = restHighLevelClient.search(request, RequestOptions.DEFAULT);

        //解析响应
        SearchHits searchHits = search.getHits();
        //获取总条数
        long value = searchHits.getTotalHits().value;
        System.out.println("共搜到"+value+"条数据");
        SearchHit[] hits = searchHits.getHits();
        for (SearchHit hit : hits) {
            String json = hit.getSourceAsString();
            HotelDoc hotelDoc = JSON.parseObject(json, HotelDoc.class);
            System.out.println("hotelDoc = " + hotelDoc);
        }

        System.out.println(search);
    }
```

![image-20230728003208697](https://cdn.jsdelivr.net/gh/yzk656/image/202307280032858.png)

![image-20230728003215940](https://cdn.jsdelivr.net/gh/yzk656/image/202307280032042.png)

![image-20230728003253986](https://cdn.jsdelivr.net/gh/yzk656/image/202307280032090.png)

![image-20230728003546890](https://cdn.jsdelivr.net/gh/yzk656/image/202307280035970.png)

ctrl+alt+m:抽取方法

![image-20230728004337727](https://cdn.jsdelivr.net/gh/yzk656/image/202307280043799.png)

```java
    @Test
    void testBool() throws IOException {
        //准备request
        SearchRequest request = new SearchRequest("hotel");

        BoolQueryBuilder boolQueryBuilder = QueryBuilders.boolQuery();
        boolQueryBuilder.must(QueryBuilders.termQuery("city","杭州"));
        boolQueryBuilder.filter(QueryBuilders.rangeQuery("price").lte(250));

        //准备DSL
        request.source()
                .query(boolQueryBuilder);
        //发送请求
        SearchResponse search = restHighLevelClient.search(request, RequestOptions.DEFAULT);

        handleResponse(search);
    }
```

![image-20230728005425085](https://cdn.jsdelivr.net/gh/yzk656/image/202307280054165.png)

![image-20230728082034452](https://cdn.jsdelivr.net/gh/yzk656/image/202307280820641.png)

```java
    @Test
    void testPageAndSort() throws IOException {
        int page=1,size=5;

        //准备request
        SearchRequest request = new SearchRequest("hotel");
        //准备DSL
        request.source().query(QueryBuilders.matchAllQuery());
        request.source().sort("price", SortOrder.ASC);
        request.source().from((page-1)*size).size(5);
        //发送请求
        SearchResponse search = restHighLevelClient.search(request, RequestOptions.DEFAULT);

        handleResponse(search);
    }
```

![image-20230728083611299](https://cdn.jsdelivr.net/gh/yzk656/image/202307280836409.png)

![image-20230728084041663](https://cdn.jsdelivr.net/gh/yzk656/image/202307280840800.png)

```java
    @Test
    void testHighlight() throws IOException {
        //准备request
        SearchRequest request = new SearchRequest("hotel");
        //准备DSL
        request.source().query(QueryBuilders.matchQuery("name","如家"));
        request.source().highlighter(new HighlightBuilder().field("name").requireFieldMatch(false));
        //发送请求
        SearchResponse search = restHighLevelClient.search(request, RequestOptions.DEFAULT);

        handleResponse(search);
    }

    private static void handleResponse(SearchResponse search) {
        //解析响应
        SearchHits searchHits = search.getHits();
        //获取总条数
        long value = searchHits.getTotalHits().value;
        System.out.println("共搜到"+value+"条数据");
        SearchHit[] hits = searchHits.getHits();
        for (SearchHit hit : hits) {
            String json = hit.getSourceAsString();
            HotelDoc hotelDoc = JSON.parseObject(json, HotelDoc.class);

            Map<String, HighlightField> highlightFields = hit.getHighlightFields();
            if(!CollectionUtils.isEmpty(highlightFields)){
                HighlightField name = highlightFields.get("name");
                if(name!=null){
                    String string = name.getFragments()[0].string();
                    hotelDoc.setName(string);
                }
            }

            System.out.println("hotelDoc = " + hotelDoc);
        }
    }
```

![image-20230728085029236](https://cdn.jsdelivr.net/gh/yzk656/image/202307280850305.png)

## 黑马旅游案例

![image-20230728085442294](https://cdn.jsdelivr.net/gh/yzk656/image/202307280854405.png)

![image-20230728085459229](https://cdn.jsdelivr.net/gh/yzk656/image/202307280854307.png)

![image-20230728085627517](https://cdn.jsdelivr.net/gh/yzk656/image/202307280856587.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307281101387.png)

![image-20230728110123213](https://cdn.jsdelivr.net/gh/yzk656/image/202307281101299.png)

![image-20230728110308271](https://cdn.jsdelivr.net/gh/yzk656/image/202307281103358.png)

==elasticsearch中的Booleanquery的作用==

在 Elasticsearch 中，`BooleanQuery` 是一种复合查询（Compound Query），用于将多个不同的查询条件组合在一起，并通过逻辑运算符（AND、OR、NOT）来实现更复杂的查询需求。它可以将多个查询条件组合成一个逻辑表达式，从而对文档进行更精确的匹配和过滤。

`BooleanQuery` 可以包含以下三种类型的子查询：

1. **Must（AND）查询**：这是一个必须匹配的查询，所有的子查询都必须匹配才能使得整个查询结果为真。类似于逻辑运算中的 "AND"。

2. **Should（OR）查询**：这是一个可选匹配的查询，至少有一个子查询匹配成功，整个查询结果就为真。类似于逻辑运算中的 "OR"。

3. **Must Not（NOT）查询**：这是一个必须不匹配的查询，所有的子查询都不能匹配才能使得整个查询结果为真。类似于逻辑运算中的 "NOT"。

通过组合这些子查询，可以实现复杂的查询需求。例如，可以通过 `BooleanQuery` 将文档的某个字段满足一个条件而且不满足另一个条件的结果筛选出来，或者同时匹配多个字段的值等等。

以下是一个简单的示例，演示如何使用 `BooleanQuery` 在 Elasticsearch 中进行复合查询：

假设我们有一个索引 `products`，包含了产品的信息，其中包含了 `name` 和 `category` 两个字段。

```json
PUT /products
{
  "mappings": {
    "properties": {
      "name": {
        "type": "text"
      },
      "category": {
        "type": "keyword"
      }
    }
  }
}
```

现在，我们想要查询名称包含 "laptop" 并且类别是 "Electronics" 的产品，可以使用 `BooleanQuery` 来实现：

```json
POST /products/_search
{
  "query": {
    "bool": {
      "must": [
        { "match": { "name": "laptop" } },
        { "term": { "category": "Electronics" } }
      ]
    }
  }
}
```

上述查询会返回符合条件的产品文档。

总结一下，`BooleanQuery` 是 Elasticsearch 中用于组合多个查询条件的复合查询类型，通过逻辑运算符来实现更精确的文档匹配和过滤。

![image-20230728124235414](https://cdn.jsdelivr.net/gh/yzk656/image/202307281242525.png)

![image-20230728124452692](https://cdn.jsdelivr.net/gh/yzk656/image/202307281244794.png)

![image-20230728131306235](https://cdn.jsdelivr.net/gh/yzk656/image/202307281313351.png)

![image-20230728133153833](https://cdn.jsdelivr.net/gh/yzk656/image/202307281331935.png)

# RabbitMQ快速实战

## MQ的劣势与优势

1. 降低耦合
2. 削峰填谷
3. 消息分发



1. 系统复杂度提高
2. 系统可用性降低
3. 一致性问题

## MQ工作流程

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307301436866.png)

# 第七天

## 数据聚合

![image-20230820220713061](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230820220713061.png)

![image-20230820221210085](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230820221210085.png)

![image-20230917224407909](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309172244096.png)

## DSL实现Bucket聚合

![image-20230917224556436](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309172245499.png)

![image-20230917225241860](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309172252925.png)

![image-20230917225423852](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309172254912.png)

![image-20230917225738152](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309172257215.png)

## DSL实现Metrics聚合

![image-20230917225955147](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309172259207.png)

## RestClient实现聚合

![](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309172319290.png)

![image-20230917235021066](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309172350310.png)

![image-20230917235144349](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309172351450.png)

## 多条件聚合

![image-20230918073433754](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309180734843.png)

![image-20230918213804859](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309182138977.png)

## 自动补全

![image-20230918222731184](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309182227259.png)

```java
POST _analyze
{
  "text": ["如家酒店还不错"]
  , "analyzer": "pinyin"
}
```

## 自定义分词器

![](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309182327952.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309182329559.png)

![image-20230918235023005](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309182350076.png)

![image-20230918235448811](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309182354883.png)

## DSL实现自动补全查询

![](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309190749070.png)

![image-20230919075044381](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309190750481.png)

```js
# 自动补全的索引库
PUT test2
{
  "mappings": {
    "properties": {
      "title":{
        "type": "completion"
      }
    }
  }
}
# 示例数据
POST test2/_doc
{
  "title": ["Sony", "WH-1000XM3"]
}
POST test2/_doc
{
  "title": ["SK-II", "PITERA"]
}
POST test2/_doc
{
  "title": ["Nintendo", "switch"]
}


# 自动补全查询
GET /test2/_search
{
  "suggest": {
    "titleSuggest": {
      "text": "w",
      "completion": {
        "field": "title",
        "skip_duplicates":true,
        "size":10
      }
    }
  }
}
```

![image-20230919080208768](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309190802829.png)

# Sentinel

![image-20230919224732761](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192247860.png)

![image-20230919224952995](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192249077.png)

![image-20230919232212502](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192322609.png)

![image-20230919232905366](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192329435.png)

![image-20230919233536077](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192335175.png)

![image-20230919233843122](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192338245.png)

![image-20230919233946490](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192339596.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192343303.png)

![image-20230919234331015](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192343113.png)

![image-20230919235302996](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309192353098.png)