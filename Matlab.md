# Matlab

> 总结：

输出矩阵最大值

```
a=[1 2;3 4]
disp(max(a(:)))
```



如果计算没有赋值的变量，结果默认为-1

```
x=i*j
disp(x)
```



对于case结果表为switch表达式的取值，当取值有多个时，用单元数据表示



Y = fix( X ) 将 X 的每个元素==朝零方向==四舍五入为最近的整数



a=a(:)：会将其变成列向量



求矩阵的迹

sum(eig(A))

trace(A)

sum(diag(A))



linspace默认点数为100



format命令会影响数据输出格式，但是不会影响数据的计算和存储



在命令行窗口，不能直接运行函数文件，但是可以通过函数调用的方式来调用他



标准函数名以及命令名必须用小写字母



保存随机数生成器的当前状态并创建一个由随机数组成的 1×5 向量。

```
s = rng;
r = randn(1,5)
```



a=std（x），值越大，说明偏离平均值的程度就越大



显示网格命令：grid on





## 第一章

![image-20220825103603339](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053413.png)

![image-20220830140237153](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053502.png)

![image-20220830140318899](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053989.png)

![image-20220830140621890](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053061.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053070.png)

![image-20220830141426331](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053478.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053773.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053254.png)

![image-20220830142814397](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053245.png)

logspace是一个MATLAB类型的函数，相关函数是[linspace](https://baike.baidu.com/item/linspace/1773011?fromModule=lemma_inlink)。其功能是行向量，生成从10的a次方到10的b次方之间按对数等分的n个元素的行向量。

![image-20220830144151042](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053055.png)

![image-20220830164143287](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220830164143287.png)

![image-20220830144533068](https://cdn.jsdelivr.net/gh/yzk656/image/202212242053927.png)

![image-20220830145916910](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054351.png)

单下标访问时：直接按照序号，先列后行

双下标访问时：访问二维数组时可以可以使用（【】，【】），如果 `,`没有左边是全部的时候需要使用`:`,而不能省略`:`

![image-20220830164332570](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054775.png)

a_2(2,3):访问2行3列的元素

![image-20220830165605597](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054223.png)

如果只是输入两个下标，就需要使用【】了，如果2:4的话，则就不需要使用【】

![image-20220830171111398](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054590.png)

![image-20220901100737719](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054487.png)

![image-20220901101017301](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054951.png)

![image-20220901104350926](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054670.png)

![image-20220904141205224](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054807.png)

![image-20220904141314085](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054526.png)

![image-20220904141434956](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054903.png)

![image-20220904142947741](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054543.png)

![image-20220904143600366](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054032.png)

![image-20220906141349802](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054097.png)

字符串和数字的区别：前面是否有空格

![image-20220906141608157](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054464.png)

![image-20220906141739590](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054511.png)

![image-20220906143441308](https://cdn.jsdelivr.net/gh/yzk656/image/202212242054573.png)

![image-20220906144953115](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055952.png)

多elseif

![image-20220906150250940](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055440.png)

![image-20220908095154768](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055576.png)

disp(3|4)：是为真：也就是1

num2cell 函数**转换具有任意数据类型（甚至是非数值类型）的数组**。 C = num2cell (A,dim) 将 A 的内容划分成 C 中单独的元胞，其中 dim 指定每个元胞包含 A 的哪个维度。

![image-20220908101129407](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055976.png)

![image-20220908103635946](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055735.png)

num2cell在matlab中的意思？

将数组变量转换成元胞变量

## 绘图

![image-20220919151240676](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055272.png)

![image-20220919151433180](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055339.png)

向量与向量相乘需要使用点乘

![image-20220919152451122](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055408.png)

![image-20220919153535943](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055905.png)

![image-20220919153739022](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055137.png)

![image-20220919155140030](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055546.png)

![image-20220919160127142](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055320.png)

![image-20220919160517543](https://cdn.jsdelivr.net/gh/yzk656/image/202212242055132.png)

![image-20220919160535035](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056322.png)

![image-20220919160918104](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056162.png)

![image-20220919160926553](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056458.png)

![image-20220920140530989](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056673.png)

![image-20220920142804996](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056960.png)

![image-20220920143718374](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056305.png)

![image-20220920144213855](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056656.png)

![image-20220920144340744](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056733.png)

![image-20220920145226487](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056538.png)

![image-20220926152028316](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056833.png)

![image-20220926152041207](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056632.png)

![image-20220926153040330](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056211.png)

![image-20220926155621525](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056890.png)

![image-20220926160141738](https://cdn.jsdelivr.net/gh/yzk656/image/202212242056805.png)

![image-20221003151218580](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057196.png)

![image-20221003151521536](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057844.png)

![image-20221003151712080](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057966.png)

![image-20221003151728916](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057532.png)

![image-20221003152051838](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057071.png)

![image-20221003152524280](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057211.png)

![image-20221003152538677](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057053.png)

![image-20221003152650035](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057350.png)

![image-20221003152727531](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057781.png)

![image-20221003152839447](https://cdn.jsdelivr.net/gh/yzk656/image/202212242057102.png)

![image-20221003153232648](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058228.png)

![image-20221003154539766](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058361.png)

![image-20221003160321031](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058317.png)

![image-20221003160552173](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058265.png)

![image-20221003160611504](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058688.png)

![image-20221004140149376](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058096.png)

![image-20221004140703169](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058790.png)

![image-20221004140756538](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058690.png)

![image-20221004141631289](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058031.png)

![image-20221004142110200](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058414.png)

![image-20221004142831970](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058776.png)

![image-20221004143110043](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058668.png)

![image-20221004143351223](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058289.png)

求范数

norm

向量范数和矩阵范数





![image-20221010152455339](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058745.png)

![image-20221010152707652](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058163.png)

![image-20221010152748042](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058061.png)

![image-20221010152905419](https://cdn.jsdelivr.net/gh/yzk656/image/202212242058951.png)

频率就是1个频率内有多少个波形
