#  异常类

## 练习1

 ```java
         int num1=10;
         int num2=0;
         //int num3=num1/num2;
         //当程序走到除0时，程序会抛出异常，ArithmeticException
         //当抛出异常后，程序就退出，不再继续往下走了
 
         //如果程序员认为一段代码可能出现问题，可以使用try-catch异常处理机制来解决，从而保证程序能正常运行
         //如果进行异常处理，那么即使出现了异常，程序也可以继续执行
         try{
             int num3=num1/num2;
         }catch (Exception e){
             //e.printStackTrace();//java.lang.ArithmeticException: / by zero
             
             //如果不想被抛出异常，而是输出出来异常，可以调用Exception类的getMessage()，通过输出语句
             System.out.println("异常原因："+e.getMessage());/// 异常原因：/ by zero
         }
         System.out.println("程序继续运行");
 ```



## 知识点1

- ![](https://gitee.com/demon_night/images/raw/master/imgs/202201291843259.png)
- 虚线：类实现了这个接口。蓝色实线：代表继承了该类
- Error：致命异常，无法通过异常处理机制处理掉。RuntimeException：运行时异常，可以通过异常处理机制处理掉【主要包括5种：NullPointerException、AirthmeticException、ArrayIndexOutOfBoundsException、ClassCastException、NumberFormatexception】
- FileNotFoundException：编译异常、ClassNotFoundException属于编译异常
- 运行时异常，是编译器检测不出来的
- 在运行javac时【将其转换成字节码文件】时发生的异常是编译异常。在运行java时【在内存中加载、运行类】时出现的异常叫运行异常
- 对于运行时异常，可以不做处理，因为这类异常很普遍，若全处理可能会对程序的可读性和运行效率产生影响
- 编译异常是编译器要求必须处置的异常
- ![image-20220112065618753](https://gitee.com/demon_night/images/raw/master/imgs/202201291843134.png)

## 五大运行时异常

```java
package Exception;

public class Exception_test2 {
    public static void main(String[] args) {
        //空指针异常,对象为空时，对对象进行操作就会抛出空指针异常
        String s1=null;
        //System.out.println(s1.length());//java.lang.NullPointerException

        //数学运算类异常：出现异常运算条件时
        int num=10;
        //System.out.println(num/0);//java.lang.ArithmeticException

        //数组下标越界异常
        int[] array=new int[]{1,2,3};
        //System.out.println(array[3]);//  java.lang.ArrayIndexOutOfBoundsException

        //类型转换异常
        A b=new B();//向上转型
        B b1=(B) b;//向下转型
        //C c=(C) b;//c、b都是a的并列子类，不能相互转换【java.lang.ClassCastException】

        //数值转换异常
        String s2="yzk";
        //System.out.println(Integer.parseInt(s2));//java.lang.NumberFormatException
    }
}
class A{}
class B extends A{}
class C extends A{} 
```

## 编译异常

> 常见的编译异常

- SQLException：操作数据库时，查表发生的异常
- IOException：操作文件时发生的异常
- FileException：当操作一个不存在的文件时，发生的异常
- ClassNotFoundException：加载类，而该类不存在时发生的异常
- EOFException：操作文件到文件末尾，发生异常
- IIIegalArgumentexception：参数异常

## 异常处理1

- try中放可能出现错误的代码块，catch用来将捕获来的异常封装成类对象，传递给catch，如果没有发生异常，就不执行catch代码块，对于finally，不管try代码块是否有异常发生，始终要执行，所以通常将释放资源的代码finally
- `try-finally:相当于没有捕获异常，该崩还是崩，但是会执行finally`  

- ![](https://gitee.com/demon_night/images/raw/master/imgs/202201291843831.png)

## 异常处理2

- 如果你没有采用try-catch方法，就默认采用throws方法，由jvm机直接输错错误信息，直接终止程序
- ![](https://gitee.com/demon_night/images/raw/master/imgs/202201291844808.png)

## 练习2

```java
package Exception;

public class Exception_test3 {
    public static void main(String[] args) {
        try {
            String s1="yzk";
            System.out.println(Integer.parseInt(s1));
            
            //如果异常发生就不会执行后面的代码块，后面代码就算有异常也不会被抛出
            System.out.println("代码执行了吗");//注：该行代码没有执行
            
        } catch (NumberFormatException e) {
            
            System.out.println("异常信息："+e.getMessage());//异常信息：For input string: "yzk"
            
        }finally{
            System.out.println("finally块被执行");//finally块被执行
        }
        System.out.println("程序继续执行");//程序继续执行
    }
}

```

> `对于多catch块的使用是，不确定是那种异常，因此通过多种异常类进行捕获`

```java
package Exception;

public class Exception_test4 {
    public static void main(String[] args) {
        //对于多个异常都想将其抛出来，可以使用多个try-catch进行多个异常捕获,注意是多个”try-catch“,因为： //如果异常发生就不会执行后面的代码块，后面代码就算有异常也不会被抛出
        //要求子类异常写在前面，父类异常写在后面
        try{
            int n1=10;
            System.out.println(n1/0);
        }catch (ArithmeticException e){
            
            System.out.println("算数异常"+e.getMessage());//算数异常/ by zero
        }

        try {
            person p=new person();
            p=null;
            System.out.println(p.getName());
        }
        catch(NullPointerException e){
            
            System.out.println("空指针异常"+e.getMessage());//空指针异常Cannot invoke "Exception.person.getName()" because "p" is null
            
        }catch(Exception e){
            System.out.println(e.getMessage());
        }finally {

        }
    }
}
class person{
    private String name;

    public String getName() {
        return name;
    }
}

```

## try-catch-finally小结

- 如果没有出现异常，则执行try块中所有的语句，不执行catch块中的语句，如果有finally，最后还要执行finally里面的语句
- 如果出现异常，则try块中异常发生后，try块中剩下的语句不再执行，将执行catch块中的语句，如果有finally，最后还要执行finally中的语句
- ![image-20220112210050467](https://gitee.com/demon_night/images/raw/master/imgs/202201291844264.png)

## 练习3

> 利用异常机制，如果不是整数就继续输入，直到输入一个整数

```java
package Exception;

import java.util.Scanner;

public class Exception_test5 {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int num;
        while(true){
            String s=sc.next();
            try{
                num=Integer.parseInt(s);
                System.out.println("输入正确");
                break;
            }catch (Exception e){
                System.out.println("输入错误，请重新输入");
            }
        }
        System.out.println(num);
    }
}
```

## throws异常处理1

```java
package Throws;

import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class throws_test1 {
    public static void main(String[] args) {

    }
    public void f2() throws FileNotFoundException,NullPointerException {
        //可以使用throws，抛出异常，让调用f2方法的调用者方法处理
        //throws后面可以抛出多个异常
        FileInputStream f=new FileInputStream("D://aa.txt");//创建1个流对象
    }
}

```

## throws异常处理2

- 对于编译异常，程序中必须处理

- 对于运行异常，程序中如果没有处理，默认就是throws的方式处理，如果都没有人处理，就会交给JVM机处理，然后中断程序，爆出红字

- 子类重写父类方法时，对抛出异常的规定是子类重写的方法，所抛出的异常类型要么和父类抛出的异常一致，要么为父类抛出的异常类型的子类型

- ```java
  class father{
      public void method() throws RuntimeException{
          
      } 
  }
  class son extends father{
      public void method() throws NullPointerException {//子类不能是Exception
          
      }
  }
  ```

- `对于1个异常【编译异常】，可以直接try-catch直接处理掉，也可以throws扔给调用异常方法者`

- `而对于运行异常，就算调用者不显式处理，也会有默认throws处理`

## 自定义异常类【通过throw扔出异常】

- 自定义异常类名继承Exception、RuntimeException
- 如果继承Exception，属于编译异常
- 如果继承RuntimeException,属于运行异常(一般来说继承RuntimeException)
- 为什么继承RuntimeException:可以使用默认的处理机制，而不是弄成编译异常，还需要挨个throws

## 练习1

```java
package Exception;

public class Exception_test6 {
    public static void main(String[] args) {
        int age=180;
        //要求范围在18~120之间，否则抛出一个自定义异常类
        if(!(age<=120&&age>=18)){
            //通过构造器，设置信息
            throw new ageException("年龄应该在18~120之间");
        }
        System.out.println("年龄范围正确");
    }
}
//自定义1个异常类
class ageException extends RuntimeException{
    public  ageException(String message){
        super(message);
    }
}
```

 ![image-20220112222854080](https://gitee.com/demon_night/images/raw/master/imgs/202201291844257.png)

## throw与throws的区别

- throws：异常处理的一种方式，位于方法声明处，后面跟的是异常类型
- throw：手动生成异常对象的关键字，位于方法体中，后面跟的是异常对象

## 练习2

> 只有交给了JVM机处理才会结束程序不执行后面的
>
> throw new RuntimeException能够把异常信息改为”制造异常“，然后getMessage方法能够在输出语句中输出错误信息

![image-20220112224733282](https://gitee.com/demon_night/images/raw/master/imgs/202201291844448.png)

# 常用类

## Integer类

```java
Integer a=1;//Integer.valueOf(1);自动装箱功能
Integer b=1;

//true
Integer e=127;
int i=127;
System.out.println(e==i);
```

1. 对于值在-128~127之间的，如果两个数值相等，则两个对象就相等，如果不在这个范围就不是相同的对象
2. 只要有基本数据类型，判断的是值是否相等

### 练习1

```java
public class Integer_test {
    public static void main(String[] args){
        //如果i在-128`127之间就从缓存数组中直接返回
        Integer a=1;
        Integer b=1;
        Integer c=128;
        Integer d=128;
        System.out.println(a==b);
        System.out.println(c==d);
    }
}
```

![image-20220109002745473](https://gitee.com/demon_night/images/raw/master/imgs/202201291851033.png)

## 练习2

> 通过命令行输入参数，判断是不是整数、参数个数、算数运算是否有异常发生

```java
package Exception;

public class ExmDef_test {
    public static void main(String[] args) {
        try {
            if(args.length!=2){
                throw new ArrayIndexOutOfBoundsException("参数不正确");
            }
            int temp1=Integer.parseInt(args[0]);
            int temp2=Integer.parseInt(args[1]);
            double temp3=cal(temp1,temp2);
            System.out.println(temp3);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println(e.getMessage());
        }catch (NumberFormatException e){
            System.out.println("参数格式不正确");
        }catch (ArithmeticException e){
            System.out.println("出现了除0异常");
        }
    }
    private static double cal(int n1,int n2){
            return n1/n2;
    }
}
```

1. 对于自己想要输出的异常信息有两种方式：1.直接打印输出。2.把异常信息放进异常对象里，扔给异常类型，然后通过getMessage打印输出
2. 如果长度不够直接爆出异常，如果长度够，但是参数类型不对仍然爆出异常，如果两者都对，出现除0爆出除0异常
3. 当出现除0时会有异常产生，cal会把异常扔给调用者，然而调用者被try-catch包括着，因此就可以捕获异常，解决异常【输出异常信息】
4. 虽然不能输出全部异常信息，但是想想就知道，只要有一处异常，就不应该继续往下走了，所以用`1`try-多catch块最好用

## 练习3

![](https://gitee.com/demon_night/images/raw/master/imgs/202201291851168.png)

# 包装类

> ### 使用字符串格式化实现四舍五入(支持float和double类型)

```java
  		double data = 3.02;
        //利用字符串格式化的方式实现四舍五入,保留1位小数
        String result = String.format("%.1f",data);
        //1代表小数点后面的位数, 不足补0。f代表数据是浮点类型。保留2位小数就是“%.2f”，依此累推。
        System.out.println(result);//输出3.0

```

## 包装类与基本数据类型的转换

- 基本数据类型-》包装类型：装箱，反之为拆箱

- 自动装箱调用的是valueOf方法，如Integer.valueOf()

- Character类的isDigit()可以判断该字符是否是数字 

- `String类可以添加字符成字符串`：

- ```java
  s1=s1+'l';
  System.out.println(s1);//hspl
  ```

```java
        //手动装箱
        int n1=100;
        Integer i1=new Integer(n1);
        Integer i2=Integer.valueOf(n1);

        //手动拆箱
        int i3=i1.intValue();

        //JDK5以后就可以实现自动装箱、拆箱功能
        int n2=200;
        Integer i4=n2;
        int n3=i4; 
```

- 三木运算符

```java
        //三目运算是一个整体
        Object a=true? new Integer(1):new Double(2.0);
        System.out.println(a);//1.0
```

![image-20220109002819666](https://gitee.com/demon_night/images/raw/master/imgs/202201291851879.png)

## Integer、String类相互转换

```java
//包装类：Integer-》String
Integer i=100;
//方式1
String str1=i+"";
//方式2
String str2=i.toString();
//方式3
String str3=String.valueOf(i);


//String->Integer
String str3="12345";
Integer i5=Integer.parseInt(str3);//自动装箱，因为Integer.parseInt方法返回值是int类型
Integer i6=new Integer(str3);
```

## Integer、Character类的常用方法

```java
//Integer的基本方法
System.out.println(Integer.MAX_VALUE);//10位的
System.out.println(Integer.MIN_VALUE);

System.out.println(Character.isDigit('a'));//判断是不是数字
System.out.println(Character.isLetter('a'));//判断是不是字母
System.out.println(Character.isUpperCase('a'));//判断是不是大写字母
System.out.println(Character.isLowerCase('a'));//判断是不是小写字母

System.out.println(Character.isWhitespace('a'));//判断是不是空格
System.out.println(Character.toUpperCase('a'));//转成大写
System.out.println(Character.toLowerCase('A'));//转成小写
```

# String类

- `String也能通过Float的valueOf将其转换成float类型`
- `String的format方法的返回值是double类型，float类型能保留小数点后六位`
- System.out.printf("%.5f",res);相当于字符串的format方法

1. String对象用于保存字符串，也就是一组字符序列
2. 字符串常量对象是用双引号括起来的字符序列
3. 字符串的字符采用unicode字符编码，一个字符（不区分字母还是汉字） 占两个字节

![image-20220108235113922](https://gitee.com/demon_night/images/raw/master/imgs/202201291851552.png)

4. 实现了serializable接口，说明可以串行化【在网上传输】。实现comparable接口，说明String对象可以比较

5. String是final类，不能被其他类继承 

6. 底层是存储在字符数组上的，数组是final类型的，不可以修改【地址不能修改，里面的值还是可以修改的】

   1. ![image-20220108235140339](https://gitee.com/demon_night/images/raw/master/imgs/202201291851446.png)
   2. 所以改变final数组地址会报错的

   ![image-20220108235208517](https://gitee.com/demon_night/images/raw/master/imgs/202201291851615.png)

### 练习1

```java
 //先从常量池查看是否有“hsp”数据空间，如果有，就直接指向；如果没有则重新创建。然后指向，s1最终指向的是常量池的空间地址
 String s1="hsp";

 //先在堆中创建空间，里面维护了value属性，指向常量池的“hsp”空间’如果常量池没有“hsp”，则重新创建，
 // 如果有，通过value指向，最终指向的是堆中的空间地址
 String s2=new String("hsp");
```

![image-20220108235224869](https://gitee.com/demon_night/images/raw/master/imgs/202201291851454.png)

### 知识点1

当调用String类的intern方法时，如果池中已经包含一个等于此String对象的字符串（用equals（Object）方法确定），则返回池中的字符串。否则，将此String**对象**添加到池中，并且返回String对象的引用

总结：b.intern（）最终返回的是常量池的地址（对象）

```java
String s1="hsp";
String s2=new String("hsp");

System.out.println(s1==s2.intern());.//true
System.out.println(s2==s2.intern());//false
```

### 练习2

```java
public class String_test2 {
    public static void main(String[] args){
        person p1=new person();
        p1.name="hspedu";
        person p2=new person();
        p2.name="hspedu";

        System.out.println(p1.name.equals(p2.name));//true
        System.out.println(p1.name==p2.name);//true,对于堆中的属性同名也采用不同的变量
        System.out.println(p1.name=="hspedu");//true
    }
}
class person{
    String name;
}
```

![image-20220108235246992](https://gitee.com/demon_night/images/raw/master/imgs/202201291851919.png)

### 知识点2

- String是final类，代表不可变的字符序列
- 字符串是不可变的，一个字符串对象一旦被分配，其内容是不变的

```java
String str4="hello";
 str4="haha";//一共创建了两个对象，刚开始指向hello字符串，后来str4指向haha字符串，但是hello字符串并没有被破坏，还在常量池中放着呢
```

```java
//先创建StringBuilder对象 String Builder sb=new StringBuilder
//sb.apend("hello")
//sb.append("world")
//String str5=sb.toString()
//其实最终str5最终指向堆中的一个value缓冲数组【`sb在堆中`】，数组指向常量池中的字符串”helloworld“,所以一共创建了三个对象
String a="hello";
String b="world"
String c=a+b
String d="helloworld"
    
c==d//结果为false，
```

```java
//编译器会把连接字符串优化成一块即”helloworld“，而不是创建三个对象
String c="hello"+"world"
```

> 总结：如果是S两个常量相加，看的是池。如果是两个变量相加，看的是堆

- 成员属性在栈里面，类属性在堆里面

### 知识点3

- 类变量：类变量是由 `static` 修饰的变量，也称为静态变量，可以通过类名访问，也可以通过实例对象来访问，通过对象访问也只是编码阶段这样写而已，在编译的时候会被自动转换成“类名称.变量名”的语法格式。
- 成员变量：非 `static` 修饰的变量都叫成员变量，也叫实例变量，也可以叫对象变量（很少这样叫），只能通过“实例对象”访问。成员变量也叫字段（field）。
- 类属性：类属性就是实例属性，也叫对象属性，是根据 `get` 方法得来的。

### 练习3

```java
public class String_test3 {
    String str =new String("hsp");
    final char[] ch={'j','a','v','a'};
    public void change(String str,char ch[]){
        str="java";
        ch[0]='h';
    }
    public static void main(String[] args){
        String_test3 ex=new String_test3();
        ex.change(ex.str,ex.ch);
        System.out.println(ex.str+"and");//hspand
        System.out.println(ex.ch);//hava
    }
}
```

![image-20220108235516578](https://gitee.com/demon_night/images/raw/master/imgs/202201292053692.png)

![image-20220129205635074](https://gitee.com/demon_night/images/raw/master/imgs/202201292056053.png)

#### 知识点

- str是ex的类属性，因此放在堆里面
- 对于字符串类型的放在池中，数组放在堆中
- 方法与其形参也放在栈里面、类对象ex也放在栈里面
- str=java，就相当于栈里面的那个str指向池中的java【String str=”java“】
- 由于数组是在堆里面存放的，因此会改变数组里面的值
- 而ex对象的类属性指向的的暂存数组里面的值还没发生改变，因此输出`hspand`与`hava`

### String 常用方法

```java
        //equals、equalsIgnoreCase
        String s1="hello";
        String s2="Hello";
        System.out.println(s1.equals(s2));//false
        System.out.println(s1.equalsIgnoreCase(s2));//true

        System.out.println("yzk".length());//3

        System.out.println(s1.indexOf('l'));//返回字符第一次出现的位置，从0开始计算，找不到返回-1.也可以搜索子字符串，按子字符串第一个字符索引为答案 
        System.out.println(s1.lastIndexOf('l'));//返回字符最后一次出现的索引

        System.out.println(s1.substring(1));//表示从索引1开始，截取后面所有的元素
        System.out.println(s1.substring(1,4));//表示从索引1开始截取，截取到索引4，但是不包含索引4【如果超出索引就会报错】
```

```java
        //toUpperCase转成大写，toLowerCase转成小写
        String s1="hello";
        System.out.println(s1.toUpperCase());

        //concat:拼接字符串
        System.out.println(s1.concat("world").concat("你好，世界"));

        //replace:替换方法,replace与replaceAll只是没有用正则表达式，作用是一样的，都是用右边的，替换掉所有左边的
        s1="helloworld你好世界";
        System.out.println(s1.replace("helloworld","你好，世界"));

        //split("这是个字符串"):分割字符串，返回是一个数组
        //如果用"\\"分割时，需要”\\\\“,因为'\'是转义字符，一个'\'只能转移生成一个'\'
        String s2="锄禾日当午,滴禾下土,谁知盘中餐,粒粒皆辛苦";
        String[] s3=s2.split(",");
        for(String s4:s3){
            System.out.println(s4);
        }

        //toCharArray（）
        String s4="happy";
        char[] s5=s4.toCharArray();
        for(char s6:s5) System.out.println(s6);

        //compareTo,如果两个字符串不相等，返回字符串长度的差值。
        //          如果两个字符串相等，返回第一个不同字符的差值，左减右
        String s7="jac";
        String s8="jack";
        System.out.println(s7.compareTo(s8));//3-4=-1

        //format[和C输出挺像的]
        String name="yzk";
        int age=18;
        float score=89.9f;
        char sex='男';
        String s9="我的名字是：%s,年龄：%d，成绩:%.2f，性别：%c.希望大家喜欢我";
        String s10=String.format(s9,name,age,score,sex);//运用占用符
        System.out.println(s10);
```

 ### 练习4

```java
package String;

public class String_test6 {
    public static void main(String[] args) {
        //对字符串中的指定部分进行反转
        String s1="abcdefg";
        //因为String是不可变的，因此需要新的变量重新接收一下改变的字符串
        try{
            s1=reverse(s1,1,4);
        }catch (Exception e){
            System.out.println(e.getMessage());
        }
        System.out.println(s1);
    }
    public static String reverse(String str,int start,int end){
        //编程技巧：******
        //判断是否符合规则【正确情况取反】参数错误输出报错信息
        if(!(str!=null&&start<end&&end<str.length())){
            throw new RuntimeException("参数不正确");
        }
        char[] chars=str.toCharArray();
        for(int i=start,j=end;i<j;i++,j--){
             char temp=chars[i];
             chars[i]=chars[j];
             chars[j]=temp;
        }
        //数组没有将数组转换成字符串的方法，因此只能将其放进字符串的构造器
        return new String(chars);
    }
}
```

### 练习5

```java
package String;

import java.util.Arrays;
import java.util.Scanner;

public class String_test7 {
    public static void main(String[] args) {
        String name;
        String password;
        String email;
        Scanner sc=new Scanner(System.in);
        System.out.println("请输入用户名");
        name= sc.next();
        if(!(name.length()==2||name.length()==3||name.length()==4)){
            throw new RuntimeException("输入错误");
        }
        System.out.println("请输入密码");
        password=sc.next();
        if(!(password.length()==6)){
            throw new RuntimeException("输入错误");
        }
        for(int i=0;i<6;i++){
            if(!(Character.isDigit(password.charAt(i)))){
                throw new RuntimeException("输入错误");
            }
        }
        System.out.println("请输入邮箱号");
        email= sc.next();
        int a=0;
        int b=0;
        for(int i=0;i<email.length();i++){
            if(email.charAt(i)=='@') a=i;
            if(email.charAt(i)=='.') b=i;
        }
        if(!(a!=0&&b!=0&&a<b)){
            throw new RuntimeException("输入错误");
        }
    }
}
```

![image-20220110214356136](https://gitee.com/demon_night/images/raw/master/imgs/202201291851575.png)

### 练习6

> 判断数字、大写字母、小写字母个数【Character类的方法 】

```java
package String;

import java.util.Scanner;

public class String_test9 {
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        String str=sc.next();
        pd(str);
    }
    public static void pd(String str){
        int num=str.length();
        int digital=0;
        int d=0;
        int x=0;
        for(int i=0;i<num;i++){
            if(Character.isUpperCase(str.charAt(i))) d++;
            else if(Character.isLowerCase(str.charAt(i))) x++;
            else if(Character.isDigit(str.charAt(i))) digital++;
        }
        System.out.println("大写字母："+d+" 小写字母："+x+" 数字："+digital);
    }
}
```

### 练习7【重点理解】

```java
package String;

public class String_test10 {
    String name;
    public String_test10(String name){
        this.name=name;
    }
    public static void main(String[] args) {
        String s1="hspedu";
        String_test10 a=new String_test10(s1);
        String_test10 b=new String_test10(s1);
        System.out.println(a==b);//false
        System.out.println(a.equals(b));//false【 if x and y refer to the same object (x == y has the value true)】
                                        //判断两个是否指向同一个对象
        System.out.println(a.name==b.name);//true【堆中的字符数组都指向池中字符串】

        String s4=new String("hspedu");
        String s5="hspedu";
        System.out.println(s1==s4);//false
        System.out.println(s4==s5);//false

        String t1="hello"+s1;
        String t2="hellohspedu";
        System.out.println(t1.intern()==t2);//true
    }
}
```

![image-20220111161055440](https://gitee.com/demon_night/images/raw/master/imgs/202201291851631.png)

# 	StringBuilder

## 知识点1

- 如果在单线程情况下尽量使用StringBuilder类，因为他作为StringBuffer的替换，速度更快，只是StringBuilder只能用于单线程
- StringBuilder实现了serializable接口，可以串行化，即可以进行网络传输，可以保存到文件里
- StringBuilder的对象内容仍然是存放在父类的的缓冲数组里面的，数组存放在堆里面、
- StringBuilder的方法没有做互斥处理，即没有sychronized关键字，因此只能用于单线程

## String、StringBuilder、StringBuffer比较

- String：不可变字符序列，效率低，但是复用率高

- StringBuffer：可变字符序列，效率较高（增删），线程安全

- Stringbuilder:可变字符序列，效率最高，线程不安全

- > 注：如果堆字符串序列做大量修改，不要使用String

# Math类

## 常用方法

```java
        //abs求绝对值
        System.out.println(Math.abs(-1));

        //pow求幂  返回值类型为double类型
        System.out.println(Math.pow(2,4));

        //ceil 向上取整 选择大于该数的最小整数,返回值是double类型
        //floor 向下取整
        System.out.println(Math.ceil(-3.1));

        //round 进行四舍五入 如果参数是float类型返回int类型
        //                  如果参数是double类型返回long类型
        System.out.println(Math.round(3.1));

        //sqrt 开平方 返回值是double类型
        System.out.println(Math.sqrt(3.0));

        //random返回一个随机数
        //random返回0~1之间的double类型的数，左闭右开
        //返回1个整数，应该用向下取整，因为如果四舍五入的话可能会取到8
        //用int强转的话会抹掉小数的
        System.out.println(Math.floor(Math.random()*6+2));

        //max,min返回最大值、最小值
        System.out.println(Math.min(1,2));
```

## 练习1

> 给定一个浮点数 n，求它的三次方根。
>
> #### 输入格式
>
> 共一行，包含一个浮点数 n。
>
> #### 输出格式 
>
> 共一行，包含一个浮点数，表示问题的解。
>
> 注意，结果保留 6位小数。
>
> #### 数据范围
>
> −10000≤n≤10000
>
> #### 输入样例：
>
> ```
> 1000.00
> ```
>
> #### 输出样例：
>
> ```
> 10.000000
> ```

```java
package 习题;
//-43.42
import java.util.Scanner;

public class cube_root {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        double num= sc.nextDouble();
        double temp=Math.abs(num);
        double res=Math.pow(temp,1.0/3);//返回值类型不能强转，否则会失去精度
        if(num<0) System.out.printf("-%.6f",res);
        else System.out.println(String.format("%.6f",res));
    }
}

```



# Arrays 类

## 知识点1

- 主要用于对数组进行操作（排序、搜索）
- toString 返回数组的字符串形式

## 常用方法1【外部比较器】

```java
        Integer[] a1={1,9,4};

        //遍历数组
        //在底层是StringBuilder通过‘{’、‘}’、‘，’进行拼接来的
        System.out.println(Arrays.toString(a1));//[1, 9, 4]


        //sort排序 由于数组是引用数据类型，调用方法后会直接改变数组的
        //返回值为空，该方法不能放在输出语句里面
        //sort 是可以重载的，也可以通过传入一个接口 comparator【比较器】 实现定制排序
        Arrays.sort(a1);
        System.out.println(Arrays.toString(a1));

        //定制排序 参数2用匿名内部类来实现接口
        //底层调用的是二分排序，内部类的返回结果的正负直接影响了排序规则，大于0：正序，小于0：逆序
 		//二分排序和冒泡排序可以看作相同的，如果左边 < 右边进行交换，【也就是左边 - 右边 <0】则说明是把大的值放在了左边，也就是逆序输出
		//如果大于0则进行交换，也就是当右边的小于左边的，也就正序排序了
		//因此就可以通过大于0、小于0来判断排序规则

        //最初是左-右，如果小于0就进行交换【逆序】，最后进行翻转【正序】
        //如果变成了右-左，与上面正好相反
        Arrays.sort(a1, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                Integer a1=(Integer) o1;
                Integer a2=(Integer) 02;
                return a2-a1;
            }
        });
        System.out.println(Arrays.toString(a1));//[9, 4, 1]
```

## 常用方法2

  ```java
          Integer[] a1={1,2,3,4,5,6,7,8,9,10};
          Integer[] a2={10,9,8,7,6,5,4,3,2,1};
  
          //二分查找,只能用于有序的，如果数组中查找不到返回 “-（应该存在的索引+1 ）”
          System.out.println(Arrays.binarySearch(a1,4));
          //从结果来看，二分查找只能用于正序排列的
          System.out.println(Arrays.binarySearch(a2,2));//-1
  
          //copyOf() 数组元素的复制
          //返回类型是复制数组的类型，a1为源数组，al.length为要复制的长度,如果要拷贝的长度大于源数组长度就添加“null”
          Integer[] new_array=Arrays.copyOf(a1,a1.length);
          System.out.println(Arrays.toString(new_array));//[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
  
          //fill 数组填充,可以理解成替换原来的数组
          Arrays.fill(a1,0);
          System.out.println(Arrays.toString(a1));//[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
  
          //equals 比较两个数组中的内容是否完全一致
          System.out.println(Arrays.equals(a1,a2));
  
          //asList，将一组值转换成List
          //l的编译类型 List(接口)
          //l的运行类型是java.util.Array里面的内部类ArrayList类型
          List<Integer> l=Arrays.asList(a2);
          System.out.println(l.toString());
          //运行类型获取:getClass
          System.out.println(l.getClass());//class java.util.Arrays$ArrayList
  ```

## 练习1【外部比较器】

> 按照书的价格正序、逆序输出、按照书名字的长度正序、逆序输出
>
> 知识点：
>
>         //由于价格可能是小数，如果，你要是把判断交给编译器的话可能不通过，因为你返回给编译器的类型是int  【public int compare(Object o1, Object o2) {】
>         //解决办法就是直接在内部类中进行返回 结果为整形的结果【也就是比较后的结果】
>         //如果要是强转返给编译器，可能会造成结果不准确 如(int)(0.3-0)=0,结果应该是大于0的，结果等于0了
>         //类里面的toString方法可以让对象以特定格式的字符串输出，因此只要类里面有toString方法，就可以通过输出语句把对象写出来
>         //而Arrays的toString方法正好能数组里面的内容【而本数组里面的内容类型是“对象”】，因此可以把数组里面的对象的内容输出
>         //小于0：交换（逆序），最后反转（正序）。因此返回小于0时返回-1，是按照正序排列
>         //对于书名没有小数，可以直接返回两个书名的长度差,此时就要有左-右【正序排列】、右-左【逆序排列】

```java
package Arrays;

import java.util.Arrays;
import java.util.Comparator;

public class arrays_test3 {
    public static void main(String[] args) {
        Book[] books=new Book[4];
        books[0]=new Book("红楼梦",100);
        books[1]=new Book("金瓶梅",90);
        books[2]=new Book("青年文摘",5);
        books[3]=new Book("java从入门到放弃",300);
        //由于价格可能是小数，如果，你要是把判断交给编译器的话可能不通过，因为你返回给编译器的类型是int  【public int compare(Object o1, Object o2) {】
        //解决办法就是直接在内部类中进行返回 结果为整形的结果【也就是比较后的结果】
        //如果要是强转返给编译器，可能会造成结果不准确 如(int)(0.3-0)=0,结果应该是大于0的，结果等于0了
        //类里面的toString方法可以让对象以特定格式的字符串输出，因此只要类里面有toString方法，就可以通过输出语句把对象写出来
        //而Arrays的toString方法正好能数组里面的内容【而本数组里面的内容类型是“对象”】，因此可以把数组里面的对象的内容输出
        //小于0：交换（逆序），最后反转（正序）。因此返回小于0时返回-1，是按照正序排列
        //对于书名没有小数，可以直接返回两个书名的长度差,此时就要有左-右【正序排列】、右-左【逆序排列】
        Arrays.sort(books, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                Book a1=(Book)o1;
                Book a2=(Book)o2;
                double price_val=a1.price-a2.price;
                if(price_val<0){
                    return -1;
                }
                else if(price_val>0){
                    return 1;
                }
                else{
                    return 0;
                }
            }
        });
        System.out.println(Arrays.toString(books));
        System.out.println("-------------------");
        Arrays.sort(books, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                Book a1=(Book)o1;
                Book a2=(Book)o2;
                double price_val=a1.price-a2.price;
                if(price_val<0){
                    return 1;
                }
                else if(price_val>0){
                    return -1;
                }
                else{
                    return 0;
                }
            }
        });
        System.out.println(Arrays.toString(books));
        System.out.println("-------------------");
        Arrays.sort(books, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                Book a1=(Book)o1;
                Book a2=(Book)o2;
                return a1.name.length()-a2.name.length();
            }
        });
        System.out.println(Arrays.toString(books));
        System.out.println("-------------------");
        Arrays.sort(books, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                Book a1=(Book)o1;
                Book a2=(Book)o2;
                return a2.name.length()-a1.name.length();
            }
        });
        System.out.println(Arrays.toString(books));
    }
}
class Book{
    String name;
    double price;
    public Book(String name,Integer price){
        this.name=name;
        this.price=price;
    }

    @Override
    public String toString() {
        return "Book{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
}
```



# System类

## 常用方法1

```java
        //exit 退出当前程序,0表示正常退出
        System.out.println("1");
        //System.exit(0);
        System.out.println("2");

        //arraycopy(源数组，从源数组的哪个索引开始，目的数组，目的数组的开始索引，复制长度)：复制数组元素，比较适合底层调用
        //一般使用Arrays.copyOf复制数组
        //src – the source array.
        //srcPos – starting position in the source array.
        //dest – the destination array.
        //destPos – starting position in the destination data.
        //length – the number of array elements to be copied.
        int[] a1={1,2,3};
        int[] a2=new int[3];
        System.arraycopy(a1,0,a2,0,3);
        System.out.println(Arrays.toString(a2));//[1, 2, 3]

        //currentTimeMillis:返回当前时间距离1970-1-1的毫秒数
        System.out.println(System.currentTimeMillis());

        //System.gc();垃圾回收机制
```

> 垃圾回收机制

```java
package system;

public class system_finalize_gc {
    public static void main(String[] args) {
        Car c=new Car("宝马");
        c=null;//这时Car对象就是1个垃圾，垃圾回收器就会销毁对象 ，在销毁对象前会调用该对象的finalize方法
                //如果程序员不重写finalize，那么就会调用Object类的的finalize方法
        //垃圾回收机制的调用，是由系统决定的（即有自己的GC算法），也可以通过System.gc()主动触发垃圾回收机制
        System.gc();//主动调用垃圾回收器
        System.out.println("程序退出");//但是目前finalize方法已经弃用
    }
}
class Car{
    private String name;

    public Car(String name) {
        this.name = name;
    }

    //重写finalize方法

    @Override
    protected void finalize() throws Throwable {
        System.out.println("我们销毁了汽车"+name);
    }
}

```



# 枚举类

## 枚举类的相关方法

1. 使用enum关键字时就不能再继承其他类，因为enum已经隐式继承了Enum类了,但是还是可以实现接口
2. 对于toString方法：如果改写了就调用重写后方法，否则调用默认的，返回对象的名字
3. valueOf():将字符串转换成对象,注：字符串必须是已有的常量名

```java
        //输出该对象的名称
        System.out.println(season.SUMMER.name);

        //输出该对象的次序，从0开始
        //因为SUMMER对象为第二个因此ordinal为1
        System.out.println(season.SUMMER.ordinal());

        //values返回值是一个数组，里面的内容是所有生命的对象
        season[] s=season.values();
        for(season s1:s){
            System.out.println(s1);
        }

        //valueOf():将字符串转换成对象
        //注：字符串必须是已有的常量名
        season summer=season.valueOf("SUMMER");
        System.out.println(summer);

        //compareTo（）：比较两个对象的编号,两编号相减【2-0=2】
        System.out.println(season.AUTUMN.compareTo(season.SPRING));

        //对于toString方法：如果改写了就调用重写后方法，否则调用默认的，返回对象的名字
        System.out.println(season.AUTUMN.toString());
```

## 代码实现

```java
package Enum1;

public class TextEnum {
    public static void main(String[] args){
        System.out.println(season.SUMMER);

        //输出该对象的名称
        System.out.println(season.SUMMER.name);

        //输出该对象的次序，从0开始
        //因为SUMMER对象为第二个因此ordinal为1
        System.out.println(season.SUMMER.ordinal());

        //values返回值是一个数组，里面的内容是所有生命的对象
        season[] s=season.values();
        for(season s1:s){
            System.out.println(s1);
        }

        //valueOf():将字符串转换成对象
        //注：字符串必须是已有的常量名
        season summer=season.valueOf("SUMMER");
        System.out.println(summer);

        //compareTo（）：比较两个对象的编号,两编号相减【2-0=2】
        System.out.println(season.AUTUMN.compareTo(season.SPRING));

        //对于toString方法：如果改写了就调用重写后方法，否则调用默认的，返回对象的名字
        System.out.println(season.AUTUMN.toString());
    }
}
//枚举类：用enum关键字代替class
 enum season {
    //参数变量必须写在后面,
    //如果有多个常量（对象），用“，”分隔
    SPRING("春天","温暖"),
    //相当于 public final static TextEnum1 SPRING=new TextEnum1("夏天","炎热")
    SUMMER("夏天","炎热"),
    AUTUMN("秋天","凉爽");
    public String name;
    public String desc;

    private season(String name, String desc) {
        this.name=name;
        this.desc=desc;
    }

    public String getName(){
        return name;
    }

    public String getdesc(){
        return desc;
    }

    @Override
    public String toString() {
        return "TextEnum1{" +
                "name='" + name + '\'' +
                ", desc='" + desc + '\'' +
                '}';
    }
}

```

### 例子1【输出星期X】

```java
package 习题;

public class TextWeek {
    public static void main(String[] args){
        week[] w=week.values();
        System.out.println("所有的星期信息如下");
        for(week num:w){
            System.out.println(num);
        }
    }
}

enum week{
    MONDY("星期一"),
    THUESDAY("星期二"),
    WEDNESDAY("星期三"),
    THURSDAY("星期四"),
    FIRDAY("星期五"),
    SATURDAY("星期六"),
    SUNDAY("星期日");
    String desc;

    private week(String desc){
        this.desc=desc;
    }

    public String toString(){
        return desc;
    }
}

```



# 内部类

## 1.1非静态内部类

```java
public class ClassOuter {
    private String OuterName;
    public void f() {
        System.out.println("外部类");
    }

    public class classinner{
        public void f() {
            System.out.println("内部类");
        }
    }

    public static void main(String[] args) {
        ClassOuter c=new ClassOuter();
        c.f();
        ClassOuter.classinner cc=c.new classinner();
        cc.f();
    }
}
```

2. 非静态内部类可以看作外部类的成员变量、成员方法来使用，所以必须依赖于外部类的对象才能调用，用法和成员变量或成员方法一样
   
   > 为什么使用内部类?
   
   采用内部类，可以隐藏细节和内部结构，封装性更好，让程序的结构更加合理
   
   1. 内部类也可以定义在方法体内，但是类的前缀 **不能加public** 
      
      ```java
      public class ClassOuter {
          private String OuterName;
      
          public void f() {
              class classinner{
                  public void ff() {
                      System.out.println("innerclass");
                  }
              }
              classinner cc=new classinner();
              cc.ff();
          }
      
          public static void main(String[] args) {
              ClassOuter c=new ClassOuter();
              c.f();
          }
      }
      ```
      
      注：由于是在方法体里面创建的对象所以不需要加前缀，而对于不在方法体内使用内部类的，需要添加前缀

## 1.2. 静态内部类

1. 静态内部类的构造不依赖于外部类对象，类中的所有静态组件都不需要依赖对象，可以直接通过类本身进行构造

```java
public class ClassOuter {
    private String OuterName;

    public void f() {
        System.out.println("外部类");
    }

    public static class classinner{
        private String name;
        public void f() {
            System.out.println("内部类");
        }
    }

    public static void main(String[] args) {
        ClassOuter.classinner s=new classinner();
        s.f();
    }
}
```

## 1.3 匿名内部类

1. 不需要创建实现类，即不需要写classinner 而是直接使用{}当成一个类来用
2. 匿名内部类一般用于接口的实现

```java
package TestInner;

interface myinterface{
    public void test();
}

//接口实现类
//class myimplement implements myinterface{
//    public void test() {
//        System.out.println("hello");
//    }
//}

public class TestInner1 {
    public static void main(String[] args) {
        myinterface m=new myinterface(){
            public void test() {
                System.out.println("hello");
            }
        };
        m.test();
    }
}
```

> 通过内部类实现接口

```java
interface myinterface{
    public void test();
}

public class TestInner1 {
    public class myimplement implements myinterface{
        public void test() {
            System.out.println("hello");
        }
    }

    public static void main(String[] args) {
        TestInner1 t=new TestInner1();
        TestInner1.myimplement tt=t.new myimplement();
        tt.test();
    }
}
```

------

# StringBuilder类

> 小明正在玩一个“翻硬币”的游戏。
>
> 桌上放着排成一排的若干硬币。我们用 * 表示正面，用 o 表示反面（是小写字母，不是零）。
>
> 比如，可能情形是：`**oo***oooo`
>
> 如果同时翻转左边的两个硬币，则变为：`oooo***oooo`
>
> 现在小明的问题是：如果已知了初始状态和要达到的目标状态，每次只能同时翻转相邻的两个硬币,那么对特定的局面，最少要翻动多少次呢？
>
> 我们约定：把翻动相邻的两个硬币叫做一步操作。

```java
public class coin_flip {
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        StringBuilder str1=new StringBuilder().append(sc.next());
        StringBuilder str2=new StringBuilder().append(sc.next());
        int ans=0;
        for(int i=0;i<str1.length()-1;i++){
            if(str2.charAt(i)!=str1.charAt(i)) {
                str1.replace(i,i+1, String.valueOf(str2.charAt(i)));
                if(str1.charAt(i+1)=='*') str1.replace(i+1,i+2,String.valueOf('o'));
                else if(str1.charAt(i+1)=='o') str1.replace(i+1,i+2,String.valueOf('*'));
                ans++;
            }
        }
        System.out.println(ans);
    }
}
```

1. 对于StringBuilder的replace（start，end，char c）方法，中截取的位置是start到end-1
2. 当要对stringBuilder的对象的数据进行修改时，要用String类的valueOf将其转换成字符，才能进行替换

# Lambda表达式

> 外部类、内部类、匿名类、Lambda表达式实现接口

1. 总的来说，Lambda 表达式可以用在任何需要使用匿名方法，或是代理的地方。编译器会将Lambda表达式编译为标准的匿名方法（可以使用ildasm.exe or reflector.exe得到确认）。

```java
interface Ilike{
    void like(int a);
}
//外部类实现接口
class Like implements Ilike{
    public void like(int a){
        System.out.println("I like you"+a);
    }
}

public class TestLambda {
    //静态内部类
    static class Innner implements Ilike{
        public void like(int a){
            System.out.println("i like you"+a);
        }
    }

    public static void main(String[] args){
        //接口作类型，实现类来创建对象
        Ilike like=new Like();
        like.like(1);

        //局部内部类
        class Innner implements Ilike{
            public void like(int a){
                System.out.println("i like you"+a);
            }
        }
        like=new Innner();
        like.like(2);

        //静态内部类不需要创建对象,若不是静态，则需要like=new Innner();
        like.like(3);

        //匿名类
        like=new Ilike() {
            @Override
            public void like(int a) {
                System.out.println("i like you"+a);
            }
        };
        like.like(4);

        //Lambda表达式
        like=(int a)->{System.out.println("i like you"+a);};
        //化简[只允许想要输出内容只有一句]
        like=(a)->System.out.println("i like you"+a);
    }
}
```

------

# 随机类

> 类名
> 
> Random

1. 种子可以直接放在构造函数里面,随机数就是产生数的初始值

```
Random random = new Random(seed);
```

2. 确定随机数范围

```
System.out.println(random.nextInt(6)+1);
```

 注：nextInt（最大值），包含0到最大值-1的区间的数

------

# Object类

1. 创建的任何类都继承Object类，所以可以使用toString()，相当于直接输出其地址
   
   ```java
   package Object; 
   
   public class TestObject {
       public static void main(String[] args) {
           A a=new A();
   
           //打印对象a相当于调用toString（）
           System.out.println(a);
           System.out.println(a.toString());
       }
   }
   
   class A{
       public void a() {
       }
   }
   ```

# BufferedReader类

## 基础

- ```
  new BufferedReader();//括号里面放的是一个流；可以是文件流、输入流
  ```
  
- 对于回车键并不会读入

```java
package BufferedReader;

import java.util.*;
import java.io.*;

public class bufferedReader_test1 {
    public static void main(String[] args) throws IOException{
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        String s=br.readLine();
        //按照单个字符来读取的
        int c=br.read();
        System.out.println(" "+c);
    }
}
```



# BigInteger类[处理整数]

## 知识点1

1. 由于BigInteger类创建的是对象，所以不能使用算数运算符“+-*/”
2. 方法：add（）、subtract（）【减】、multiply（）【乘】、divide（）【除】、divideAndRemainder（）【取余】
3. 方法里面只能放类对象
3. 乘的那数要用BigInteger的valueOf包起来
3. 对于从字符串中的获得的单个字符
3. 注意对于取余的话，返回值是一个数组，

```java
public class TestBig {
    public static void main(String[] args) {
        Scanner s=new Scanner(System.in);
        int num=s.nextInt();
        //创建对象
        BigInteger B=new BigInteger("1");
        //给sum赋初始值
        BigInteger sum=B.multiply(B);
        //循环
        for(int i=1;i<=num;i++) {
            sum=sum.multiply(BigInteger.valueOf(i));
        }
        System.out.println(sum);
    }
}
```

> 对于取余的运算：divideAndRemainder

```java
package 习题1;

import java.math.BigInteger;
import java.util.Arrays;
import java.util.Scanner;

public class dd_test1 {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        BigInteger s1=new BigInteger(sc.next());
        BigInteger s2=new BigInteger(sc.next());
        BigInteger s3=new BigInteger(sc.next());
        BigInteger ans=(s1.multiply(s2));
        //数组【商，余数】
        BigInteger[] ans1=ans.divideAndRemainder(s3);
        System.out.println(Arrays.toString(ans1));
    }
}
```



## 练习1

```java
package Biginteger;
import java.math.BigInteger;
import java.util.*;
public class Biginteger_test1 {
    public static void main(String[] args) {
        BigInteger b1=new BigInteger("123456789987654321");
        System.out.println(b1);
        //在对BigInteger进行+-*/时需要调用特定的方法,只能对同类型进行运算
        
        System.out.println(b1.add(new BigInteger("12")));
        System.out.println(b1.subtract(new BigInteger("12")));
        System.out.println(b1.multiply(new BigInteger("2")));
        System.out.println(b1.divide(new BigInteger("2")));
    }
}
```



# BigDecimal【处理小数】

## 常用方法1

```java
package BigDecimal;

import java.math.BigDecimal;
import java.math.RoundingMode;

public class bigDecimal_test1 {
    public static void main(String[] args) {
        BigDecimal b1=new BigDecimal("13.123456789987654321");
        System.out.println(b1);
        //对BigDecimal进行运算时，需要使用对应的方法
        
        System.out.println(b1.add(new BigDecimal(1)));
        System.out.println(b1.subtract(new BigDecimal(2)));
        System.out.println(b1.multiply(new BigDecimal(2)));
        System.out.println(b1.divide(new BigDecimal(2)));//可能会抛出异常【可能会除不尽】
        
        //解决方法：指定精度即可 RoundingMode.CEILING:如果有无限循环小数就会保留小数精度范围
        System.out.println(b1.divide(new BigDecimal(3), RoundingMode.CEILING));//可能会抛出异常【可能会除不尽】
    }
}
```



# 日期类

## 第一代日期类Data

1. 可以自己设定格式
2. 用SimpleDateFormat类的format方法将国外格式的时间转换成自己设定的格式的时间

```java
package data;

/**
 * 第一代日期类
 */

import java.text.SimpleDateFormat;
import java.util.*;

public class Data1 {
    public static void main(String[] args) throws Exception{
        Date d1=new Date();
        //获取当前系统时间
        System.out.println(d1);

        //定义格式
        //导包：import java.text.SimpleDateFormat
        SimpleDateFormat d2=new SimpleDateFormat("yyyy年MM月DD日 hh:mm:ss E");
        //将日期转换成指定格式的字符串
        String s=d2.format(d1);
        System.out.println(s);

        //对于中文格式字符串也可以转换成国外形式的，同样需要用到SimpleDateFormat对象
        //需要用到SimpleDateFormat对象的parse方法进行转换
        String s1="2021年12月340日 06:30:44 周一";
        System.out.println(d2.parse(s1));
    }
}

```

## 第二代日期类：Calendar

1. 不能自己设定格式
2. 可以输出自己想要的时间段，如分或秒

```java
package data;

import java.util.Calendar;

/**
 * 第二代日期类：Calendar
 */

public class Calendar1 {
    public static void main(String[] args){
        //Calendar是抽象类，只能通过getInstance来获取实例
        Calendar c= Calendar.getInstance();

        //由于Calendar没有提供对应的格式化类，因此需要需要自己组合：用get来获取想要的字段
        System.out.println("年："+c.get(Calendar.YEAR));
        //由于月份是从0开始的，因此需要加1才能表示正确的月份
        //得到是数字，因此结果是（数字+1）而不是把+数字+1，否则会将其p当成字符串在数字末尾加1
        System.out.println("月："+(c.get(Calendar.MONTH)+1));
        System.out.println("日："+c.get(Calendar.DAY_OF_MONTH));
        System.out.println("小时："+c.get(Calendar.HOUR));
        //获取24小时进制的时间
        System.out.println("小时："+c.get(Calendar.HOUR_OF_DAY));
        System.out.println("分钟："+c.get(Calendar.MINUTE));
        System.out.println("秒："+c.get(Calendar.SECOND));
    }

}

```

## 第三代日期类：LocalDateTime

1. 结合了第一代和第二代
2. 其格式类变成DateTimeFormatter，其实现方法依然是format方法
3. 拥有更多的方法：可以加上一段时间或者减去一段时间

```java
package 习题;
import javax.swing.text.DateFormatter;
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;
import java.time.format.DateTimeFormatter;
import java.util.Date;
import java.util.Locale;

/*
    第3代日期类：LocalDataTime
 */
public class LacaDataTime1 {
    public static void main(String[] args){
        //获取日期
        LocalDate l= LocalDate.now();
        System.out.println(l);//2022-01-11
        
        //获取时间
        LocalTime l1=LocalTime.now();
        System.out.println(l1);//16:32:37.212067200
        
        //获取日期与时间
        LocalDateTime l3=LocalDateTime.now();
        System.out.println(l3);//2022-01-11T16:32:37.212067200

        //获取时间的各部分字段
        System.out.println(l3.getHour());//16
        System.out.println(l3.getMonth());//JANUARY

        //格式化[对于LocalDateTime有对应的格式化类：DataTimeFormatter]
        DateTimeFormatter D= DateTimeFormatter.ofPattern("YYYY-MM-dd HH:mm:ss");
        String s=D.format(l3);
        System.out.println(s);//2022-01-11 16:32:37

        //加上270天
        LocalDateTime l4=l3.plusDays(270);
        String s1=D.format(l4);
        System.out.println(s1);//2022-10-08 16:32:37

        //270分钟之前
        LocalDateTime l5=l3.minusMinutes(270);
        String s2=D.format(l5);
        System.out.println(s2);//2022-01-11 12:02:37

    }
}


```

# 多线程

> 创建线程方式一：继承线程类

1. process：进程   thread：线程【进程包含若干线程】
   * 线程开启不一定立即执行，由CPU调度执行

```java
public class TestTread extends Thread{
    //创建线程【重写run方法】
    public void run() {
        for(int i=0;i<20;++i) {
            System.out.println("11");
        }
    }

    //主线程
    public static void main(String[] args) {

        //创建线程对象
        TestTread T=new TestTread();
        //run方法先执行
        T.run();
        //stsrt()方法:同时执行
        T.start();

        for(int i=0;i<20;++i) {
            System.out.println("22");
        }
    }
}
```

> 创建线程方式二：实现接口

```java
public class TestTread1 implements Runnable{
    //同样重写run方法
    public void run() {
        for(int i=0;i<200;++i) {
            System.out.println("11");
        }
    }

    public static void main(String[] args) {
        //创建Runnable接口的实现类对象
        TestTread1 T=new TestTread1();
        //创建线程对象构造方法里面填”接口实现类对象“
        Thread TT=new Thread(T);
        //调用线程方法
        TT.start();

        //可以简写成
        //new Thread(T).start();

        for(int i=0;i<200;i++) {
            System.out.println("22");
        }
    }
}
```

> 注：建议使用Runnable接口实现，可以避免面向对象单继承所带来的局限性

### callable接口

1. Runnable是执行工作的独立任务，但是不返回任何值。如果我们希望任务完成之后有返回值，可以实现Callable接口。在JavaSE5中引入的Callable是一个具有类型参数的范型，他的类型参数方法表示为方法call()而不是run()中返回的值，并且必须使用ExecutorService.submint()方法进行调用。

```java
//实现接口Callable 参数类型是String
public class TaskWithResult implements Callable<String> {
    private int id;
    public TaskWithResult(int id){
        this.id=id;
    }
    @Override
    public String call() throws Exception {
        return "result of TaskWithResult "+id;
    }
}
```

2. 实现callable接口，可以添加泛型，从而增加返回值的限制
3. 创建一个 FutureTask ，将在运行时执行给定的 Runnable ，并安排 get将在成功完成后返回给定的结果。【和Thread可以看作是同等级的】

### 例题1

```java
//模拟买票
public class TestThread2 implements Runnable{
    private int ticketNum=10;
    //重写run方法
    public void run() {
        do {
            System.out.println(Thread.currentThread().getName()+"买到了第"+ticketNum+"张票");
        }while(ticketNum-->0);
    }

    public static void main(String[] args) {
        //创建接口实现类对象
        TestThread2 T=new TestThread2();
        //调用Thread的start方法
        new Thread(T,"小明").start();
        new Thread(T,"小兰").start();
        new Thread(T,"黄牛").start();
    }
}
```

### 例题2

> 龟兔赛跑

注：Thread.currentThread().getName()用来获取对象名称

```java
public class Race implements Runnable{
    //由于胜利者只有一人，定义成static类型
    private static String winner;
    public void run() {
        for(int i=0;i<=1000;++i) {
            if(gameover(i)) {
                break;
            }
            System.out.println(Thread.currentThread().getName()+"跑了第"+i+"步");
        }
    }
    //判断比赛是否结束
    public boolean gameover(int i) {
        if(i>=1000){
            //给winner赋值
            winner=Thread.currentThread().getName();
            System.out.println(winner+"赢得了比赛");
            return true;
        }
        return false;
    }

    public static void main(String[] args) {
        Race race=new Race();

        new Thread(race,"乌龟").start();
        new Thread(race,"小兔").start();
    }
}
```

### 例3

> 结婚【代理的概念】

```java
/*
真实对象和代理对象实现同一个接口
代理对象要代理真实角色
好处：
代理对象可以去做真实对象所做不了的事情
真实对象可以专注做自己的事情
 */
```

```java
interface Marry{
    void HappyWedding();
}

public class TestWedding {
    public static void main(String[] args){
        new weddingcompany(new You()).HappyWedding();
    }
}

class You implements Marry{
    public void HappyWedding(){
        System.out.println("老秦今天结婚，太开心了，嘿嘿");
    }
}
//代理公司
class weddingcompany implements Marry{
    //都实现接口，所以可以直接定义成接口类型的变量
    private Marry target;
    public weddingcompany(Marry target){
        this.target=target;
    }
    public void HappyWedding(){
        before();
        this.target.HappyWedding();
        after();
    }
    private void before(){
        System.out.println("布置婚礼现场，准备开始");
    }
    private void after(){
        System.out.println("婚礼结束，收尾款");
    }
}
```

### 线程停止

```java
/*
建议线程自己停止，利用次数，而不是死循环
建议使用标志位
不要使用stop或者destroy等过时或者JDK比建议使用的方法
 */
```

```java
public class TestStop implements Runnable{
    //建立标志位
    private boolean flag=true;

    public void run(){
        int i=0;
        while (flag) {
            System.out.println("run thread " + i++);
        }
    }

    public void stop(){
        this.flag=false;
    }

    public static void main(String[] args){
        TestStop T=new TestStop();
        new Thread(T).start();

        for(int i=0;i<=1000;i++){
            System.out.println("main"+i);
            if(i==900){
                T.stop();
                System.out.println("Thread结束");
            }
        }
    }
}
```

### 例题：sleep的应用【倒计时】

```java
public class TestSleep {
    //模拟倒计时
    public static void tenDown(){
        int num=10;
        while(true){
            //抛出异常
            try{
                Thread.sleep(1000);
            }
            catch(Exception e){
                e.printStackTrace();
            }
            System.out.println(num--);
            if(num==0){
                break;
            }
        }
    }

    public static void main(String[] args){
        tenDown();
    }
}
```

### 线程礼让【yield（）】

1. 礼让不一定成功
2. 礼让就是遇到yield，重新返回就绪状态，让另一个对象先执行，可能成功不了

```java
public class Testyield implements Runnable{
    public void run(){
        System.out.println(Thread.currentThread().getName()+"在执行");
        Thread.yield();
        System.out.println(Thread.currentThread().getName()+"执行结束");
    }
    public static void main(String[] args){
        Testyield T=new Testyield();

        new Thread(T,"a").start();
        new Thread(T,"b").start();
    }
}
```

### 插队：Join（）

```java
public class TestJoin implements Runnable{
    public void run(){
        for(int i=0;i<1000;++i){
            System.out.println("Vip" +i);
        }
    }

    public static void main(String[] args){
        TestJoin T=new TestJoin();
        Thread TT=new Thread(T);
        //TT也必须进入就绪状态
        TT.start();

        for(int i=0;i<200;++i){
            if(i==100){
                try{
                    TT.join();
                }
                catch(Exception e){
                    e.printStackTrace();
                }
            }
            System.out.println("main "+i);
        }
    }
}
```

### 线程状态

1. 状态类型用Thread.State
2. 对于需要代理的可以直接使用Lambda表达式
3. [`NEW`](../../java/lang/Thread.State.html#NEW)
   尚未启动的线程处于此状态。
4. [`RUNNABLE`](../../java/lang/Thread.State.html#RUNNABLE)
   在Java虚拟机中执行的线程处于此状态。
5. [`BLOCKED`](../../java/lang/Thread.State.html#BLOCKED)
   被阻塞等待监视器锁定的线程处于此状态。
6. [`WAITING`](../../java/lang/Thread.State.html#WAITING)
   正在等待另一个线程执行特定动作的线程处于此状态。
7. [`TIMED_WAITING`](../../java/lang/Thread.State.html#TIMED_WAITING)
   正在等待另一个线程执行动作达到指定等待时间的线程处于此状态。
8. [`TERMINATED`](../../java/lang/Thread.State.html#TERMINATED)
   已退出的线程处于此状态

```java
public class TestStatue{

    public static void main(String[] args){
        Thread T=new Thread(()->{
            for(int i=0;i<5;i++){
                try{
                    //sleep是Thread类的静态方法
                    Thread.sleep(1000);
                }
                catch(Exception e){
                    e.printStackTrace();
                }
            }
            System.out.println("等待时间过去");
        });

        //观察初始状态，状态类型为State,注意是大写
        Thread.State s=T.getState();
        System.out.println(s);

        //运行后状态
        T.start();
        s=T.getState();
        System.out.println(s);

        //当等待时间结束了，s还没有更新，所以还能再进去一次，输出结果TERMINATED
        while(s!=Thread.State.TERMINATED){
            //防止Cpu爆满
            try{
                Thread.sleep(100);
            }
            catch(Exception e){
                e.printStackTrace();
            }
            s=T.getState();
            System.out.println(s);
        }
    }
}
```

### 优先级：priority

1. 优先级低只是代表CPU调用该线程的概率低，并不是不调用了
2. 调用时也并不全是高优先级优先调用，优先级低的也有可能先调用
3. main线程最先调用
4. getPriority（）：获取优先级

```java
public class TestPriority implements Runnable{
    public void run(){
        System.out.println(Thread.currentThread().getName()+" "+Thread.currentThread().getPriority());
    }
    public static void main(String[] args){
        System.out.println(Thread.currentThread().getName()+" "+Thread.currentThread().getPriority());

        TestPriority T=new TestPriority();
        Thread T1=new Thread(T);

        Thread T2=new Thread(T);

        Thread T3=new Thread(T);

        Thread T4=new Thread(T);

        T1.setPriority(1);
        T1.start();

        T2.setPriority(3);
        T2.start();

        T3.setPriority(5);
        T3.start();

        T4.setPriority(10);
        T4.start();
    }
}
```

### 守护线程：deamon

1. 线程分为用户线程和守护线程
2. 虚拟机必须保证用户线程执行完毕
3. 虚拟机不用等待守护线程执行完毕

```java
/**
 * 守护线程
 */
public class TestDeamon {
    public static void main(String[] args){
        God G=new God();

        Thread T=new Thread(G);
        T.setDaemon(true);//默认为false，表示用户线程，正常的线程都是用户线程
        T.start();

        new Thread(new Person()).start();
    }
}
class God implements Runnable{
    public void run(){
        while(true)
        System.out.println("上帝守护着你");
    }
}
class Person implements Runnable{
    public void run(){
        for(int i=0;i<=36500;++i){
            System.out.println("开心过了一天");
        }
        System.out.println("GoodBye World");
    }
}
```

### 并发：synchronized

1. 在100万基金面前等待，时间一过，两个人都会去拿，从而方法事件并发问题

#### 基金问题

```java
public class unSafeBank {
    public static void main(String[] args){
        Acount A=new Acount(100,"结婚基金");

        //将人交给银行
        Bank you=new Bank(A,50,"you");

        Bank girlFriend=new Bank(A,100,"girlFriend");

        //两人开始就绪
        you.start();
        girlFriend.start();

    }
}
class Acount{
    public int money;
    private String countName;
    public Acount(int money,String countName){
        this.money=money;
        this.countName=countName;
    }
}
class Bank extends Thread{
    Acount acount;
    int drawingMonney;
    int nowmoney;
    String name;
    public Bank(Acount acount,int drawingMonney,String name){
        this.name=name;
        this.acount=acount;
        this.drawingMonney=drawingMonney;
    }
    public void run(){
        if(acount.money-drawingMonney<0) {
            System.out.println("余额不足");
            return;
        }

        //在100万基金面前等待，时间一过，两个人都会去拿，从而方法事件并发问题
        try{
            Thread.sleep(1000);
        }
        catch(Exception e){
            e.printStackTrace();
        }
        nowmoney=acount.money-drawingMonney;
        acount.money=acount.money-drawingMonney;
        System.out.println(name+" "+drawingMonney);
        System.out.println(acount.money);
    }
}
```

2. 方法里面需要修改的内容才需要锁，锁的太多会降低性能
3. synchronized是关键字，分为synchronized方法和synchronized块【比synchronized小】

#### 解决买票问题

```java
//模拟买票
public class TestSynchronized implements Runnable{
    private int ticketNum=10;
    boolean flag=true;

    //加上同步锁可以解决并发问题，锁的是对象
    public synchronized void run(){
        while(flag){
            System.out.println(Thread.currentThread().getName()+"拿到了第"+ticketNum+"张票");
            stop(ticketNum--);
            if(!flag){
                break;
            }
        }
    }

    public boolean stop(int i) {
        if (ticketNum<=0) {
            flag = false;
        }
        return flag;
    }

    public static void main(String[] args) {
        //创建接口实现类对象
        TestSynchronized T=new TestSynchronized();
        //调用Thread的start方法
        new Thread(T,"小明").start();
        new Thread(T,"小兰").start();
        new Thread(T,"黄牛").start();

        try{
            Thread.sleep(100);
        }
        catch(Exception e){
            e.printStackTrace();
        }
    }
}
```

#### 总结【Synchronized的三种方法】

1. 修饰实例方法：作用于当前对象实例加锁，**进入同步代码前要获得当前对象实例的锁**。

```java
synchronized void method() {
  //业务代码
}
```

2. 修饰静态方法：给当前类加锁【静态成员不属于任何一个对象，不管new了多少个对象，静态资源只有一份】

所以当如果一个线程 A 调用一个实例对象的非静态 synchronized 方法，而线程 B 需要调用这个实例对象所属类的静态 synchronized 方法，是允许的，不会发生互斥现象，**因为访问静态 synchronized 方法占用的锁是当前类的锁，而访问非静态 synchronized 方法占用的锁是当前实例对象锁。**

```java
synchronized void method() {
  //业务代码
}
```

3. 修饰代码块：**指定加锁对象，对给定对象/类加锁。synchronized(this / object) 表示进入同步代码库前要获得给定对象的锁。synchronized(类.class) 表示进入同步代码前要获得当前 class 的锁**

```java
synchronized(this) {
  //业务代码
}
```

4. synchronized 关键字加到 static 静态方法和 synchronized(class) 代码块上都是是给 Class 类上锁。
   synchronized 关键字加到实例方法上是给对象实例上锁。

#### 死锁

1. 互斥使用，即当资源被一个线程使用 (占有)时，别的线程不能使用.即存在一个等待队列：P1占有P2的资源，P2占有P3的资源，P3占有P1的资源，互相等待彼此释放线程这样一个死循环

```java
System.out.println(Thread.currentThread().getName()+"获得口红的锁");
      try{
            Thread.sleep(1000);
         }
      catch(Exception e){
            e.printStackTrace();
          }
      synchronized(mirror){
           System.out.println(Thread.currentThread().getName()+"获得镜子的锁");
      }
}
```

```java
//拿口红还想要镜子
//拿镜子还想要口红
package statue;

public class TestDeadLock {
    public static void main(String[] args){
        MakeUp M=new MakeUp(0,"灰姑凉");
        MakeUp M1=new MakeUp(1,"白雪公主");

        M.start();
        M1.start();
    }
}

class lipstick{

}

class mirror{

}

class MakeUp extends Thread{

    static lipstick lipstick=new lipstick();
    static mirror mirror=new mirror();

    int choice;
    String girlname;

    public MakeUp(int choice,String girlname){
        this.choice=choice;
        this.girlname=girlname;
    }

    public void run(){
        makeup();
    }

    private void makeup(){
        if(choice==0){
            synchronized(lipstick){
                System.out.println(Thread.currentThread().getName()+"获得口红的锁");
                try{
                    Thread.sleep(1000);
                }
                catch(Exception e){
                    e.printStackTrace();
                }
                synchronized(mirror){
                    System.out.println(Thread.currentThread().getName()+"获得镜子的锁");
                }
            }
        }
        else{
            synchronized(mirror){
                System.out.println(Thread.currentThread().getName()+"获得镜子的锁");
                try{
                    Thread.sleep(1000);
                }catch (Exception e){
                    e.printStackTrace();
                }
                synchronized(lipstick){
                    System.out.println(Thread.currentThread().getName()+"获得口红的锁");
                }
            }
        }
    }
}

```

#### 生产者与消费者的问题

```java
package statue;
/*
 * 模拟3个人排队买票，张某、李某和赵某买电影票，售票员只有3张5元钱，
 * 电影票5元钱一张。张某拿一张20元的人民币排在李某的前面买票，
 * 李某排在赵某的前面拿一张10元的人民币买票，赵某拿一张5元的人民币买票。
 * 请使用多线程类完成上述过程。
 */
public class TestTicket {
    public static void main(String[] args){
        //创建线程
        windows w1 = new windows("张某", 20);
        windows w2 = new windows("李某", 10);
        windows w3 = new windows("赵某", 5);

        try{
            new Thread(w1).start();
            new Thread(w2).start();
            new Thread(w3).start();
        }catch(Exception e){
            e.printStackTrace();
        }
    }
}

class windows implements Runnable{

    String name;
    static int twentymoney=0;
    static int fivemoney=3;
    static int tenmoney=0;
    int drawingmoney;

    public windows(String name,int drawingmoney){
        this.name=name;
        this.drawingmoney=drawingmoney;
    }

    public synchronized void run(){

        if(drawingmoney==5){
            System.out.println(name+"给你票，正好");
            fivemoney++;
        }
        else if(drawingmoney==20){
                while(fivemoney < 3)
                {
                    try
                    {
                        Thread.sleep(100);
                    }
                    catch(InterruptedException e){}
                }
                fivemoney = fivemoney-3;
                twentymoney++;
                System.out.println( "给你入场券，你给我20元，找你15元。");
        }
        else if(drawingmoney==10){
            while(fivemoney < 1)
            {
                try
                {
                    Thread.sleep(100);
                }
                catch(InterruptedException e){}
            }
            fivemoney = fivemoney-1;
            tenmoney++;
            System.out.println("给你入场券，你给我10元，找你5元。");
        }
        notifyAll();
    }
}
```

#### 生产者与消费者----红绿灯法

```java
package statue;

public class TestPC {
    public static void main(String[] args){
        TV tv=new TV();
        new player(tv).start();
        new watcher(tv).start();
    }
}

class player extends Thread{
    TV tv;//把平台对象拿过来
    public player(TV tv){
        this.tv=tv;
    }
    //进行表演
    public void run(){
        for(int i=1;i<=20;i++){
            if(i%2==1)
            tv.play("快乐大本营");
            else
            tv.play("电视剧");
        }
    }
}

class watcher extends Thread{
    TV tv;//将平台对象拿出来
    public watcher(TV tv){
        this.tv=tv;
    }
    //观看节目
    public void run(){
        //表演二十次，观看也要二十次
        for(int i=0;i<20;i++){
            tv.watch();
        }
    }
}

class TV{
    boolean flag=true;//表演节目
    String voice;
    public synchronized void play(String voice){
        if(!flag){
            try{
                wait();//等待，观众去看电视
            }catch (Exception e){
                e.printStackTrace();
            }
        }
        System.out.println("演员表演了"+voice);
        this.voice=voice;
        notifyAll();//唤醒等待的所有线程【即观众】
        this.flag=!this.flag;
    }
    public synchronized void watch(){
        if(flag){
            try{
                wait();//等待，表演者去表演电影
            }catch (Exception e){
                e.printStackTrace();
            }
        }
        System.out.println("观众观看了"+voice);
        notifyAll();//唤醒等待的演员线程
        this.flag=!this.flag;
    }
}
```

## 2023年7月28日再次学习

### 什么是多线程

![image-20230806105704524](https://cdn.jsdelivr.net/gh/yzk656/image/202308061057612.png)



![](https://cdn.jsdelivr.net/gh/yzk656/image/202308061101480.png)



![image-20230806110307869](https://cdn.jsdelivr.net/gh/yzk656/image/202308061103964.png)

![image-20230806110424160](https://cdn.jsdelivr.net/gh/yzk656/image/202308061104264.png)

![image-20230806113801958](https://cdn.jsdelivr.net/gh/yzk656/image/202308061138086.png)



---

三种实现方式

继承Thread

```java
package class1;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 11:40
 */
public class ThreadDemo {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        MyThread myThread2 = new MyThread();

        myThread.setName("线程1");
        myThread2.setName("线程2");
        myThread.start();
        myThread2.start();
    }
}
```

```java
package class1;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 11:41
 */
public class MyThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(getName()+"hello world");
        }
    }
}
```

==实现Runable接口==

```java
package class2;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 11:47
 */
public class ThreadDemo {
    public static void main(String[] args) {
        //线程要执行的对象
        MyThread myThread = new MyThread();
        //创建线程对象
        Thread thread = new Thread(myThread);
        Thread thread2 = new Thread(myThread);

        //给线程设置名字
        thread.setName("run1");
        thread2.setName("run2");

        thread.start();
        thread2.start();
    }
}

```

```java
package class2;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 11:47
 */
public class MyThread implements Runnable{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            Thread thread = Thread.currentThread();
            System.out.println(thread.getName()+"hello runable");
        }
    }
}
```

==实现Callable接口==

```java
package class3;

import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 12:26
 */
public class ThreadDemo {
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        //创建Callable对象（表示多线程要执行的任务）
        MyCallable myCallable = new MyCallable();
        //创建FutureTask对象，用于存放结果
        FutureTask<Integer> integerFutureTask = new FutureTask<Integer>(myCallable);
        //创建多线程对象
        Thread thread = new Thread(integerFutureTask);

        //接收结果
        thread.start();
        Integer i = integerFutureTask.get();
        System.out.println(i);
    }
}
```

```java
package class3;

import java.util.concurrent.Callable;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 12:26
 */
public class MyCallable implements Callable<Integer> {
    @Override
    public Integer call() throws Exception {
        int sum=0;
        for (int i = 1; i < 100; i++) {
            sum+=i;
        }

        return sum;
    }
}
```

![image-20230806123508750](https://cdn.jsdelivr.net/gh/yzk656/image/202308061235848.png)

### 常见的成员方法

![image-20230806123552146](https://cdn.jsdelivr.net/gh/yzk656/image/202308061235295.png)

![image-20230806124742719](https://cdn.jsdelivr.net/gh/yzk656/image/202308061247807.png)

对于线程的名字我们可以通过setName（）进行设置，也可以通过Thread的构造方法进行设置方法，也就可以在MyThread的构造方法中去调用Thread类的有参构造方法

```java
package class4;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 12:49
 */
public class ThreadDemo {
    public static void main(String[] args) {
        //创建线程对象
        MyThread myThread = new MyThread("坦克");
        MyThread myThread2 = new MyThread("飞机");
        myThread.start();
        myThread2.start();

        Thread thread = Thread.currentThread();
        System.out.println(thread.getName());
    }
}
```

```java
package class4;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 12:49
 */
public class MyThread extends Thread{
    public MyThread() {
    }

    public MyThread(String name) {
        super(name);
    }

    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(getName()+"@"+i);
        }
    }
}
```

![image-20230806125630093](https://cdn.jsdelivr.net/gh/yzk656/image/202308061256217.png)

线程的默认值是5，优先级越大只是说抢到的概率越高

```java
package class5;

import class5.MyThread;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 12:49
 */
public class ThreadDemo {
    public static void main(String[] args) {
        MyThread myThread1 = new MyThread();
        //创建线程对象
        Thread thread1 = new Thread(myThread1, "坦克");
        Thread thread2 = new Thread(myThread1, "飞机");

        thread1.setPriority(1);
        thread2.setPriority(10);

        thread1.start();
        thread2.start();
    }
}
```

```java
package class5;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 12:49
 */
public class MyThread implements Runnable{
    @Override
    public void run() {
        for (int i = 0; i <=100; i++) {
            System.out.println(Thread.currentThread().getName()+"@"+i);
        }
    }
}
```

---

守护线程：[对于不同线程之间]

​	当其他非守护线程执行完毕后，守护线程也会陆续结束，并不完整执行守护线程

```java
package class6;

import class1.MyThread;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 13:24
 */
public class ThreadDemo {
    public static void main(String[] args) {
        //获取线程对象
        MyThread1 myThread1 = new MyThread1();
        MyThread2 myThread2 = new MyThread2();

        //设置线程名
        myThread1.setName("女神");
        myThread2.setName("备胎");

        //设置守护线程
        myThread2.setDaemon(true);

        myThread1.start();
        myThread2.start();
    }
}
```

```java
package class6;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 13:24
 */
public class MyThread1 extends Thread {
    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println(getName() + "@" + i);
        }
    }
}
```

```java
package class6;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 13:24
 */
public class MyThread2 extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(getName()+"@"+i);
        }
    }
}
```

礼让线程：

​	就是你让我，我让你（让出CPU的执行权）

```java
package class7;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 14:21
 */
public class ThreadDemo {
    public static void main(String[] args) {
        MyThread myThread1 = new MyThread();
        MyThread myThread2 = new MyThread();

        myThread1.setName("飞机");
        myThread2.setName("坦克");

        myThread1.start();
        myThread2.start();
    }
}
```

```java
package class7;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 14:21
 */
public class MyThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(getName()+"@"+i);

            Thread.yield();
        }
    }
}
```

插入线程

​	可以让一个线程在另一个线程之前运行

```java
package class8;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 15:58
 */
public class ThreadDemo {
    public static void main(String[] args) throws InterruptedException {
        MyThread myThread = new MyThread();
        myThread.setName("tudou");
        myThread.start();

        myThread.join();
        for (int i = 0; i < 10; i++) {
            System.out.println("main线程"+i);
        }
    }
}
```

```java
package class8;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 15:58
 */
public class MyThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(getName()+"@"+i);
        }
    }
}
```

---

![image-20230806163005150](https://cdn.jsdelivr.net/gh/yzk656/image/202308061630265.png)

static解决了每个窗口都卖100张票的问题

synchronized解决了多个线程进入同一个代码块，导致变量变大的问题，参数就可以使用本类

锁的嵌套容易导致死锁

```java
package class9;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 17:21
 */
public class ThreadDemo {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        MyThread myThread2 = new MyThread();
        MyThread myThread3 = new MyThread();
        myThread.setName("窗口1");
        myThread2.setName("窗口2");
        myThread3.setName("窗口3");

        myThread.start();
        myThread2.start();
        myThread3.start();
    }
}
```

```java
package class9;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 17:21
 */
public class MyThread extends Thread {
    //设置多个线程共享变变量，static可以使变量变成类相关而不是实例相关
    static int ticket = 0;

    //锁对象，一定是唯一的
    static Object object = new Object();

    @Override
    public void run() {
        while (true) {
            //同步代码块
            synchronized (object){
                try {
                    Thread.sleep(10);
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                }
                ticket++;
                if(ticket>100){
                    break;
                }else {
                    System.out.println(getName()+"正在卖"+ticket+"张票");
                }
            }
        }
    }
}
```

锁对象参数因为必须要唯一，所以可以改为类本身

```java
package class9;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 17:21
 */
public class MyThread extends Thread {
    //设置多个线程共享变变量，static可以使变量变成类相关而不是实例相关
    static int ticket = 0;

    @Override
    public void run() {
        while (true) {
            //同步代码块
            synchronized (MyThread.class){
                try {
                    Thread.sleep(10);
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                }
                ticket++;
                if(ticket>100){
                    break;
                }else {
                    System.out.println(getName()+"正在卖"+ticket+"张票");
                }
            }
        }
    }
}
```

![image-20230806180120096](https://cdn.jsdelivr.net/gh/yzk656/image/202308061801199.png)



如果当前锁方法是非静态的，那个里面那个参数就是指的调用者

如果当前锁方法是静态的，那么那个参数指的就是当前类的字节码对象

```java
package class10;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 17:50
 */
public class ThreadDemo {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();

        Thread thread = new Thread(myThread, "窗口1");
        Thread thread2 = new Thread(myThread, "窗口2");
        Thread thread3 = new Thread(myThread, "窗口3");

        thread.start();
        thread2.start();
        thread3.start();
    }
}
```

```java
package class10;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 17:50
 */
public class MyThread implements Runnable {
    //由于Thread中引入的参数都是一个类，所以这个变量就是唯一的，不用加上static了
    int ticket = 0;

    @Override
    public void run() {
        while (true) {
            //同步代码块（同步方法）
            if (method()) break;
        }
    }

    private synchronized boolean method() {
        if (ticket == 100) {
            return true;
        } else {
            try {
                Thread.sleep(10);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            ticket++;
            System.out.println(Thread.currentThread().getName() + "正在卖" + ticket + "张票");
        }
        return false;
    }
}
```

![image-20230806185258406](https://cdn.jsdelivr.net/gh/yzk656/image/202308061852536.png)



```java
package class11;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 18:59
 */
public class ThreadDemo {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        MyThread myThread2 = new MyThread();
        MyThread myThread3 = new MyThread();

        myThread.setName("窗口1");
        myThread2.setName("窗口2");
        myThread3.setName("窗口3");

        myThread.start();
        myThread2.start();
        myThread3.start();
    }
}
```

```java
package class11;

import java.util.concurrent.locks.ReentrantLock;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 18:59
 */
public class MyThread extends Thread {

    static int ticket = 0;

    static ReentrantLock lock = new ReentrantLock();

    @Override
    public void run() {
        while (true) {
            lock.lock();
            try {
                if(ticket==100){
                    break;
                }else {
                    Thread.sleep(10);
                    ticket++;
                    System.out.println(getName()+"正在卖"+ticket+"张票");
                }
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            } finally {
                lock.unlock();
            }
        }
    }
}
```

### 生产者与消费者

![image-20230806194215382](https://cdn.jsdelivr.net/gh/yzk656/image/202308061942522.png)

![image-20230806194243569](https://cdn.jsdelivr.net/gh/yzk656/image/202308061942688.png)



等待唤醒机制写法

```java
package class12;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 21:53
 */
public class ThreadDemo {
    public static void main(String[] args) {
        //设置线程对象
        Cook cook = new Cook();
        Foodie foodie = new Foodie();

        //给线程设置名字
        cook.setName("厨师");
        foodie.setName("吃货");

        //开启线程
        cook.start();
        foodie.start();
    }
}
```

```java
package class12;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 19:53
 */
public class Cook extends Thread{
    @Override
    public void run() {
        while (true){
            synchronized (Desk.lock){
                if(Desk.count==0){
                    break;
                }else {
                    //判断桌子上是否有食物
                    if(Desk.foodFlag==1){
                        try {
                            Desk.lock.wait();
                        } catch (InterruptedException e) {
                            throw new RuntimeException(e);
                        }
                    }else {
                        //制作食物
                        System.out.println("厨师做了一碗面条");
                        //修改桌子状态
                        Desk.foodFlag=1;
                        //唤醒消费者开吃
                        Desk.lock.notifyAll();
                    }
                }
            }
        }
    }
}
```

```java
package class12;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 21:53
 */
public class Foodie extends Thread {

    @Override
    public void run() {
        while (true) {
            synchronized (Desk.lock) {
                if (Desk.count == 0) {
                    break;
                } else {
                    //判断桌子上是否有面条
                    if (Desk.foodFlag == 0) {
                        try {
                            //让当前线程与锁进行绑定
                            Desk.lock.wait();
                        } catch (InterruptedException e) {
                            throw new RuntimeException(e);
                        }
                    } else {
                        //有面条
                        Desk.count--;
                        System.out.println("吃货正在吃面条，还能吃" + Desk.count + "碗面条");
                        //唤醒厨师继续做
                        Desk.lock.notifyAll();
                        //修改桌子状态
                        Desk.foodFlag = 0;
                    }
                }
            }
        }
    }
}
```

```java
package class12;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 19:53
 */
public class Desk {
    /**
     * 控制生产者和消费者的执行
     */

    /**
     * 是否有面条
     * 1：有
     * 0：没有
     */
    public static int foodFlag=0;

    /**
     * 能吃的总个数
     */
    public static int count=10;

    /**
     * 锁对象
     */
    public static Object lock=new Object();
}
```

![image-20230806224207811](https://cdn.jsdelivr.net/gh/yzk656/image/202308062242997.png)

![image-20230806224320932](https://cdn.jsdelivr.net/gh/yzk656/image/202308062243032.png)

使用阻塞队列方式会导致打印语句会在锁的外边运行；在锁的外边可能就会有多个线程访问该打印语句，可能会导致输出多语句的情况

```java
package class14;

import java.util.concurrent.ArrayBlockingQueue;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 22:56
 */
public class ThreadDemo {
    public static void main(String[] args) {
        //声明阻塞队列对象
        ArrayBlockingQueue<String> blockingQueue = new ArrayBlockingQueue<>(1);

        //声明线程对象
        Cook cook = new Cook(blockingQueue);
        Foodie foodie = new Foodie(blockingQueue);

        //启动线程
        cook.start();
        foodie.start();

    }
}
```

```java
package class14;

import java.util.concurrent.ArrayBlockingQueue;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 22:56
 */
public class Cook extends Thread{
    ArrayBlockingQueue<String> arrayBlockingQueue;

    public Cook(ArrayBlockingQueue<String> arrayBlockingQueue) {
        this.arrayBlockingQueue = arrayBlockingQueue;
    }

    @Override
    public void run() {
        while (true){
            //向阻塞队列中添加面条
            try {
                arrayBlockingQueue.put("面条");
                System.out.println("厨师做了一碗面条");
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```

```java
package class14;

import java.util.concurrent.ArrayBlockingQueue;

/**
 * @Author: 杨振坤
 * @date: 2023/8/6 22:57
 */
public class Foodie extends Thread{
    ArrayBlockingQueue<String> arrayBlockingQueue;

    public Foodie(ArrayBlockingQueue<String> arrayBlockingQueue) {
        this.arrayBlockingQueue = arrayBlockingQueue;
    }

    @Override
    public void run() {
        while (true){
            //从阻塞队列中获取面条
            try {
                Object take = arrayBlockingQueue.take();
                System.out.println("吃货吃了一碗面条");
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```

![image-20230806231230443](https://cdn.jsdelivr.net/gh/yzk656/image/202308062312584.png)

其实是只有6个状态

![](https://cdn.jsdelivr.net/gh/yzk656/image/202308062315402.png)

### 线程栈

每个线程都有一个自己的栈，但是堆是共有的

> 内存图

![image-20230821144247676](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230821144247676.png)

### 线程池

![image-20230821173855585](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230821173855585.png)





![image-20230821190051504](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230821190051504.png)

![image-20230821190318456](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230821190318456.png)

### 自定义线程池

![](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230821193636191.png)

![image-20230821193510358](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230821193510358.png)

```java
package class25;

import java.util.concurrent.*;

public class ThreadPoolDemo {
    public static void main(String[] args) {
        //自定义线程池
        ThreadPoolExecutor poolExecutor = new ThreadPoolExecutor(
                3,//核心线程数量
                6,//最大线程数量
                60,//空闲线程存活时间
                TimeUnit.SECONDS,//时间单位
                new ArrayBlockingQueue<>(3),//任务队列
                Executors.defaultThreadFactory(),//创建线程工厂
                new ThreadPoolExecutor.AbortPolicy()//任务的拒绝策略
        );
    }
}
```





# 集合

## List接口

- 集合分两组：单列集合、双列集合

- Collection 接口有两个重要的子接口 List、Set【他们的实现子类都是单列集合】

- Map 接口的实现子类是双列集合，存放的K-V

  

- ![image-20220111224201462](https://gitee.com/demon_night/images/raw/master/imgs/202201291852522.png)

- ![image-20220111224649094](https://gitee.com/demon_night/images/raw/master/imgs/202201291852497.png)

### ArrayList实现类常用方法

```java
package Collection;

import java.util.ArrayList;
import java.util.Collection;
import java.util.List;

public class Collection_test1 {
    public static void main(String[] args) {
        List l=new ArrayList();
        //add。添加单个元素
        l.add("jack");
        l.add(1);
        l.add('c');
        l.add(false);
        System.out.println(l);//[jack, 1, c, false]

        //remove:删除指定元素
        l.remove("jack");
        //l.remove(1);
        //输入字符串可以删除集合里面与字符串相同的元素，如果为删除数字，会优先看作删除集合下标为该数字的元素
        System.out.println(l);//[1, c, false]

        //查看元素是否存在。contains,返回值为布尔型、
        System.out.println(l.contains(1));//true

        //获取元素个数
        System.out.println(l.size());//3

        //判断集合是否为空：isEmpty
        System.out.println(l.isEmpty());//false

        //清空集合：clear
        l.clear();
        System.out.println(l);//[]

        //addAll:添加多个元素
        ArrayList l1=new ArrayList();
        l1.add("红楼梦");
        l1.add("三国演义");
        l.addAll(l1);
        System.out.println(l);//[红楼梦, 三国演义]

        //查找多个元素是否都存在：containsAll,返回值为布尔型
        System.out.println(l.containsAll(l1));//true

        //删除多个元素 removeAll
        l.add("xX");
        l.removeAll(l1);
        System.out.println(l);//[xX]
    }
}
```

### 迭代器遍历：Iterator

```java
package Collection;

import java.util.ArrayList;
import java.util.*;
import java.util.Iterator;

public class Collection_test2 {
    public static void main(String[] args) {
        Collection col=new ArrayList();
        col.add(new Book("红楼梦","曹雪芹",10.1));
        col.add(new Book("西游记","吴承恩",8.1));
        col.add(new Book("水浒传","老曹",4.1));

        //使用Iterator遍历集合,要想实现Iterator接口，就要实现Iterator里面的方法
        Iterator iterator=col.iterator();
        //从索引-1开始
        while(iterator.hasNext()){
            Object i=iterator.next();
            System.out.println(i);
            //Book{name='红楼梦', actor='曹雪芹', price=10.1}
			//Book{name='西游记', actor='吴承恩', price=8.1}
			//Book{name='水浒传', actor='老曹', price=4.1}
        }
    }
}
class Book{
    private String name;
    private String actor;
    private double price;

    public Book(String name, String actor, double price) {
        this.name = name;
        this.actor = actor;
        this.price = price;
    }

    @Override
    public String toString() {
        return "Book{" +
                "name='" + name + '\'' +
                ", actor='" + actor + '\'' +
                ", price=" + price +
                '}';
    }
}
```

### 知识点

- 增强for循环不仅可以用在数组上，还可以用在集合上

- 增强for的底层还是迭代器

- ```java
          for(Object i:col){
              System.out.println(i);
          }
  ```

### 练习1

```java
package Collection;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class collection_test4 {
    public static void main(String[] args) {
        List l=new ArrayList();
        l.add(new Dog("大黄",3));
        l.add(new Dog("小黄",1));
        l.add(new Dog("大黑",7));
        Iterator i=l.iterator();
        
        while(i.hasNext()){
            Object a=i.next();
            System.out.println(a);
        }
        
        for(Object a:l){
            System.out.println(a);
        }
    }
}
class Dog{
    private String name;
    private int age;
    public Dog(String name,int age){
        this.name=name;
        this.age=age;
    }

    @Override
    public String toString() {
        return "Dog{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}

```

### 常用方法1

```java
        List l=new ArrayList();
        l.add("张三丰");
        l.add("贾宝玉");

        //指定索引添加元素
        l.add(1,"韩顺平");
        System.out.println(l);

        //addAll(int index,list),从索引中将集合添加进来
        List l1=new ArrayList();
        l1.add("jack");
        l1.add("marry");
        l.addAll(1,l1);//是把l1中所有元素加到l里面，如果，不带All，就会把l1看成一个对象，将其加到l里面
        //l.add(1,l1);//[张三丰, [jack, marry], 韩顺平, 贾宝玉]
        System.out.println(l);//[张三丰, jack, marry, 韩顺平, 贾宝玉]

        //get()：获取指定位置的元素
        System.out.println(l.get(1));//jack

        //indexOf():返回指定内容第一出现的索引
        //lastIndexOf:返回当前集合中最后一次出现该内容的下标
        System.out.println(l.indexOf("jack"));//1

        //remove()：删除指定索引位置的元素
        l.remove(0);
        System.out.println(l);//[jack, marry, 韩顺平, 贾宝玉]
        //删除集合中指定内容的元素
        l.remove("marry");
        System.out.println(l);//[jack, 韩顺平, 贾宝玉]

        //set()：替换
        l.set(0,"lll");
        System.out.println(l);//[lll, 韩顺平, 贾宝玉]

        //subList():返回1个子集合,前闭右开
        System.out.println(l.subList(0,1));//[lll]
```

> List接口【实现子类：ArrayList、LinkedList、vector】有三种遍历方式:增强for、迭代器、普通for循环

### 练习1[外部比较器]

> 要注意，当时Arrays类，用的外部比较器时，是需要对象，而List对象不需要引入对象,都是重写new comparator方法

```java
//按照价格进行排序
package List;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Comparator;
import java.util.List;

public class List_test3 {
    public static void main(String[] args) {
        List l1=new ArrayList();
        l1.add(new Book("红楼梦","曹雪芹",100));
        l1.add(new Book("西游记","吴承恩",10));
        l1.add(new Book("水浒传","施耐庵",9));
        l1.add(new Book("三国演义","罗贯中",80));
        l1.add(new Book("西游记","吴承恩",10));
        l1.sort(new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                Book a1=(Book) o1;
                Book a2=(Book) o2;
                double a1_price= a1.getPrice();
                double a2_price= a2.getPrice();
                if(a1_price>a2_price)  return 1;
                else if(a1_price<a2_price) return -1;
                else return 0;
            }
        });
        for(Object i:l1) System.out.println(i);
    }
}
class Book{
    private String name;
    private String actor;
    private double price;
    public Book(String name,String actor,double price){
        this.name=name;
        this.actor=actor;
        this.price=price;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    @Override
    public String toString() {
        return "名称：" + name + "   " +
                ", 价格：" + price + "    " +
                ", 作者：" + actor ;
    }
}
```

![image-20220116222146627](https://gitee.com/demon_night/images/raw/master/imgs/202201291852033.png)

### 练习2

```java
//ArrayList可以加入空值，可以加入多个
//线程不安全
List l1=new ArrayList();
l1.add(null);
l1.add("lili");
System.out.println(l1);//[null, lili]
```

### ArrayList知识点1

- ArrayList中维护了一个Object类型的数组：elementData

- 当创建ArrayList对象时，如果使用无参构造器，则初始化elementData容量为0，第一次添加，则扩容elementData为10，如需再次扩容，则扩容elementData为1。5倍

- 如果使用指定大小的构造器，则初始化elementData容量为指定大小，如果需要扩容，则直接扩容elementData为1.5倍d

- > 使用无参构造器

  ![image-20220117123626648](https://gitee.com/demon_night/images/raw/master/imgs/202201291852288.png)

  ![image-20220117123704824](https://gitee.com/demon_night/images/raw/master/imgs/202201291852231.png)

- > 对于基本数据类型会将其进行装箱

- > 扩容机制：
  >
  > ![](https://gitee.com/demon_night/images/raw/master/imgs/202201291852472.png)
  >
  > ![image-20220117130833506](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220117130833506.png)

  > 使用有参构造器时

  - 如果该数大于0，就创建了1个指定大小的elementData数组
  - 如果是有参构造器，第一次扩容就按照elementData的1。5倍扩容，整个执行流程和无参构造器流程10之后相同的

  ![image-20220117133503874](https://gitee.com/demon_night/images/raw/master/imgs/202201291852776.png)

### ArrayList1

* 增加
* add(num)
* add(index,num)
* addAll(list)
* addAll(index,list)
* 
* 删除
* remove(index)---用下标
* remove(new Integer(数据内容))
* removeAll(list)
* retainAll(list)
* clear()
* 
* 修改
* list.set(index,修改后的内容)
* 
* 下查询
* size()
* get()
* indexOf(查找的内容)
* contains(查找的内容)//返回值为boolean类型
* isEmpty()//判断是否为空
* 
* 循环
* iterator
* foreach()-------list.foreach(System.out::println)

```java
public class generic01 {
    public static void main(String args[]) {
        //<Integer>两边都必须写，限制只能存入整型
        ArrayList<Integer> list=new ArrayList<Integer>();
        list.add(78);
        list.add(10);
        //list.add(true);

        //添加集合
        ArrayList<Integer> list2=new ArrayList<Integer>();
        list2.add(10);
        list2.add(20);
        list2.add(30);

//        //查询
//        System.out.println(list2.contains(10));
//        System.out.print(list2.indexOf(10));
//        System.out.print(list2.isEmpty());

//        //将list2--->list
//        list.addAll(list2);
//        //Lambda+流式编程
//        //System.out.println(list);//输出链表里面的内容，如果想输出单个内容可选择调用get（）方法
//        list.forEach(System.out::println);
//        
//        //添加到特定位置
//        list2.addAll(2,list);//只要是添加链表中的所有内容就用addAll（）方法
//        System.out.println(list2);
//        System.out.println("--------");
//        
//        //删除list中含有list2中的元素
//        list.removeAll(list2);
//        System.out.println("----"+list);

//        //保留两者共有的数据
//        list.retainAll(list2);
//        System.out.print(list);

//        //删除
//        list2.remove(0);
//        System.out.println(list2);
//        list2.remove(new Integer(10));
//        list2.forEach(System.out::print);
//        //删除所有元素
//        list2.clear();
//        System.out.print(list2);

//        //修改
//        list2.set(1,99);
//        list2.forEach(System.out::println);

//        int num=list.get(0);
//        System.out.println(num);
//        
//        for(int i:list) {//如何调用方法则选用Integer类，相反只想输出数据，也可以定义成int型
//            System.out.println(i);
//        }
//        
        Iterator<Integer> i=list.iterator();//我们只给ArrayList加了<Integer>，所以使用迭代器这个类我们也要添加<Integer>
        while(i.hasNext()) {//方法里面的变量不能和局部变量相同
            int num1=i.next();
            System.out.println(num1);
        }
    }
}
```

### ArrayList2

* 为了解决需要强制转换的问题
* 因此引入泛型generic
* java.lang.ClassCastException----
* 数组中既可以放基本数据类型也可以放引用数据类型
* 集合中只可以放引用数据类型，不能放基本数据类型

```java
public class test {
    public static void main(String args[]) {
        ArrayList list =new ArrayList();

        //向末尾添加
        list.add(78);//自动装箱
        list.add(89);
        list.add(56);
        list.add(89);

        //添加一个节点
        list.add(2,100);
        ArrayList list2=new ArrayList();
        list2.add(1);

        //获取指定索引的元素
        int num=(int)list.get(1);
        System.out.println(num);

        //元素的数量
        System.out.println(list.size());

        //遍历元素
        System.out.println("-----");
        System.out.println(list.toString());

        //逐行输出
        for(int i=0;i<list.size();i++) {
            int num1=(int)list.get(i);
            System.out.println(num1);
        }

        //for----each循环   for(元素类型t 元素变量x : 遍历对象obj){
        for(Object num2:list) {//由于Object是父类，所以List的数据类型可以用Object来代替
            System.out.println(num2);
        }

        System.out.println("---------");

        //迭代器Iterator
        Iterator it=list.iterator();//迭代的游标最开始为-1，因此返回it.next()就是下一个，也就是第一个元素了
        while(it.hasNext()){//是否还有元素，有：boolean
            int num3=(int) it.next();//由于在set中，存的是对象，所以，it.next（）获取的就是这个对象，因此需要进行强转
            System.out.println(num3);
        }

        //Lambda表达式+流式编程
        list.forEach((i)->System.out.println(i));
        list.forEach(System.out::println);
    }
}
```

### Vector知识点

- Vector底层也是1个对象数组：elementData[]
- Vector是线程同步的，即线程安全
- 在开发时，需要线程同步时，考虑使用Vector

> Vector与ArrayList的比较

![image-20220118164500832](https://gitee.com/demon_night/images/raw/master/imgs/202201291852687.png)

```java
        //对于调用无参构造器，会将elementData数组大小默认长度为10
        //扩容时，会默认两倍两倍的扩
        //对于有参构造器，其elementData数组的长度为参数的大小
        //扩容时，会以自己定的长度两倍两倍的扩容
        Vector v=new Vector();
        for(int i=0;i<10;i++){
            v.add(i);
        }
```

### LinkedList知识点

- LinkedList底层实现了双向链表、双端队列
- 可以添加任意元素(可以重复)，包括null
- 线程不安全，没有实现同步
- LinkedList中维护了两个属性first、last分别指向首节点和尾节点
- 每个节点(Node对象)，里面维护了prev【指向前一个】、next【指向后一个节点】、item三个属性
- LinkedList的元素不是存储在数组里面，因此添加删除的效率较高

#### LinkedList常用方法

```java
        LinkedList l1=new LinkedList();
        l1.add(1);
        l1.add(2);
        l1.add(3);

        //删除节点：remove
        //默认删除第一个
       //l1.remove();//[2, 3]
        //删除指定索引位置的元素
        //l1.remove(2);//[1, 2]
        System.out.println(l1);

        //修改节点set()
        l1.set(1,10);//[1, 10, 3]
        System.out.println(l1);

        //得到某个节点对象
        System.out.println(l1.get(1));//10

        //遍历
        //因为实现了List接口，因此可以使用迭代器进行遍历
        Iterator i1=l1.iterator();
        while(i1.hasNext()){
            System.out.print(i1.next()+" ");//1 10 3
        }
        System.out.println();
        //还可以使用增强for循环
        for(Object i:l1) System.out.print(i+" ");//1 10 3
```



### LinkedList类

* LinkedList
* 采用双向存储链表
* 缺点：遍历和随机访问元素效率低下
* 优点：插入、删除效率比较高（前提是必须低效率查询才行）
* 可以作为线性表、栈、队列来使用 

```java
public class linkdelist {
    public static void main(String[] args) {
        int[] a = { 1, 2, 1, 4 };
        LinkedList<Integer> list = new LinkedList<Integer>();
        // System.out.println(list.size());
        // 将数组里面的内容赋值到List集合中
        for (int i = 0; i < a.length; i++) {
            list.add(i, a[i]);
        }
        list.add(100);
        list.add(90);
        list.add(100);
        int[] indexs = new int[a.length];

        list.addFirst(60);
        list.addLast(100);
        list.push(1000);
        System.out.println(list.contains(30));

        // 寻找数组中指定元素的所有下标位置
        int count = finAllIndex(a, indexs, 1);
        for (int i = 0; i < count; i++) {
            System.out.println(indexs[i]);
        }

        // System.out.println(list.lastIndexOf(100));
        // System.out.print(list);
    }

    // 寻找下表的方法
    private static int finAllIndex(int[] a, int[] indexs, int num) {
        int count = 0;
        for (int i = 0; i < a.length; i++) {
            if (num == a[i]) {
                indexs[count++] = i;
            }
        }
        return count;
    }
}
```

### 队列1

* vector已经被ArrayList替代,Stack也不建议使用
* Deque接口：双端队列
* ArrayDeque：底层使用数组
* LinkedList：底层使用双端链表
* push():入栈
* pop():出栈
* peek()：查看栈顶元素
* 
* 队列接口：Queue
* ArrayDeque：底层使用数组
* LinkedList：底层使用双端链表

```java
public class testLinkedList {
    public static void main(String[] args) {
        Stack<String> stack=new Stack<String>();

        Deque deque=new LinkedList();
        deque.push("盘子1");
        deque.push("盘子二");
        deque.push("盘子三");

        System.out.println(deque.size());
//        //查看栈顶元素
//        System.out.println(deque.peek());
//        //出栈--->删除栈顶元素
        System.out.println(deque.pop());
        System.out.println(deque.size());
        System.out.println(deque.peek());
    }
}
```

### 队列2

> offer与add的区别

一些队列有大小限制，如果想在一个满的队列加入一个新项，多余的项就会被拒绝，这时offer方法就可以起作用了，它不是对调用 add() 方法抛出一个 unchecked 异常，而只是得到由 offer() 返回的 false。 

> **poll，remove 区别：**

remove() 和 poll() 方法都是从队列中删除第一个元素。remove() 的行为与 Collection 接口的版本相似， 但是新的 poll() 方法在用空集合调用时不是抛出异常，只是返回 null。因此新的方法更适合容易出现异常条件的情况。l;

> **peek，element区别：**

element() 和 peek() 用于在队列的头部查询元素。与 remove() 方法类似，在队列为空时， element() 抛出一个异常，而 peek() 返回 null。

```java
        Queue q1=new LinkedList();
        q1.offer("a");
        q1.offer("b");
        q1.offer("c");
        //输出,同样可以使用增强for循环、Iterator
        System.out.println(q1);//[a, b, c]

        //poll():返回第一个元素，并在队列中删除
        System.out.println(q1.poll());//a
        System.out.println(q1);//[b, c]

        //element():返回第一个元素
        System.out.println(q1.element());//b
        System.out.println(q1.peek());//b
```



### List注意事项

1、List是一个接口，而ListArray是一个类。
2、ListArray继承并实现了List。
3、所以List不能被构造，但可以向上面那样为List创建一个引用，而ListArray就可以被构造。
List list;     //正确   list=null;
List list=new List();    //   是错误的用法
List list = new ArrayList();这句创建了一个ArrayList的对象后把上溯到了List。此时它是一个List对象了，有些ArrayList有但是List没有的属性和方法，它就不能再用了。
4、而ArrayList list=new ArrayList();创建一对象则保留了ArrayList的所有属性。

5. of（）方法只是Map，List，Set这三个借口的静态方法，其父类接口和子类实现并没有这类方法，比如HashSet，ArrayList等待；这是一个例子：

```java
import java.util.*;
public class TestList{
    public static void main(String[] args){
        List list = new ArrayList();
        ArrayList arrayList = new ArrayList();
        list.trimToSize(); //错误，没有该方法。
        arrayList.trimToSize();   //ArrayList里有该方法。
```

## Set接口

### 知识点

- 无序(添加和取出顺序不一样)，没有索引
- 不允许重复元素，所以最多包含一个null
- 和List接口一样，Set接口也是Collection的子接口，因此常用方法和Collection接口一样
- 对于Set接口的遍历方式：同Collection接口一样，因为Set接口是Collection的子接口，可以使用迭代器、增强for、【不能通过索引的方式来获取】

### 常用方法

```java
        //Set接口实现类的对象(Set接口对象)，不能存放重复元素，只能存放1个null
        //Set接口对象存放数据是无序的
        //虽然添加顺序和取出顺序不一样，但是，每次取出的结果都是固定的
        Set s1=new HashSet();
        s1.add("jack");
        s1.add("merry");
        s1.add("LILI");
        s1.add("jack");
        s1.add(null);
        s1.add(null);
        System.out.println(s1);//[null, LILI, jack, merry]
        //遍历1.迭代器
        Iterator iterator=s1.iterator();
        while(iterator.hasNext()){
            System.out.print(iterator.next()+" ");//null LILI jack merry
        }
        System.out.println();
        //遍历2.增强for循环
        for(Object i:s1) System.out.print(i+" ");//null LILI jack merry
```



### HashSet类

### 知识点1

* HashSet底层是HashMap
* ![image-20220119190023507](https://gitee.com/demon_night/images/raw/master/imgs/202201291853776.png)
* 添加1个元素时会得到一个Hash值，会将其转成索引
* 根据索引去table数组里找相应的索引，看这个索引位置是否已经存放元素，如果没有就直接加入，如果有元素，就调用equals方法进行比较，如果相同，就放弃添加，如果不相同，则添加到最后
* 在JDK8中如果table数组长度大于64，并且链表长度>=8时就会进行树化(转换成红黑树)
* 如果链表达到8，但是table数组没有达到64，就会对table数组进行扩容

```java
public class hashset1 {
    public static void main(String[] args) {
        Set<String> s=new HashSet<String>();
        s.add("HTML");
        s.add("CSS");
        s.add("XML");
        s.add("Web");
        s.add("JavaSE");
        s.add("HTML");//重新更新数据，把数据放在当前的位置
        System.out.println(s);
        System.out.println(s.size());
        //s.add(null);//默认在第一个位置添加
        System.out.print(s);
    }
}
```

### TreeSet类【适合排序】

```java
package Set;
import java.util.*;
public class TreeSet_test {
    public static void main(String[] args) {
        //1. 当我们使用无参构造器，创建TreeSet时，仍然是无序的
        //2. 使用TreeSet提供的构造器，可以传入一个比较器(匿名内部类)并指定排序规则
        //TreeSet treeSet=new TreeSet();
        /*
            1. 构造器把传入的比较器对象，赋给了treeSet底层TreeMap的属性this.comparator
            2. 在add元素时，在底层会执行到匿名内部类对象

         */
        TreeSet treeSet=new TreeSet(new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                //调用字符串的CompareTo方法
                //从小到大
                //return ((String)o1).compareTo((String)o2);
                //按照长度从小到大排列
                //添加顺序也是按照长度，如果长度相等即使内容不同也添加不进去
                return ((String)o1).length()-((String)o2).length();
            }
        });
        treeSet.add("jack");
        treeSet.add("tom");
        treeSet.add("sp");
        treeSet.add("a");
        System.out.println(treeSet);//[a, jack, sp, tom]
    }
}
```





#### HashSet注意点

```java
public class HashSet_test1 {
    public static void main(String[] args) {
        Set s1=new HashSet();
        //可以存放1个null
        //add方法的返回值是布尔型
        s1.add(null);
        s1.add(null);
        System.out.println(s1);//[null]

        s1=new HashSet();
        s1.add("lucy");
        s1.add("lucy");
        //对于两个new出来的对象，可以认为不是同一个，因此可以添加进去
        s1.add(new Dog("tom"));
        s1.add(new Dog("tom"));
        System.out.println(s1);//[Dog{name='tom'}, lucy, Dog{name='tom'}]

        s1.add(new String("yzk"));//能添加进去
        s1.add(new String("yzk"));//不能添加进去
        System.out.println(s1);//[Dog{name='tom'}, yzk, lucy, Dog{name='tom'}]
    }
}
class Dog{
    private String name;
    public Dog(String name){
        this.name=name;
    }

    @Override
    public String toString() {
        return "Dog{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

> HashSet的add()方法详解

```java
package Set;

import java.util.HashSet;
import java.util.Set;

public class HashSet_test2 {
    public static void main(String[] args) {
        Set s1=new HashSet();
        s1.add("java");
        s1.add("php");
        s1.add("java");
        System.out.println(s1);
        //流程
        /**
         * 1. public HashSet() {
         *      map = new HashMap<>();
         *    }
         
         * 2.     public boolean add(E e) {
         *         return map.put(e, PRESENT)==null;//PRESENT:由于hashset用不到value值，但还必须使用HashSet结构，因此统一使用PRESENT作为Value
         *     }
         
         * 3.    public V put(K key, V value) {//key:"java"  value:PRESENT
         *         return putVal(hash(key), key, value, false, true);
         *     }
         
         * 3*.    static final int hash(Object key) {//哈希值是通过hashcode进行转换得来的
         *         int h;
         *         return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);//算法：可以让不同的key得到不同的hash值
         *     }
         
         * 4.final V putVal(int hash, K key, V value, boolean onlyIfAbsent,//核心代码、
         *                    boolean evict) {
         
         *         Node<K,V>[] tab; Node<K,V> p; int n, i;//辅助变量
         
         *         //table就是HashMap的一个数组，类型为Node【】
         *         //if语句表示如果当前table是null或者大小为0，就进行第一次扩容，长度为16个空间
         *         if ((tab = table) == null || (n = tab.length) == 0)
         *             n = (tab = resize()).length;
         
         *         //根据key，得到hash值去计算key应该存放在table表的哪个索引位置，并把该位置的对象，赋给P
         *         //判断P是否为null，如果为空，表示还没有存放元素，就创建1个Node，就放在tab[i] = newNode(hash, key, value, null);
         *         if ((p = tab[i = (n - 1) & hash]) == null)
         *             tab[i] = newNode(hash, key, value, null);
         
         *         else {
         *             Node<K,V> e; K k;
         
         *             //如果当前索引位置对应的链表的第一个元素和准备添加的key的hash值相同，
         *             //并且满足下面两个条件之一：
         *             //1. 准备加入的key和p指向的Node节点的key时同一个对象
         *             //2. p指向的Node结点的key的equals()和准备加入的key比较后相同
         			   //   注意：equals方法由程序员来重写，比不一定是比较值
         *             //就不能加入
         *             if (p.hash == hash &&
         *                 ((k = p.key) == key || (key != null && key.equals(k))))
         *                 e = p;
         
         *             //再判断 p 是不是一颗红黑树
         *             //如果是红黑树就调用putTreeVal进行添加元素2
         *             else if (p instanceof TreeNode)
         *                 e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
         *             else {
         
         *             //如果table对应的索引位置，已经是一个链表，就使用for循环比较
         *             //1. 依次和该链表的每一个元素比较后都不相同，则加入到该链表的最后
         *             //   注意：在把元素添加到链表后，就立即判断该链表是否有8个结点，
         *             //   如果达到就调用treeifyBin(tab, hash);对当前链表进行树化(红黑树)
         *             //   注意：在进行树化时，还要进行一个判断，如果该table数组的大小小于64
         *             //       如果小于64，必须要先对table数组扩容，只有链表长度大于8，数组长度大于64时才进行树化
         *             //2. 依次和该链表的每一个元素比较过程中，如果有相同的情况就直接break
         *                 for (int binCount = 0; ; ++binCount) {
         *                     if ((e = p.next) == null) {
         *                         p.next = newNode(hash, key, value, null);
         *                         if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
         *                             treeifyBin(tab, hash);
         *                         break;
         *                     }
         *                     if (e.hash == hash &&
         *                         ((k = e.key) == key || (key != null && key.equals(k))))
         *                         break;
         *                     p = e;
         *                 }
         *             }
         *             if (e != null) { // existing mapping for key
         *                 V oldValue = e.value;
         *                 if (!onlyIfAbsent || oldValue == null)
         *                     e.value = value;
         *                 afterNodeAccess(e);
         *                 return oldValue;
         *             }
         *         }
         
         *         ++modCount;
         
         *         //如果当前长度大于16*0.75，就在进行扩容
         *         if (++size > threshold)
         *             resize();
         *         afterNodeInsertion(evict);
         
         *         return null;//返回null代表添加成功【代表进行第一次添加】
         *     }
         */
    }
}
```

### 知识点2

- HashSet底层是HashMap，第一次添加时，table数组扩容到16，临界值：16*加载因子(0.75)=12

- 数组table使用到了临界值12就会扩容到16*2=32，新的临界值：32乘0.75=24，依次类推

- 在Java8中，如果一条链表的元素个数达到8，并且table数组长度大小为64，就进行树化，`否则仍采用数组扩容机制`

- `当链表长度为9时，table数组就已经从16扩容到32，在添加1个，链表长度为10，table长度已经扩容为64，下一次添加链表长度为11，table长度为64【不再进行扩容】，此时哈希表树化`【你看到的结果是前一步已经做好的】

  ```java
  package Set;
  
  import java.util.HashSet;
  import java.util.Objects;
  
  public class HashSet_test3 {
      public static void main(String[] args) {
          HashSet h1=new HashSet();
          //当链表长度为9时，table数组就会从16扩容到32，在添加1个，链表长度为10，table长度扩容为64，下一次添加链表长度为11，table长度为64【不再进行扩容】，此时哈希表树化
          for (int i=0;i<11;i++){
              h1.add(new A(i));
          }
      }
  }
  class A{
      private int a;
      public A(int a){
          this.a=a;
      }
  
      @Override//返回相同的hash值
      public int hashCode() {
          return 100;
      }
  }
  
  ```

### 知识点3

```java
package Set;

import java.util.HashSet;
import java.util.Objects;
import java.util.Set;

public class HashSet_test4 {
    public static void main(String[] args) {
        Set s1=new HashSet();
        //结点数只要达到了12，就会扩容,因为用的++size，所以达到12个的时候就会扩容，结果在下一次添加就可以看到
        for(int i=0;i<7;i++){//在table数组上的某一条链表添加7个C对象
            s1.add(new C(i));
        }
        for(int i=0;i<7;i++){//在table数组上的某一条链表添加7个D对象
            s1.add(new D(i));
        }
    }
}
class C{
    private int a;
    public C(int a){
        this.a=a;
    }

    @Override
    public int hashCode() {
        return 100;
    }
}
class D {
    private int a;
    public D(int a){
        this.a=a;
    }

    @Override
    public int hashCode() {
        return 200;
    }
}
```

![image-20220120170050848](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220120170050848.png)

### 为什么重写equals和hashcode方法

> 因为默认的equals方法是Object的方法，比较的是内存地址；而默认的hashcode方法返回的是对象的内存地址转换成的一个整数，实际上指的的也是内存，两个方法可以理解为比较的都是内存地址
>
> new出来的两个对象可能添加的内容一样，但是内存地址不同，就会被认为两个不同的对象，但是我们想要对相同内容的对象添加一份，因此需要我们重写hashcode、equals方法

![image-20220120172937623](https://gitee.com/demon_night/images/raw/master/imgs/202201291904833.png)

### 知识点4

- Hashmap是通过hashcode来确定元素的下标的，具体的代码如下； int hash = hash（key.hashcode()）;  通过算出来的hash值，还有hashmap表的长度，可以确定元素在hashmap表中的下标，但是这种hash算法过于简单，会导致很多冲突发生，因为不同的key可以算出相同的hashcode，所以每个下标对对应的链表位置上会有很多的Entry对象

- 对于两个对象，Java要求如下：

  equals()相等，hashcode()一定相等；

  equals()不等，hashcode()可能相等，也可能不等;

  hashcode()不等，一定能推出equals()也不等；

  hashcode()相等，equals()可能相等，也可能不等。

- Hashmap是通过hashcode来确定元素的下标的，具体的代码如下； int hash = hash（key.hashcode()）;  通过算出来的hash值，还有hashmap表的长度，可以确定元素在hashmap表中的下标，但是这种hash算法过于简单，会导致很多冲突发生，因为不同的key可以算出相同的hashcode，所以每个下标对对应的链表位置上会有很多的Entry对象

- 如果不重写hashcode和equals方法的话，放入相同的key时（特殊情况下），就不知道取哪一个。

### 重写hashcode、equals练习【遇到与地址有关的就要做对应的重写】

```java
package Set;

import java.util.HashSet;
import java.util.Objects;
import java.util.Set;

public class HashSet_test6 {
    public static void main(String[] args) {
        Set s1=new HashSet();
        s1.add(new Employee1("小王","男",new MyDate(2000,1,14)));
        s1.add(new Employee1("小刘","男",new MyDate(2001,9,14)));
        s1.add(new Employee1("小王","女",new MyDate(2000,1,14)));
        System.out.println(s1);
    }
}
class Employee1{
    private String name;
    private String sal;
    private MyDate birthday;
    public Employee1(String name, String sal, MyDate birthday){
        this.name=name;
        this.sal=sal;
        this.birthday=birthday;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Employee1 employee1 = (Employee1) o;
        return name.equals(employee1.name) && birthday.equals(employee1.birthday);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, birthday);
    }

    @Override
    public String toString() {
        return "Employee1{" +
                "name='" + name + '\'' +
                ", sal='" + sal + '\'' +
                ", birthday=" + birthday +
                '}';
    }
}
class MyDate{
    private int year;
    private int month;
    private int day;
    public MyDate(int year,int month,int day){
        this.year=year;
        this.month=month;
        this.day=day;
    }

    @Override
    public String toString() {
        return "MyDate{" +
                "year=" + year +
                ", month=" + month +
                ", day=" + day +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        MyDate myDate = (MyDate) o;
        return year == myDate.year && month == myDate.month && day == myDate.day;
    }

    @Override
    public int hashCode() {
        return Objects.hash(year, month, day);
    }
}
```





### 例：数组转换成Set

* 声名一个数组
* int[] a=new int[5];
* ArrayList是一个可以动态增长的Object数组，StringBuilder是一个长度可以动态增长的char数组
* 在jdk1.7ArrayList默认长度为10
* 在jdk1.8中默认数组为0，第一次添加元素，容量不足就要进行扩容
* 因此我们也可以指定数组的长度：ArrayList list=new ArrayList(100)//数组长度为100
* 每次扩容为50%，如果扩容50%还不足，就扩容为能容纳新增元素的最小数量
* 接口可以一个方法都不提供，例：RandomAcess，Cloneable，Java.io.serializble;
* 格式化代码：ctrl+shift+F
* list.contains(index):查看数组下标的范围

```java
public class 数组转换为set {
    public static void main(String[] args) {
        int[] a = { 1, 2, 1, 4 };
        ArrayList<Integer> list = new ArrayList<Integer>();
        // System.out.println(list.size());
        // 将数组里面的内容赋值到List集合中
        for (int i = 0; i < a.length; i++) {
            list.add(i, a[i]);
        }
        list.add(100);
        list.add(90);
        list.add(100);
        int[] indexs = new int[a.length];


        System.out.println(list.contains(30));

        // 寻找数组中指定元素的所有下标位置
        int count = finAllIndex(a, indexs, 1);
        for (int i = 0; i < count; i++) {
            System.out.println(indexs[i]);
        }

        // System.out.println(list.lastIndexOf(100));
        // System.out.print(list);
    }

    // 寻找下表的方法
    private static int finAllIndex(int[] a, int[] indexs, int num) {
        int count = 0;
        for (int i = 0; i < a.length; i++) {
            if (num == a[i]) {
                indexs[count++] = i;
            }
        }
        return count;
    }
}
```

### LinkedHashSet类

* 与HashSet【哈希表】所不同的是，LinkedHashSet存取的内容有顺序【哈希表+链表】
* TreeSet：有序(自然顺序)，唯一【红黑树(二叉树、二叉查找树、二叉平衡树)】】
* set是无序的，相比collection没有增加任何方法，List相比Collection增加和索引相关的方法
* get(i) remove(i) add(index,num) remove(index,num)

```java
public class testLinkedhashset {
    public static void main(String[] args) {
        //LinkedHashSet：按照输入的先后顺序进行排序
        //Set<String> set=new LinkedHashSet<String>();

        //TreeSet：按照字母的Ascll码进行比较大小
        Set<String> set=new TreeSet<String>();

        set.add("1111");
        set.add("aaaa");
        set.add("dddd");
        set.add("aaaa");
        set.add("web");
        set.add("CSS");
        set.add("HTML");
        set.add("JAVASE");

//        //一行输出
//        System.out.println(set);
//        
//        //逐行输出
//        for(String num:set){
//            System.out.println(num);
//        }

        //迭代器逐行输出
//        Iterator<String> it=set.iterator();
//        //注：是hasNext()检查序列中是否还有元素
//        while(it.hasNext()) {
//            //因为迭代的游标最初为-1
//            String num=it.next();
//            System.out.println(num);
//        }

        //Lambda表达式+流式编程   逐行输出
        set.forEach(System.out::println);

    }
}
```

### LinkedHashSet知识点

![](https://gitee.com/demon_night/images/raw/master/imgs/202201291904432.png)

- LinkedHashSet是HashSet的子类
- LinkedHashSet底层是一个LinkedHashMap，底层维护了一个数组+双向链表【使得不同索引之间也能有有了联系】
- LinkedHashSet根据元素的hashcode值来决定元素的的存储位置，同时使用链表维护元素的次序，这使得元素看起来是以插入顺序保存的
- LinkedHashSet不允许添加重复元素
- 在每一个节点都有before和after属性，这样就可以形成双向链表
- 在添加一个元素时，先求hash值，再求索引，确定该元素在table中的位置，然后将添加的元素加入到双向链表，如果已经存在，就不添加
- `能够让我们在遍历的时候确保和插入的顺序一致`

### LinkedHashSet的equals、hashCode的重写

```java
package Set;

import java.util.LinkedHashSet;
import java.util.Objects;
import java.util.Set;

public class LinkedHashSet_test2 {
    public static void main(String[] args) {
        Set s1=new LinkedHashSet();
        s1.add(new car("宝马",199999));
        s1.add(new car("小马",999999));
        s1.add(new car("宝马",199999));
        System.out.println(s1);
    }
}
class car{
    private String name;
    private double price;
    public car(String name,double price){
        this.name=name;
        this.price=price;
    }

    @Override
    public boolean equals(Object o){
        if(this==o) return true;
        if(o==null||getClass()!=getClass()) return false;
        car car=(car) o;
        return Double.compare(car.price,price)==0&&Objects.equals(name,car.name);
    }

    @Override
    public int hashCode(){
        return Objects.hash(name,price);
    }
    @Override
    public String toString() {
        return "car{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
}
```

### TreeSet



### 例1【知识点】

* 特点：无序，唯一
* 
* HashSet
* 采用Hashtable哈希表存储结构
* 优点：添加速度快，查询速度快，删除速度快
* 缺点：无序
* 
* LinkedHashSet
* 采用哈希表存储结构，同时使用链表维护次序
* 有序（添加顺序）
* 
* TreeSet
* 采用二叉树（红黑树）的存储方式【红黑树：左分支小于根节点，右分支大于根节点】
* 优点：有序 查询速度比List快（按照内容查询）
* 缺点：查询速度没有HashSet快

```java
public class testset01 {
    public static void main(String[] args) {
        Set<String> set=new HashSet<String>();

        set.add("JavaSE");
        set.add("MySQL");
        set.add("HTML");
        set.add("JavaSE");
        set.add("Web");
        set.add("MySQL");
        set.add(null);

        System.out.println(set.size());
        System.out.println(set);
    }
}
```

### 例2【Student】

> Student1类

```java
public class student1 implements Comparable<student1>{
    private String name;
    private String sex;
    private int age;
    private double score;

    public student1() {
    }
    public student1(String name,String sex,int age,double score) {
        this.name=name;
        this.sex=sex;
        this.age=age;
        this.score=score;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getSex() {
        return sex;
    }

    public void setSex(String sex) {
        this.sex = sex;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public double getScore() {
        return score;
    }

    public void setScore(double score) {
        this.score = score;
    }

    @Override
    public int hashCode() {
        return Objects.hash(age, name, score, sex);
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        student1 other = (student1) obj;
        return age == other.age && Objects.equals(name, other.name)
                && Double.doubleToLongBits(score) == Double.doubleToLongBits(other.score)
                && Objects.equals(sex, other.sex);
    }

    @Override
    public String toString() {
        return "student1 [name=" + name + ", sex=" + sex + ", age=" + age + ", score=" + score + "]";
    }

    @Override
    public int compareTo(student1 o) {
        // TODO Auto-generated method stub
        return this.name.compareTo(o.name);
    }
}
```

> 外部比较器

```java
public class stuScoreNameDescomparator implements Comparator<student1>{

    @Override
    public int compare(student1 o1, student1 o2) {
        if(o1.getScore()>o2.getScore()) {
            return 1;
        }
        else if(o1.getScore()<o2.getScore()) {
            return -1;
        }
        else {
            //return 0;
            //如果两者相等，就比较姓名
            return o1.getName().compareTo(o2.getName());
            //若按照姓名降序排序，只需要在返回值的结果添加个”负号“即可
        }

        //此处不能使用强转，因为如果98.5-98=0.5-->0，会导致结果判断错误
        //return (int)(o1.getScore()-o2.getScore());    
    }
}
```

> 主函数

* 1:为什么HsahSet是唯一的，但是存储<student1>不唯一？
* 2:为什么TreeSet存储的String是有序的，但是存储<student1>却报异常
* Exception in thread "main" java.lang.ClassCastException:
* class Student.student1 cannot be cast to class java.lang.Comparable (Student.student1 is in unnamed module of loader 'app'; java.lang.Comparable is in module java.base of loader 'bootstrap')
* 
* 原因：String是系统类，应该已经做过了某些操作，studen1为自定义类
* 解决问题1：重写equals方法和hashCode方法
* 解决问题2：由于缺少comparable，所以要实现一个接口，实现compareTo方法，其中的返回值需要改为：return this.compareTo(o.name)//以名字进行比较
* 由于返回的compareTo的返回值是int型，还需要强转，所以我们可以直接添加泛型<student1>，就解决了需要强转的问题
* [制定规则]：比较：对于String类型：this.name.compareTo(other.name)//other为类
* 对于int类型[可以直接进行相减]：this.age-other.age
* 原因：返回值为int类型
* 
* 内部类：在类里面声名一个对象在外边添加上”大括号“+“，”
* 由于该类默认为Object类型的参数，而我们进行比较的类是“student1”类型的，因此我们需要将其定义成泛型<student1>

```java
public class testStudent{
    public static void main(String[] args) {

        //Set<student1> set=new HashSet<student1>();

        //Set<student1> set=new LinkedHashSet<student1>();

        //添加个外部比较器，达到的效果：使用外部比较器【因为外部比较器优先】
        //Comparator comp=new stuScoreNameDescomparator();

        //由于我们可能只使用一次这个自定义比较器，因此我们可以将其定义成内部类
        //内部类
//        Comparator comp=new Comparator<student1>() {
//
//            @Override
//            public int compare(student1 o1, student1 o2) {
//                if(o1.getScore()>o2.getScore()) {
//                    return 1;
//                }
//                else if(o1.getScore()<o2.getScore()) {
//                    return -1;
//                }
//                else {
//                    //return 0;
//                    //如果两者相等，就比较姓名
//                    return o1.getName().compareTo(o2.getName());
//                    //若按照姓名降序排序，只需要在返回值的结果添加个”负号“即可
//                }
//            }
//        };
//        
//        //外部比较器以参数的形式传进来
//        Set<student1> set=new TreeSet<student1>(comp);

//        //使用Lambda表达式，将其放在创建对象的参数里面
//        //注意：(参与比较的对象1，参与比较的对象2)->{比较规则}
//        Set<student1> set=new TreeSet<student1>((o1,o2)->{if(o1.getScore()>o2.getScore()) {
//            return 1;
//        }
//        else if(o1.getScore()<o2.getScore()) {
//            return -1;
//        }
//        else {
//            //return 0;
//            //如果两者相等，就比较姓名
//            return o1.getName().compareTo(o2.getName());
//            //若按照姓名降序排序，只需要在返回值的结果添加个”负号“即可
//        }});

        //lambda简写
        //数字类型不能用compareTo，nt跟int的比较不能用compareTo方法
        //直接用大于(>) 小于(<) 或者 等于(==) 不等于(!=)来比较即可
        //Set<student1> set=new TreeSet<student1>((stu1,stu2)->{return stu1.getName().compareTo(stu2.getName());});

        //Lambda表达式还可再简写
        Set<student1> set=new TreeSet<student1>((stu1,stu2)->stu1.getName().compareTo(stu2.getName()));

        student1 s1=new student1("zhangsan","男",23,90);
        student1 s2=new student1("lisi","女",21,91);
        student1 s3=new student1("wangwu","女",24,90);
        student1 s4=new student1("zhangsan","男",23,90);

        set.add(s1);
        set.add(s2);
        set.add(s3);
        set.add(s4);

        System.out.println(set.size());
//        //Lambda表达式
//        //set.forEach(System.out::println);
//        //已将将泛型定义为<student1>类型
        for(student1 stu:set) {
            System.out.println(stu);
        }
    }
}
```

## Map接口

### 知识点1

- Map与Collection并列存在，用于保存具有映射关系的数据：key-value(双列元素)
- Map中的key和Value可以是任何引用数据类型，会封装在HashMap$Node对象中
- Map中的key不允许重复
- Map中的key可以为null，value也可以为空，但是key为空只能有1个，而value为空可以有多个
- key和Value之间是单向一对一关系，即通过指定的key总能找到对应的Value
- 通过get方法，传入key，会返回对应的Value

### 常用方法

```java
        Map m1=new HashMap();

        //put():添加
        m1.put(1,"NO1");
        System.out.println(m1);//{1=NO1}

        //remove():根据键删除对应关系
        m1.remove(1);
        System.out.println(m1);//{}

        m1.put(2,9999);
        //get():根据键获取一个值
        System.out.println(m1.get(2));//9999

        //size():获取元素个数
        System.out.println(m1.size());//1

        //isEmpty():判断个数是否为0
        System.out.println(m1.isEmpty());//false

        //clear():清空键值对
        m1.clear();
        System.out.println(m1);//{}

        //containsKey():查找键是否存在
        m1.put(1,1);
        System.out.println(m1.containsKey(1));//true
```



> Map接口实现类的特点 1 

```java
        Map m1=new HashMap();
        m1.put("NO1","韩顺平");
        m1.put("NO2","张无忌");

        //当有相同的key时，等价于替换
        m1.put("NO1","张三丰");//{NO2=张无忌, NO1=张三丰}

        //Map中的Value可以重复
        m1.put("NO3","张三丰");//{NO2=张无忌, NO1=张三丰, NO3=张三丰}

        //Map中的key可以为null，value也可以为空，但是key为空只能有1个，而value为空可以有多个
        m1.put(null,null);
        m1.put(null,"abc");//{NO2=张无忌, null=abc, NO1=张三丰, NO3=张三丰}
        m1.put("NO4",null);//{NO2=张无忌, null=abc, NO1=张三丰, NO4=null, NO3=张三丰}

        //常用String类作为Map的key

        //key和Value之间是单向一对一关系，即通过指定的key总能找到对应的Value
        //通过get方法，传入key，会返回对应的Value
        System.out.println(m1.get("NO1"));//张三丰
```

> Map接口特点2【Node(实际存储位置)->entry->entrySet集合】

![image-20220123204439851](https://gitee.com/demon_night/images/raw/master/imgs/202201291904087.png)

```java
        Map m1=new HashMap();
        m1.put("NO1","韩顺平");
        m1.put("NO2","张无忌");
        //1. k-v最后是HashMap$Node  node=newNode(hash,key,value,null)
        //2. key-value是为了方便程序员的遍历，还会创建EntrySet集合，该集合存放的元素的类型Entry，而一个Entry对象就有k，v EntrySet<Entry<k,v>>
        //3. entrySet中，定义的类型是Map.Entry,但是实际上存放的还是HashMap$Node
        //4. entrySet中，定义的数据类型是Map.Entry，但实际上存放的还是HashMap$Node,这是因为HashMap$Node implements Map.Entry【Entry是编译类型，Node是运行类型】
        //5. 当把HashMap$Node对象存放到entrySet，为的是方便我们的遍历【Map.Entry提供了重要的方法】
        //   1. getKey()
        //   2. getValue()
        //        HashMap.Node<K,V> newNode(int hash, K key, V value, Node<K,V> next) {
        //            return new HashMap.Node<>(hash, key, value, next);
        //        }

        Set set=m1.entrySet();
        System.out.println(set.getClass());//HashMap$EntrySet
        for(Object i:set){
            System.out.println(i.getClass());//class java.util.HashMap$Node
            //为了从HashMap$Node取出k-v
            //1. 先做向下转型
            Map.Entry entry=(Map.Entry) i;
            System.out.println(entry.getKey()+"--"+entry.getValue());//NO2--张无忌  NO1--韩顺平
        }

        //同样里面也有keySet集合、Values集合
        Set s1=m1.keySet();
        System.out.println(s1.getClass());//class java.util.HashMap$KeySet
        Collection values=m1.values();//编译类型是Collection
        System.out.println(values.getClass());//class java.util.HashMap$Values
```

> table数组中存的是Node类型的，Set集合的子类还有entrySet子集合【集合指向table表中的节点】

![image-20220123204759229](https://gitee.com/demon_night/images/raw/master/imgs/202201291904815.png)

### Key-Value的遍历

```java
        Map m1=new HashMap();
        m1.put("邓超","孙俪");
        m1.put("王宝强","马蓉");
        m1.put("宋哲","马蓉");
        m1.put("刘灵哲",null);
        m1.put(null,"刘亦菲");
        m1.put("鹿晗","关晓彤");

        //六大遍历
        //第一组。 先取出所有的key，通过key取出对应的value
        //keySet():是将集合中所有的key封装成1个集合
        System.out.println("------第一种方式';/i-------");
        Set s1=m1.keySet();
        //增强for循环
        for(Object key:s1){
            System.out.println(key+"--"+m1.get(key));
        }
        System.out.println("------第二种方式-------");
        //迭代器
        Iterator iterator=s1.iterator();
        while(iterator.hasNext()){
            Object i=iterator.next();
            System.out.println(i+"--"+m1.get(i));
        }

        //第二组。 把所有的values取出,实现的是Collection集合，因此Collection的三种遍历方式都可以使用
        Collection values=m1.values();
        //增强for【通过values是不能反向取key的】
        System.out.println("-------取出所有的value  增强for-----");
        for(Object i:values){
            System.out.println(i);
        }
        System.out.println("-------取出所有的value-----");
        //迭代器
        Iterator iterator1=values.iterator();
        while (iterator1.hasNext()){
            System.out.println(iterator1.next());
        }

        //第三组：通过EntrySet来获取k-v【通过entrySet方法可以获得entry集合，entry里面封装的是一个k-v键值对】->【EntrySet<Map.Entry<k,v>>】
        Set entrySet=m1.entrySet();
        //for循环
        System.out.println("-------使用EntrySet的增强for循环-----");
        for(Object entry:entrySet){
            //将entry转成Map.Entry
            //Object->Entry【向下转型】
            Map.Entry m=(Map.Entry) entry;
            System.out.println(m.getKey()+"--"+m.getValue());
        }
        //迭代器
        System.out.println("-------使用EntrySet的迭代器-----");
        Iterator iterator2=entrySet.iterator();
        while(iterator2.hasNext()){
            Object Entry=iterator2.next();
            //System.out.println(Entry.getClass());//HashMap$Node【实际的】 -》实现了Map.Entry(getKey,getVaalue);
            //向下转型【本身应该向下转型直接转到HashMap$Node,但是Node没有相应的方法[getKey()、getValue()]，因此只能转到他的接口Entry】
            Map.Entry m=(Map.Entry) Entry;
            System.out.println(m.getKey()+"--"+m.getValue());
        }
```

### key-value遍历练习题

> 找出员工工资大于180000的员工

![image-20220125215804210](https://gitee.com/demon_night/images/raw/master/imgs/202201291904943.png)

```java
package Map;

import java.util.*;

public class HashMap_test5 {
    public static void main(String[] args) {
        HashMap h1=new HashMap();
        h1.put(1,new Employee("小王",18000,01));
        h1.put(2,new Employee("小刘",16000,02));
        h1.put(3,new Employee("小李",19000,03));
        Set s1=h1.keySet();
        for(Object i:s1){
            Employee e=(Employee) h1.get(i);
            if(e.getSalary()>18000){
                System.out.println(e);
            }
        }
        System.out.println("---------分割线--------");
        Iterator iterator= s1.iterator();
        while (iterator.hasNext()){
            Employee ee=(Employee) h1.get(iterator.next());
            if(ee.getSalary()>18000)
            System.out.println(ee);
        }
        System.out.println("--------分割线---------");
        Set s2=h1.entrySet();
        for(Object i:s2){
            Map.Entry m=(Map.Entry) i;
            Employee ee=(Employee) m.getValue();
            if(ee.getSalary()>18000){
                System.out.println(ee);
            }
        }
        System.out.println("------分割线-------");
        //EntrySet同样有迭代器方法
        Iterator iterator1=s2.iterator();
        while(iterator1.hasNext()){
            Map.Entry m=(Map.Entry)iterator1.next();
            Employee ee=(Employee) m.getValue();
            if(ee.getSalary()>18000){
                System.out.println(ee);
            }
        }
    }
}
class Employee{
    private String name;
    private double salary;
    private int id;
    public  Employee(String name,double salary,int id){
        this.name=name;
        this.salary=salary;
        this.id=id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    @Override
    public String toString() {
        return "Employee{" +
                "name='" + name + '\'' +
                ", salary=" + salary +
                ", id=" + id +
                '}';
    }
}
```

### HashMap小结

1. Map接口的常用实现类：HashMap、Hahstable、Properties
2. HashMap是Map接口使用频率最高的的实现类
3. HashMap是以key-val对对的方式来存储数据(HashMap$Node类型)
4. key不能重复，但是值可以重复，允许使用null键和null值
5. 如果添加相同的key，则会覆盖原来的key-val，等同于修改(key不会替换，但是val会被替换)
6. 与HahsSet一样，不保证映射的顺序，因为底层是以hash表的方式来存储的
7. HahsMap没有实现同步，因此是线程不安全

### HahsMap接口的实现【源码分析】

```java
package Map;

import java.util.HashMap;

public class HashMap_test6 {
    public static void main(String[] args) {
        HashMap map=new HashMap();
        map.put("java",10);
        map.put("php",10);
        map.put("java",20);
        System.out.println(map);

        /*
        1. 执行构造器 new HashMap();
            初始化加载因子this.loadFactor = DEFAULT_LOAD_FACTOR;为0.75
        2. 执行put方法
            1. 先执行装箱操作
               public static Integer valueOf(int i) {
                     if (i >= IntegerCache.low && i <= IntegerCache.high)
                            return IntegerCache.cache[i + (-IntegerCache.low)];
                    return new Integer(i);
                }
            2. 再执行put方法
                public V put(K key, V value) {//key为”java“，value为10
                    return putVal(hash(key), key, value, false, true);
                }
           3。 计算hash值【通过hashcode来计算的。hashcode是通过地址得来的】
                static final int hash(Object key) {
                    int h;
                    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
                }
            4. 进入putVal方法
                final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                               boolean evict) {
                    Node<K,V>[] tab; Node<K,V> p; int n, i;//辅助变量
                    //如果底层的table数组为null，或者length=0，就扩容到16
                    if ((tab = table) == null || (n = tab.length) == 0)
                        n = (tab = resize()).length;
                    //取出hash值对应的table的索引位置的Node，如果为空，就直接把加入的k-v创建成1个Node，加入到该位置即可
                    if ((p = tab[i = (n - 1) & hash]) == null)
                        tab[i] = newNode(hash, key, value, null);
                    else {
                        Node<K,V> e; K k;
                        //如果与table索引位置存放的Node的key的哈希值相同并且满足table现有的节点的key和
                        // 准备添加的key是同一个对象或者equals相同时就返回真，就不能加入。然后做一个value替换工作【hashcode、equals比的都是地址】
                        if (p.hash == hash &&
                            ((k = p.key) == key || (key != null && key.equals(k))))
                            e = p;
                        //如果当前的table中已有的node是红黑树，就按照红黑树的方式进行处理
                        else if (p instanceof TreeNode)
                            e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
                        else {
                        //如果找到的节点，后面是链表，就循环比较
                            for (int binCount = 0; ; ++binCount) {
                            //如果整个链表没有和他相同，就加到该链表的最后
                                if ((e = p.next) == null) {
                                    p.next = newNode(hash, key, value, null);
                                    //加入后，判断当前链表的个数，是否已经达到八个，到8个后【同时table表长度>=64】就调用treeifyBin进行红黑树的转换
                                    if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                                        treeifyBin(tab, hash);
                                    break;
                                }
                                //如果在循环比较过程中，发现有相同的，就break，进行替换value即可
                                if (e.hash == hash &&
                                    ((k = e.key) == key || (key != null && key.equals(k))))
                                    break;
                                p = e;
                            }
                        }
                        if (e != null) { // existing mapping for key
                            V oldValue = e.value;
                            if (!onlyIfAbsent || oldValue == null)
                                e.value = value;
                            afterNodeAccess(e);
                            return oldValue;
                        }
                    }
                    ++modCount;
                    //每增加1个Node，就size++
                    if (++size > threshold)
                    //如果size>临界值，就进行扩容
                        resize();
                    afterNodeInsertion(evict);
                    return null;
                }
             5. 树化方式
                final void treeifyBin(Node<K,V>[] tab, int hash) {
                    int n, index; Node<K,V> e;
                    //如果table数组小于64，就进行扩容
                    否则才会真正的树化
                    if (tab == null || (n = tab.length) < MIN_TREEIFY_CAPACITY)
                        resize();
                    else if ((e = tab[index = (n - 1) & hash]) != null) {
                        TreeNode<K,V> hd = null, tl = null;
                        do {
                            TreeNode<K,V> p = replacementTreeNode(e, null);
                            if (tl == null)
                                hd = p;
                            else {
                                p.prev = tl;
                                tl.next = p;
                            }
                            tl = p;
                        } while ((e = e.next) != null);
                        if ((tab[index] = hd) != null)
                            hd.treeify(tab);
                    }
                }

         */
    }
}
```

### Map的接口实现类-HahsMap

1. HahMap底层维护了Node类型的数组table，默认为null
2. 当创建类型时，将加载因子初始化为0.75
3. 当添加key-val时，通过key的哈希值得到table的索引，然后判断该索引处是否有元素，如果没有元素就直接添加，如果该索引处有元素，继续判断该元素的key是否和准备加入的key相等，如果相等就直接替换val，如果不相等需要判断是树结构还是链表结构、做出相应的处理，如果添加时发现容量不够，则需要扩容
4. 第一次添加，则需要扩容table容量为16，临界值threshold为12
5. 以后再扩容，则需要扩容table容量为原来的两倍，临界值也为原来的二倍，即24
6. 在java8中如果一条链表的元素个数超过treeify-threshold(默认为8)，并且table的大小>=min_treeify_capacity(默认为64)，就会进行树化(红黑树)

### Map的接口实现类-Hahstable

1. 存放的元素是键值对，即k-v
2. `Hashtable的键和值都不能为null`，否则会抛出NullPointerException
3. Hashtable的使用方法基本和HashMap一样
4. hashtable是线程安全的，hashMap是线程不安全

<img src="https://gitee.com/demon_night/images/raw/master/imgs/202201291904232.png" alt="image-20220127105140960"  />

#### 代码实现

```java
        Hashtable h1=new Hashtable<>();
        h1.put("join",100);//ok
        //h1.put("null",100);//抛出NullPointerException异常
        //h1.put("join",null);//抛出异常
        h1.put("lucy",100);//ok
        h1.put("lic",100);//ok
        h1.put("lic",88);//进行替换

        //解读
        /**
         * 1. 底层有数组hashtable$Entry[]，初始化大小为11
         * 2. threshold为8:12*0.75=8
         * 3. 扩容：按照自己的扩容机制来进行扩容
         *    1. 将k-v封装到Entry里面
         *    2. 当当前数量大于等于临界值时进行扩容：table.size>>1+1【11*2+1=23，threshold=23*0.75约等于17】
         */
```

> Hashtable与HashMap对比

![image-20220127113023011](https://gitee.com/demon_night/images/raw/master/imgs/202201291905387.png)

### Map接口实现类-Properties

1. Properties类继承自Hashtable类并实现了Map接口，也是使用键值对的形式来保存数据
2. 他的使用特点和hashtable类似
3. Properties还可以用于从XXX.properties文件中，加载到Properties类对象，并进行读取和修改
4. 说明：工作后xxx.properties文件通常作为配置文件

```java
        Properties properties=new Properties();
        //1. Properties继承了Hashtable
        //2. 可以通过键值对来添加数据，key、value不能为空
.
        properties.put("join",100);
        properties.put("lucy",100);
        properties.put("lic",100);
        properties.put("lic",88);

        System.out.println(properties);//{lic=88, join=100, lucy=100}

        //get()：获取元素
        System.out.println(properties.get("join"));//100

        //remove():删除某一元素
        properties.remove("join");
        System.out.println(properties);//{lic=88, lucy=100}

        //修改
        properties.put("lucy",9999);
        System.out.println(properties);//{lic=88, lucy=9999}
```



> HashMap类、LinkedHashMap类、TreeMap类

* 1、Map集合一次存储两个对象，一个键对象，一个值对象
* 2、键对象在集合中是唯一的，可以通过键来查找值z`
* HashMap特点：
* 1、使用哈希算法对键去重复，效率高，但无序
* 2、HashMap是Map接口的主要实现类
* 
* 接口是可以创建对象的
* 
* HashMap 哈希表
* 底层还是采用哈希表来存储的
* key：无序，唯一
* value：无序，不唯一
* 
* LinkedHashMap 哈希表+链表
* key：有序(添加顺序)，唯一
* value：无序(说的是存储顺序无序，但是映射关系还是确定的)，不唯一
* 
* TreeMap 红黑树
* key：有序(自然顺序)，唯一
* value：无序，不唯一
* 
* set和map的关系
* 如果map中只存储key不存储value就是对应的Set
* Set就是对应Map的key的集合
* 
* 使用map最多的四个操作
* 创建对象        Map<String,String> map=new HashMap<String,String>();
* 添加key-value键值对        map.put("cn","china")
* 根据key获取value        map.get("cn")
* 遍历map
* 
* map的节点类型：entry

```java
public class testMap {
    public static void main(String[] args) {
        //创建Map对象
        //Map<String, String> map = new HashMap<String, String>();

        //创建LinkedHashMap
        //有序，按照输入内容的顺序进行输出
        //Map<String,String> map=new LinkedHashMap<String,String>();

        //创建TreeMap
        //有序，key有序
        Map<String,String> map=new TreeMap<String,String>();

        //使用Map对象存储键值对
        map.put("cn","china");
        map.put("jp","Japan");
        map.put("us","the United States");
        map.put("us","America");
        map.put("en", "England");

        //使用键来查找对象
        System.out.println(map.get("cn"));

        //使用map直接输出对象里面的值
        //如果“键”一样，“值”不一样，会覆盖之前“键”所对应的值
        System.out.println(map.size());
        //所有的key-value
        System.out.println(map);
        //所有的key
        System.out.println(map.keySet());
        //所有的value
        System.out.println(map.values());

        //遍历map
        //1：得到所有的key组成的set
        Set<String> keyset=map.keySet();
        for(String key:keyset) {
            System.out.println(key+"----"+map.get(key));
        }

        //2:得到所有的Entry(就是哈希表或者红黑树中节点类)组成的集合
        //类型为节点类型Map.Entry    节点里面的key与value的类型为String，String
        //迭代器的使用：Iterator it=对象.iterator()
        Set<Map.Entry<String,String>> entrySet=map.entrySet();
        Iterator<Map.Entry<String,String>> it=entrySet.iterator();
        while(it.hasNext()) {
            Map.Entry<String, String> entry=it.next();
            //System.out.println(entry);
            System.out.println(entry.getKey()+":"+entry.getValue());
        }
    }
}
```

### 例1

> Student类

```java
public class Student {
    private int id;
    private String name;
    private int age;
    private Double score;

    public Student(int id, String name, int age, Double score) {
        super();
        this.id = id;
        this.name = name;
        this.age = age;
        this.score = score;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public Double getScore() {
        return score;
    }

    public void setScore(Double score) {
        this.score = score;
    }

    @Override
    public String toString() {
        return "Student [id=" + id + ", name=" + name + ", age=" + age + ", score=" + score + "]";
    }
}
```

> TestMap类

* 为什么不重写equals和hascode
* 因为我们调的事key的hashcode，而不是调用student的hascode
* key是比较简单的，而Student是比较复杂的
* Entry是链表中的节点

```java
public class TestMap2 {
    public static void main(String[] args) {
        //Map<Integer,Student> map=new HashMap<Integer,Student>();
        //Map<Integer,Student> map=new LinkedHashMap<Integer,Student>();
        Map<Integer,Student> map=new TreeMap<Integer,Student>();
        Student stu=new Student(10,"zhangsan",23,98.0);
        Student stu1=new Student(20,"lisi",24,100.0);
        Student stu2=new Student(30,"wangwu",20,85.0);
        Student stu3=new Student(10,"zhangsan",23,98.0);

        map.put(stu.getId(),  stu);
        map.put(stu1.getId(), stu1);
        map.put(stu2.getId(), stu2);
        map.put(stu3.getId(), stu3);

        //map.clear();
        System.out.println("-------");
        System.out.println(map.containsKey(10));
        System.out.println(map.containsValue(stu3));

        //根据ley来判断是否是同一个
        System.out.println(map.size());
        System.out.println(map);
        //根据key值来查找
        System.out.println(map.get(40));

        //遍历：entrySet
        Set<Entry<Integer,Student>> entryset=map.entrySet();
        for(Entry<Integer,Student> entry:entryset) {
            //System.out.println(entry.getKey()+"----"+entry.getValue());
            //若只想要student中的一部分
            Student st=entry.getValue();
            System.out.println(st.getId()+":"+st.getName());
        }
    }
}
```

### HashMAp

* 哈希表默认索引长度为16，装填因子为0.75f【对于float类型一定要加f后缀】//达到75%就会扩容原来的2倍
* table为主数组引用【索引数组】
* key为null时默认放在索引数组为0的位置
* 当链表存储数据个数>=8时，不再采用链表存储，而采用红黑树存储结构，如果又少于8个时又会立即变成链表存储
* HashSet的底层使用的是HashMap，所以底层结构也是哈希表
* HashSet的元素到HashMap中作key，value统一是同一个Object();

```java
public class TestHashMap {
    public static void main(String[] args) {
        HashMap map=new HashMap(16,0.75f);
    }
}
```

### TreeMap类【适合排序】

- 需要注意的是比较规则，如果是按照长度来比较的话，就是当长度相等时，即使内容一样也添加不进去【`但是value会被替换`】

```java
package Map;

import java.util.Comparator;
import java.util.TreeMap;

public class TreeMap_test1 {
    public static void main(String[] args) {
        /**
         * 1. 构造器把传入的实现了Comparator接口的匿名内部类(对象)，传给TreeMap的Comparator
         * 2. 第一次添加，把k-v封装到Entry对象，放入root
         * 3. 以后添加就通过do-while遍历所有的key，和当前的key进行比较寻找适当的位置
         * 4. 如果遍历过程中发现准备添加的key和当前已有的key相等就不添加了直接返回
         */
        //TreeMap t1=new TreeMap();
        TreeMap t1=new TreeMap(new Comparator(){
           public int compare(Object o1,Object o2){
               //return ((String)o1).compareTo((String)o2);
               //按照字符串长度大小来排序
               return ((String)o1).length()-((String)o2).length();
           }
        });
        t1.put("jack","杰克");
        t1.put("tom","汤姆");
        t1.put("tt","体体");
        t1.put("smith","史密斯");
        System.out.println(t1);//{jack=杰克, smith=史密斯, tom=汤姆, tt=体体}
    }
}
```

### HashMap注意事项：

------

获取hashCode
对于各种基本数据类型哈希码的表达形式：
1：Integer  直接返回数值
2：Double     经过一系列的变化将其变成long型，然后将其后移32位，与之前的数值进行异或
3：String    1*字符1+2*字符2+3*字符3+...
4:”类“类型    对于属性的各个类型进行计算，然后进行相乘或相除等操作返回一个数值

减少冲突
装填因子：表中的记录数/哈希表的长度。4/16=0.25，8/16=0.25，
一般情况下，装填因子取经验值0.5
哈希函数的选择：直接定址法，平方取中法、折叠法、除留取余法（y=x%11)

处理冲突的方法：
链地址法、开放地址法、再散列法、建立一个公共溢出区

Map
存储的键值对映射关系，根据key值可以找到value

HashMap
采用Hashtable哈希表存储结构
key无序

HashMap的子类LinkedHashMap
采用Hashtable哈希表存储结构
key有序(添加顺序)

HashMap的兄弟：TreeMap
采用二叉树(红黑树)的存储结构
key有序，查询速度比List快但是没有HashMap速度快

### Java HashMap getOrDefault() 方法

- ```
  hashmap.getOrDefault(Object key, V defaultValue)
  ```

- 如果找到对应的key则返回key对应的value，返回defalutValue

## 总结

> 如何选择集合实现类

1. 先判断存储类型(一组对象【单列】或一组键值对【双列】)

2. 一组对象

   允许重复：List

   ​	增删多：LinkedList【底层维护了一个双向链表】

   ​	改查多：ArrayList【底层维护了Object类型的可变数组】

   不允许重复：Set

   ​	无序：HashSet【底层是HashMap，维护了一个哈希表，即数组+链表+红黑树】

   ​	排序：TreeSet

   ​	插入和取出顺序一致:LinkedHashSet，维护数组+双向链表

3. 一组键值对：Map

   1. 键无序HashMap【底层是哈希表 数组+链表+红黑树】
   2. 键排序：TreeMap
   3. 键插入顺序和取出顺序一致：LinkedHashMap
   4. 读取文件：Properties

## Collections工具类

> Collections类的常用方法

```java
package Collections;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;
@SuppressWarnings({"all"})
public class Collections_test1 {
    public static void main(String[] args) {
        List l=new ArrayList();
        l.add("tom");
        l.add("smith");
        l.add("King");
        l.add("million");

        //1. reverse(List):翻转List中元素的顺序
        Collections.reverse(l);//[million, King, smith, tom]

        //shuffle(List):对List集合中的元素进行随机排序
        Collections.shuffle(l);//[King, million, tom, smith]

        //sort(List):根据元素的自然顺序对指定List集合按升序排序
        Collections.sort(l);//[King, million, smith, tom]

        //指定比较规则[按照字符串的长度]
        Collections.sort(l, new Comparator() {
            public int compare(Object o1,Object o2){
                return ((String)o1).length()-((String)o2).length();
            }
        });//[tom, King, smith, million]

        //swap(List,i,j):将List集合中的i处元素与j处元素进行交换
        Collections.swap(l,0,1);//[King, tom, smith, million]

        //max(List)：根据元素的自然顺序，返回集合中最大的元素
        //min(List):根据元素的自然顺序，返回集合中最小的元素
        System.out.println(Collections.max(l));//tom

        //按照自定规则返回最大的
        System.out.println(Collections.max(l, new Comparator() {
            public int compare(Object o1,Object o2){
                return ((String)o1).length()-((String)o2).length();
            }
        }));//million

        //frequency(list,a):返回集合中a出现的次数
        System.out.println(Collections.frequency(l,"tom"));//1

        //copy(List dest,List list):将list里面的内容复制到dest集合中
        ArrayList dest=new ArrayList();
        //为了完成一个copy，我们需要给dest赋值，使它的长度不小于list的长度,注意不能使用有参构造器来确定长度
        for(int i=0;i<l.size();i++) dest.add("");
        Collections.copy(dest,l);
        System.out.println(dest);//[King, tom, smith, million]

        //replace(List,a,b):使用新值来替换List集合中华的旧值a
        Collections.replaceAll(l,"tom","Tom");
        System.out.println(l);//[King, Tom, smith, million]
    }
}

```

### 练习

#### 练习1

```java
package 习题1;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class homework_test1 {
    public static void main(String[] args) {
        news n1=new news("新闻一：新冠确诊病例超千万，数百万印度教信徒赴恒河\"圣浴\"引起民众担忧");
        news n2=new news("新闻二：男子突然想起2个月前钓的鱼还在网兜里，捞起一看赶紧放生");
        List l=new ArrayList();
        l.add(n1);
        l.add(n2);
        Collections.reverse(l);
        for(Object i:l){
            news t=(news) i;
            String temp=t.getTitle();
            if(temp.length()>=15) {
                StringBuilder temp2 = new StringBuilder(temp.substring(0, 15)).append("...");
                System.out.println(temp2);
            }else{
                System.out.println(temp);
            }
        }
    }
}
class news{
    private String title;
    private String content;
    public news(String title){
        this.title=title;
    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getContent() {
        return content;
    }

    public void setContent(String content) {
        this.content = content;
    }

    @Override
    public String toString() {
        return "news{" +
                "title='" + title + '\'' +
                '}';
    }
}
```

#### 练习2

```java
package 习题1;

import java.util.ArrayList;
import java.util.List;

public class homework_test2 {
    public static void main(String[] args) {
        List l=new ArrayList();
        Car c1=new Car("宝马",400000);
        Car c2=new Car("宾利",5000000);

        //添加
        l.add(c1);
        l.add(c2);
        System.out.println(l);//[Car{name='宝马', price=400000.0}, Car{name='宾利', price=5000000.0}]

        //删除
        l.remove(c1);
        //l.remove(1);
        System.out.println(l);//[Car{name='宾利', price=5000000.0}]

        //查询是否存在
        System.out.println(l.contains(c1));//false

        //查询个数
        System.out.println(l.size());//1

        //清空
        //l.clear();

        //加入一个集合
        l.addAll(l);
        System.out.println(l);//[Car{name='宾利', price=5000000.0}, Car{name='宾利', price=5000000.0}]

        //查找多个元素是否存在
        System.out.println(l.containsAll(l));//true

        //删除多个元素
        //l.removeAll(l);
        //System.out.println(l);//[]

        //增强for训话遍历
        for(Object i:l){
            System.out.println(i);//Car{name='宾利', price=5000000.0}
                                 //Car{name='宾利', price=5000000.0}
        }

    }
}
class Car{
    private String name;
    private double price;
    public Car(String name,double price){
        this.name=name;
        this.price=price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    @Override
    public String toString() {
        return "Car{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
}

```

#### 练习3

```java
package 习题1;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;

public class homework_test3 {
    public static void main(String[] args) {
        Map m=new HashMap();
        m.put("jack",650);
        m.put("tom",1200);
        m.put("smith",2900);
        m.get("jack");

        m.put("jack",2600);

        //使用keySet
        Set s=m.keySet();
        for(Object key:s){
            m.put(key,(Integer)m.get(key)+100);
        }

        //使用EntrySet
        Set s1=m.entrySet();
        Iterator iterator=s1.iterator();
        while(iterator.hasNext()){
            Map.Entry entry=(Map.Entry) iterator.next();
            m.put(entry.getKey(),(Integer)m.get(entry.getKey())+100);
        }


        for(Object key:s){
            System.out.println(key);
        }
        for(Object key:s){
            System.out.println(m.get(key));
        }
    }
}
```

#### 练习4

- HashSet的去重机制：hashcode（）+equals（）,底层先通过存入对象，进行运算得到一个hash值，通过hash值得到相应的索引，如果发现table索引所在的位置，没有数据，就直接进行存放，如果有数据，进行equals比较【遍历比较】，如果比较后不相同就加入，否则不加入
- TreeSet的去重机制：如果你传入了一个comparator匿名对象，就使用重写的comapre方法进行去重，如果返回0，就认为是相同元素就不进行添加，如果没有传入Comparartor匿名对象，则以你添加的对象实现的Comapreable接口的compareTo进行去重【字符串默认实现了Compareable接口，字符串存储在常量池】
- 需要注意的是对于TreeSet:如果不导入比较器的话，就需要我们添加的数据`实现了Compareable对象`，否则会爆类型转换错误
  - ![image-20220203222524750](https://gitee.com/demon_night/images/raw/master/imgs/202202032325600.png)

#### 练习5

![image-20220203225925074](https://gitee.com/demon_night/images/raw/master/imgs/202202032359989.png)

```java
package 习题1;

import java.util.HashSet;
import java.util.Objects;

public class homework_test4 {
    public static void main(String[] args) {
        //总结：只要添加到集合中，无论是否修改元素值，元素在table中的索引中的位置都不会发生改变
        HashSet set=new HashSet();
        person p1=new person(1001,"AA");
        person p2=new person(1002,"BB");
        set.add(p1);//假设存放在索引1
        set.add(p2);//假设存放在索引2
        p1.setName("CC");//可以将集合中的对象进行修改,索引位置不发生改变
        set.remove(p1);//删除失败，因为p1的值修改后，虽然位置没有改变但是，计算的结果的索引值可能发生了改变，可能计算的索引位置为3
        System.out.println(set);
        set.add(new person(1001,"CC"));//由于和刚才修改的结果一样，因此将该对象放在索引3
        System.out.println(set);
        set.add(new person(1001,"AA"));//此时计算的索引值肯定为索引1，但是和索引1位置的头一个值不相同，因此将其加到索引1头节点的下一个
        System.out.println(set);//[person{}, person{}, person{}, person{}]

    }
}
class person{
    private int id;
    private String name;
    public person(int id,String name){
        this.id=id;
        this.name=name;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        person person = (person) o;
        return id == person.id && Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, name);
    }

    @Override
    public String toString() {
        return "person{" +
                "id=" + id +
                ", name='" + name + '\'' +
                '}';
    }
}
```

> ArrayList与Vector的扩容

![image-20220203230335712](https://gitee.com/demon_night/images/raw/master/imgs/202202040003148.png)

## 泛型

### 泛型介绍

1. 泛型又称参数化类型，是Jdk5.0出现的新特性，解决数据类型的安全性问题
2. 在类声明或实例化时只要指定好需要的具体的类型即可
3. Java泛型可以保证如果程序在编译时没有发生警告，运行时就不会产生ClassCastException异常，同时使代码更简洁和健壮
4. 泛型的作用：可以在类声明时通过一个标识表示类中某个属性的类型，或者是某个方法的返回值类型，或者是参数类型

```java
package generic;

public class generic_test2 {
    public static void main(String[] args) {
        //此时person的实现类的E的数据类型代表的是String
        //注意：E具体的数据类型在定义Person对象时指定，即在编译期间，就确定E是什么数据类型
        Person<String> person=new Person<>("100");
        person.ff();
    }
}
class Person<E>{
    E s;//E表示s的数据类型，该数据类型在定义Person对象时指定，即在编译期间，就确定E是什么类型
    public Person(E s){//E也可以是参数类型
        this.s=s;
    }
    public E f(){//返回类型使用E
        return s;
    }
    public void ff(){
        System.out.println(s.getClass());//class java.lang.String
    }
}
```

### 练习1

![image-20220204175937985](https://gitee.com/demon_night/images/raw/master/imgs/202202041859477.png)

```java
package generic;

import java.util.HashMap;
import java.util.HashSet;
import java.util.Iterator;
import java.util.*;

public class generic_test3 {
    public static void main(String[] args) {
        HashSet<Student> h1=new HashSet<>();
        h1.add(new Student("小王",10));
        h1.add(new Student("小刘",7));
        h1.add(new Student("小李",11));
        
        for(Student i:h1){
            System.out.println(i);
        }
        
        System.out.println("-------------");
        
        Iterator iterator=h1.iterator();
        while (iterator.hasNext()){
            System.out.println(iterator.next());
        }
        
        System.out.println("-------------");
        
        HashMap<String,Student> h2=new HashMap<>();
        h2.put("小王",new Student("小王",10));
        h2.put("小刘",new Student("小刘",7));
        h2.put("小李",new Student("小李",11));
        Set<String> s1=h2.keySet();
        
        for(String i:s1){
            System.out.println(i+"---"+h2.get(i));
        }
        
        System.out.println("-------------");
        
        Set<Map.Entry<String,Student>> set=h2.entrySet();
        Iterator<Map.Entry<String ,Student>> iterator1=set.iterator();
        while(iterator1.hasNext()){
            Map.Entry<String,Student> next=iterator1.next();
            System.out.println(next.getKey()+"---"+next.getValue());
        }
        
        System.out.println("-------------");
        
        for(Map.Entry<String,Student> i:set){
            System.out.println(i.getKey()+"---"+i.getValue());
        }
    }
}
class Student{
    public String name;
    public int age;
    public Student(String name,int age){
        this.name=name;
        this.age=age;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}

```

### 泛型语法使用

```java
package generic;

import java.util.ArrayList;
import java.util.List;

public class generic_test4 {
    public static void main(String[] args) {
        //给泛型指向数据类型时，要求时引用数据类型，不能是基本数据类型
        List<Integer> l1=new ArrayList<>();
        //List<int> l2=new ArrayList<>();//Wrong

        //在给泛型指定具体类型后，可以传入该类型或者其子类型
        //E指定了类型，需要按照类型传入
        pig<A> p1=new pig<>(new A());
        p1.f();//class generic.A
        pig<A> p2=new pig<>(new B());//向下转型
        p2.f();//class generic.B
        //pig<B> p3=new pig<>((B)new A());
        //p3.f();//错误，不能进行向上转型

        //可以进行简写
        //编译器会进行类型判断
        List<Integer> l2=new ArrayList<>();

        //如果这样写，泛型默认为Object类型
        List l3=new ArrayList();//===>List<Object> l3=new ArrayList<>();
    }
}
class A{}
class B extends A{}
class pig<E>{
    E e;
    public pig(E e){
        this.e=e;
    }
    public void f(){
        System.out.println(e.getClass());
    }
}
```

### 泛型介绍2

* 没有采用泛型之前
* 1：不安全：添加元素时无检查  宽进
* 2：繁琐：获取元素时需要强制转换类型 严出
* 采用泛型
* 1：安全  严进
* 2：简单  宽出
* 
* 泛型：参数化类型
* 比如使用方法时add()就只能添加相应的类型
* 
* 泛型有三大类：泛型接口、泛型类、泛型方法

```java
public class WhyGeneric {
    public static void main(String[] args) {
        List<Integer> list=new ArrayList();
        list.add(10);
        list.add(20);
        list.add(30);
        //list.add("kjdsjfh");
        //list.add(true);
        //list.add(new Data());

        for(int i=0;i<list.size();i++) {
            Object num=list.get(i);    
            //不能进行运算，因为是类类型
            //System.out.println(num+10);

            //解决办法：强转
            //int num1=(int) list.get(i);
        }

        for(Object num:list) {
            System.out.println(num);
            //同样不能进行算术运算
            //System.out.println(num+10);
        }
    }
}
```

### 练习2

![image-20220204230939304](https://gitee.com/demon_night/images/raw/master/imgs/202202050009530.png)

```java
package generic;

import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

public class generic_test5 {
    public static void main(String[] args) {
        List<Employee> l=new ArrayList<>();
        l.add(new Employee("小李","男",new MyDate(2000,01,01)));
        l.add(new Employee("小刘","女",new MyDate(2001,9,18)));
        l.add(new Employee("小李","男",new MyDate(1999,02,18)));
        for(Employee i:l){
            System.out.println(i);
        }
        System.out.println("-------------");        
        l.sort(new Comparator<Employee>() {
            @Override
            public int compare(Employee o1, Employee o2) {
                String name1=o1.getName();
                String name2= o2.getName();
                int y1=o1.getBirthday().getYear();
                int m1=o1.getBirthday().getMonth();
                int d1=o1.getBirthday().getDay();
                int y2=o2.getBirthday().getYear();
                int m2=o2.getBirthday().getMonth();
                int d2=o2.getBirthday().getDay();
                if(!name1.equals(name2)){
                    return name1.compareTo(name2);
                }else{
                    //过关斩将法
                    if(y1!=y2) return y1-y2;
                    if(m1!=m2) return m1-m2;
                    if(d1!=d2) return d1-d2;
                    return 0;
                }
            }
        });
        for(Employee i:l){
            System.out.println(i);
        }
    }
}
class Employee{
    private String name;
    private String sal;
    private MyDate birthday;

    public Employee(String name, String sal, MyDate birthday) {
        this.name = name;
        this.sal = sal;
        this.birthday = birthday;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getSal() {
        return sal;
    }

    public void setSal(String sal) {
        this.sal = sal;
    }

    public MyDate getBirthday() {
        return birthday;
    }

    public void setBirthday(MyDate birthday) {
        this.birthday = birthday;
    }

    @Override
    public String toString() {
        return "Employee{" +
                "name='" + name + '\'' +
                ", sal='" + sal + '\'' +
                ", birthday=" + birthday +
                '}';
    }
}
class MyDate{
    private int year;
    private int month;
    private int day;

    public MyDate(int year, int month, int day) {
        this.year = year;
        this.month = month;
        this.day = day;
    }

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        this.year = year;
    }

    public int getMonth() {
        return month;
    }

    public void setMonth(int month) {
        this.month = month;
    }

    public int getDay() {
        return day;
    }

    public void setDay(int day) {
        this.day = day;
    }

    @Override
    public String toString() {
        return "MyDate{" +
                "year=" + year +
                ", month=" + month +
                ", day=" + day +
                '}';
    }
}
```

> 为了体现更好的封装性，可以将过关斩将放在MyDate里面【即MyDate实现了Compareable接口，重写comparaTo方法】

```java
package generic;

import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

public class generic_test5 {
    public static void main(String[] args) {
        List<Employee> l=new ArrayList<>();
        l.add(new Employee("小李","男",new MyDate(2000,01,01)));
        l.add(new Employee("小刘","女",new MyDate(2001,9,18)));
        l.add(new Employee("小李","男",new MyDate(1999,02,18)));
        for(Employee i:l){
            System.out.println(i);
        }
        System.out.println("-------------");
        l.sort(new Comparator<Employee>() {
            @Override
            public int compare(Employee o1, Employee o2) {
                String name1=o1.getName();
                String name2= o2.getName();
//                int y1=o1.getBirthday().getYear();
//                int m1=o1.getBirthday().getMonth();
//                int d1=o1.getBirthday().getDay();
//                int y2=o2.getBirthday().getYear();
//                int m2=o2.getBirthday().getMonth();
//                int d2=o2.getBirthday().getDay();
                if(!name1.equals(name2)){
                    return name1.compareTo(name2);
                }else{
                    //过关斩将法
//                    if(y1!=y2) return y1-y2;
//                    if(m1!=m2) return m1-m2;
//                    if(d1!=d2) return d1-d2;
//                    return 0;
                    return o1.getBirthday().compareTo(o2.getBirthday());
                }
            }
        });
        for(Employee i:l){
            System.out.println(i);
        }
    }
}
class Employee{
    private String name;
    private String sal;
    private MyDate birthday;

    public Employee(String name, String sal, MyDate birthday) {
        this.name = name;
        this.sal = sal;
        this.birthday = birthday;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getSal() {
        return sal;
    }

    public void setSal(String sal) {
        this.sal = sal;
    }

    public MyDate getBirthday() {
        return birthday;
    }

    public void setBirthday(MyDate birthday) {
        this.birthday = birthday;
    }

    @Override
    public String toString() {
        return "Employee{" +
                "name='" + name + '\'' +
                ", sal='" + sal + '\'' +
                ", birthday=" + birthday +
                '}';
    }
}
class MyDate implements Comparable<MyDate>{
    private int year;
    private int month;
    private int day;

    public MyDate(int year, int month, int day) {
        this.year = year;
        this.month = month;
        this.day = day;
    }

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        this.year = year;
    }

    public int getMonth() {
        return month;
    }

    public void setMonth(int month) {
        this.month = month;
    }

    public int getDay() {
        return day;
    }

    public void setDay(int day) {
        this.day = day;
    }

    @Override
    public String toString() {
        return "MyDate{" +
                "year=" + year +
                ", month=" + month +
                ", day=" + day +
                '}';
    }

    @Override
    public int compareTo(MyDate o) {
        int y1=year;
        int m1=month;
        int d1=day;
        int y2=o.getYear();
        int m2=o.getMonth();
        int d2=o.getDay();
        if(y1!=y2) return y1-y2;
        if(m1!=m2) return m1-m2;
        if(d1!=d2) return d1-d2;
        else return 0;
    }
}
```

## 自定义泛型

### 细节1

1. 普通成员可以使用泛型(属性、方法)
2. 使用泛型的数组，不能初始化
3. 静态方法中不能使用类的的泛型
4. 泛型类的类型，是在创建对象时确定的(因为创建对象时，需要指定确定类型)
5. 如果在创建对象时，没有指定类型，默认为Object

### 练习1[自定义泛型类]

```java
package generic;

public class generic_test6 {
    public static void main(String[] args) {
        Tiger<Double,String,Integer> g=new Tiger<>("join");
        g.setT(10.9);
        //g.setT("yy");//错误，类型不对
        System.out.println(g);
        Tiger g1=new Tiger("join~~");
        g1.setT("yy");//可以，因为此时T、R、M默认设置成Object类型，String-》Object：向上转型
        System.out.println(g1);
    }
}
//T、R、M为泛型的标识符
class Tiger<T,R,M>{
    String name;
    R r;
    M m;
    T t;

    public Tiger(String name) {
        this.name = name;
    }

    public Tiger(R r, M m, T t) {
        this.r = r;
        this.m = m;
        this.t = t;
        //由于不确定类型，因此编译器不知道开多大空间，因此不能初始化
        //T[] ts=new T[4];
        //但是可以定义
        T[] ts;
    }

    //对于静态方法、静态属性也是不能使用泛型的,因为静态是和类有关的，在类加载时，，对象还没创建
    //所以，在静态方法和静态属性使用了泛型，Jvm就无法完成初始化
    //static T tt;

//    public static void f(T t){
//
//    }


    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public R getR() {//返回类型可以使泛型
        return r;
    }

    public void setR(R r) {
        this.r = r;
    }

    public M getM() {
        return m;
    }

    public void setM(M m) {
        this.m = m;
    }

    public T getT() {
        return t;
    }

    public void setT(T t) {
        this.t = t;
    }

    @Override
    public String toString() {
        return "Tiger{" +
                "name='" + name + '\'' +
                ", r=" + r +
                ", m=" + m +
                ", t=" + t +
                '}';
    }
}
```

### 自定义泛型接口

1. 接口中，静态成员也不能使用泛型（这个和泛型类规定一样）
2. 泛型接口类型的类型，在继承接口或者实现接口时确定
3. 没有指定类型时，默认为Object

```java
package generic;

public class generic_test7 {
    public static void main(String[] args) {

    }
}

/**
 * 泛型接口使用说明：
 * 1. 接口中，静态成员也不能使用泛型
 * 2. 泛型接口类型的类型，在继承接口或者实现接口时确定
 */

//没有指定类型时，就默认为Object
class CC implements IUsb{

    @Override
    public Object get(Object o) {
        return null;
    }

    @Override
    public void hi(Object o) {

    }

    @Override
    public void run(Object r1, Object r2, Object u1, Object u2) {

    }
}

//在继承接口时确定泛型接口的类型
interface IA extends IUsb<String,Double>{

}

//同样也可以在实现接口时，直接指定接口类型
//给U指定为Integer,R为Float
class BB implements IUsb<Integer,Float>{

    @Override
    public Float get(Integer integer) {
        return null;
    }

    @Override
    public void hi(Float aFloat) {

    }

    @Override
    public void run(Float r1, Float r2, Integer u1, Integer u2) {

    }
}
interface IUsb<U,R>{
    //接口中的成员默认为静态
    //U u;//错误，静态成员不能使用泛型
    R get(U u);
    void hi(R r);
    void run(R r1,R r2,U u1,U u2);
    //在jdk8中，可以在接口中，使用默认方法，也可以使用泛型

    //实现改接口的类，可以不用实现该方法
    default R method(U u){
        return null;
    }
}
//当我们去实现IA接口时，因为IA在继承IUsb接口时，因此也要实现IUsb中方法，，同时也指定了U为String类型，R为Double类型
//在实现IUsb接口的方法时，使用String替换U，使用Double替换R
class AA implements IA{

    @Override
    public Double get(String s) {
        return null;
    }

    @Override
    public void hi(Double aDouble) {

    }

    @Override
    public void run(Double r1, Double r2, String u1, String u2) {

    }
}
```

### 自定义泛型方法

1. 泛型方法，可以定义在普通类中，也可以定义在泛型类中
2. 当泛型方法调用时，类型会确定
3. public void eat(E e){},修饰符后没有<T,R>,eat方法不是泛型方法，而是使用了泛型

```java
package generic;

import java.util.ArrayList;

public class generic_test8 {
    public static void main(String[] args) {
        car c=new car();
        //1. 当泛型方法调用时，类型会确定
        c.fly("宝马",100);//此时，T-》String，R-》Integer【class java.lang.String----class java.lang.Integer】

        Fish<String, ArrayList> f=new Fish<>();//此时Fish实现类中泛型标识符的T代表String，R代表ArrayList
        f.hello(new ArrayList(),103.f);//class java.util.ArrayList----class java.lang.Float【需要注意的是此时第一个在类定义时，就已经确定
                                        //  而第二个参数是根据你填的值自动判断是什么类型的 】
    }
}
//泛型方法，可以定义在普通类中，也可以定义在泛型类中
class car{
    public void run(){}//普通方法
    public <T,R> void fly(T t,R r){//泛型方法
        System.out.println(t.getClass()+"----"+r.getClass());
    }
}
class Fish<T,R>{//泛型类
    public void fun(){};//普通方法
    public <U,R> void eat(U u,R r){//泛型方法

    }

    //public void eat(E e){},修饰符后没有<T,R>,eat方法不是泛型方法，而是使用了泛型
    //下面这个方法并不是泛型方法，而是使用了泛型
    //需要注意的是泛型方法可以使用类声明的泛型，也可以使用自己声明的泛型
    public void hi(T t){

    }
    //需要注意的是泛型方法可以使用类声明的泛型，也可以使用自己声明的泛型
    public <K> void hello(R r,K k){
        System.out.println(r.getClass()+"----"+k.getClass());
    }
}
```

### 练习2

![image-20220205154849991](https://gitee.com/demon_night/images/raw/master/imgs/202202051648570.png)

- 答案：Integer、Dog、eat方法不行、run方法ok

### 泛型的继承和通配符

1. 泛型不具备继承性【List<Object> l=new ArrayList<ArrayList>();】
2. List<?>:表示任意的泛型类型都可以接受
3. ？extends A：表示上限，可以接受AA或者AA子类
4. ？super 子类类名AA：表示AA类以及AA类的父类，不限于直接父类

```java
package generic;

import java.util.ArrayList;
import java.util.List;

public class generic_test9 {
    public static void main(String[] args) {
        List<Object> l1=new ArrayList<>();
        List<String> l2=new ArrayList<>();
        List<AAA> l3=new ArrayList<>();
        List<BBB> l4=new ArrayList<>();
        List<CCC> l5=new ArrayList<>();

        printCollections1(l1);
        printCollections1(l2);
        printCollections1(l3);
        printCollections1(l4);
        printCollections1(l5);

        //printCollections2(l1);//错误，只能传AAA类或其子类
        //printCollections2(l2);//错误
        printCollections2(l3);
        printCollections2(l4);
        printCollections2(l5);

        printCollections3(l1);
        //printCollections3(l2);//错误，只能传AAA类或其父类
        printCollections3(l3);
        //printCollections3(l4);
        //printCollections3(l5);

    }
    //List<?>:表示任意的泛型类型都可以接受
    public static void printCollections1(List<?> c){
        for(Object object:c){
            System.out.println(object);
        }
    }
    //？extends A：表示上限，可以接受AA或者AA子类
    public static void printCollections2(List<? extends AAA> c){
        for(Object object:c){
            System.out.println(object);
        }
    }
    //？super 子类类名AA：表示AA类以及AA类的父类，不限于直接父类
    public static void printCollections3(List<? super AAA> c){
        for(Object object:c){
            System.out.println(object);
        }
    }

}

class AAA{

}
class BBB extends AAA{

}
class CCC extends BBB{

}
```

### 练习3

![image-20220206155658440](https://gitee.com/demon_night/images/raw/master/imgs/202202061657121.png)

```java
package generic;

import org.junit.jupiter.api.Test;

import java.util.*;

public class generic_test10 {
    public static void main(String[] args) {

    }
    @Test
    public void Junit_test(){
        DAO<User> d=new DAO();

        d.save("01",new User(01,13,"jack"));
        d.save("02",new User(02,17,"Lucy"));
        d.save("03",new User(03,19,"smith"));
        System.out.println(d.get("01"));
        d.update("01",new User(01,16,"mm"));
        List<User> ll=d.list();
        System.out.println(ll.toString());
        d.delete("01");
        ll=d.list();
        System.out.println(ll.toString());
    }
}
class DAO<T>{
    //Map是可以初始化的是因为只要没有放入键值对，Map里面的Node就不会创建，自然不需要知道T是什么类型
    //而对于数组要进行初始化是必须先创建空间的，因此需要知道是什么类型，因此如果创建泛型数组是必须要知道是什么类型的
    Map<String,T> t=new HashMap<>();

    @Test
    public void save(String id,T entity){
        t.put(id,entity);
    }

    public T get(String id){
        return t.get(id);
    }

    public void update(String id, T entity){
        t.put(id,entity);
    }

    public List<T> list(){
        List<T> l=new ArrayList<>();

        //第一种方法
//        Set<Map.Entry<String,T>> s=t.entrySet();
//        Iterator<Map.Entry<String ,T>> iterator=s.iterator();
//        while(iterator.hasNext()){
//            T temp=iterator.next().getValue();
//            l.add(temp);
//        }

        //第二种方法【比较推荐】，装集合用
        l.addAll(t.values());

        return l;
    }

    public void delete(String id){
        t.remove(id);
    }
}
class User{
    private int id;
    private int age;
    private String name;

    public User(int id, int age, String name) {
        this.id = id;
        this.age = age;
        this.name = name;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "User{" +
                "id=" + id +
                ", age=" + age +
                ", name='" + name + '\'' +
                '}';
    }
}
```

# IO流

## IO流介绍

- 分为输入流：读数据；输出流：写数据
- 按照类型来分：字节流：字节输入流、字节输出流；字符流：字符输入流、字符输出流

## 字节流

### 字节流写数据

- InputStream：这个抽象类是表示字节输入流的所有类的超类
- OutputStream：这个抽象类是表示字节输出流所有类的超类
- 子类命名特点：子类名称都是以其父类名作为子类名后缀
- FileOutStream(String name)：创建文件输出流以指定的名称写入文件

![image-20220217124804642](https://gitee.com/demon_night/images/raw/master/imgs/202202171248094.png)

> 常用方法

```java
package Stream;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.nio.charset.StandardCharsets;

public class stream_test1 {
    public static void main(String[] args) throws IOException {
        //创建字节输出流对象,指向文件
        FileOutputStream f=new FileOutputStream("C:\\Users\\Demon Night\\IdeaProjects\\yzk\\src\\Stream\\file\\f.txt");
        //如果该文件不为空，就重新创建1个,可以匿名new
        //FileOutputStream f1=new FileOutputStream(new File("C:\\Users\\Demon Night\\IdeaProjects\\yzk\\f.txt"));
        FileOutputStream f1=new FileOutputStream("C:\\Users\\Demon Night\\IdeaProjects\\yzk\\src\\Stream\\file\\f1.txt");

        //将指定字节写入文件
        f.write(97);//a

        //void write(byte[] b)
        //写 b.length字节从指定字节数组输出流。
        byte[] b={90,100,101};
        f1.write(b);

        //byte[] getBytes():返回字符串所对应的字符数组
        f1.write("abcde".getBytes());

        //void write(byte[] b, int off, int len),左闭右开
        //写 len字节从指定字节数组开始抵消 off输出流。
        f1.write(b,0,2);

        //void close()
        //关闭此输出流并释放与此流相关的任何系统资源。
        f.close();
    }
}

```



# 反射



## 反射概述、获取Class对象

![image-20230326185958567](https://cdn.jsdelivr.net/gh/yzk656/image/202303261859668.png)

![image-20230326190103660](https://cdn.jsdelivr.net/gh/yzk656/image/202303261901723.png)

![image-20230326190208858](https://cdn.jsdelivr.net/gh/yzk656/image/202303261902936.png)





![](https://cdn.jsdelivr.net/gh/yzk656/image/202303261912831.png)

![image-20230326191911421](https://cdn.jsdelivr.net/gh/yzk656/image/202303261919493.png)

## 反射获取Constructor、Field、Method对象

![image-20230326192128091](https://cdn.jsdelivr.net/gh/yzk656/image/202303261921176.png)

![image-20230326192158243](https://cdn.jsdelivr.net/gh/yzk656/image/202303261921325.png)

![image-20230326192805371](https://cdn.jsdelivr.net/gh/yzk656/image/202303261928451.png)

![image-20230326193656453](https://cdn.jsdelivr.net/gh/yzk656/image/202303261936528.png)

![image-20230326193834174](https://cdn.jsdelivr.net/gh/yzk656/image/202303261938264.png)

![image-20230326194224414](https://cdn.jsdelivr.net/gh/yzk656/image/202303261942512.png)

![image-20230326194405240](https://cdn.jsdelivr.net/gh/yzk656/image/202303261944323.png)

![image-20230326194420622](https://cdn.jsdelivr.net/gh/yzk656/image/202303261944700.png)

![image-20230326200125275](https://cdn.jsdelivr.net/gh/yzk656/image/202303262001344.png)

![image-20230326200618651](https://cdn.jsdelivr.net/gh/yzk656/image/202303262006725.png)

![image-20230326200712691](https://cdn.jsdelivr.net/gh/yzk656/image/202303262007777.png)

![image-20230326200901689](https://cdn.jsdelivr.net/gh/yzk656/image/202303262009768.png)

![image-20230326200915582](https://cdn.jsdelivr.net/gh/yzk656/image/202303262009665.png)

![image-20230326202619640](https://cdn.jsdelivr.net/gh/yzk656/image/202303262026721.png)

![image-20230326203132041](https://cdn.jsdelivr.net/gh/yzk656/image/202303262031194.png)

![image-20230326203353890](https://cdn.jsdelivr.net/gh/yzk656/image/202303262033978.png)

## 反射的作用：绕过编译阶段、做企业通用框架

![image-20230326233554019](https://cdn.jsdelivr.net/gh/yzk656/image/202303262335163.png)

![image-20230326233707455](https://cdn.jsdelivr.net/gh/yzk656/image/202303262337553.png)

![image-20230326234441514](https://cdn.jsdelivr.net/gh/yzk656/image/202303262344587.png)

![image-20230326234624420](https://cdn.jsdelivr.net/gh/yzk656/image/202303262346523.png)

![image-20230326234749040](https://cdn.jsdelivr.net/gh/yzk656/image/202303262347139.png)

![image-20230327001053034](https://cdn.jsdelivr.net/gh/yzk656/image/202303270010152.png)

# lambda表达式

## Lambda简介

- Lambda表达式就是一个匿名函数
- Lambda表达式能够对一个接口进行非常简单的实现
- 要求接口中定义的必须要实现的抽象方法只能有一个
- @FunctionalInterface：修饰函数式接口【接口中得抽象方法只有一个】，因此在接口上面最好写一个这个“FunctionalInterface”

```java
package Lambda;

public class Lambda_test1 {
    public static void main(String[] args) {
        //1. 使用接口实现类的
        Comparator compararor=new MyComparator();

        //2. 使用匿名内部类
        Comparator comparator1=new Comparator() {
            public int compare(int a,int b){
                return a-b;
            }
        };

        //3.使用Lambda表达式来实现接口
        Comparator comparator2=(a,b)->a-b;
    }
}

class MyComparator implements Comparator{
    public int compare(int a,int b){
        return a-b;
    }
}

@FunctionalInterface
interface Comparator{
    int compare(int a,int b);
}
```

## Lambda基础语法

```java
package Lambda;

import Lambda.Interface.*;

public class Lambda_test2 {
    public static void main(String[] args) {
        /**
         * Lambda函数基本语法
         * （）；用来描述参数列表
         * {}：用来描述方法体
         * ->：Lambda运算法读作goes to
         */

        //1. 无参数无返回值
        Interface_test1 interface_test1=()->{
            System.out.println("hello world");
        };
        interface_test1.test();//hello world

        //2.无返回值、单个参数
        Interface_test2 interface_test2=(int a)->{
            System.out.println(a);
        };
        interface_test2.test(10);//10

        //3. 无返回值、多个参数
        Interface_test3 interface_test3=(int a,int b)->{
            System.out.println(a+" "+b);
        };
        interface_test3.test(10,11);//10 11

        //4.有返回值，无参数
        Interface_test1_1 interface_test1_1=()->{
            System.out.println("hello");
            return 10;
        };
        System.out.println(interface_test1_1.test());//hello \n 10

        //4.有返回值，单个参数
        Interface_test2_2 interface_test2_2=(int a)->{
            return a*3;
        };
        System.out.println(interface_test2_2.test(10));//30

        //4.有返回值，多个参数
        Interface_test3_3 interface_test3_3=(int a,int b)->{
            return a*b;
        };
        System.out.println(interface_test3_3.test(10,20));//200
    }
}
```

## Lambda语法精简

```java
package Lambda;

import Lambda.Interface.*;

public class Lambda_test3 {
    public static void main(String[] args) {
        /**
         * 语法精简
         * 1.参数
         *  由于在接口得抽象方法中已经定义了参数的类型和数量，所以在Lambda表达式中参数的类型可以省略
         *  备注：如果需要省略类型，则每一个参数的类型都要省略
         */
        Interface_test3 interface_test3=(a,b)->{
            System.out.println("hello world");
        };
        /**
         * 2. 参数小括号
         *  如果参数列表中只有一个参数，则此时小括号可以省略
         */
        Interface_test2 interface_test2=a->{
            System.out.println(a);
        };
        /**
         * 3. 方法大括号
         *  如果方法体中只有一条语句则可以省略大括号
         */
        Interface_test2 interface_test2_21=a->System.out.println(a);
        //4. 如果方法体中只有一条语句且是返回语句，则在大括号省略的同时，也必须省略return
        Interface_test2_2 interface_test2_2=(a)->a*2;;
        Interface_test3_3 interface_test3_3=(a,b)->a*b;
    }
}
```



## Lambda语法进阶

```java
package Lambda;

import Lambda.Interface.Interface_test2_2;

public class Lambda_test4 {
    public static void main(String[] args) {
        //方法引用
        //可以快速的将一个Lambda表达式的实现指向一个已经实现的方法
        //语法：方法的隶属者::方法名

        //注意事项：
        //1.参数数量、类型一定要和接口中定义的一致
        //2.返回值的类型一定要和接口中定义的方法一致

        //这样当我们多次调用时，想要更改表达式时，只需要更改change()方法的代码一次
        Interface_test2_2 interface_test2_2=a->change(a);

        //进阶后
        Interface_test2_2 interface_test2_21=Lambda_test4::change;
    }
    private static int change(int a){
        return a*3;
    }
}
```

> 对于构造方法的引用

```java
package Lambda;

import Lambda.data.person;

public class Lambda_test5 {
    public static void main(String[] args) {
        //如果想要某个对象，这时候则可以引用构造方法，new能够返回一个对象
        person_Creat p1=()->new person();
        person_Creat p2=person::new;
        p1.getPerson();//person类的无参构造方法
        person_Creat1 p3=person::new;
        person p4=p3.getPerson("xiaoming",11);
    }
}
interface person_Creat{
    person getPerson();
}
interface person_Creat1{
    person getPerson(String name,int age);
}
```

> 创建的person类

```java
package Lambda.data;

public class person {
    public String name;
    public int age;

    public person(){
        System.out.println("person类的无参构造方法");
    }

    public person(String name,int age){
        this.name=name;
        this.age=age;
        System.out.println("person类的有参构造方法");
    }

}
```



## Lambda综合案例



## 系统内置函数式接口



## 闭包问题

# 坦克大战

## Java绘图坐标体系

### 介绍

- 坐标原点位于左上角，以像素为单位，在Java坐标系中，第一个是x坐标，表示当前位置为水平方向，距离坐标原点x个像素，第二个是y坐标，表示当前位置为垂直方向，距离坐标原点y个像素
- ![image-20220206213416242](https://gitee.com/demon_night/images/raw/master/imgs/202202062234154.png)

```java
package draw;

import javax.swing.*;
import java.awt.*;

//Frame:框架【对应于1个窗口】
public class draw_circle_test1 extends JFrame{

    //先定义一个面板
    private MyPanel mp =null;

    public static void main(String[] args) {
        /**
         * 1. 当组件第一次在屏幕显示的时候，程序会自动的调用paint()方法来绘制组件
         * 2. 档窗口最小化再最大化是也会调用paint方法
         * 3. 窗口大小发生变化时也会调用
         * 4. repaint函数被调用
         */

        new draw_circle_test1();
    }
    public draw_circle_test1(){
        //初始化面板
        mp=new MyPanel();
        //把面板放到窗口里
        this.add(mp);
        //设置窗口大小
        this.setSize(400,300);

        //退出程序
        this.setDefaultCloseOperation(3);
        this.setVisible(true);
    }
}
//先定义1个MyPanel，继承JPanel，就可以在面板上画图了
class MyPanel extends JPanel{
    @Override
    //1. panel:画板  Graphics：
    public void paint(Graphics g) {//绘图方法
        super.paint(g);//调用父类的方法完成初始化
        g.drawOval(10,10,100,100);
    }
}
```

## 绘图常用方法

```java
package draw;

import javax.swing.*;
import java.awt.*;

//Frame:框架【对应于1个窗口】
public class draw_circle_test1 extends JFrame{

    //先定义一个面板
    private MyPanel mp =null;

    public static void main(String[] args) {
        /**
         * 1. 当组件第一次在屏幕显示的时候，程序会自动的调用paint()方法来绘制组件
         * 2. 档窗口最小化再最大化是也会调用paint方法
         * 3. 窗口大小发生变化时也会调用
         * 4. repaint函数被调用
         */

        new draw_circle_test1();
    }
    public draw_circle_test1(){
        //初始化面板
        mp=new MyPanel();
        //把面板放到窗口里
        this.add(mp);
        //设置窗口大小
        this.setSize(300,300);

        //退出程序
        this.setDefaultCloseOperation(3);
        this.setVisible(true);
    }
}
//先定义1个MyPanel，继承JPanel，就可以在面板上画图了
class MyPanel extends JPanel{
    @Override
    //1. panel:画板  Graphics：
    public void paint(Graphics g) {//绘图方法
        super.paint(g);//调用父类的方法完成初始化
        //g.drawOval(10,10,100,100);

        //演示绘制不同的图形
        //1. 画直线：drawLine
//        g.drawLine(10,10,100,100);

        //画矩形边框
//        g.drawRect(10,10,100,100);

        //设置画笔演示
//        g.setColor(Color.blue);
//        g.fillRect(10,10,100,100);

        //填充椭圆
//        g.setColor(Color.red);
//        g.fillOval(10,10,100,100);

        //花图片
        //1. 获取图片资源
        //易错点：MyPanel,"/":代表在当前项目下
//        Image image=Toolkit.getDefaultToolkit().getImage(MyPanel.class.getResource("/bb.png"));
//        g.drawImage(image,10,10,998,467,this);

        //写字
        //给画笔设置颜色和字体
        g.setColor(Color.red);
        g.setFont(new Font("隶书",1,50));
        //坐标对应于首字的左下角
        g.drawString("北京你好",100,100);

    }
}	
```



# 数据库

## 基础知识

1. 连接到MySQL服务：mysql -h localhost -P 3306 -u root -p密码
   1. -p密码之间不能有空格
   2. 若-p后面没有密码，回车后，会要求输入密码
2. 进入D盘：cd /D 地址
3. my.ini配置

```mysql
[client]
port=3306
default-character-set=utf8
[mysqld]
basedir=D:\mysql-5.7.34-winx64\
datadir=D:\mysql-5.7.34-winx64\data\
port=3306
character_set_server=utf8
skip-grant-tables
```

4. 安装服务：mysqld -install
5. 初始化数据库，生成data文件：mysqld --initalize-insecure--user=mysql
6. 一定要以管理员身份运行cmd
7. 进入mysql管理终端：mysql -u root -p
8. 修改密码

```java
use mysql;#使用数据库，后面有分号
update user set authentication_string=password('密码')where user='root' and Host=’localhost‘；
```

9. 刷新权限：flush privileges
10. 设置完密码后，就需要把”skip-grant-tables“注释掉；

## SQL三层结构

### SQL语句分类

1. DDL：数据定义语句【create 表、库】
2. DML：数据操作语句【增加 insert、修改 update、删除delete】
3. DQL：数据查询语句【select】
4. DCL：数据控制语句【数据管理库：比如用户权限 grant【授权命令】、revoke【收回权限命令】】

### 三层结构

> 数据库-表的本质还是文件

![image-20211213164744716](https://gitee.com/demon_night/images/raw/master/imgs/202201291905922.png)

## 创建数据库

1. character set：指定数据库采用的字符集，如果不指定，默认为utf8
2. COLLATE:指定数据库字符集的校对规则（utf8_bin:区分大小写、utf8_gengeal_ci:不区分大小写）
3. 删除数据库：：drop database 数据库名称
4. 查询表中的内容：SELECT * FROM T1 WHERE NAME ='TOM'
5. 如果创建表时不去指定字符集与校对规则，则默认按照数据库的设置来查找

## 查询数据库

1. 显示所有数据库：SHOW DATABASES【注意有‘s’】
2. 显示创建的数据库的定义信息：SHOW CREATE DATABASE 数据库名称
3. 在创建库、表时，为了规避关键字，可以使用反引号解决：``
4. 删库：DROP DATABASE 库名；

## 备份、恢复数据库

> 备份数据库：在doc窗口执行mysqldump指令

mysqldump -u 登录MySQL服务账号 -p -B 库名 > 保存地址【密码可以再回车后填写】

eg：mysqldump -u root -p -B yzk_db01 > d:\\bank.sql

![image-20211214201600468](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20211214201600468.png)

> 备份数据库中的表[t1为库中的一个表]

mysqldump -u root -p yzk_db01 ti >d:\\yzk_db01_t1

> 恢复数据库1

1. 进入MySQL命令行：就是登录一下MySQL服务
2. 然后输入：source 备份地址【source d:\\bak.sql】

> 恢复数据库2

1. 直接把bak.sql里面的内容粘贴在navicat查询页面再执行也可以恢复

## 创建表

```mysql
CREATE TABLE `user` (
	id INT, 
	`name` VARCHAR(255),
	 `password` VARCHAR(255), 
	 birthday DATE) 
	 CHARACTER SET utf8 COLLATE utf8_bin ENGINE INNODB;#ENGINE：存储引擎
```

## MySQL列类型

列类型——MySQL的数据类型

> 数值类型、文本类型、二进制数据类型、日期类型

1. 数值类型
   1. 整形：tinyint[一个字节]、smallint【两个字节】、mediumint【三个字节】、int【四个字节】、bigint【8个字节】、decimal[M:长度]【字节数由D的长度来确定】
   2. 小数类型：float【单精度：四个字节】、double【双精度：八个字节】、decimal【M：长度、D：小数位数】【字节数由M、D的长度来确定】
2. 文本类型[字符串类型]
   1. char:0~255、varchar：0~2^16-1、text:0~2^16-1、longtext：0~2^32-1
3. 二进制数据类型
   1. blob：0~2^16-1、longblob：0~2^32-1
4. 日期类型
   1. date【日期：年月日】、time【时间：时分秒】、datetime【年月日时分秒】、timestamp【时间戳】、year【年】

## 创建含有整形数据的表

1. 有符号的

```mysql
CREATE TABLE t3 (
	id TINYINT);#默认是有符号的-128~127
INSERT INTO t3 VALUES(127);
SELECT * FROM t3;
```

2. 无符号的

```mysql
CREATE TABLE t2 (
	id TINYINT UNSIGNED);#对于无符号类型的直接在后面添加unsigned：0~255
INSERT INTO t2 VALUES(255);
SELECT * FROM t2;
```

注：执行成功一次insert就会增加一条数据，不管数据是否相同

## 数值型（bit）的使用

```mysql
CREATE TABLE t01(num BIT(8));#创建一个8位的【一个字节】数据空间【1~64】
INSERT INTO t01 VALUES(255);#添加内容
SELECT * FROM t01;#查询内容方式1
SELECT * FROM t01 WHERE num=255;#查询内容方式2
```

## 数值型（小数）的使用

```mysql
CREATE TABLE t02(num1 FLOAT,num2 DOUBLE,num3 DECIMAL(30,20));
INSERT INTO t02 VALUES(12345.12345678912345,12345.12345678912345,12345.12345678912345);
SELECT * FROM t02;

CREATE TABLE t03(id DECIMAL(65));
INSERT INTO t03 VALUES(123456789123456789123456789);
SELECT * FROM t03;
```

1. decimal[M,D]:如果M被省略，默认为10，D被省略，默认为0，M最大65，D最大是30
2. 如果希望小数的精度更高，最好使用decimal
3. 对于超过范围的数据，是不能zz功存放的

## 字符串的使用

```mysql
CREATE TABLE t06 (`name` CHAR);
INSERT INTO t06 VALUES('s');#如果不指定size，则默认为1

CREATE TABLE to7 (`name` VARCHAR(21844));#对于默认的utf8，size大小最大为21844
CREATE TABLE t08 (`name` VARCHAR(32766)) CHAR SET gbk;#对于gbk，size大小最大为32766
DROP TABLE t08
```

1. char（size）：size是字符的长度【最大255个字符】【不写长度默认为1】

2. varchar（size）：size：字节的长度【0~65535”字节“】，但是最大只能使用65532个字节，因为那三个字节用于记录大小
   1. 如果表的编码是utf8，则最大字符数是21844，即size最大就是21844 
   2. size=（65535-3）/3=21844【utf8是三个字节表示一个字符】
   3. 如果表的编码是gbk，size=（65535-3）/2=32766 【gbk类型是两个字节表示一个字符】

3. char（4）和varchar（4）中的4表示字符数，而不是字节，字节数要根据编码类型来确定

4. char（4）是定长，如果你添加两个字符”aa“，也是占用四个空间

5. 而varchar(4)是变长实际占用长度：内容的长度+1~3个字节【记录存放内容长度的】

6. char的优点：查询速度比varchar速度快，所以对于定长最好使用char类型

7. 对于字符串要用单引号引起来

8. 如果varchar不够用时，可以使用Text、mediumtext、longtext

   ```mysql
   CREATE TABLE t09(content1 TEXT,content2 MEDIUMTEXT,content3 LONGTEXT);
   INSERT INTO t09 VALUES('杨振坤','杨振坤123','杨振坤123456');
   SELECT * FROM t09;
   ```

   ![image-20211217190923905](https://gitee.com/demon_night/images/raw/master/imgs/202201291905471.png)

   对于数字字符是一个字符一个字节，对于其他字符是一个字符三个字节【utf8编码类型】

## 日期的使用

```mysql
CREATE TABLE	t10(
				BIRTHDAY DATE,
				JOB_TIME DATEtIME,
				LOGIN_TME TIMESTAMP
				NOT NULL DEFAULT CURRENT_TIMESTAMP#用于赋值为登陆时间
				ON UPDATE CURRENT_TIMESTAMP);
				
INSERT INTO t10(BIRTHDAY,JOB_TIME) VALUES('2021-11-11','2021-11-11 20:20:20');#由于添加参数少一个，因此添加的时候																			  #要指明添加的变量
SELECT * FROM T10;
```

![image-20211217194144146](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20211217194144146.png)

## 创建表【添加，查询】

```mysql
create table `emp`(
				id int,
				`name` varchar(32),
				sex char(1),
				`birthday` date,
				entry_date   date,
				job char(4),
				salary float,
				resume text);
				
select * from emp;

insert into emp values(100,'杨振坤','男','2000-1-1',
								'2020-1-4','寻山',100.3,'干的挺好的');
```

## 修改表

1. 使用alter table语句追加、修改、或删除列
2. 添加列
   1. alter table table_name add(列名  数据类型)
3. 修改列
   1. alter table table_name modify 列名 数据类型
4. 修改表名： rename table 表名 to 新表名
4. 修改列名：alter table table_name 列名 新列名 数据类型
5. 修改表字符集：alter table 表名 character set 字符集；
7. 删除列：alter table table_name  drop 列名【desc 表名：可以查看表的结构】
5. 语句后面添加 not null default ‘ ‘【使之不为空】

```mysql
alter table emp
	add (image varchar(32)) after resume;# 在特定位置添加列
alter table emp modify job varchar(60);# 修改列的数据类型
rename table emp to employee;# 修改表名
alter table employee character set utf8;# 修改表的编码格式
alter table employee change `name` user_name varchar(32) not null default ''# 修改列名
desc employee# 查看表的结构
```

## insert 语句

```mysql
create table goods(
				id int,
				goods_name varchar(10),
				price double);
				select * from employee;
				
insert into goods values(11,'苹果手机',1999.99)
    
insert into employee (id,user_name,sex) values(101,'正如森','男');
insert into employee (id,user_name,sex) values(102,'郑伟','男');
```

1. 创建表---添加数据
2. 添加就算指出变量也要有顺序

注意事项：

1. 插入的数据应与字段的数据类型相同
2. 对于加了单引号的数字，MySQL会自动将其转化成整形
3. 数据的长度应在列的规定的范围内
4. 在values中列出的数据位置必须与加入的列的排列位置相对应
5. 字符和日期型数据必须加上单引号
6. 列允许插入空值（null）【首先该字段必须允许插入空值】
   1. insert into employee (id,user_name,sex) values(102,'郑伟',null);
   2. insert into employee (id,user_name,sex,birthday) values(102,'郑伟',NULL,'2000-1-1');【可以添加默认值，但是不能跳过不填】
7. 允许一下添加多条数据
   1. insert into employee (id,user_name,sex) values(102,'郑伟','男')，(102,'郑伟','男');
8. 如果是给表中的所有字段添加数据可以不用写字段名称
9. 当不给某个字段值时，如果有默认值就会添加默认值，**否则就会报错**
   1. ![image-20211220231405967](https://gitee.com/demon_night/images/raw/master/imgs/202201291905770.png)
   2. insert into employee (id,user_name,sex) values(102,'郑伟','男');【只添加了几个特定值】
10. 如果我们希望指定某个列的默认值，可以在创建表时指定
    1. create table goods(
       				id int,
          				goods_name varchar(10),
          				price double not null default 100);

## update语句

```mysql
UPDATE employee SET salary=5000【不加限制条件，作用与所有列】

UPDATE employee set salary =3000 WHERE user_name='杨振坤'【添加限制条件】

select * from employee
    
UPDATE employee set salary =salary+1000 WHERE user_name='杨振坤'【将薪水在原有基础上增加1000】
```

1. update 语句可以用于更新原有表中的序列
2. set子句指示要修改那些列和要给予哪些值
3. where子句指定要更新哪些行，如果没有where子句就更新所有行**【慎用】**
4. 如果要修改多个字段，可以通过set 字段1=值1，字段2=值2。。。

## delete语句

```mysql
DELETE from employee where user_name='杨振坤'【删除特定语句】

DELETE FROM employee;【删除所有语句】
```

1. delete语句不能删除某一列的值，只能使用update将某一列置 “ null ”或‘’
2. 使用delete语句只能删除记录，不能删除表本身，要想删除表只能：drop table 表名

## select语句

<img src="C:\Users\Demon Night\Desktop\图片\image-20211230191415577.png" alt="image-20211230191415577" style="zoom:50%;" />

```mysql
CREATE TABLE student (
	id INT NOT NULL DEFAULT 1,
	`name` VARCHAR ( 20 ) NOT NULL DEFAULT '',
	chinese FLOAT NOT NULL DEFAULT 0.0,
	english FLOAT NOT NULL DEFAULT 0.0,
	math FLOAT NOT NULL DEFAULT 0.0 
);
SELECT
	* 
FROM
	student
	
INSERT INTO student(id,`name`,chinese,english,math) VALUES(1,'杨振坤',100,3,40);
INSERT INTO student(id,`name`,chinese,english,math) VALUES(2,'张飞',11,22,33);
INSERT INTO student(id,`name`,chinese,english,math) VALUES(3,'宋江',22,45,67);
INSERT INTO student(id,`name`,chinese,english,math) VALUES(4,'关羽',12,32,43);
INSERT INTO student(id,`name`,chinese,english,math) VALUES(5,'赵云',24,35,40);
INSERT INTO student(id,`name`,chinese,english,math) VALUES(1,'欧阳',22,32,40);
INSERT INTO student(id,`name`,chinese,english,math) VALUES(1,'黄蓉',23,34,46);

UPDATE student set id=6 WHERE `name`='欧阳'

UPDATE student set id=7 WHERE `name`='黄蓉'

SELECT `name`,english from student  #查询表中所有学生的姓名和英语成绩
select DISTINCT english FROM student#过滤掉重复数据：distinct
select DISTINCT `name`,english FROM student#只有查询地记录中每个字段都相同才会去重

SELECT `name`,(chinese+english+math) from student# 统计每个学生的总分
SELECT `name`,(chinese+english+math+10) from student# 在所有学生总分+10分
SELECT	`name` AS '名字',(chinese+english+math) AS '总分' FROM student# 使用别名表示名字、总分

SELECT * from student where `name`='赵云'# 查询姓名为赵云地学生的成绩
SELECT * from student where english>50# 查询英语成绩大于50的同学
select * from student where (chinese+english+math)>100# 查询总分大于100的同学

SELECT * FROM student where math>60 AND id>4
SELECT * FROM student where english>chinese# 查询英语成绩大于语文成绩的
SELECT * FROM student where(chinese+english+math)>10 AND math<chinese AND `name` LIKE '杨%'# 杨%表示名字以杨开头的就可以【模糊查询】

```

### 练习1

```mysql
SELECT * from student where english>=10 AND english<=30
select * from student where english between 10 and 30# 查询成绩位于10-30之间的，between是闭区间

SELECT * from student where math=33 or math=40 or math=34
SELECT * from student where math IN(33,40)# 查询数学分数为33、40的学生

SELECT * from student where english>=10 AND math>=30# 查询数学大于40，英语大于10分的学生
```

### 练习2

```mysql
SELECT * from student where chinese between 50 and 100
SELECT * from student where (chinese+english+math) IN(143,144,145)# 查询总分为143,144,145的学生
SELECT * from student where `name` LIKE '杨%' OR `name` LIKE '张%'# 查询所有姓杨、张的学生
SELECT * from student where math-chinese>30# 查询数学比语文多三十分的学生
```

### 练习3

```mysql
SELECT * from student ORDER BY math;# order by默认为升序
SELECT `name`,(chinese+english+math) AS total_score from student ORDER BY total_score DESC # desc表示降序显示
SELECT `name`,(chinese+english+math) AS total_score from student WHERE `name` LIKE '黄%' ORDER BY total_score# 总分升序排序显示【并且模糊查询】
```

##  分组

```mysql
# 显示每个部门的每种岗位的平均工资和最低工资
SELECT AVG(sal),MIN(sal),deptno,job
				FROM emp GROUP BY deptno ,job#   先按部门分、再按岗位分
				
# 对分组后的数据进行过滤
# 显示平均工资低于两千的部门号和他的平均工资
SELECT avg(sal),deptno from emp group by depton HAVING AVG(sal)<2000 # 如果使用了别名会失败
```

## 字符串相关函数

```mysql
# 演示字符串相关函数的使用
# CHARSET(str) 返回字符串的的字符集形式
SELECT CHARSET(name) FROM student 

# CONCAT(str1,str2,...) 连接字符串，将多个列拼接成一列
SELECT CONCAT(`name`,'语文成绩：',chinese) from student

# INSTR(str,substr),返回substring在string出现的位置，没有则返回0【返回的是开头的位置,从1开始数】
# DUAL为亚元表，系统表，可以作为测试表使用
SELECT INSTR('yyyyyzzzzz','zzzz') from DUAL

# UCASE(str)转换成大写 、LCASE(str)转换成小写
SELECT UCASE(`name`) FROM student

# LEFT(str,len) 从str的左边取len个字符
# RIGHT(str,len) 从str的右边去len个字符
SELECT LEFT(`name`,2) from student

# LENGTH(str)，求str的长度[按照字节]
SELECT LENGTH(`name`) from student

# REPLACE(str,from_str,to_str) 在str中用to_str替换from_str
SELECT `name`,REPLACE(chinese,100,0) from student

# STRCMP(expr1,expr2),逐字符比较两字符串
SELECT STRCMP('hsp','jsp') from DUAL

# SUBSTRING(str FROM pos FOR len) 从str的pose位置【从1开始计算】，取len个字符
SELECT SUBSTRING(`name`,1,2) from student

# LTRIM(str) 去除前端空格 RTRIM(str) 去除后端空格
# TRIM(str) 去除前后端空格
SELECT LTRIM('    hsp') FROM DUAL;
```

### 练习1

> 以首字母大写的形式显示所有员工name表小的姓名

```mysql
SELECT CONCAT(UCASE(SUBSTRING(name,1,1)),SUBSTRING(name,2)) FROM t15
```

1. 注意此处用的字段是name而不是 `name``,当然name建的字段有加引号的，也可以是不加引号的 
2. 如果substring从某个位置到最后，就可以不用写substring（str，x，y）中y的值

## 数学函数

```mysql
# 数学函数

# ABS(X) 求绝对值
SELECT ABS(-10) from dual

# BIN(N) 将十进制转换成二进制
SELECT BIN(10) from dual

# CEILING(X) 向上取整 得到比x大的数
# FLOOR(X) 向下取整，得到比x小的数
SELECT CEILING(-1.1) from DUAL

# CONV(N,from_base,to_base) 将N从from_base进制转换成to_base进制
SELECT CONV(8,10,2) from DUAL

# FORMAT(X,D) 保留小数位数【四舍五入】
SELECT FORMAT(34.125,2) from dual

# HEX(N_or_S) 转换成16进制
SELECT HEX(16) from dual

# LEAST(value1,value2,...) 求最小值
SELECT LEAST(1,0,-1) from dual

# MOD(N,M) 对n进行求余
SELECT MOD(10,3) from DUAL

# RAND() 随机函数 ，范围是【0~1】
SELECT RAND() from DUAL
# 如果想要每次生成的数不变，就给个种子
SELECT RAND(3) FROM DUAL
```

## 日期、时间函数

```mysql
# CURRENT_DATE 当前日期
SELECT CURRENT_DATE() FROM dual

# CURRENT_TIME 当前时间
SELECT CURRENT_TIME() FROM DUAL

# CURRENT_TIMESTAMP() 当前时间戳【日期、时分秒】
SELECT CURRENT_TIMESTAMP() FROM DUAL
select now() from dual # 和时间戳的功能相同
```

### 练习1

```mysql
create table mes( id INT,
							content VARCHAR(20),
							send_time datetime);
							
select * from mes;
							
INSERT into mes VALUES(1,'北京新闻',CURRENT_TIMESTAMP())
INSERT into mes VALUES(2,'上海新闻',now())
INSERT into mes VALUES(3,'广州新闻',NOW())

# 只显示日期不显示时间
SELECT id,content,DATE(send_time) from mes

# 查询10分钟内发布的新闻
# interval:间隔
select * from mes where date_add(send_time,interval 100 minute)> NOW(); 
SELECT * from mes WHERE DATE_SUB(now(),interval 100 minute)<=send_time;

# 相差多少天
select	DATEDIFF('2022-01-01','2001-01-01') from DUAL
```

### 练习2

```mysql
# 查询自己活了多少天
select DATEDIFF(NOW(),'2001-01-14') from DUAL

# 查询如果自己能活到80岁，自己还能活多少天
select DATEDIFF(DATE_ADD('2001-01-14',interval 80 YEAR),NOW()) from DUAL
```

### 练习3

```mysql
# 如果只想返回当前时间的部分内容
select YEAR(NOW()) from DUAL

# UNIX_TIMESTAMP()返回的是1970-1-1到现在的秒数
select UNIX_TIMESTAMP() from DUAL

# FROM_UNIXTIME(unix_timestamp) 可以把秒数转换成指定格式的日期
SELECT FROM_UNIXTIME('1641191516l','%Y-%m-%d') from DUAL 
SELECT FROM_UNIXTIME('1641191516l','%Y-%m-%d %H:%i:%s') from DUAL 
```

### 细节

1. date_add()后面的interval可以是year、month、day、hour、minute、second
2. date_sub()后面的interval可以是year、month、day、hour、minute、second
3. datediff（d1，d2）得到的是天数，而且是d1-d2的天数，因此可以是负数
4. 这四个函数的日期类型可以是date、datetime、datestamp

# Java数据结构与算法

## 优先队列

1. ![image-20220422151927551](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220422151927551.png)
2. ![image-20220422152907909](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220422152907909.png)
   1. 先进行优先级比较，优先级相同的按照添加的顺序【也就是按照队列】

> 单调队列

1. ![image-20220422213619676](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220422213619676.png)
   1. 单调队列：下标从左到右依次递增，对应的值是从左到右依次递减
   2. 多余的元素：如果添加一个元素，比前面的两项大，那两项就叫做多余元素
      1. <img src="C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220422214011015.png" alt="image-20220422214011015" style="zoom: 50%;" />
2. ![](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220422214618058.png)
3. ![image-20220422214601042](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220422214601042.png)
4. ![image-20220422214856287](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220422214856287.png)
5. 

# BufferedReader

此流为字符缓冲流，他提供了一个readLine()方法，可以从流中一次一行的读取文本

读取文件

1. 先创建节点流
2. 创建一个缓冲流，对节点流进行包装
3. 使用readLine() 方法读取文本
4. 关闭缓冲流

```java
package acwing;

import java.io.BufferedReader;
import java.io.FileReader;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception{
        FileReader fr=new FileReader("E:/io.txt");//创建一个节点流
        BufferedReader br=new BufferedReader(fr);//创建一个缓冲流，对节点流进行包装
        String str=br.readLine();
        System.out.println(str);
        br.close();//关闭缓冲流
    }
}

```

读取输入

```java
package acwing;

import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception{
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));//创建一个缓冲流，对节点流进行包装
        String str=br.readLine();
        System.out.println(str);

        br.close();//关闭缓冲流
    }
}
```



# MySQL

```mysql
-- ------------------------------------> 多表查询 <--------------------------------------------
-- 准备数据
create table dept(
    id   int auto_increment comment 'ID' primary key,
    name varchar(50) not null comment '部门名称'
)comment '部门表';

create table emp(
    id  int auto_increment comment 'ID' primary key,
    name varchar(50) not null comment '姓名',
    age  int comment '年龄',
    job varchar(20) comment '职位',
    salary int comment '薪资',
    entrydate date comment '入职时间',
    managerid int comment '直属领导ID',
    dept_id int comment '部门ID'
)comment '员工表';

-- 添加外键
alter table emp add constraint fk_emp_dept_id foreign key (dept_id) references dept(id);

INSERT INTO dept (id, name) VALUES (1, '研发部'), (2, '市场部'),(3, '财务部'), (4, '销售部'), (5, '总经办'), (6, '人事部');
INSERT INTO emp (id, name, age, job,salary, entrydate, managerid, dept_id) VALUES
            (1, '金庸', 66, '总裁',20000, '2000-01-01', null,5),

            (2, '张无忌', 20, '项目经理',12500, '2005-12-05', 1,1),
            (3, '杨逍', 33, '开发', 8400,'2000-11-03', 2,1),
            (4, '韦一笑', 48, '开发',11000, '2002-02-05', 2,1),
            (5, '常遇春', 43, '开发',10500, '2004-09-07', 3,1),
            (6, '小昭', 19, '程序员鼓励师',6600, '2004-10-12', 2,1),

            (7, '灭绝', 60, '财务总监',8500, '2002-09-12', 1,3),
            (8, '周芷若', 19, '会计',48000, '2006-06-02', 7,3),
            (9, '丁敏君', 23, '出纳',5250, '2009-05-13', 7,3),

            (10, '赵敏', 20, '市场部总监',12500, '2004-10-12', 1,2),
            (11, '鹿杖客', 56, '职员',3750, '2006-10-03', 10,2),
            (12, '鹤笔翁', 19, '职员',3750, '2007-05-09', 10,2),
            (13, '方东白', 19, '职员',5500, '2009-02-12', 10,2),

            (14, '张三丰', 88, '销售总监',14000, '2004-10-12', 1,4),
            (15, '俞莲舟', 38, '销售',4600, '2004-10-12', 14,4),
            (16, '宋远桥', 40, '销售',4600, '2004-10-12', 14,4),
            (17, '陈友谅', 42, null,2000, '2011-10-12', 1,null);
```





## 多表关系

![image-20230714153851623](https://cdn.jsdelivr.net/gh/yzk656/image/202307141538727.png)

![image-20230714153927191](https://cdn.jsdelivr.net/gh/yzk656/image/202307141539276.png)



![image-20230714160654096](https://cdn.jsdelivr.net/gh/yzk656/image/202307141606189.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307141610455.png)

## 多表查询概述

![image-20230714162430436](https://cdn.jsdelivr.net/gh/yzk656/image/202307141624528.png)

![image-20230714162717296](https://cdn.jsdelivr.net/gh/yzk656/image/202307141627372.png)

## 内连接

![image-20230714164056500](https://cdn.jsdelivr.net/gh/yzk656/image/202307141640592.png)

## 外连接

![image-20230714164218567](https://cdn.jsdelivr.net/gh/yzk656/image/202307141642661.png)

![image-20230714164413476](https://cdn.jsdelivr.net/gh/yzk656/image/202307141644549.png)

## 自连接

![image-20230714164649307](https://cdn.jsdelivr.net/gh/yzk656/image/202307141646390.png)

## 联合查询

![image-20230714181924500](https://cdn.jsdelivr.net/gh/yzk656/image/202307141819580.png)

![image-20230714202605628](https://cdn.jsdelivr.net/gh/yzk656/image/202307142026692.png)

![image-20230714182146031](https://cdn.jsdelivr.net/gh/yzk656/image/202307141821117.png)

## 子查询

![image-20230714202810172](https://cdn.jsdelivr.net/gh/yzk656/image/202307142028248.png)

### 标量子查询

![image-20230714214232659](https://cdn.jsdelivr.net/gh/yzk656/image/202307142142753.png)

```mysql
select * from emp where dept_id = (select id from dept where name = '销售部');

select * from emp where entrydate > (select entrydate from emp where name = '方东白');
```

### 列子查询

![image-20230714214425549](https://cdn.jsdelivr.net/gh/yzk656/image/202307142144629.png)

```mysql
select id from dept where name='财务部';
select salary from emp where dept_id = (select id from dept where name='财务部');

select * from emp where salary > any (select salary from emp where dept_id = (select id from dept where name='研发部'));
```

### 行子查询

![image-20230714221350383](https://cdn.jsdelivr.net/gh/yzk656/image/202307142213438.png)

```mysql
select * from emp where (salary,managerid) = (select salary,managerid from emp where name = '张无忌');
```

### 表子查询

![image-20230714222352085](https://cdn.jsdelivr.net/gh/yzk656/image/202307142223149.png)

```mysql
select * from emp where (job,salary) in (select job,salary from emp where name = '鹿杖客' or name = '宋远桥');

select e.*,d.* from (select * from emp where entrydate > '2006-01-01') e left join dept d on e.dept_id = d.id;
```

## 多表查询案例

![image-20230714223442183](https://cdn.jsdelivr.net/gh/yzk656/image/202307142234283.png)

```mysql
select e.name,e.age,e.job,d.* from emp e left join dept d on e.dept_id = d.id;

select e.name,e.age,e.job,d.* from emp e left join dept d on e.dept_id = d.id where e.age < 30;

select * from dept where id in (select dept_id from emp);

select e.*,d.name from emp e left join dept d on e.dept_id = d.id where age > 40;

select e.*, s.grade from emp e,salgrade s where e.salary >= s.losal and e.salary <= s.hisal;

select e.*,s.grade from (select * from emp where dept_id = (select id from dept where dept.name = '研发部')) e,salgrade s where e.salary >= s.losal and e.salary <= s.hisal;
select e.*,s.grade from emp e,dept d,salgrade s where e.dept_id=d.id and (e.salary >= s.losal and e.salary <= s.hisal) and d.name = '研发部';

select avg(salary) from emp where dept_id = (select id from dept where dept.name = '研发部');
select avg(e.salary) from emp e,dept d where e.dept_id = d.id and d.name = '研发部';

select * from emp where salary > (select salary from emp where name = '灭绝');

select * from emp where salary > (select avg(salary) from emp);

select * from emp e2 where e2.salary < (select avg(salary) from emp e where e.dept_id = e2.dept_id);

select d.id,d.name , (select count(*) from emp e where e.dept_id = d.id) '人数' from dept d;

无
```

![image-20230714232504184](https://cdn.jsdelivr.net/gh/yzk656/image/202307142325243.png)

![image-20230714232959878](https://cdn.jsdelivr.net/gh/yzk656/image/202307142329955.png)

## 总结

![image-20230715003715301](https://cdn.jsdelivr.net/gh/yzk656/image/202307150037410.png)



# 代理模式

![image-20230717160704997](https://cdn.jsdelivr.net/gh/yzk656/image/202307171607078.png)

![image-20230717155426788](https://cdn.jsdelivr.net/gh/yzk656/image/202307171554895.png)

![image-20230717155638991](https://cdn.jsdelivr.net/gh/yzk656/image/202307171556046.png)

![image-20230717160002118](https://cdn.jsdelivr.net/gh/yzk656/image/202307171600205.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307172135792.png)

![image-20230717160629179](https://cdn.jsdelivr.net/gh/yzk656/image/202307171606243.png)

## 静态代理

![image-20230717162254483](https://cdn.jsdelivr.net/gh/yzk656/image/202307171622556.png)

![image-20230717162313765](https://cdn.jsdelivr.net/gh/yzk656/image/202307171623834.png)

![image-20230717162626344](https://cdn.jsdelivr.net/gh/yzk656/image/202307171626413.png)

![image-20230717214149908](https://cdn.jsdelivr.net/gh/yzk656/image/202307172141992.png)

![image-20230717215553294](https://cdn.jsdelivr.net/gh/yzk656/image/202307172155366.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307172157114.png)

![image-20230717220124832](https://cdn.jsdelivr.net/gh/yzk656/image/202307172201899.png)

## jdk动态代理

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307172351398.png)

```java
public class TransactionHandler implements InvocationHandler {

    //需要代理的目标对象
    private Object object;
    //增强类对象
    private DaoTransaction daoTransaction;

    public TransactionHandler(DaoTransaction daoTransaction, Object object) {
        this.daoTransaction = daoTransaction;
        this.object = object;
    }


    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        Object ret = null;

        //判断当前方法是不是save方法，是才做事务操作
        if ("save".equals(method.getName())) {
            daoTransaction.before();
            ret = method.invoke(object, args);
            daoTransaction.after();
        } else {
            ret = method.invoke(object, args);
        }

        return ret;
    }
}
```

测试

```java
    @Test
    public void testSave() {
        //增强类
        DaoTransaction daoTransaction = new DaoTransaction();
        //目标类
        IStudentService studentService = new StudentServiceImpl();

        //方法拦截处理器
        TransactionHandler transactionHandler = new TransactionHandler(daoTransaction, studentService);

        //获取代理实例对象
        IStudentService proxyStudentService =(IStudentService) Proxy.newProxyInstance(StudentServiceImpl.class.getClassLoader(),
                StudentServiceImpl.class.getInterfaces(), transactionHandler);

        proxyStudentService.save();
        proxyStudentService.query(1L);

        saveProxyClass("E:\\Code\\homework\\jdk-proxy-02\\src\\");
    }
```

## JDK动态代理原理分析

IDEA 测试 JDK 动态代理找不到符号 ProxyGenerator

​	将 JDK 版本更换为 JDK8 即可。

![image-20230718010252044](https://cdn.jsdelivr.net/gh/yzk656/image/202307180102129.png)

生成字节码反编译

```java
//
// Source code recreated from a .class file by IntelliJ IDEA
// (powered by FernFlower decompiler)
//

import cn.yzk.domain.Student;
import cn.yzk.service.IStudentService;
import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;
import java.lang.reflect.UndeclaredThrowableException;

public final class $Proxy extends Proxy implements IStudentService {
    private static Method m1;
    private static Method m4;
    private static Method m3;
    private static Method m2;
    private static Method m0;

    public $Proxy(InvocationHandler var1) throws  {
        super(var1);
    }

    public final boolean equals(Object var1) throws  {
        try {
            return (Boolean)super.h.invoke(this, m1, new Object[]{var1});
        } catch (RuntimeException | Error var3) {
            throw var3;
        } catch (Throwable var4) {
            throw new UndeclaredThrowableException(var4);
        }
    }

    public final Student query(Long var1) throws  {
        try {
            return (Student)super.h.invoke(this, m4, new Object[]{var1});
        } catch (RuntimeException | Error var3) {
            throw var3;
        } catch (Throwable var4) {
            throw new UndeclaredThrowableException(var4);
        }
    }

    public final void save() throws  {
        try {
            super.h.invoke(this, m3, (Object[])null);
        } catch (RuntimeException | Error var2) {
            throw var2;
        } catch (Throwable var3) {
            throw new UndeclaredThrowableException(var3);
        }
    }

    public final String toString() throws  {
        try {
            return (String)super.h.invoke(this, m2, (Object[])null);
        } catch (RuntimeException | Error var2) {
            throw var2;
        } catch (Throwable var3) {
            throw new UndeclaredThrowableException(var3);
        }
    }

    public final int hashCode() throws  {
        try {
            return (Integer)super.h.invoke(this, m0, (Object[])null);
        } catch (RuntimeException | Error var2) {
            throw var2;
        } catch (Throwable var3) {
            throw new UndeclaredThrowableException(var3);
        }
    }

    static {
        try {
            m1 = Class.forName("java.lang.Object").getMethod("equals", Class.forName("java.lang.Object"));
            m4 = Class.forName("cn.yzk.service.IStudentService").getMethod("query", Class.forName("java.lang.Long"));
            m3 = Class.forName("cn.yzk.service.IStudentService").getMethod("save");
            m2 = Class.forName("java.lang.Object").getMethod("toString");
            m0 = Class.forName("java.lang.Object").getMethod("hashCode");
        } catch (NoSuchMethodException var2) {
            throw new NoSuchMethodError(var2.getMessage());
        } catch (ClassNotFoundException var3) {
            throw new NoClassDefFoundError(var3.getMessage());
        }
    }
}
```

![image-20230718083503486](https://cdn.jsdelivr.net/gh/yzk656/image/202307180835623.png)

1. 对于静态代理是代理类与被代理类是在编译期间确定的，每一个代理类只能为一个接口服务，这样的话，程序开发中就会产生很多代理
2. 对于动态代理是代理类与被代理类是运行期间确定的，通过编译生成的字节码文件反射出来被代理类，这样你加载哪个类，我就是生成哪个代理类，我实现和被代理类一样的接口
3. 被代理类相当是被 代理类包装了一层

![image-20230718100547893](https://cdn.jsdelivr.net/gh/yzk656/image/202307181005014.png)

- 对于动态代理，只需要传入被代理类对象、被代理类实现的接口、方法拦截器就可以动态创建出一个代理类的实例，对于不同的被代理类，可以创建出不同的代理类对象实例
- 首先创建一个代理对象，代理对象实现对应的接口，就能拿到对应的方法，拿到方法后就走方法拦截器，通过代理对象就可以调用对应的方法
- 通过实现接口，获取到接口里面的所有方法
- 通过Proxy创建代理类实例
- 通过反射机制，获取一个个的方法对象
- 使用InvocarionHandler接口中的Invoke方法，实现业务增强

## cglib动态代理

![image-20230718103703249](https://cdn.jsdelivr.net/gh/yzk656/image/202307181037323.png)

![image-20230718104121645](https://cdn.jsdelivr.net/gh/yzk656/image/202307181041722.png)

![image-20230718104133482](https://cdn.jsdelivr.net/gh/yzk656/image/202307181041564.png)

![image-20230718104927851](https://cdn.jsdelivr.net/gh/yzk656/image/202307181049931.png)

![image-20230718105803215](https://cdn.jsdelivr.net/gh/yzk656/image/202307181058297.png)

![image-20230718113628718](https://cdn.jsdelivr.net/gh/yzk656/image/202307181136805.png)

- 对于代理类的save方法是继承被代理类的save方法，然后如果发现需要增强，则执行增强的Interceptor里面的方法，如果不需要，只调用父类的save

![image-20230718114509248](https://cdn.jsdelivr.net/gh/yzk656/image/202307181145348.png)

- 通过继承的方式获取到目标对象的方法
- 通过传递方法拦截器MethodInterceptor实现方法拦截，在这里做具体的增强
- 调用生成的代理类对象具体执行重写save方法，直接调用方法拦截器里面的interceptor方法
- 前后增加了增强操作，从而实现了不修改目标代码实现业务增强

## 动态代理总结

![image-20230718120141319](https://cdn.jsdelivr.net/gh/yzk656/image/202307181201403.png)

- 静态代理是编译时就已经确定的代理，需要手动编写代理类，代理类与被代理类实现同样的接口

- 动态代理分为jdk动态代理、cglib动态代理

  - 动态代理是在运行时生成的代理，不需要事先编写好代理类的代码，生成动态代理主要依靠的是Java反射机制，通过反射机制在运行时动态地创建代理类对象

  - 对于jdk代理，只能代理接口，而不能代理具体的类

  - > - 定义一个接口，该接口包含被代理对象的方法。
    > - 创建一个实现 InvocationHandler 接口的代理处理类，该类中实现 invoke 方法，在该方法中可以添加额外的逻辑。
    > - 使用 Proxy 类的静态方法 newProxyInstance() 创建代理对象，传入被代理类的类加载器、接口数组以及代理处理类的实例。
    > - 通过代理对象调用方法时，会触发代理处理类的 invoke 方法，从而执行代理逻辑。

  - 对于cglib代理，不只能代理接口还能代理类

    > - 定义一个类，该类即为被代理的类。
    > - 创建一个 Callback 类，实现 MethodInterceptor 接口，在该类中可以添加额外的逻辑。
    > - 使用 Enhancer 类创建代理对象，设置被代理类的类对象和 Callback 对象。
    > - 通过代理对象调用方法时，会触发 Callback 对象的 intercept 方法，从而执行代理逻辑。

> jdk代理与cglib代理

当谈到动态代理时，通常会提到两个常用的库：JDK 动态代理和 CGLIB 动态代理。它们都提供了在运行时生成代理类的能力，但使用不同的实现方式。

1. JDK 动态代理：
JDK 动态代理是 Java 标准库提供的一种动态代理方式，它依赖于 Java 的反射机制。JDK 动态代理只能代理接口，而不能代理具体的类。

JDK 动态代理的工作原理如下：
- 定义一个接口，该接口包含被代理对象的方法。
- 创建一个实现 InvocationHandler 接口的代理处理类，该类中实现 invoke 方法，在该方法中可以添加额外的逻辑。
- 使用 Proxy 类的静态方法 newProxyInstance() 创建代理对象，传入被代理类的类加载器、接口数组以及代理处理类的实例。
- 通过代理对象调用方法时，会触发代理处理类的 invoke 方法，从而执行代理逻辑。

以下是使用 JDK 动态代理的示例：

```java
import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;

// 定义接口
public interface UserService {
    void save();
}

// 实现接口的类
public class UserServiceImpl implements UserService {
    public void save() {
        System.out.println("Saving user...");
    }
}

// 代理处理类
public class UserServiceProxy implements InvocationHandler {
    private Object target;

    public UserServiceProxy(Object target) {
        this.target = target;
    }

    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        System.out.println("Before saving user...");
        Object result = method.invoke(target, args);
        System.out.println("After saving user...");
        return result;
    }
}

// 使用示例
public class Main {
    public static void main(String[] args) {
        UserService userService = new UserServiceImpl();
        UserService proxy = (UserService) Proxy.newProxyInstance(
                userService.getClass().getClassLoader(),
                userService.getClass().getInterfaces(),
                new UserServiceProxy(userService));

        proxy.save();
    }
}
```

在上述示例中，我们定义了一个 `UserService` 接口，并实现了一个具体的类 `UserServiceImpl`。然后，我们创建了一个代理处理类 `UserServiceProxy`，实现了 `InvocationHandler` 接口，在 `invoke` 方法中添加了额外的逻辑。最后，通过调用 `Proxy.newProxyInstance()` 方法创建代理对象，并使用该对象调用方法。

2. CGLIB 动态代理：
CGLIB（Code Generation Library）是一个基于字节码生成的开源库，它可以在运行时生成代理类。与 JDK 动态代理不同，CGLIB 动态代理可以代理具体的类，而不仅限于接口。

CGLIB 动态代理的工作原理如下：
- 定义一个类，该类即为被代理的类。
- 创建一个 Callback 类，实现 MethodInterceptor 接口，在该类中可以添加额外的逻辑。
- 使用 Enhancer 类创建代理对象，设置被代理类的类对象和 Callback 对象。
- 通过代理对象调用方法时，会触发 Callback 对象的 intercept 方法，从而执行代理逻辑。

以下是使用 CGLIB 动态代理的示例：

```java
import net.sf.cglib.proxy.MethodInterceptor;
import net.sf.cglib.proxy.MethodProxy;
import net.sf.cglib.proxy.Enhancer;

// 被代理的类
public class UserService {
    public void save() {
        System.out.println("Saving user...");
    }
}

// Callback 类
public class UserServiceInterceptor implements MethodInterceptor {
    public Object intercept(Object obj, Method method, Object[] args, MethodProxy proxy) throws Throwable {
        System.out.println("Before saving user...");
        Object result = proxy.invokeSuper(obj, args);
        System.out.println("After saving user...");
        return result;
    }
}

// 使用示例
public class Main {
    public static void main(String[] args) {
        Enhancer enhancer = new Enhancer();
        enhancer.setSuperclass(UserService.class);
        enhancer.setCallback(new UserServiceInterceptor());

        UserService proxy = (UserService) enhancer.create();
        proxy.save();
    }
}
```

在上述示例中，我们创建了一个 `UserService` 类作为被代理类。然后，我们定义了一个 `UserServiceInterceptor` 类，实现了 `MethodInterceptor` 接口，在 `intercept` 方法中添加了额外的逻辑。最后，通过 `Enhancer` 类创建代理对象，并设置被代理类和回调对象。

总结：
JDK 动态代理和 CGLIB 动态代理都提供了在运行时生成代理类的能力。JDK 动态代理只能代理接口，而 CGLIB 动态代理可以代理具体的类。JDK 动态代理依赖于 Java 的反射机制，而 CGLIB 动态代理依赖于 CGLIB 库。选择使用哪种动态代理方式，取决于具体的需求和场景。





# 网络编程

## 网络编程概述

CS、BS

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307210847532.png)

### IP地址

![image-20230721084840388](https://cdn.jsdelivr.net/gh/yzk656/image/202307210848466.png)

![image-20230721085444095](https://cdn.jsdelivr.net/gh/yzk656/image/202307210854186.png)

![image-20230721154411430](https://cdn.jsdelivr.net/gh/yzk656/image/202307211544571.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307211601113.png)

![image-20230721160520263](https://cdn.jsdelivr.net/gh/yzk656/image/202307211605349.png)

## 学习

# 枚举

![image-20231003134748836](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310031347997.png)

![image-20231003134848998](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310031348125.png)

两者区别

![image-20231003135244724](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310031352861.png)

![image-20231003152719908](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310031527142.png)

![image-20231003153006058](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310031530121.png)

![image-20231003153014615](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310031530674.png)

![image-20231003153242509](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310031532582.png)

![image-20231003155714921](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310031557053.png)

对于dto放的是post请求参数对应的属性

po是对应表的属性

query是对应的get请求的属性

vo是返回给前端的属性

> 主键生成策略

![image-20231003205638829](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310032056044.png)

![image-20231003210149184](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310032101272.png)

> 建议使用jackJson

![image-20231003211026812](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310032110945.png)

![image-20231003211139666](https://cdn.jsdelivr.net/gh/yzk656/image/img/202310032111744.png)
