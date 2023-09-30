## XML概述

![image-20230212121241052](https://cdn.jsdelivr.net/gh/yzk656/image/202302121212121.png)

![image-20230212121449848](https://cdn.jsdelivr.net/gh/yzk656/image/202302121214902.png)

## XML快速入门

```xml
<?xml version='1.0' encoding='UTF-8'?>

<users>
	<user id='1'>
		<name>张三</name>
		<age>11</age>
		<gender>mal</gender>
	</user>
	
	<user id='2'>
		<name>lisi</name>
		<age>12</age>
		<gender>femal</gender>
	</user>
</users>
```

![image-20230212122512906](https://cdn.jsdelivr.net/gh/yzk656/image/202302121225945.png)

## XML组成部分

![image-20230212205550411](https://cdn.jsdelivr.net/gh/yzk656/image/202302122055504.png)

![image-20230212205908281](https://cdn.jsdelivr.net/gh/yzk656/image/202302122059329.png)

## XML约束概述

![image-20230212213015991](https://cdn.jsdelivr.net/gh/yzk656/image/202302122130050.png)

![image-20230212213602960](https://cdn.jsdelivr.net/gh/yzk656/image/202302122136005.png)

dtd外部引入

![image-20230212213827327](https://cdn.jsdelivr.net/gh/yzk656/image/202302122138367.png)

![image-20230212213840166](https://cdn.jsdelivr.net/gh/yzk656/image/202302122138210.png)

dtd内部引入

![image-20230212213854040](https://cdn.jsdelivr.net/gh/yzk656/image/202302122138097.png)

schema外部引入

![image-20230212214533976](https://cdn.jsdelivr.net/gh/yzk656/image/202302122145039.png)

![image-20230212221225757](https://cdn.jsdelivr.net/gh/yzk656/image/202302122212807.png)

![image-20230212221545957](https://cdn.jsdelivr.net/gh/yzk656/image/202302122215061.png)

## XML解析

![image-20230212223055058](https://cdn.jsdelivr.net/gh/yzk656/image/202302122230116.png)

## XML常见解析器

![image-20230212223435347](https://cdn.jsdelivr.net/gh/yzk656/image/202302122234394.png)

## jsoup快速入门

![image-20230212224604896](https://cdn.jsdelivr.net/gh/yzk656/image/202302122246930.png)

```java
package com.yzk.xml.jsoup;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import java.io.File;
import java.io.IOException;

/**
 * @ClassName: Jsoup_demo1
 * @Description: Jsoup快速入门
 * @Author: 杨振坤
 * @date: 2023/2/12 22:49
 */
public class Jsoup_demo1 {
    public static void main(String[] args) throws IOException {
        /*获取Document对象，根据xml文档获取*/
        /*通过类加载器获取xml的地址*/
        String path = Jsoup_demo1.class.getClassLoader().getResource("student.xml").getPath();
        /*解析xml文档，加载文档进内存，获取dom树*/
        Document document = Jsoup.parse(new File(path), "UTF-8");
        /*获取元素对象*/
        Elements elements = document.getElementsByTag("name");

        System.out.println(elements.size());

        /*获取第一个name的element对象*/
        Element element=elements.get(0);
        /*获取数据*/
        String name=element.text();
        System.out.println(name);
    }
}
```

```xml
<?xml version="1.0" encoding="UTF-8" ?>

<students>
    <student number="heima_0001">
        <name>tom</name>
        <age>18</age>
        <sex>male</sex>
    </student>
    <student number="heima_0002">
        <name>jack</name>
        <age>18</age>
        <sex>female</sex>
    </student>
</students>
```

## Jsoup对象

![image-20230213003629520](https://cdn.jsdelivr.net/gh/yzk656/image/202302130036573.png)

## Document对象

![image-20230213111037810](https://cdn.jsdelivr.net/gh/yzk656/image/202302131110859.png)

```java
package com.yzk.xml.jsoup;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import java.io.File;
import java.io.IOException;

/**
 * @ClassName: Jsoup_demo2
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/13 0:23
 */
public class Jsoup_demo3 {
    public static void main(String[] args) throws IOException {
        String path= Jsoup_demo3.class.getClassLoader().getResource("student.xml").getPath();
        Document document = Jsoup.parse(new File(path), "UTF-8");

        /*1. 通过标签名获取*/
        Elements elements=document.getElementsByTag("student");
        System.out.println(elements);

        System.out.println("--------------------");

        /*2. 通过属性名获取*/
        Elements elements1=document.getElementsByAttribute("id");
        System.out.println(elements1);

        System.out.println("--------------------");

        /*3. 通过属性值获取*/
        Elements elements2=document.getElementsByAttributeValue("number","heima_0001");
        System.out.println(elements2);

        System.out.println("--------------------");

        /*4. 通过id的来获取*/
        Element element=document.getElementById("id_test");
        System.out.println(element);
    }
}
```

```xml
<?xml version="1.0" encoding="UTF-8" ?>

<students>
    <student number="heima_0001">
        <name id="id_test">tom</name>
        <age>18</age>
        <sex>male</sex>
    </student>
    <student number="heima_0002">
        <name>jack</name>
        <age>18</age>
        <sex>female</sex>
    </student>
</students>
```

## Element对象

![image-20230213112236707](https://cdn.jsdelivr.net/gh/yzk656/image/202302131122762.png)

```java
package com.yzk.xml.jsoup;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import java.io.File;
import java.io.IOException;

/**
 * @ClassName: Jsoup_demo2
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/13 0:23
 */
public class Jsoup_demo4 {
    public static void main(String[] args) throws IOException {
        String path= Jsoup_demo4.class.getClassLoader().getResource("student.xml").getPath();
        Document document = Jsoup.parse(new File(path), "UTF-8");

        /*1. 通过Document对象获取name标签，获取所有的name标签，可以获取两个*/
        Elements elements=document.getElementsByTag("name");
        System.out.println(elements.size());

        System.out.println("--------------------");

        /*2.通过Element对象获取子标签对象*/
        Element element_student=document.getElementsByTag("student").get(0);
        Elements ele_name=element_student.getElementsByTag("name");
        System.out.println(ele_name.size());

        System.out.println("--------------------");

        /*3. 获取student对象的属性值*/
        String number=element_student.attr("number");
        System.out.println(number);

        System.out.println("--------------------");

        /*4.获取文本内容*/
        String text=ele_name.text();
        String html=ele_name.html();
        /*获取的是纯文本内容*/
        System.out.println(text);
        /*获取的是可以包含html标签的内容*/
        System.out.println(html);
    }
}
```

```xml
<?xml version="1.0" encoding="UTF-8" ?>

<students>
    <student number="heima_0001">
        <name id="id_test">
            <xing>张</xing>
            <ming>三</ming>
        </name>
        <age>18</age>
        <sex>male</sex>
    </student>
    <student number="heima_0002">
        <name>jack</name>
        <age>18</age>
        <sex>female</sex>
    </student>
</students>
```

![image-20230213114222675](https://cdn.jsdelivr.net/gh/yzk656/image/202302131142710.png)

## 查询方式-根据选择器查询

![image-20230213120925930](https://cdn.jsdelivr.net/gh/yzk656/image/202302131209959.png)

![image-20230213131040479](https://cdn.jsdelivr.net/gh/yzk656/image/202302131310527.png)

```java
package com.yzk.xml.jsoup;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import java.io.File;
import java.io.IOException;

/**
 * @ClassName: Jsoup_demo2
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/13 0:23
 */
public class Jsoup_demo5 {
    public static void main(String[] args) throws IOException {
        String path= Jsoup_demo5.class.getClassLoader().getResource("student.xml").getPath();
        Document document = Jsoup.parse(new File(path), "UTF-8");

        /*1. 通过标签选择器查询*/
        Elements elements=document.select("name");
        System.out.println(elements);

        System.out.println("--------------------");

        /*2. 通过id选择器查询*/
        Elements elements1=document.select("#id_test");
        System.out.println(elements1);

        System.out.println("--------------------");

        /*3. 获取student标签并且属性名为heima_0001*/
        /*注意：这里的双引号要加上转义符号，使用单引号不行*/
        Elements elements2=document.select("student[number=\"heima_0001\"]");
        System.out.println(elements2);

        System.out.println("--------------------");

        /*3. 获取student标签并且属性名为heima_0001下的age子标签*/
        /*注意：这里的双引号要加上转义符号，使用单引号不行*/
        Elements elements3=document.select("student[number=\"heima_0001\"]>age");
        System.out.println(elements3);
    }
}
```

## 查询方式-XPath查询

![image-20230213131940152](https://cdn.jsdelivr.net/gh/yzk656/image/202302131319197.png)

![image-20230213132436979](https://cdn.jsdelivr.net/gh/yzk656/image/202302131324038.png)

![image-20230213132735407](https://cdn.jsdelivr.net/gh/yzk656/image/202302131327447.png)

```java
package com.yzk.xml.jsoup;

import cn.wanghaomiao.xpath.exception.XpathSyntaxErrorException;
import cn.wanghaomiao.xpath.model.JXDocument;
import cn.wanghaomiao.xpath.model.JXNode;
import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.select.Elements;

import java.io.File;
import java.io.IOException;
import java.util.List;

/**
 * @ClassName: Jsoup_demo2
 * @Description: TODO
 * @Author: 杨振坤
 * @date: 2023/2/13 0:23
 */
public class Jsoup_demo6 {
    public static void main(String[] args) throws IOException, XpathSyntaxErrorException {
        String path= Jsoup_demo6.class.getClassLoader().getResource("student.xml").getPath();
        Document document = Jsoup.parse(new File(path), "UTF-8");

        /*1. 根据document对象，创建JXDocument对象*/
        JXDocument jxDocument=new JXDocument(document);

        /*2. 结合XPath语法查询*/
        /*查询所有的student标签：// */
        List<JXNode> jxNodes = jxDocument.selN("//student");
        for(JXNode jxNode:jxNodes){
            System.out.println(jxNode);
        }

        System.out.println("--------------------");

        /*查询所有student标签下的name标签*/
        List<JXNode> jxNodes1=jxDocument.selN("//student/name");
        for (JXNode jxNode:jxNodes1){
            System.out.println(jxNode);
        }

        System.out.println("--------------------");

        /*查询student标签下带有id属性的name标签*/
        List<JXNode> jxNodes2=jxDocument.selN("//student/name[@id]");
        for (JXNode jxNode:jxNodes2){
            System.out.println(jxNode);
        }

        System.out.println("--------------------");

        /*查询student标签下带有id属性的name标签,并且id属性值为id_test*/
        List<JXNode> jxNodes3=jxDocument.selN("//student/name[@id='id_test']");
        for (JXNode jxNode:jxNodes3){
            System.out.println(jxNode);
        }

    }
}
```

