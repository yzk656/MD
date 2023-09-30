# JAVA八股文

## JDK、JRE、JVM三者区别和联系

1. JDK：java开发工具
2. JRE：java运行时环境
3. JVM：java虚拟机
4. ![image-20220527071216951](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220527071216951.png)

## ==和equals

1. ==比较的是栈中的值，如果是基本数据类型比较的是变量值；引用数据类型是堆中内存对象的地址
   1. ![image-20220527072208436](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220527072208436.png)
   2. 左栈右堆，其实可以看做都是取右方的值：基本数据类型的变量值，引用数据类型的对象的地址
2. equals：Object中默认也是采用==比较，通常会重写
3. ![image-20220527072514782](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220527072514782.png)
4. String
   1. ![image-20220527072645426](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220527072645426.png)
   2. 也就是说对于object类是使用==，对于String类是采用equals
   3. 通过String类的equals可以看出比较的是两个字符串中的内容
5. 常量池是位于堆中
   1. ![image-20220527073156892](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220527073156892.png)

## final

简述final的作用

1. 最终的

2. - 修饰类：表示类不可被继承
   - 修饰方法：表示方法不可被子类覆盖，但是可以重载
   - 修饰变量：表示变量一旦被赋值就不可以更改他的值

3. 修饰成员变量

   - 如果final修饰的是类变量，只能在静态初始化块指定初始值或者生命该变量时指定初始值
   - 如果final修饰的是成员变量，可以在非静态初始化块中声明该变量或者构造器中执行初始值
   - 区别：成员变量位于类里面方法外，加上static就成为了类变量

4. 修饰局部变量

   系统不会为局部变量进行初始化，局部变量必须由程序员显示初始化，因此使用final修饰局部变量时，即可以在定义时指定默认值（后面的代码不能再对该变量进行赋值），也可以不指定默认值，而在后面的代码中对final赋初值（仅一次）

5. ![image-20220527075804292](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220527075804292.png)

6. 修饰基本数据类型和引用数据类型

   - 如果是基本数据类型，则其数值在确定后就不可以更改
   - 如果是引用数据类型，则对其初始化后便不能再让其指向另一个对象，但是引用值是可以变的

   ![image-20220527181858350](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220527181858350.png)

为什么局部内部类和匿名内部类只能访问局部final变量

1. 编译之后会生成两个class文件，Test.class、Test1.class

![image-20220527182630072](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220527182630072.png)

![image-20220527182653041](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220527182653041.png)

1. 首先要记住的一点是：内部类和外部类是处于同一级别的，内部类不会因为定义在方法中就会随着方法的执行完毕就被销毁

2. 这里就会产生问题：当外部类的方法结束时，局部变量就会被销毁，但是内部类对象可能还存在（只有没有人再访问他时，才会死亡）。这里就出现一个矛盾：内部类对象访问了一个不存在的变量。为了解决这个问题，就将局部变量复制了一份作为内部类的成员变量，这样当局部变量死亡后，内部类仍然可以访问他，实际访问是局部变量的“copy”，这样就延长了局部变量的生命周期

   

   将局部变量复制为内部类的成员变量时，必须保证这两个变量是一样的，也就是如果我们在内部类中修改了成员变量，方法中的局部变量也会跟着改变，怎么解决呢？

   

   就将局部变量设置成final，对它初始化后，我就不让你再去修改这个变量，就保证了内部类的成员变量和方法的局部变量的一致性。这实际上也是一种妥协，使得局部变量和内部类内建立的拷贝保持一致


## String、StringBuffer、StringBuilder区别及使用场景

1. String是final修饰的，不可变，每次操作都会产生新的String对象
2. StringBuffer、StringBuilder都是在原对象上进行操作
3. StringBuffer是线程安全的，StringBuilder线程不安全
4. StringBuffer方法都是synchronized修饰的
5. 性能：StringBuilder>StringBuffer>String



场景：经常需要改变字符串内容时使用后面两个

优先使用StringBuilder，多线程使用共享变量时使用StringBuffer

## 重载和重写的区别

**重载**：发生在同一类中，方法名必须相同，参数类型不同、个数不同、顺序不同，方法返回值和访问修饰符可以不同，发生在编译时；和返回值没有关系、访问修饰符没有关系

**重写**：发生在父子类中，方法名、参数列表必须相同，返回值范围小于等于父类，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类；

![image-20220528074342965](C:\Users\Demon Night\AppData\Roaming\Typora\typora-user-images\image-20220528074342965.png)

private：禁止重写

## 接口和抽象类的区别

- 抽象类可以存在普通成员函数，而接口中只能存在public abstract方法
- 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是pulic static final类型的
- 抽象类只能继承1个，接口可以实现多个

接口的设计目的，是对类的行为进行约束（更准确的说是一种“有”约束，因为接口不能规定类不可以有什么行为），也就是提供一种机制，可以强制要求不同的类具有相同的行为，他只约束了行为的有无，但不对如何实现行为进行限制。

而抽象类的设计目的，是代码的复用。当不同的类具有某些相同的行为（记作行为集合A），且其中一部分行为的实现方式一致时（A的非真子集，记作B），可以让这些类派生与1个抽象类。这个抽象类中实现了B，避免让所有的子类来实现B，这就达到了代码复用的目的。而A-B的部分，留给各个子类自己实现。正是因为A-B在这里还没有实现，所以抽象类不允许实例化出来（否则当调用A-B时，无法执行）

抽象类是对类本质进行抽象，表达的是is-a的关系，比如：`BMW is a car`。抽象类包含并实现子类的通用特性，将子类存在差异化的特性进行抽象，交由子类去实现

而接口是对行为的抽象，表达的是`like a`关系。比如：`bird like a Air`，但其本质is a bird。接口的核心是定义行为，即实现类可以做什么，至于实现类的主体是谁，如何实现的，接口并不关心。

使用场景：当关注一个事物的本质时，用抽象类；当关注一个操作时，用接口

抽象类的功能要远超接口，但是抽象类的代价高，因为高级语言来说（从实际设计上来说）每个类只能继承1个类，在这个类中，你必须继承或编写其所有子类的所有共同特性。虽然接口在功能上会弱化很多，但是他只是针对一个动作的描述。而且你可以在一个类中同时实现多个接口。在设计阶段会降低难度

## List和Set的区别

- List：有序，按照对象进入的顺序保存对象，可重复，允许多个null元素对象，可以使用Iterator取出所有元素，在逐一遍历，还可以使用get（int index）获取指定下标的元素
- Set：无序，不可重复，最多允许1个nulll元素对象，取元素时只能用Iterator接口取得所有元素，再逐一遍历各个元素

## Hashcode和equals

**Hashcode介绍**

hashcode()的作用是获取哈希码，也称为散列码，他实际上是返回1个int整数。这个哈希码的作用是确定该对象在哈希表中索引位置。hashcode()定义在JDK的的Object.Java中，java的任何类中都包含hashcode()函数。散列表存储的是键值对(key-value)，他的特点是能根据“键”快速的检索出对应的值，这其中就利用到了散列码(可以快速找到所需要的对象)



