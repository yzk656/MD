##  Java语言

### Java基础一

1. 为什么Java代码可以实现一次编写，到处运行

   ```java
   jvm是跨平台的关键
   在程序运行前，Java源代码编译成字节码，jvm负责将字节码翻译成特定平台下的机器码来运行
       编译好的字节码是jvm这个中间桥梁实现跨平台的
       源代码-》字节码=》机器码
   ```

2. Java文件可以有多个类吗

   ```java
   1个java文件可以有多个类，但是只能有一个public修饰的类
   
   这个public修饰的类是必须要与文件名相同
   ```

3. Java访问权限

   ```java
   修饰成员变量/方法：
   	private：该成员可以被该类内部类访问
   
   	default：改成员可以被该类内部类访问，也可以被同一包下的其他类访问
   
   	protect：该成员可以被该类内部类访问，也可以被同一个包下的其他类访问，也可以被其子类访问
   
   	public：该成员可以被任意包下的类访问到
       
   修饰类：
       default：该类可以被同一个包下的其他类访问到
       public：该类可以被任意包下的类访问到
   ```

4. Java数据类型

   ```java
   基本数据类型、引用数据类型
       基本数据类型：byte、short、int、long、float、double、char、boolean
       引用数据类型：数组、类、接口
       数字类型之间可以相互之间转换
       引用数据类型是对一个对象的引用、本质是通过指针指向堆中的一块内存空间
       int类型占四个字节（4*8=32）=》-2^31-2^31-1
   ```

5. 全局变量与局部变量

   ```java
   Java中的变量分为成员变量、局部变量
       成员变量：在类的范围内定义的变量、有默认值、未被static修饰的变量叫做实例变量，存储在堆内存中，生命周期与对象相同、被static修饰的变量叫做类变量，存储在方法区中，生命周期与当前类相同
       类会在实例化、访问静态成员、调用静态方法、反射操作和继承关系中被加载到内存中。这些时机会触发类的加载，使得类的定义和相关信息可用于程序的执行。
       静态成员变量属于类本身，实例成员变量属于类的实例
       
       局部变量：
       局部变量是方法里定义的变量、局部变量没有初始值
       局部变量存储在栈中
   ```

6. 为什么要有包装类？

   ```java
   一切皆对象
       Java为每个基本数据类型定义一个对应的引用数据类型，这就是包装类
       自动装箱、拆箱是Jdk1.5提供的
       自动装箱：可以将一个基本数据类型直接赋值给对应的包装类型
       自动拆箱：可以将一个包装类型直接复制给对应的基本类型
   ```

7. Integer类型和Double类型判断相等

   ```java
   不同类型不能直接进行判断
       整数、浮点型数据都继承与Number类型
       
   Integer i = 100;
   Double d = 100.00;
   System.out.println(i.doubleValue() == d.doubleValue());
   ```

8. 栈、堆、常量池，他们之间的关系

   ```java
   栈：用于存储方法调用（将方法的调用信息存储）、局部变量。每个线程都有自己的栈
   堆：用于存储对象的内存区域。堆中的对象是由垃圾回收器自动进行管理的
   常量池：存储字符串变量、基本数据类型的常量。常量池中的内容在类加载时被存储，运行时被使用    
   ```


### Java基础二

1. 多态

   ```java
   因为子类其实是一种特殊的父类，因此Java允许把一个子类对象直接赋给一个父类引用变量，无须任何类型转换，或者被称为向上转型，向上转型由系统自动完成。
   
   当把一个子类对象直接赋给父类引用变量时，例如 BaseClass obj = new SubClass();，这个obj引用变量的编译时类型是BaseClass，而运行时类型是SubClass，当运行时调用该引用变量的方法时，其方法行为总是表现出子类方法的行为特征，而不是父类方法的行为特征，这就可能出现：相同类型的变量、调用同一个方法时呈现出多种不同的行为特征，这就是多态。
   ```

2. Java中多态是如何实现的

   ```java
   多态的实现离不开继承
       在调用程序，传入该父类型的某个子类型的实例
   ```

3. 重载与重写的区别

   ```java
   重载发生在同一个类中，若多个方法之间参数名相同，但是参数不同，则他们之间就构成了重载关系。重载与方法返回值以及访问修饰符无关，即重载的方法不能根据返回类型进行区分
       
   重写发生在父类子类，要想发生重写关系，方法名、参数列表必须要与父类方法相同，返回值要小于等于父类方法
   ```

   方法的重载（Overloading）和方法的重写（Overriding）是两个与方法相关的概念，它们在功能和应用上有一些不同。

   **方法的重载（Overloading）**：
   方法的重载指的是在同一个类中定义多个具有相同名称但参数列表不同的方法。重载方法具有相同的方法名，但参数个数、类型或顺序不同。重载方法之间可以有不同的返回类型。

   重载的主要特点：
   - 发生在同一个类中。
   - 方法名相同，但参数列表不同。
   - 返回类型可以相同也可以不同。
   - 编译器根据调用时提供的参数类型和数量，决定调用哪个重载方法。

   **方法的重写（Overriding）**：
   方法的重写指的是在子类中重新实现（覆盖）从父类继承而来的方法。重写方法具有与父类方法相同的方法名、参数列表和返回类型，但可以有不同的实现逻辑。重写方法允许子类修改或扩展父类方法的行为，实现多态性。

   重写的主要特点：
   - 发生在继承关系的父类和子类之间。
   - 方法名、参数列表都与父类方法相同。
   - 重写方法的访问修饰符不能比父类的更严格。
   - 子类的重写方法必须遵循父类方法的方法签名。

   总结：
   - 方法的重载是在同一个类中根据参数的不同定义多个具有相同名称但参数列表不同的方法，用于提供不同的参数处理方式。
   - 方法的重写是在子类中对从父类继承的方法进行重新实现，以改变或扩展方法的行为。重写方法具有与父类方法相同的方法签名。

4. int与Integer的区别，在做相等运算时会出现什么情况

   ```java
   在做运算时，Integer会自动拆箱
   ```

### Java基础三

1. 说一下hashcode（）和equals（）的关系

   ```java
   如果两个对象相等，必须要有相同的哈希码
   如何两个对象哈希码相同，却未必是相同对象
       
       当向hashset中加入一个元素时，hashset对调用对象的hashcode（）获得哈希码，通过哈希码确定对象在集合中的位置，如何这个位置已经存在一个对象，hashset会调用equals（）对两个对象进行比较，如果相等说明对象重复，此时就不会保存新加的对象
   ```

2. 为什么要重写equals和hashcode

   ```java
   因为Object类提供的equals（）默认是比较的两个对象的地址，但是我们通常认为内容相同时，就认为两个对象是相等的，因此要进行重写
       因为hashcode是根据内存地址计算出来的，这与对象的相等性没有关系，因此如果你重写了equals方法，判断两个对象相同了（重写后判断内容相同），但是两个对象的地址却不相同，导致hashcode不同，这就违反了equals与hashcode的协定
       equals与hashcode的协定：
       	两个对象相等，hashcode一定相等
       	两个对象的hashcode相等，但是两个对象不一定相等
   ```

3. ==与equals的区别

   ```java
   ==:
      对于基本数据类型，是比较俩个数值是否相同
      对于引用数据类型，是比较两个对象的内存地址是否相同
    
   equals：
       没有重写是以= =来实现
       重写后，是按照对象内容来比较
   ```

4. 谈谈String类

   ```java
   Object类的hashcode是根据对象地址计算出来的，但是String类是根据内容计算出来的
   
   在Java中，对象的默认hashCode()方法确实使用对象的内存地址计算哈希码。这是因为Object类中的hashCode()方法是一个本地方法，并且默认的实现就是根据对象的内存地址计算哈希码。
       
   然而，对于字符串对象，String类重写了hashCode()方法。String类中的hashCode()方法是根据字符串的内容计算出来的，而不是基于对象的内存地址。
       
   StringBuffer是线程安全的，StringBuilder是线程不安全的
   ```

5. 使用字符串时“”和new推荐哪种方式

   ```java
   推荐使用“”这种直接量的方式来创建字符串
       当使用“”这种方式时，JVM会使用常量池来管理这个字符串
       当使用new时，JVM会先使用常量池来管理“hello”直接量，再调用String类的构造器创建一个新的String对象，新创建的String对象被保存在堆内存中
   ```

6. 两个字符串相加的底层是如何实现的

   ```java
   如果拼接的字符串都是直接量，则编译时会直接进行拼接
    
   如果拼接的字符串包含变量，则编译时会采用StringBuilder对其进行优化，即采用append（）方法进行拼接
   ```

7. String a=“abc”：说一下和过程会创建什么，放在哪里

   ```java
   JVM会去常量池中检查是否有该字符串，如果没有，就进行创建，如果有就将其引用赋值给a
   ```

8. new String("abc") 是去了哪里，仅仅是在堆里面吗？

   ```java
   JVM会首先去常量池中管理字符串，然后创建一个String对象，该对象会保存在堆内存中，堆中对象的数据会指向常量池中的直接量
   ```

9. 接口和抽象类有什么区别

   ```java
   接口是一种规范，接口提供了实现者必须向外提供哪些服务，对于接口的调用者来说，接口规定了调用者可以调用哪些服务，以及如何调用这些服务
   
   抽象类体现的是模板式设计，可以当做系统实现过程中的中间产品，这个产品已经实现了系统的部分功能，但是这个产品依旧不能当成最终产品，必须要有更近一步的完善
       
       接口中只能包含抽象方法、静态方法、默认方法、私有方法，不能为普通方法提供实现，抽象类可以包含普通方法
       接口中只能定义静态常量、不能定义普通成员变量；抽象类则可以定义普通成员变量，也可以定义静态变量
       接口中不能包含构造器。抽象类里可以包含构造器，抽象类的构造器并不是用于创建对象，而是让其子类调用这些构造器完成对抽象类的初始化操作
       一个类最多只有一个直接父类，包括抽象类，但是一个类可以实现多个接口，通过接口可以弥补Java单继承的不足
       
   注意事项：
       接口和抽象类都不能被实例化，他们都位于继承树的顶端，用于被其他类实现和继承
       接口和抽象类都可以包含抽象方法，实现接口或继承抽象类的子类都必须实现这些方法
   ```

   抽象类（Abstract Class）和接口（Interface）是面向对象编程中的两种重要概念，用于描述类之间的关系和行为规范。它们有一些共同点，也有一些不同之处。

   **抽象类（Abstract Class）**：
   1. 抽象类是一种普通类和接口的中间形式。它既可以包含普通方法的实现，又可以包含抽象方法的声明。
   2. 抽象类可以拥有字段（属性），构造方法，普通方法（包含方法体），以及抽象方法（只有方法签名，没有实际实现）。
   3. 一个类可以继承自另一个抽象类，并且只能继承一个类（抽象类或普通类）。
   4. 抽象类的主要目的是为子类提供一些通用的方法实现，同时也可以强制子类实现抽象方法。

   **接口（Interface）**：

   1. 接口是一种纯粹的规范定义，它只包含方法的声明，没有方法的实现。
   2. 接口可以定义常量（静态常量字段）和抽象方法，但不能定义普通方法的实现。
   3. 一个类可以实现多个接口，从而具备多个接口所定义的方法签名。
   4. 接口的主要目的是定义类之间的契约（contract），让实现了接口的类保证提供特定的方法。

   **共同点**：

   - 都是用于实现多态性，让不同的类能够共享一些相似的行为规范。
   - 都不能被实例化，即不能直接创建对象。

   **不同之处**：
   - 抽象类可以提供部分实现，而接口只提供方法的声明。
   - 一个类只能继承一个类（包括抽象类），但可以实现多个接口。
   - 抽象类的目的更多地是代码的重用，而接口的目的更多地是约定和多态性的实现。

   选择使用抽象类还是接口取决于你的设计目标。如果你需要在不同的类之间共享一些通用的方法实现，可以使用抽象类；如果你需要定义一组规范来确保不同类具备相似的方法，可以使用接口。通常，Java 推荐优先使用接口，因为它能够更灵活地支持多继承和组件的拼装。

   那个抽象类的构造函数被子类通过super进行调用，实现初始化

   ```java
   package abstractClass;
   
   abstract class Shape {
       String name;
   
       public Shape(String name) {
           this.name = name;
       }
   
       abstract double area();
   }
   
   // 定义一个继承自抽象类的子类
   class Circle extends Shape {
       double radius;
   
       public Circle(String name, double radius) {
           super(name);
           this.radius = radius;
       }
   
       // 实现抽象方法来计算圆的面积
       @Override
       double area() {
           return 3.14159 * radius * radius;
       }
   }
   
   // 定义另一个继承自抽象类的子类
   class Rectangle extends Shape{
       double width;
       double height;
   
       public Rectangle(String name, double width, double height) {
           super(name);
           this.width = width;
           this.height = height;
       }
   
       @Override
       double area() {
           return width*height;
       }
   }
   public class Main {
       public static void main(String[] args) {
           Circle circle = new Circle("circle",2);
           Rectangle rectangle=new Rectangle("rectangle",2,3);
           System.out.println(circle.area());
           System.out.println(rectangle.area());
       }
   }
   ```

10. 什么是自动装箱和自动拆箱

   自动装箱（Autoboxing）和自动拆箱（Unboxing）是 Java 中的两个特性，用于在基本数据类型和对应的包装类之间进行转换。它们让编程过程中在基本数据类型和包装类之间转换变得更加便捷。

   **自动装箱（Autoboxing）**：
   自动装箱是指将基本数据类型自动转换为对应的包装类对象。在需要包装类对象的地方，可以直接使用基本数据类型，编译器会自动将其转换为相应的包装类对象。

   例如，下面的代码演示了自动装箱的过程：

   ```java
   int num = 42;
   Integer numObj = num; // 自动装箱
   ```

   **自动拆箱（Unboxing）**：
   自动拆箱是指将包装类对象自动转换为对应的基本数据类型。在需要基本数据类型的地方，可以直接使用包装类对象，编译器会自动将其拆箱为相应的基本数据类型。

   例如，下面的代码演示了自动拆箱的过程：

   ```java
   Integer numObj = 10;
   int num = numObj; // 自动拆箱
   ```

   总结：
   自动装箱和自动拆箱是 Java 的语法糖，使得基本数据类型和包装类之间的转换更加方便。不过，在频繁进行自动装箱和自动拆箱的操作时，需要注意性能和潜在的空指针异常问题。 

11. String和StringBuffer的区别

    `String` 和 `StringBuffer` 是 Java 中两种处理字符串的不同类，它们在字符串的操作和性能上有一些区别。

    **String**：
    - `String` 是一个不可变类，一旦创建，其值就不能被修改。每次对字符串的操作都会生成一个新的字符串对象，原来的字符串对象不会改变。
    - 当需要对字符串进行频繁的修改、拼接或替换时，每次操作都会产生一个新的字符串对象，可能导致内存的浪费和性能下降。
    - 由于不可变性，`String` 在多线程环境下是线程安全的。

    **StringBuffer**：

    - `StringBuffer` 是一个可变类，它允许对字符串进行修改、拼接和删除等 操作，而不会创建新的对象。
    - 当需要频繁修改字符串内容时，使用 `StringBuffer` 可以避免产生大量的临时对象，从而提高性能。
    - `StringBuffer` 是线程安全的，它的方法使用了同步机制来保证多线程环境下的安全性。
    - `StringBuffer` 的性能相对较差，因为在每次修改时都需要进行同步操作。

    **总结**：

    - 如果你需要处理频繁的字符串修改、拼接等操作，并且不涉及多线程环境，可以使用 `StringBuilder`，它是非线程安全的可变字符串类，性能较好。
    - 如果你需要处理频繁的字符串操作，且涉及多线程环境，可以使用 `StringBuffer`，它是线程安全的可变字符串类，但性能相对较差。
    - 如果你需要处理不可变的字符串内容，可以使用 `String`。不可变性有助于确保字符串的安全性和可预测性。

12. string的indexof的作用

    `indexOf` 是 `String` 类中的一个方法，用于查找一个指定的子字符串在原字符串中第一次出现的位置索引。它返回子字符串在原字符串中的起始位置，如果未找到则返回 -1。

    `indexOf` 方法的语法为：

    ```java
    int indexOf(String str)
    int indexOf(String str, int fromIndex)
    ```

    其中，`str` 是要查找的子字符串，`fromIndex` 是起始查找的位置索引。

    **作用**：
    - **查找子字符串的位置**：`indexOf` 方法用于查找一个特定的子字符串在原字符串中第一次出现的位置。如果找到了该子字符串，它会返回子字符串在原字符串中的起始索引；如果没有找到，它会返回 -1。

    **示例**：

    ```java
    String text = "Hello, world!";
    int index = text.indexOf("world");
    System.out.println("Index of 'world': " + index); // 输出：Index of 'world': 7
    
    index = text.indexOf("Java");
    System.out.println("Index of 'Java': " + index); // 输出：Index of 'Java': -1
    ```

    在上面的示例中，`indexOf` 方法分别查找了子字符串 "world" 和 "Java" 在原字符串中的位置。"world" 存在于原字符串中，所以返回其起始索引 7，而 "Java" 不存在，所以返回 -1。

13. 谈谈你对面向接口的理解

   ```java
   接口体现的是一种规范和实现分离的设计哲学，利用接口可以降低模块之间的耦合
   ```

当谈论接口降低模块耦合时，让我们考虑一个简单的例子：一个图形绘制应用程序。假设你有一个绘图模块和一个保存图形到文件的模块。使用接口可以降低这两个模块之间的耦合度。

```java
// 定义一个接口来表示可绘制的图形
interface Drawable {
    void draw();
}

// 实现接口的一个具体类：圆形
class Circle implements Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing a circle");
    }
}

// 实现接口的另一个具体类：矩形
class Rectangle implements Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing a rectangle");
    }
}

// 模拟一个保存图形到文件的模块
class FileSaver {
    void saveToFile(Drawable drawable) {
        // 将可绘制的图形保存到文件
        System.out.println("Saving the drawable to a file");
    }
}

public class Main {
    public static void main(String[] args) {
        Circle circle = new Circle();
        Rectangle rectangle = new Rectangle();

        // 保存图形到文件
        FileSaver fileSaver = new FileSaver();
        fileSaver.saveToFile(circle);
        fileSaver.saveToFile(rectangle);
    }
}
```

在这个例子中，`Drawable` 接口定义了一个 `draw` 方法，表示可以绘制的图形。`Circle` 和 `Rectangle` 类都实现了这个接口，并提供了各自的 `draw` 方法实现。`FileSaver` 类负责将绘制的图形保存到文件。

注意以下几点：

1. `FileSaver` 类的 `saveToFile` 方法接受一个 `Drawable` 参数，而不是具体的 `Circle` 或 `Rectangle` 对象。这种设计允许你传递任何实现了 `Drawable` 接口的对象，而不仅仅是特定类型的图形对象。

2. 这种设计方式使得 `FileSaver` 类不依赖于具体的图形类型，从而降低了模块之间的耦合度。你可以轻松地添加新的可绘制图形类，而不需要修改 `FileSaver`。

通过这个例子，你可以看到如何使用接口将不同的模块解耦，使得模块之间的关系更加灵活和可维护。

### Java基础四

1. 说一说Java的异常机制

   ```java
   关于异常处理：
       处理异常语句由try、catch、finally三部分组成
   关于异常跟踪栈
       异常从发生异常处向外传播，首先传给方法调用者，再传给上层调用者，最终会传给main方法，如果依旧没有得到处理，JVM会终止程序，并打印异常跟踪栈的信息
   ```

   

2. 如何理解面向对象

   当谈论面向对象编程时，一个经典的例子是描述汽车的系统。我们可以将汽车看作是一个对象，并定义与汽车相关的属性和行为。

   假设我们要设计一个简单的汽车系统，下面是一个基本的示例：

   ```java
   // 定义汽车类
   class Car {
       private String brand;  // 汽车品牌
       private String color;  // 汽车颜色
       private int speed;     // 当前速度
       
       // 构造方法
       public Car(String brand, String color) {
           this.brand = brand;
           this.color = color;
           this.speed = 0;
       }
       
       // 获取汽车品牌
       public String getBrand() {
           return brand;
       }
       
       // 获取汽车颜色
       public String getColor() {
           return color;
       }
       
       // 获取当前速度
       public int getSpeed() {
           return speed;
       }
       
       // 加速
       public void accelerate(int increment) {
           speed += increment;
       }
       
       // 减速
       public void decelerate(int decrement) {
           if (speed >= decrement) {
               speed -= decrement;
           } else {
               speed = 0;
           }
       }
   }
   
   // 主类
   public class Main {
       public static void main(String[] args) {
           // 创建一个汽车对象
           Car myCar = new Car("Toyota", "Red");
           
           // 获取汽车的品牌和颜色
           System.out.println("品牌：" + myCar.getBrand());
           System.out.println("颜色：" + myCar.getColor());
           
           // 加速并输出当前速度
           myCar.accelerate(50);
           System.out.println("当前速度：" + myCar.getSpeed());
           
           // 减速并输出当前速度
           myCar.decelerate(20);
           System.out.println("当前速度：" + myCar.getSpeed());
       }
   }
   ```

   在上述示例中，我们定义了一个`Car`类，该类具有品牌、颜色和速度等属性，以及获取这些属性和进行加速、减速的行为。在主类中，我们创建了一个`Car`对象，并使用对象的方法来操作和访问该对象的属性。

   这个例子中，汽车对象就是面向对象的概念中的一个实例。我们可以通过创建多个汽车对象来表示不同的汽车，并对每个对象进行独立的操作和访问。

   面向对象的设计思想使得我们可以更好地建模现实世界的问题，并通过对象之间的交互和封装来实现代码的组织、重用和扩展。

3. 介绍Java异常接口

   ```java
   Throwable是异常父类，有两个子类：Error、Exception
       Error：是不可能被捕获的
       Exception：分为Checked异常、Runtime异常
       	其中checked异常是可以被处理的，因此Java程序必须显式处理，否则在编译时就会报错
       	Runtime异常使用try...catch进行处理
   ```

4. 在finally中return会发生什么？

   ```java
   try与catch中的return语句将会失效
       
   try、catch中内容-》寻找finally，没有就执行try、catch中的return语句，如果有执行finally中语句，如果在finally中有return，就会从finally中返回了，就不会执行try、catch中的return语句了、
   ```

5. static关键字的理解

   ```java
   类成员不能访问实例成员，因为类成员是属于类的，而实例成员是属于实例对象的，可能会出现类成员已经初始化完成，但实例成员还未初始化的现象，因此类成员不能访问实例成员
       
   static关键字的作用是把类的成员变成类相关，而不是实例相关，即static修饰的成员属于整个类，而不属于单个对象。
   外部类的上一级程序单元是包，所以不可使用static修饰；而内部类的上一级程序单元是外部类，使用static修饰可以将内部类变成外部类相关，而不是外部类实例相关。因此static关键字不可修饰外部类，但可修饰内部类。
       
   静态内部类可以包含静态成员，也可以包含非静态成员
   静态内部类不能访问外部类的实例成员，只能访问它的静态成员；
   外部类的所有方法、初始化块都能访问其内部定义的静态内部类；
   在外部类的外部，也可以实例化静态内部类，语法如下：
       外部类.内部类 变量名 = new 外部类.内部类构造方法();
   ```

6. static和final有什么区别？

   ```java
   static关键字可以修饰成员变量、成员方法、初始化块、内部类，被static修饰的成员是类的成员，它属于类、不属于单个对象。以下是static修饰这4种成员时表现出的特征：
       
       初始化块可以用来给实例变量赋初值。
           // 初始化块
       {
           System.out.println("实例初始化块被执行");
           myNumber = 10;
       }
   
   	类变量：被static修饰的成员变量叫类变量（静态变量）。类变量属于类，它随类的信息存储在方法区，并不随对象存储在堆中，类变量可以通过类名来访问，也可以通过对象名来访问，但建议通过类名访问它。
   
   	类方法：被static修饰的成员方法叫类方法（静态方法）。类方法属于类，可以通过类名访问，也可以通过对象名访问，建议通过类名访问它。
   
   	静态块：被static修饰的初始化块叫静态初始化块。静态块属于类，它在类加载的时候被隐式调用一次，之后便不会被调用了。
   
   	静态内部类：被static修饰的内部类叫静态内部类。静态内部类可以包含静态成员，也可以包含非静态成员。静态内部类不能访问外部类的实例成员，只能访问外部类的静态成员。外部类的所有方法、初始化块都能访问其内部定义的静态内部类。
   
   final关键字可以修饰类、方法、变量，以下是final修饰这3种目标时表现出的特征：
   
   	final类：final关键字修饰的类不可以被继承。
   
   	final方法：final关键字修饰的方法不可以被重写。
   
   	final变量：final关键字修饰的变量，一旦获得了初始值，就不可以被修改。
   ```

7. 说一说对泛型的理解

   ```java
   Java集合有个缺点—把一个对象“丢进”集合里之后，集合就会“忘记”这个对象的数据类型，当再次取出该对象时，该对象的编译类型就变成了Object类型（其运行时类型没变）。
   
   Java集合之所以被设计成这样，是因为集合的设计者不知道我们会用集合来保存什么类型的对象，所以他们把集合设计成能保存任何类型的对象，只要求具有很好的通用性。但这样做带来如下两个问题：
   
   	集合对元素类型没有任何限制，这样可能引发一些问题。例如，想创建一个只能保存Dog对象的集合，但程序也可以轻易地将Cat对象“丢”进去，所以可能引发异常。
   
   	由于把对象“丢进”集合时，集合丢失了对象的状态信息，只知道它盛装的是Object，因此取出集合元素后通常还需要进行强制类型转换。这种强制类型转换既增加了编程的复杂度，也可能引发ClassCastException异常。
   
   从Java 5开始，Java引入了“参数化类型”的概念，允许程序在创建集合时指定集合元素的类型，Java的参数化类型被称为泛型（Generic）。例如 List<String>，表明该List只能保存字符串类型的对象。
   
   有了泛型以后，程序再也不能“不小心”地把其他对象“丢进”集合中。而且程序更加简洁，集合自动记住所有集合元素的数据类型，从而无须对集合元素进行强制类型转换。
   ```

8. 介绍一下泛型擦除

   **参考答案**

   在严格的泛型代码里，带泛型声明的类总应该带着类型参数。但为了与老的Java代码保持一致，也允许在使用带泛型声明的类时不指定实际的类型。如果没有为这个泛型类指定实际的类型，此时被称作raw type（原始类型），默认是声明该泛型形参时指定的第一个上限类型。

   当把一个具有泛型信息的对象赋给另一个没有泛型信息的变量时，所有在尖括号之间的类型信息都将被扔掉。比如一个 List<String> 类型被转换为List，则该List对集合元素的类型检查变成了泛型参数的上限（即Object）。

   上述规则即为泛型擦除，可以通过下面代码进一步理解泛型擦除：

   ```
   List<String> list1 = ...; List list2 = list1; // list2将元素当做Object处理
   ```

   **扩展阅读**

   从逻辑上来看，List<String> 是List的子类，如果直接把一个List对象赋给一个List<String>对象应该引起编译错误，但实际上不会。对泛型而言，可以直接把一个List对象赋给一个 List<String> 对象，编译器仅仅提示“未经检查的转换”。

   上述规则叫做泛型转换，可以通过下面代码进一步理解泛型转换：

   ```
   List list1 = ...; List<String> list2 = list1; // 编译时警告“未经检查的转换”
   ```

9. 什么是带泛型声明的类

   带泛型声明的类（Generic Class）是指在类定义中使用泛型参数来定义类的类型。通过使用泛型，可以在类的定义中指定一个或多个类型参数，以便在类中使用这些参数来增加代码的灵活性和可重用性。

   泛型类的语法形式如下：

   ```java
   class ClassName<T1, T2, ...> {
       // 类的成员和方法
   }
   ```

   在泛型类的定义中，`T1`、`T2`等表示泛型参数（也称为类型变量），可以根据需要进行命名。这些泛型参数可以在类的成员变量、方法参数和返回值类型中使用。

   泛型类的主要作用是允许我们在使用该类时指定具体的类型，并提供类型安全和代码重用的好处。通过使用泛型，我们可以创建更通用、更灵活的类，减少代码重复和类型转换的需要。

   以下是一个示例：

   ```java
   class Box<T> {
       private T content;
   
       public void setContent(T content) {
           this.content = content;
       }
   
       public T getContent() {
           return content;
       }
   }
   
   public class Main {
       public static void main(String[] args) {
           Box<String> stringBox = new Box<>();
           stringBox.setContent("Hello, world!");
           String content = stringBox.getContent();
           System.out.println(content);  // 输出: Hello, world!
   
           Box<Integer> integerBox = new Box<>();
           integerBox.setContent(42);
           int value = integerBox.getContent();
           System.out.println(value);    // 输出: 42
       }
   }
   ```

   在上面的例子中，`Box`类是一个带有泛型声明的类，用于存储和获取某个类型的内容。通过在`Box`类的定义中使用泛型参数`T`，我们可以在使用该类时指定具体的类型，例如`Box<String>`和`Box<Integer>`。这样，我们就可以创建具有不同类型内容的`Box`对象，而不需要为每种类型编写不同的类。

10. List<? super T>和List<? extends T>有什么区别？

    **参考答案**

    - ? 是类型通配符，List<?> 可以表示各种泛型List的父类，意思是元素类型未知的List；
    - List<? super T> 用于设定类型通配符的下限，此处 ? 代表一个未知的类型，但它必须是T的父类型；
    - List<? extends T> 用于设定类型通配符的上限，此处 ? 代表一个未知的类型，但它必须是T的子类型。

    **扩展阅读**

    在Java的早期设计中，允许把Integer[]数组赋值给Number[]变量，此时如果试图把一个Double对象保存到该Number[]数组中，编译可以通过，但在运行时抛出ArrayStoreException异常。这显然是一种不安全的设计，因此Java在泛型设计时进行了改进，它不再允许把 List<Integer> 对象赋值给 List<Number> 变量。

    数组和泛型有所不同，假设Foo是Bar的一个子类型（子类或者子接口），那么Foo[]依然是Bar[]的子类型，但G<Foo> 不是 G<Bar> 的子类型。Foo[]自动向上转型为Bar[]的方式被称为型变，也就是说，Java的数组支持型变，但Java集合并不支持型变。Java泛型的设计原则是，只要代码在编译时没有出现警告，就不会遇到运行时ClassCastException异常。

11.    

    ```java
    ```

12. Java反射在项目中的应用场景

    ```java
    AOP的实现方案，是程序运行时创建目标对象的代理类，这也就是需要反射才能实现的
    ```

13. 如果类中的方法不想在外边执行

    静态代码块中调用、普通代码块、构造器中调用

    实现某个接口可以通过匿名内部类实现接口中的方法

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

    在Java中，接口本身是不能被实例化的，即不能使用 `new` 关键字直接创建接口的对象。然而，您可能会注意到，在上面的代码示例中，似乎我们使用了 `new ActionListener()` 来创建一个 ActionListener 对象。这其实是匿名内部类的语法。

    Java中的匿名内部类允许您在需要接口或抽象类的地方，使用匿名类来实现该接口或继承该抽象类。这种方式可以让您在创建临时对象并实现接口的同时，避免显式地定义一个具名的类。

    具体来说，当您编写 `new ActionListener()` 时，实际上创建的是一个 `ActionListener` 接口的匿名内部类的实例，而不是直接创建接口的对象。匿名内部类会自动实现接口的抽象方法，您可以在匿名内部类中提供这些方法的具体实现。这样，您可以通过匿名内部类的实例来使用接口中定义的方法。

    在之前的代码示例中，`new ActionListener()` 就是创建了一个 ActionListener 接口的匿名内部类实例，并在其中覆盖了 `actionPerformed` 方法的具体实现。然后，将该匿名内部类实例赋值给一个 ActionListener 类型的引用变量 `listener`，并将该 `listener` 添加到 `sendButton` 上，以便在按钮被点击时触发匿名内部类中的 `actionPerformed` 方法。

    所以，虽然接口本身不能被实例化，但通过匿名内部类的方式，我们可以在需要接口的地方创建接口的实例并实现其方法。

### 集合类

1. Java中有哪些容器

   ```java
   Java中的集合类主要有两个接口派生而出：Collection、Map
   	对于Collection接口派生出三个子接口：set、List、Queue
   ```

   **![img](https://uploadfiles.nowcoder.com/images/20220224/4107856_1645688819081/74C2C3389688C6364FF2DE8AA768A039)**

​	![img](https://uploadfiles.nowcoder.com/images/20220224/4107856_1645688841352/E26BABF74692B006DA33C112A6FD5EEC)

2. Java中的容器，线程安全和线程不安全的分别有哪些

   ```java
   例如我们常用的HashSet、TreeSet、ArrayList、LinkedList、ArrayDeque、HashMap、TreeMap，这些都是线程不安全的集合类，但是它们的优点是性能好。如果需要使用线程安全的集合类，则可以使用Collections工具类提供的synchronizedXxx()方法，将这些集合类包装成线程安全的集合类。
   ```

3. 为什么数据库中金额要用bigdecimal类型定义，这样不是有误差吗

   在数据库中，金额通常会使用`BigDecimal`类型进行定义，而不是使用浮点数类型（如`float`或`double`）。这是因为`BigDecimal`类型在处理精确的十进制数值方面具有优势，特别是在涉及货币、金融和其他要求高精度计算的场景中。

   使用浮点数类型可能会导致精度问题，这是由于浮点数在计算机内部表示时采用二进制表示，而不是十进制。在转换和计算过程中，可能会出现舍入误差，导致计算结果与预期的数值不完全匹配。这种舍入误差可能在累积的过程中逐渐放大，导致不可忽视的错误。

   举例说明：

   假设使用浮点数类型表示金额，执行以下计算：
   ```
   0.1 + 0.2
   ```
   预期结果应该是`0.3`，但由于浮点数的舍入误差，实际结果可能是`0.30000000000000004`，这是一个微小的差异，但在货币计算中可能会产生重要影响。

   相比之下，`BigDecimal`类型通过使用十进制表示，可以避免大部分浮点数舍入误差问题，因为它以字符串形式存储数字，能够精确表示任意位数的小数。

   但是需要注意的是，`BigDecimal`类型并不是完全免疫于精度问题，它也有可能在一些运算中产生误差。在进行除法运算时，如果除不尽，就需要指定精度和舍入模式，以确保结果的准确性。

   总的来说，对于金额和其他要求高精度计算的场景，使用`BigDecimal`类型更为合适，可以避免浮点数带来的舍入误差问题，但在使用过程中仍需小心处理精度和舍入问题。

4. 三次握手四次挥手

   "三次握手四次挥手"是指TCP（传输控制协议）建立连接和终止连接的过程。

   三次握手（Three-way Handshake）是在客户端和服务器之间建立TCP连接时所采取的步骤：

   1. 第一次握手：客户端向服务器发送一个连接请求，即发送SYN（同步）包，其中包含一个随机序列号（Seq=X）。

   2. 第二次握手：服务器收到客户端的连接请求后，回复一个确认应答，即发送SYN+ACK（同步+确认）包。该包中也包含一个随机序列号（Seq=Y），同时确认收到客户端的序列号（ACK= X+1）。

   3. 第三次握手：客户端收到服务器的确认应答后，再次回复一个确认包，即发送ACK（确认）包。该包中包含服务器发送的序列号（ACK=Y+1），表示客户端收到了服务器的确认。

   建立了三次握手之后，客户端和服务器之间的TCP连接就正式建立，可以进行数据传输。

   四次挥手（Four-way Handshake）是在客户端和服务器之间终止TCP连接时所采取的步骤：

   1. 第一次挥手：当客户端想要关闭连接时，它会向服务器发送一个关闭请求，即发送FIN（结束）包。客户端进入FIN_WAIT_1状态。

   2. 第二次挥手：服务器收到客户端的关闭请求后，会发送一个确认应答，即发送ACK包。服务器进入CLOSE_WAIT状态，而客户端进入FIN_WAIT_2状态。

   3. 第三次挥手：当服务器也想要关闭连接时，会向客户端发送一个关闭请求，即发送FIN包。服务器进入LAST_ACK状态。

   4. 第四次挥手：客户端收到服务器的关闭请求后，会发送一个确认应答，即发送ACK包。此时，客户端进入TIME_WAIT状态，等待一段时间（通常是两倍的最大段生存期），确保服务器收到了确认。服务器收到客户端的确认后，进入CLOSED状态，而客户端在等待时间结束后，也进入CLOSED状态。

   通过这样的四次挥手，TCP连接得以正常终止。

   值得注意的是，三次握手和四次挥手是为了确保连接的可靠建立和终止。在实际网络通信中，可能会有一些额外的步骤来处理异常情况，以保证数据传输的稳定和可靠性。

5. mysql聚合函数

   MySQL提供了多种聚合函数，用于对数据进行汇总和计算。这些聚合函数可以用于SELECT语句的SELECT子句中，通常结合GROUP BY子句一起使用。以下是一些常用的MySQL聚合函数：

   1. COUNT：用于计算行数或非NULL值的数量。
      语法：COUNT(expression)或COUNT(*)

   2. SUM：用于计算指定列的和。
      语法：SUM(column)

   3. AVG：用于计算指定列的平均值。
      语法：AVG(column)

   4. MAX：用于找出指定列的最大值。
      语法：MAX(column)

   5. MIN：用于找出指定列的最小值。
      语法：MIN(column)

   6. GROUP_CONCAT：用于将分组的结果合并为一个字符串，可用于将某列的值以逗号分隔连接在一起。
      语法：GROUP_CONCAT(column)

   这些聚合函数可以与GROUP BY子句一起使用，以便按照特定的列对结果进行分组，然后在每个组上应用聚合函数。例如：

   ```sql
   SELECT department, COUNT(*) AS employee_count, AVG(salary) AS avg_salary
   FROM employees
   GROUP BY department;
   ```

   以上示例中，我们按照"department"列对"employees"表进行分组，并计算每个部门的员工数量和平均工资。

   此外，MySQL还提供了其他一些聚合函数和相关的扩展功能，如DISTINCT、HAVING等，以满足更复杂的查询需求。

6. springboot的启动方式

   Spring Boot可以通过多种方式来启动应用程序。以下是一些常用的Spring Boot应用程序启动方式：

   1. 使用main方法启动：在Spring Boot应用程序的主类中，包含一个名为"main"的静态方法。该方法通过调用SpringApplication类的静态run方法来启动Spring Boot应用程序。

   ```java
   @SpringBootApplication
   public class MyApplication {
   
       public static void main(String[] args) {
           SpringApplication.run(MyApplication.class, args);
       }
   }
   ```

   2. 使用Maven插件启动：如果你使用Maven构建你的Spring Boot项目，可以使用spring-boot-maven-plugin插件来启动应用程序。在项目根目录下运行以下命令：

   ```bash
   mvn spring-boot:run
   ```

   3. 使用Gradle插件启动：如果你使用Gradle构建你的Spring Boot项目，可以使用org.springframework.boot插件来启动应用程序。在项目根目录下运行以下命令：

   ```bash
   gradle bootRun
   ```

   4. 打包成可执行JAR文件并运行：通过Maven或Gradle将Spring Boot应用程序打包成可执行的JAR文件，然后使用java命令运行该JAR文件。

   ```bash
   java -jar your-application.jar
   ```

   以上是几种常用的Spring Boot应用程序启动方式。选择合适的方式取决于你的项目需求和个人喜好。最常用的方式是使用main方法启动或使用Maven/Gradle插件来快速启动和开发应用程序。

7. 建立一个快速的springboot微服务，核心依赖是什么

   对于快速建立一个简单的Spring Boot 微服务，核心依赖通常包括以下内容：

   1. Spring Boot Starter：`spring-boot-starter`，它包含了Spring Boot核心模块和自动配置，能够简化项目的配置。
   2. Spring Web Starter：`spring-boot-starter-web`，用于构建Web应用程序，包括Web MVC。
   3. Spring Data JPA Starter：`spring-boot-starter-data-jpa`，用于与数据库交互，简化JPA的配置。
   4. 数据库驱动依赖：根据你选择的数据库，添加相应的数据库驱动依赖，例如MySQL数据库可以添加`mysql-connector-java`。
   5. 日志依赖：Spring Boot 默认使用Logback作为日志实现，所以无需添加额外的日志依赖。

   这些核心依赖会帮助你快速构建一个简单的Spring Boot 微服务。如果你需要其他功能，还可以根据项目需求添加其他依赖。

8. springboot的核心注解

   Spring Boot提供了许多核心注解，这些注解帮助开发者实现快速的配置和开发。以下是一些Spring Boot的核心注解：

   1. `@SpringBootApplication`: 这是一个组合注解，包含了多个注解的元注解。通常用于标记主类，表示这是Spring Boot应用程序的入口点。它相当于同时使用了`@Configuration`、`@EnableAutoConfiguration`和`@ComponentScan`注解。

   2. `@Configuration`: 声明一个类是配置类，相当于Spring的XML配置文件。可以在这个类中定义Bean。

   3. `@EnableAutoConfiguration`: 开启Spring Boot的自动配置机制。根据classpath下的依赖自动配置Bean。

   4. `@ComponentScan`: 扫描指定包下的组件，并将它们注册为Spring Bean。

   5. `@RestController`: 结合`@Controller`和`@ResponseBody`，表示这个类是一个控制器，处理HTTP请求，并将返回值直接写入响应体中。

   6. `@RequestMapping`: 定义请求的URL映射，用于处理HTTP请求。可以用在控制器类上或具体的处理方法上。

   7. `@Autowired`: 自动装配，将依赖的Bean注入到目标对象中。

   8. `@Value`: 用于将外部配置文件中的属性值注入到Bean中。

   9. `@Bean`: 定义一个Bean，并交由Spring容器管理。

   10. `@Profile`: 定义Bean的激活条件，只有指定的Profile处于激活状态时，才会创建这个Bean。

   11. `@ConfigurationProperties`: 将外部配置文件中的属性绑定到一个带有`@ConfigurationProperties`注解的JavaBean上。

   12. `@Conditional`: 根据条件判断是否创建一个Bean。

   这些是Spring Boot的一些核心注解，它们在开发Spring Boot应用程序时非常常用，可以帮助简化配置和开发过程。

9. mysql实现一个分页列表功能需要做些什么，只需要考虑后端接口

   1. 接收前端传递的分页参数：前端通常会传递两个参数给后端，即页码（page）和每页显示的记录数（pageSize）。
   2. 构建DAO层：在DAO层（数据访问对象）定义相应的数据库操作接口，包括查询分页数据和查询总记录数。
   3. 实现DAO层：在DAO层实现定义的接口，使用Spring的JdbcTemplate或Spring Data JPA来执行数据库查询。
   4. 构建Service层：在Service层定义业务逻辑，调用DAO层的方法获取数据。
   5. 实现Controller层：在Controller层实现接口，接收前端传递的分页参数，并调用Service层的方法获取分页数据。

10. mysql的联表查询有几种方式，各个关键字的不同点

   MySQL的联表查询有三种方式，分别是内连接（INNER JOIN）、左连接（LEFT JOIN或LEFT OUTER JOIN）和右连接（RIGHT JOIN或RIGHT OUTER JOIN）。这些关键字用于指定不同类型的联接方式，从而获取不同的查询结果。

   1. 内连接（INNER JOIN）：
      - 语法：`SELECT ... FROM table1 INNER JOIN table2 ON condition`
      - 内连接返回两个表之间满足连接条件的交集，即只返回同时存在于两个表中的记录。连接条件在ON子句中指定。

   2. 左连接（LEFT JOIN或LEFT OUTER JOIN）：
      - 语法：`SELECT ... FROM table1 LEFT JOIN table2 ON condition`
      - 左连接返回左表（table1）的所有记录，以及右表（table2）中满足连接条件的记录。如果右表中没有匹配的记录，则右表部分的字段会显示为NULL。

   3. 右连接（RIGHT JOIN或RIGHT OUTER JOIN）：
      - 语法：`SELECT ... FROM table1 RIGHT JOIN table2 ON condition`
      - 右连接返回右表（table2）的所有记录，以及左表（table1）中满足连接条件的记录。如果左表中没有匹配的记录，则左表部分的字段会显示为NULL。

   这里的关键点在于联接方式的选择，从而决定了哪些数据会出现在查询结果中。在使用这些联接方式时，要根据业务需求和数据结构来选择合适的方式。

   另外，MySQL还支持其他类型的连接，如全外连接（FULL JOIN或FULL OUTER JOIN）和交叉连接（CROSS JOIN）。但需要注意的是，全外连接在MySQL中并不常见，而交叉连接会返回两个表的笛卡尔积，因此通常要谨慎使用，以避免产生大量无用的结果。

11. 懒汉式与饿汉式

    "懒汉式"和"饿汉式"是两种常见的单例设计模式，用于确保在整个应用程序的生命周期内只创建一个实例对象。

    **懒汉式**（Lazy Initialization）：

    懒汉式是一种延迟加载的方式，在需要的时候才会创建实例对象。具体说就是在第一次调用获取实例的方法时才会创建实例。懒汉式的典型实现方式是在类中声明一个私有的静态成员变量，并提供一个公共的静态方法来获取该实例。在该方法内部，判断实例是否已经被创建，如果没有，则创建一个新的实例并返回，如果已经存在，则直接返回已有的实例。

    懒汉式的优点是在应用程序启动时不会立即创建实例，节省了系统资源。但是在多线程环境下，需要考虑线程安全性，需要使用同步机制（如synchronized）来保证只有一个线程能够创建实例。

    **饿汉式**（Eager Initialization）：

    饿汉式是一种在类加载的时候就创建实例的方式，因此也称为"饿汉"。在类加载时，实例对象就已经被创建，不管是否会被使用。饿汉式通常是直接在类的定义中初始化实例，并且把构造函数私有化，确保不能从外部直接创建新的实例。

    饿汉式的优点是简单、线程安全，因为实例在类加载时就已经创建，不会有多线程竞争的问题。但是缺点是如果该实例在应用程序运行期间没有被使用，就会造成资源浪费。

    示例代码：

    **懒汉式示例：**
    ```java
    public class LazySingleton {
        private static LazySingleton instance;
    
        private LazySingleton() {}
    
        public static synchronized LazySingleton getInstance() {
            if (instance == null) {
                instance = new LazySingleton();
            }
            return instance;
        }
    }
    ```

    **饿汉式示例：**
    ```java
    public class EagerSingleton {
        private static final EagerSingleton instance = new EagerSingleton();
    
        private EagerSingleton() {}
    
        public static EagerSingleton getInstance() {
            return instance;
        }
    }
    ```

    注意：以上示例没有考虑到线程安全问题。在实际应用中，为了确保线程安全，懒汉式需要使用同步机制，而饿汉式则无需担心多线程问题。

# Spring

## 为什么通过名字能够获取相同的bean

类-》构造方法-》对象=》通过Autoware进行依赖注入-》Bean对象-》存储到Map结构中存储起来(单例池)

因为底层是根据Map来进行存储bean的

![image-20230723160104543](https://cdn.jsdelivr.net/gh/yzk656/image/202307231601607.png)



bean对象也是可以实现方法，只需要实 现InitalingBean的接口就行，用于bean的初始化



依赖注入完成后，还有对这个bean的其他操作，就可以写在这个afterPropertiesSet（）方法里面。一般用于属性验证，验证不通过，就可以抛出创建bean异常



初始化后就可以进行AOP，如果进行了AOP，那存储在单例池中的对象就是AOP产生的代理对象；如果不进行AOP的话，单例池中的对象就是普通的bean对象



推断构造方法：

1个类中如果只有一个构造方法，那就用这个构造方法去构造bean对象，如果有链各个构造方法，一个无参一个有参，那么默认使用无参构造方法去构造bean对象，如果有两个有参的构造方法，那么spring就不知道使用哪个构造方法了，就会进行报错。但是我们可以使用Autoware来指定构造方法



对于构造方法中的参数，会去单例池中查找是否有该bean对象，如果没有该对象，它会创建一个对象，并将其放在单例池中。但是如果这个类没有被容器管理，就会发生报错。也就是这个类需要是个bean



对于参数获取bean对象时，是先byType=》byName，就是根据类型找，再根据名字找，如果根据类型就找到了一个，那就不在根据名称去找了，如果根据类型找到了多个bean，那就再根据名称去找



我们最开始进行依赖注入是通过构造器进行注入的，他是根据参数中的bean的类型和名称去单例池中查找并注入的；为了方便我们可以使用Autowired注解进行注入，这个就涉及到了依赖查找



AOP后会生成代理对象，这个代理类会继承原类，同时会生成一个普通对象（创建bean完成前的普通对象）的属性；在执行继承的方法时它会先执行切面逻辑，处理完后再去处理普通对象的方法，也就是bean的方法，而不是代理对象的方法。Spring并没有针对代理对象进行依赖注入

代理对象的作用就是为了执行那段切面逻辑，执行完后再调用原对象

就是你想对原对象进行一些功能增强，这时你就需要生成一个代理对象，这个代理对象执行完切面逻辑后就会执行被代理对象的方法，这个方法是从代理对象的target中获取的普通对象也就是被代理对象



## AOP底层是怎么工作的

如果进行了AOP操作，那么单例池中放的就是代理对象，Spring并不会对代理对象进行依赖注入【下图中的test（）是重写方法】

对于代理对象，并不会进行依赖注入，，所以可以换个对象不使用需要依赖注入的那个对象，而是将需要依赖注入的普通对象赋值给代理类中的target，这样就可以调用父类的test方法了

![image-20230729110442448](https://cdn.jsdelivr.net/gh/yzk656/image/202307291104530.png)



![image-20230723225708778](https://cdn.jsdelivr.net/gh/yzk656/image/202307232257858.png)

![image-20230723231022007](https://cdn.jsdelivr.net/gh/yzk656/image/202307232310060.png)

 

在进行事务操作时，开启事务=》创建连接=》修改AutoCommit=false=》执行SQL=》判断是否有错=》修改AutoCommit=true

在执行方法是是使用的代理对象，如果一个bean对象进行了AOP，那这个单例池中存储的就是这个bean的代理对象，然后你再执行本类中的方法，他就会调用的是普通对象的方法，普通对象的方法不想代理对象方法功能那么全，他不会去判断注解。要想使用代理对象判断注解，就可以在本对象中注入本对象，这样拿到的就是代理对象

一个方法的注解能不能生效，只需要判断调用这个方法是不是代理对象

如果进行了AOP那Spring容器中存储的是代理对象，如果没有进行AOP那么Spring中存储的就是普通对象



对于一个SQL语句，他的执行调用的是JDBCtemplete，而对于事务处理他调用的是事务管理器，这两个都调用datasource（），获得的是两个不同的连接，Configuration的作用就是在查找bean时，如果容器中有对应的bean，就返回想要的bean，也就能获取相同的bean了

![image-20230724144607836](https://cdn.jsdelivr.net/gh/yzk656/image/202307241446979.png)



@PostConstruct注解可以完成初始化后的操作；也可以实现InitializingBean接口中的afterPropertiesSet（）方法

![image-20230725071727547](https://cdn.jsdelivr.net/gh/yzk656/image/202307250717602.png)

![image-20230725071948603](https://cdn.jsdelivr.net/gh/yzk656/image/202307250719652.png)

![image-20230729065215449](https://cdn.jsdelivr.net/gh/yzk656/image/202307290652533.png)

## Spring中常用注解

在 Spring 框架中，有许多常用的注解用于简化配置和实现依赖注入。以下是一些常见的 Spring 注解：

1. **@Component**：用于标识一个类为 Spring 组件（Bean），让 Spring 自动扫描并将其注册到容器中。

2. **@Controller**：标识一个类为 Spring MVC 的控制器，处理用户请求。

3. **@Service**：标识一个类为服务层组件，通常用于注解服务层的 Bean。

4. **@Repository**：标识一个类为数据访问层组件，通常用于注解数据访问层的 Bean。

5. **@Autowired**：自动装配，用于依赖注入，可以在字段、构造函数、Setter 方法上使用。

6. **@Qualifier**：与@Autowired一起使用，用于指定具体要注入的 Bean 的名称。

7. **@Value**：用于注入简单值类型的属性。

8. **@RequestMapping**：在 Spring MVC 中用于映射请求路径到相应的处理方法。

9. **@PathVariable**：用于从 URL 中获取路径变量的值。

10. **@RequestParam**：用于从请求参数中获取值。

11. **@RequestBody**：用于接收 HTTP 请求体中的数据，通常用于处理 JSON 或 XML 数据。

12. **@ResponseBody**：用于将方法的返回值直接写入 HTTP 响应体中，通常用于返回 JSON 或 XML 数据。

13. **@Configuration**：用于标识一个类为配置类，相当于传统的 XML 配置文件。

14. **@Bean**：在配置类中使用，用于声明一个 Bean。

15. **@PostConstruct**：在 Bean 初始化之后执行的方法上添加该注解，用于执行一些初始化操作。

16. **@PreDestroy**：在 Bean 销毁之前执行的方法上添加该注解，用于执行一些清理操作。

这些是 Spring 中一些常用的注解，它们能够极大地简化 Spring 应用的配置和开发工作。请注意，不同的 Spring 模块和扩展可能会引入更多特定的注解。

## restcontroller是谁和谁的结合

@RestController 是 Spring 4.x 版本以后新增的注解，它是 @Controller 和 @ResponseBody 注解的结合体。

- **@Controller**：用于标识一个类为 Spring MVC 的控制器，它表示该类可以处理用户的请求。在传统的 Spring MVC 中，Controller 类的方法返回一个视图名称（一般是通过视图解析器解析得到的）来渲染页面内容。

- **@ResponseBody**：用于将方法的返回值直接写入 HTTP 响应体中，通常用于返回数据格式，比如 JSON 或 XML 数据。

@RestController 注解的作用就是将 @Controller 和 @ResponseBody 两个注解合并在一起，简化了 RESTful 风格的开发。使用 @RestController 注解的类中的方法，不再返回视图名称，而是直接返回数据对象，Spring 会自动将返回的数据对象转换为 JSON 或其他格式，并将其写入到 HTTP 响应中，而不需要通过视图解析器进行视图渲染。

示例：

```java
@RestController
public class MyRestController {
    
    @GetMapping("/hello")
    public String hello() {
        return "Hello, world!";
    }
    
    @GetMapping("/user")
    public User getUser() {
        User user = new User("John", 30);
        return user;
    }
}
```

在上述示例中，如果使用 @Controller 注解，`hello()` 方法返回的是一个视图名称，而 `getUser()` 方法返回的是一个 User 对象，Spring 会尝试通过视图解析器查找对应的视图页面。但如果使用 @RestController 注解，`hello()` 方法的返回值直接作为字符串响应，而 `getUser()` 方法的返回值会被转换成 JSON 数据返回给客户端。

## spring容器既管理bean，又管理bean对象吗

在 Spring 容器中，它实际上管理的就是 Bean 对象。Bean 是 Spring 容器中管理的对象实例，所以说 Spring 容器既管理 Bean 也就是管理 Bean 对象。

当我们在 Spring 配置文件或者通过注解配置定义一个 Bean 时，实际上是在告诉 Spring 容器如何创建和管理这个对象。Spring 容器会根据配置信息实例化这个 Bean，并将其放入容器中。在容器中，Spring 会维护这些 Bean 对象的生命周期、依赖关系、作用域等。

当我们需要使用某个 Bean 时，可以通过容器的 getBean() 方法获取对应的 Bean 实例。Spring 容器会根据配置的信息，从容器中找到相应的 Bean 对象，并将其返回给我们使用。

所以，可以说 Spring 容器既管理 Bean，也管理 Bean 对象，这两者实际上是同一个含义。Spring 容器负责创建、配置和管理 Bean 对象，让我们能够通过容器来方便地获取和使用这些 Bean 对象。

## SpringBoot自动原理

![](https://cdn.jsdelivr.net/gh/yzk656/image/202307260838067.png)

![image-20230807180350091](https://cdn.jsdelivr.net/gh/yzk656/image/202308071803269.png)

Spring Boot 的自动配置原理是其核心特性之一，它使得开发者可以快速构建应用程序而无需手动配置大量的组件和依赖。

Spring Boot 的自动配置原理主要依赖于以下两个核心组件：

1. Spring Boot Starter：Spring Boot Starter 是一组依赖包，它们包含了特定功能的默认配置和必要的依赖。例如，`spring-boot-starter-web` 包含了构建 Web 应用所需的默认配置和依赖，包括 Spring MVC、Tomcat 等。

2. Spring Boot Auto-Configuration：Spring Boot 通过自动配置类（`@Configuration`）来自动配置各种功能。自动配置类使用条件注解（`@Conditional`）来判断是否满足特定条件，如果满足条件，则自动配置相关的组件。

自动配置原理的步骤如下：

1. Spring Boot 启动时，会自动扫描项目中的依赖，并加载对应的 Spring Boot Starter。

2. Spring Boot Starter 中包含了自动配置类，它们通过条件注解判断是否需要进行自动配置。

3. 条件注解会根据项目的依赖、配置文件和其他条件来判断是否满足自动配置的条件。例如，当项目中有 Web 相关的依赖时，`@ConditionalOnWebApplication` 条件注解会满足，从而触发自动配置 Web 相关的组件。

4. 如果条件满足，Spring Boot 会自动执行配置类中的代码，创建相关的 Bean 并注入到 Spring 容器中。

5. 开发者也可以通过自定义配置文件和属性，覆盖默认的自动配置。Spring Boot 的配置优先级规则可以让开发者方便地进行个性化定制。

通过这种自动配置机制，Spring Boot 可以根据项目的依赖和环境自动配置各种组件，极大地减少了开发者的配置工作，让开发更加简单快捷。同时，开发者也可以根据需要进行自定义配置，使得 Spring Boot 在灵活性和便利性之间取得了平衡。

## postconstruct注解调用的方法和initialzingbean接口中实现的方法的区别

`@PostConstruct`注解和`InitializingBean`接口都是在Java Bean和Spring框架中用于在bean初始化过程中执行特定任务的工具。然而，它们在使用方法和功能上有一些区别：

1. `@PostConstruct`注解：
   - `@PostConstruct`是Spring特有的注解，用于标识一个方法，该方法应该在bean被构造后、完全初始化之前执行。
   - 它允许您执行自定义的初始化逻辑，而无需实现任何特定的接口或扩展特定的类。
   - 此注解可以用在bean的任何方法上（不能是`final`方法），Spring将在bean被实例化并且依赖项被注入后自动调用该方法。
   - 它提供了一种清晰方便的方式来执行初始化任务，而无需在bean的构造函数中添加额外逻辑。

示例：
```java
public class MyBean {

    @PostConstruct
    public void init() {
        // 自定义初始化逻辑
    }
}
```

2. `InitializingBean`接口：
   - `InitializingBean`是Spring提供的接口。如果一个bean实现了这个接口，Spring将在bean被实例化并且它的依赖项被注入后自动调用`afterPropertiesSet()`方法。
   - 这个接口定义了一个方法`afterPropertiesSet()`，您必须实现该方法来添加自定义的初始化逻辑。
   - 尽管它是一种标准的初始化bean的方式，但它的缺点是将您的bean与Spring紧密耦合，因为您必须实现Spring特定的接口。

示例：
```java
import org.springframework.beans.factory.InitializingBean;

public class MyBean implements InitializingBean {

    @Override
    public void afterPropertiesSet() throws Exception {
        // 自定义初始化逻辑
    }
}
```

总结而言，`@PostConstruct`注解和`InitializingBean`接口都提供了在Spring bean中执行自定义初始化逻辑的方法。选择使用哪种方式取决于个人偏好和您希望bean与Spring框架之间的耦合程度。一般而言，由于它使代码与Spring特定的接口解耦，推荐使用`@PostConstruct`注解，而不是实现`InitializingBean`接口。

## 注解失效

只有代理对象执行a（）方法时才会判断a（）上面有没有注解，对于普通对象调用的，不会进行判断是否有注解，因为test方法是代理对象执行的，所以会判断是否有注解，但是对于里面的a（）方法则是通过普通方法进行调用的，则不会判断a（）方法上面是否有注解

解决办法：

	1. 可以新建一个类，然后注入进来。因为这个类添加了事务注解，也就是进行了AOP，所以说注入进来的就是代理类，索引执行a（）也就是通过代理对象进行调用的
	1. 也可以注入自己，由于当前对象进行了AOP，所以引入的自己也是代理对象

![image-20230729115544922](https://cdn.jsdelivr.net/gh/yzk656/image/202307291155994.png)

## 不加Configuration注解的后果

事务管理器新建到数据库连接，会将他放在ThreadLocal中，他的存储类型是Map<DaataSource,coon>,是根据数据源来拿数据库连接的，如果你拿的数据源没有找到，则会创建新的coon，对于新的连接，他的coon.commit=true（因为没有受到事务管理器的管理）,所以sql执行了之后就会自动提交

因为JdbcTemplate中调用的datasource（）和事务管理器中调用的datasource（）产生的是两个数据源，拿到的是两个不同的coon

为什么添加configuration注解后就可以呢？

因为@configuration可以将本类成为代理对象，这样使用datasource（）时会先检查Spring容器中是否有这个bean，如果有直接返回，没有则创建，这样两个方法中拿到的数据源就是同一个，也就能拿到同一个coon

![image-20230729144735130](https://cdn.jsdelivr.net/gh/yzk656/image/202307291447213.png)



## bean对象名字易错点

如果类名前两个是大写，那么Spring生成的bean对应的名字是大写的，AService=》AService；UserService=》userService

## 过滤器与拦截器的区别

1. 实现原理不同

   过滤器是基于函数回调的，拦截器是基于Java的反射机制（动态代理）实现的

   一般的过滤器会实现doFilter（）方法，这个方法中有一个FilterChain参数，他是一个回调接口

2. 使用范围不同

​	过滤器这个接口是在Servlet规范中定义的，也就是说Filter依赖于tomcat容器，导致他只能在web程序中使用

​	拦截器是Spring组件，并由Spring容器管理，并不依赖Tomcat等容器，是可以单独运行的

3. 使用场景不同

   拦截器更接近系统，所以拦截器主要用来实现项目中业务判断，比如日志记录，权限判断等

   过滤器通常实现通用功能，比如敏感词过滤

4. 触发时机不同

   过滤器是进入容器后，但在进入servlet之前；拦截器是请求进入servlet之后处理的

5. 拦截的请求范围不同

   请求进入容器->进入过滤器->进入Servlet->进入拦截器->执行控制器

## 判断是不是循环依赖

A创建时需要B，B创建时需要A

在创建普通对象之前，将该对象放在createingSet()中一份，创建B时如果发现需要A，并且A正在创建时，则说明是循环依赖

一旦出现了循环依赖，则提前进行AOP，生成代理对象，然后将他放在map中

 在A创建玩普通对象后，将他先放在一个map中，如果![image-20230731100336961](https://cdn.jsdelivr.net/gh/yzk656/image/202307311003096.png)

![image-20230731125940665](https://cdn.jsdelivr.net/gh/yzk656/image/202307311259735.png)

## 三级缓存解决循环依赖

<img src="https://cdn.jsdelivr.net/gh/yzk656/image/202307311303699.png" alt="image-20230731130349575" style="zoom:200%;" />

创建A的bean对象时，先将该类放在creatingSet中进行标记，如果创建一个普通对象，将他放在三级缓存中。然后进行依赖注入需要引入B的bean，因此先去单例池中去查找B的bean对象，如果没有就去创建；

先创建一个B的普通对象（该对象没有进行依赖注入、AOP等操作），然后再进行依赖注入，先从单例池中去查找是否有对象的bean对象，如果需要依赖注入的对象是正在创建的bean对象（从creatingSet中判断），则说明发生了循环依赖。此时从earlySingleObject（二级缓存）中判断是否对应的对象，如果没有，则对A进行提前操作，如果A有AOP操作，则提前进行AOP，如果没有，则将普通对象放进singletonFactory（三级缓存），然后返回给B用于依赖注入，同时将该对象放在earlySingleObject（二级缓存）中。这样就能够在其他对象依赖A对象时，提供给他们，保障了单例bean

## spring中async注解的作用

在Spring框架中，"async"是一个注解，用于指示某个方法是一个异步方法。通过在方法上添加"@Async"注解，Spring将会在调用该方法时，将其放入一个线程池中异步执行，而不会阻塞当前线程。

使用"@Async"注解的方法可以在方法返回类型前加上`java.util.concurrent.Future`，从而可以获取异步方法的执行结果。

使用异步方法可以提高应用程序的并发性和响应性能。当某些操作可能需要较长时间完成，而不希望阻塞主线程时，可以使用异步方法来处理这些操作，从而释放主线程继续执行其他任务。

使用异步方法的步骤：

1. 在Spring配置中启用异步支持：在配置类上添加@EnableAsync注解或在XML配置文件中添加<task:annotation-driven />，以启用Spring的异步支持。

2. 在希望异步执行的方法上添加@Async注解：在目标方法上添加@Async注解，以指示该方法是异步的。

以下是一个简单的示例：

```java
import org.springframework.scheduling.annotation.Async;
import org.springframework.stereotype.Service;

@Service
public class MyService {

    @Async
    public void asyncMethod() {
        // 异步执行的任务
        System.out.println("Async method is running in a separate thread.");
    }
}
```

在上面的示例中，MyService类中的asyncMethod()方法被标记为异步方法，当该方法被调用时，Spring将会在一个新的线程中异步执行其中的任务。

需要注意的是，使用@Async注解时，需要确保该注解被应用在Spring容器能够管理的Bean中，因为异步方法的执行是通过代理实现的，只有Spring托管的Bean才能被正确代理。



## 集合

Java集合主要由两个根接口Collection、Map派生出来的

​	Collection下面有三个子接口：List、Queue、Set

​		List接口的实现类：ArrayList、LinkedList

​		Queue接口

​			Deque接口的实现类：ArrayDeque、LinkedList

​			PriorityQueue

​		Set接口：HashSet、TreeSet

​	

​	Map接口：

​		HashMap、TreeMap

其中线程安全的是CurrentHashMap、HashTable

## MySQL的隔离级别

解决多个事务竞争导致的安全性问题。可能会出现以下三种现象：

脏读：T1事务可能会读到T2事务未提交的事务，但是未提交的事务T2可能会发生回滚，也就可能T1事务读取到不一定存在的数据，产生脏读的现象

不可重复读：假设两种事务同时执行，事务T1在不同的时刻读取同一行数据，结果可能不一样，从而导致不可重复读的问题

幻读：假设两种事务同时执行，事务T1执行范围查询或者范围修改的过程中，事务T2插入了一条事务T1查询范围内的数据并且提交了，这时候事务T1查询中发现多出一条数据或者T1事务执行过程中发现数据没有被修改，从而产生幻读现象



读未提交：产生脏读、不可重复度、幻读

读已提交：不可重复读、幻读

可重复读：幻读（默认）

串行化：多个并行事务串行化执行不会产生安全性问题（性能最低）

![image-20230802202846544](https://cdn.jsdelivr.net/gh/yzk656/image/202308022028660.png)

![image-20230802203105558](https://cdn.jsdelivr.net/gh/yzk656/image/202308022031672.png)

![image-20230802203307326](https://cdn.jsdelivr.net/gh/yzk656/image/202308022033426.png)



## MVCC工作原理

MVCC（Multi-Version Concurrency Control）是一种数据库管理系统中用于实现并发控制的技术。它的目标是在多个事务同时运行时，保证数据的一致性和隔离性，避免常见的并发问题，如脏读、不可重复读和幻读。

在传统的并发控制技术中，通常会使用锁来保护共享资源，但锁机制可能会导致事务之间的阻塞和死锁，影响数据库的性能。MVCC 是为了解决这些问题而引入的一种替代方法。

MVCC 的基本思想是为每个数据行创建多个版本，并在每个事务中保留该事务开始时的数据库快照。每个事务看到的数据是根据其开始时间确定的。这样，当一个事务修改数据时，它实际上是创建了一个新版本，而不是直接修改原始数据。其他事务仍然可以访问之前版本的数据，从而实现了并发的读写操作而不会相互干扰。

MVCC 的工作原理如下：

1. 事务开始时，系统为该事务创建一个时间戳（Transaction ID）。

2. 当事务执行读操作时，它只能看到在该事务开始之前已经提交的数据版本，避免了脏读和不可重复读。

3. 当事务执行写操作时，它会创建一个新的数据版本，并使用事务的时间戳作为版本号，其他事务仍然可以读取旧版本的数据，避免了幻读。

4. 当事务提交时，它的时间戳将被标记为已提交，其他事务将可以看到该事务所做的修改。

MVCC 可以提高并发性能，避免了大部分锁相关的问题。在实际应用中，MVCC 往往用于支持数据库的事务隔离级别，例如可重复读。然而，MVCC 也会增加存储开销，因为每个数据行都需要维护多个版本。因此，在设计数据库应用时，需要根据业务需求和性能要求来选择合适的并发控制方法。

## MySQL主从复制

主要是为了实现读写分离，分为主库与从库，当进行增删改时，操作主库，将产生的对应的二进制文件传给从库，从而实现数据库内容的一致性。当进行查询时，访问的是从库，通过读写分离减轻服务器压力，提高数据库性能

## MySQL优化

1. 选择合适的索引

2. 尽量避免使用Select *
3. 使用Limit限制查询结果的数量
4. 尽量避免使用通配符查询
5. 避免范围查询：Between、Like、In、大于、小于等，因为需要对索引树扫描，所以效率很低



## MySQL连接池

池化技术是为了实现连接的复用：主要参数时最大连接数、单次数据最大报文长度

SQL接口->SQL解析器->SQL优化器

MySQL的存储引擎有多种：MyISAM、InnoDB（主要引擎）、Cluster、Flacon

`红色的是SQL优化器`

![image-20230801215239566](https://cdn.jsdelivr.net/gh/yzk656/image/202308012152767.png)



## SQL数据读入处理

为了解决内存与硬盘速度不一致问题：

一切的逻辑处理和写入、读取都是只操作内存中的数据，这个内存缓冲区称为Buffer Pool

为了防止断电后数据丢失：

​	引入Redo Log体系。数据写入内存缓冲区后，同时会将数据写入Redo Log Buffer中

​	为了保险。提供了刷盘策略。innodb_flush_log_at_trx_commit=1;就是将数据写到Redo Log Buffer的同时写到操作系统内存中，并立刻进行刷盘

​	而0、2两个策略则没有那么强；

​		0：只会写入到Redo Log Buffer中，隔一秒钟才会放入到系统内存中和刷盘
​		2：会写入Redo Log Buffer中和操作系统内存中，但是也会等待刷盘操作完成



BinLog提供历史查询、数据库备份和恢复、主从复制

## MySQL存储结构

内存与硬盘交互的最小存储单元是：页；固定大小：16KB

![image-20230801224729603](https://cdn.jsdelivr.net/gh/yzk656/image/202308012247767.png)

## SQL执行原理

客户端与服务端是半双工通信，只能在一端发送消息，另一端必须接收完整消息才能响应他

## MySQL运行原理

![image-20230802094414946](https://cdn.jsdelivr.net/gh/yzk656/image/202308020944125.png)

## MySQL页结构

默认16KB

## BIO、NIO、AIO，同步和阻塞区别

BIO：同步并阻塞；客户端有一个请求时服务器就启动一个线程

NIO:同步并非阻塞；客户端发送的连接请求都会注册到多路复用器上；多路复用器轮询到有IO请求时才会启动一个线程进行处理

AIO：异步并非阻塞 ；一个有效请求一个线程；客户端的IO请求都是通过操作系统先完成之后再通知服务器应用去启动线程去处理

---

BIO（Blocking I/O）、NIO（Non-blocking I/O）、AIO（Asynchronous I/O）是 Java 中用于处理 I/O 操作的不同方式，它们在处理 I/O 时有不同的特点和适用场景。

**1. BIO（Blocking I/O）**：
BIO 是传统的阻塞式 I/O 模型。在 BIO 中，当一个线程在进行 I/O 操作（如读取文件、网络通信等）时，如果数据没有准备好，该线程会被阻塞，直到数据准备就绪或操作完成。这就意味着一个线程一次只能处理一个连接/请求。

**2. NIO（Non-blocking I/O）**：
NIO 是一种非阻塞式 I/O 模型，引入了 Channel 和 Buffer 的概念。在 NIO 中，一个线程可以管理多个连接/请求，而不需要为每个连接/请求创建一个单独的线程。它使用 Selector 选择器来监视多个通道的事件，当某个通道有数据可读或可写时，线程可以执行相应的操作，不需要等待阻塞。

**3. AIO（Asynchronous I/O）**：
AIO 是一种更高级的异步 I/O 模型，也叫作 NIO.2。在 AIO 中，应用程序向操作系统发起 I/O 操作，并在操作完成时接收通知。这意味着应用程序不需要主动等待 I/O 操作完成，而是可以继续执行其他任务，当 I/O 操作完成后，操作系统会通知应用程序。

**适用场景**：
- BIO 适用于连接数较少且每个连接都有较长的数据传输时间的情况，比如传统的阻塞式 Socket 编程。
- NIO 适用于需要管理大量连接的场景，如聊天服务器、即时通讯等，能够提供较好的并发性能。
- AIO 适用于需要进行大量并发 I/O 操作的场景，如高性能网络服务器，可以减少线程的数量，提供更好的可扩展性和资源利用率。

总之，BIO、NIO 和 AIO 分别对应不同的 I/O 模型，根据应用场景的不同选择合适的模型可以提高应用程序的性能和资源利用率。

## 聚簇索引和非聚簇索引

聚簇索引是一级索引

首先会选用主键作为聚簇索引，如果没有主键则会选择unique列作为聚簇索引，如果没有unique则使用隐藏的DB_ROW_ID作为聚簇索引

非聚簇索引是二级索引

聚簇索引与非聚簇索引的非叶子节点都是只记录这个行的索引值

对于非聚簇索引中key->value中的key是二级索引，value是一级索引

![image-20230803001739932](https://cdn.jsdelivr.net/gh/yzk656/image/202308030017079.png)

## MySQL的explain核心功能解读

`EXPLAIN` 是 MySQL 数据库中用于查询性能分析的关键命令。通过运行 `EXPLAIN` 命令，你可以获取关于查询语句执行计划的详细信息，从而了解查询是如何被优化和执行的。以下是 `EXPLAIN` 的核心功能解读：

`EXPLAIN` 命令的使用格式如下：

```sql
EXPLAIN SELECT columns FROM table WHERE conditions;
```

执行这个命令后，MySQL 返回一组行，每行对应查询语句中的一个操作步骤（也称为执行计划）的详细信息。以下是解读 `EXPLAIN` 结果的重要字段和相关信息：

1. **id：** 表示查询的唯一标识符。在一个复杂的查询中，每个操作步骤都会有一个唯一的 id。

2. **select_type：** 表示操作的类型，可以是 `SIMPLE`（简单查询）、`PRIMARY`（主查询）、`SUBQUERY`（子查询）等。这个字段描述了操作的层级关系。

3. **table：** 表示涉及的表，或者是派生表的别名。

4. **partitions：** 表示涉及的分区，如果查询涉及分区表的话。

5. **type：** 表示访问类型，是查询性能分析中的重要指标。常见的值有 `ALL`（全表扫描）、`INDEX`（通过索引扫描）、`RANGE`（范围查找）、`REF`（使用非唯一索引查找）、`eq_ref`（使用唯一索引查找）等。

6. **possible_keys：** 表示在当前操作步骤中可能被使用的索引。

7. **key：** 表示实际被使用的索引。如果没有使用索引，该字段为 `NULL`。

8. **key_len：** 表示索引中使用的字节数。

9. **ref：** 表示连接条件中使用的列，如果没有则为 `NULL`。

10. **rows：** 表示操作步骤估计会检查的行数。

11. **filtered：** 表示通过某个操作步骤的行数占总行数的百分比。

12. **Extra：** 提供附加的信息，如使用了临时表、使用了文件排序等。

通过分析 `EXPLAIN` 的输出，你可以了解查询语句的执行计划，从而进行性能优化。你可以确定是否正确地使用了索引、了解连接操作的复杂度，以及找到潜在的瓶颈等。这对于优化复杂查询和保障数据库性能非常重要。

![image-20230803001931988](https://cdn.jsdelivr.net/gh/yzk656/image/202308030019074.png)

![image-20230803002141277](https://cdn.jsdelivr.net/gh/yzk656/image/202308030021376.png)

## ACID和三大问题

![image-20230803085314508](https://cdn.jsdelivr.net/gh/yzk656/image/202308030853679.png)

![image-20230803085706381](https://cdn.jsdelivr.net/gh/yzk656/image/202308030857523.png)

如果在进行从内存缓冲区写入磁盘之前发生了故障，可以通过Redo Log机制保证故障后内存中丢失的数据会被恢复到磁盘中

ACID：原子性、一致性、隔离性、持久性；其他三种特性都是服务于一致性；

原子性确保事务被视为单个、不可分割的操作单元，要么完全成功，要么完全失败

通过undo log机制，在每次进行数据的增删改时需要把对应的undo log记录下来，如果某个操作出现异常则会触发回滚操作，反向执行undo log，将数据进行恢复

## MVCC原理-事务隔离性

mvcc的实现是基于undo log版本链和readview来达成的

MVCC**在快照读的情况下可以解决幻读问题，但是在当前读的情况下是不能解决幻读的**

## 数据库三范式

数据库设计中的三范式（Normalization）是一种规范化数据的方法，旨在减少冗余数据、提高数据一致性和维护性。三范式分为三个级别，每个级别都有特定的规则，帮助设计者将数据结构划分为更小、更规范的部分。

1. **第一范式（1NF）：** 在第一范式中，表中的每个列必须是原子的，即不可再分。每个单元格中只能存储单一的值，不允许有多个值或者数组。这有助于消除重复数据和数据不一致性。

2. **第二范式（2NF）：** 在第二范式中，表必须满足第一范式，而且非主键列必须完全依赖于主键列。换句话说，非主键列不应该部分依赖于主键，它们应该完全依赖于主键。这有助于消除部分依赖造成的数据冗余。

3. **第三范式（3NF）：** 在第三范式中，表必须满足第二范式，并且非主键列之间不能存在传递依赖关系。换句话说，非主键列不应该依赖于其他非主键列。这有助于消除传递依赖造成的数据冗余。

适用三范式可以帮助设计更加规范和高效的数据库结构，从而减少数据冗余、提高查询效率，并且减少了数据更新时的异常情况。然而，有时候过度的规范化也可能导致复杂的查询，因此在实际设计中需要权衡范式的要求和实际业务需求。

需要注意的是，虽然三范式是一种很好的设计原则，但并不适用于所有情况。在某些情况下，可能会选择部分违反范式，以满足特定的性能要求或查询需求。

## Bean的生命周期

![image-20230803142222824](https://cdn.jsdelivr.net/gh/yzk656/image/202308031422986.png)

![image-20230803142324990](https://cdn.jsdelivr.net/gh/yzk656/image/202308031423170.png)

## SpringBoot的自动装配

Spring Boot 的自动装配（Auto-Configuration）是一种特性，旨在简化 Spring 应用程序的配置过程。它通过约定大于配置的方式，自动地为你的应用程序配置和集成各种常见的功能和库，从而减少了开发人员在繁琐的配置上所需的工作量。

在传统的 Spring 应用中，你可能需要手动配置许多不同的组件，如数据源、Web 容器、安全性、日志等等。而 Spring Boot 的自动装配通过提前定义好一系列条件和规则，当你引入特定的依赖时，Spring Boot 会根据这些条件和规则自动配置相关的组件。

自动装配的好处包括：

1. **减少配置工作**：开发人员不再需要手动配置大量的组件，因为 Spring Boot 会根据需要自动配置这些组件。

2. **快速入门**：你可以更快地开始开发应用程序，因为很多基础配置已经为你准备好。

3. **约定大于配置**：Spring Boot 使用一些约定，使得开发者只需要关注核心业务逻辑，而不需要过多担心配置细节。

4. **集成常见功能**：Spring Boot 自动装配了许多常见的功能，如数据库访问、Web 开发、安全性等，使得集成这些功能变得更加简单。

要使用 Spring Boot 的自动装配，你只需要在项目中引入相关的 Spring Boot Starter 依赖，Spring Boot 会自动根据你的依赖来进行适当的配置。如果你需要自定义配置，你仍然可以通过配置文件或代码来覆盖自动配置的行为。

总之，Spring Boot 的自动装配是一种能够显著简化 Spring 应用程序配置的特性，使得开发者可以更专注于业务逻辑的开发。

## Nacos配置中心的配置文件有什么作用

Nacos（Naming and Configuration Service）是一个开源的注册中心和配置中心，用于实现微服务架构中的服务注册、发现和配置管理。在Nacos中，配置中心的配置文件扮演着非常重要的角色，用于存储应用程序的配置信息。这些配置文件有以下用途：

1. **应用程序配置管理**：配置中心的配置文件用于管理应用程序的各种配置选项，如数据库连接信息、缓存配置、服务调用的URL等。通过将这些配置信息集中管理，可以轻松地修改和更新应用程序的配置，而无需重新部署应用。

2. **环境分离**：Nacos支持不同的环境（如开发、测试、生产）之间的配置分离。通过使用不同的配置文件，可以在不同的环境中为应用程序设置不同的配置值，从而避免了配置在不同环境之间手动切换的麻烦。

3. **动态配置更新**：Nacos的配置中心支持动态配置更新，意味着应用程序可以在运行时动态获取最新的配置信息，而无需重启应用。这对于需要频繁修改配置或快速响应变化的场景非常有用。

4. **统一管理和集中控制**：通过将配置信息集中存储在配置中心，可以实现统一管理和集中控制。这样，不同的应用程序可以共享相同的配置信息，确保配置的一致性和可维护性。

5. **版本管理**：Nacos的配置中心支持配置的版本管理，可以对配置进行版本控制和回滚操作，确保配置的变更可追溯和可恢复。

总之，Nacos中的配置中心的配置文件用于管理和存储应用程序的各种配置信息，提供了一种方便、集中和动态的方式来管理配置，从而帮助简化应用程序的配置管理和维护。

## 介绍一下SPring IOC的工作流程

IOC就是控制翻转，将对象的管理权限交给容器，好处是降低了对象与对象之间的耦合性

Spring中bean的生命方式：可以通过XML中bean的标签、Service注解（ `@Component`、`@Service`、`@Repository`、`@Controller`）、或者通过Configuration配置类中通过Bean注解去声明

IOC的工作流程：分为两个阶段IOC容器的初始化、完成Bean的初始化和依赖注入

​	IOC容器的初始化：XML、注解、Bean等声明方式解析加载生成BeanDefinition，然后把BeanDefinition注册到IOC容器里面

​	完成Bean的初始化和依赖注入:

​		通过反射去针对没有设置lazy-init属性的单例bean进行初始化

​		完成bean的依赖注入

​		bean的使用：通过Autowired、Beanfactory.getBean()从IOC容器中获取指定bean的实例；



## Springboot打成的jar包和普通的jar包的区别

Spring Boot 应用程序打成的 JAR 包和普通的 JAR 包有一些区别，这些区别主要涉及了应用程序的部署和执行方式，以及包含的内容。下面是一些主要的区别：

**1. 执行方式：**
- **Spring Boot JAR 包**：Spring Boot JAR 包是可执行的，它包含了一个嵌入式的 Web 服务器，可以直接通过 `java -jar` 命令来运行应用程序。这使得部署和运行应用程序变得非常简单，不需要额外的应用服务器。
- **普通 JAR 包**：普通的 JAR 包通常是库或模块，需要在一个容器或应用程序中被加载和使用，不能直接作为可执行程序运行。

**2. 主类和启动类：**
- **Spring Boot JAR 包**：Spring Boot JAR 包需要一个特定的启动类（Main Class），这个类包含了 `main` 方法，可以通过 `java -jar` 命令启动应用程序。
- **普通 JAR 包**：普通的 JAR 包也可以包含 `main` 方法，但通常不会被直接用于启动，而是被其他应用程序调用。

**3. 内嵌的 Web 服务器：**
- **Spring Boot JAR 包**：Spring Boot JAR 包通常包含了一个内嵌的 Web 服务器（如 Tomcat、Jetty 或 Undertow），这使得应用程序可以直接作为一个独立的 Web 服务运行。
- **普通 JAR 包**：普通的 JAR 包通常不包含内嵌的 Web 服务器，如果需要将其部署为 Web 服务，需要将其部署到外部的 Web 服务器中。

**4. 依赖管理：**
- **Spring Boot JAR 包**：Spring Boot 使用了自动化的依赖管理和版本控制，可以在 `pom.xml` 或 `build.gradle` 文件中简单地指定所需的依赖，而不需要过多的配置。
- **普通 JAR 包**：普通的 JAR 包需要开发者手动管理依赖，可能需要更多的配置工作。

**5. 打包方式：**
- **Spring Boot JAR 包**：Spring Boot JAR 包通常使用 Maven 或 Gradle 进行打包，会将依赖的 JAR 包一并打包到生成的 JAR 中。
- **普通 JAR 包**：普通的 JAR 包也使用 Maven 或 Gradle 进行打包，但是它通常只包含项目本身的代码和资源。

总之，Spring Boot JAR 包和普通的 JAR 包在部署和执行方式、包含的内容以及依赖管理等方面存在一些区别，主要是因为 Spring Boot 的目标是简化 Spring 应用程序的开发、部署和运行。

## java的运行环境可以说是jvm吗

是的，Java 的运行环境通常被称为 JVM，即 Java 虚拟机（Java Virtual Machine）。JVM 是 Java 的核心组件之一，它是一个在计算机上运行 Java 字节码的虚拟机。Java 代码在编译成字节码之后，可以被 JVM 解释和执行。

JVM 提供了一个虚拟化的环境，使得 Java 代码可以在不同的操作系统上执行，而不需要重新编译。它负责加载、解释和执行字节码，管理内存、资源和线程，以及提供一些必要的运行时库和支持。

在运行 Java 应用程序时，你需要先安装适当版本的 Java Development Kit（JDK），它包含了编译器用于将 Java 代码编译成字节码的工具，同时也包含了 JVM 用于运行字节码。

所以，JVM 是 Java 程序在不同平台上运行的关键组件，它实现了 Java 的 "一次编写，到处运行" 的理念。

## Springboot的核心注解

Spring Boot 提供了许多核心注解，这些注解用于配置和自定义 Spring Boot 应用程序的行为。以下是一些常见的 Spring Boot 核心注解：

1. **@SpringBootApplication**：这是一个组合注解，用于标注主应用程序类。它等价于同时使用 `@Configuration`、`@EnableAutoConfiguration` 和 `@ComponentScan`，表示这是一个 Spring Boot 应用程序的入口类。

2. **@RestController**：用于声明一个类是控制器（Controller），处理 HTTP 请求并返回响应。相比于 `@Controller` 注解，`@RestController` 还会将方法的返回值直接序列化为 JSON 等格式，常用于构建 RESTful API。

3. **@RequestMapping**：用于将请求 URL 映射到控制器的方法上，指定请求的路径和 HTTP 方法。

4. **@Autowired**：用于依赖注入，将对象自动注入到 Spring Bean 中。它可以用在构造函数、属性、方法等位置。

5. **@Value**：用于从配置文件中读取属性值，并将其注入到 Spring Bean 中。

6. **@Configuration**：标记一个类为配置类，通常与 `@Bean` 注解一起使用，用于定义 Spring Bean。

7. **@EnableAutoConfiguration**：开启自动配置，让 Spring Boot 自动根据依赖的 jar 包和配置文件来配置 Spring 应用程序。

8. **@ComponentScan**：用于指定扫描的包路径，让 Spring Boot 找到并注册标有 `@Component` 注解的组件。

9. **@Profile**：用于根据不同的配置文件或环境激活特定的配置。

10. **@Conditional**：根据特定的条件决定是否创建或注册 Bean。

11. **@Bean**：用于声明一个 Spring Bean。通常与 `@Configuration` 注解一起使用。

12. **@EnableConfigurationProperties**：用于启用对配置属性的绑定。

13. **@EnableDiscoveryClient**：用于将服务注册到服务注册中心，如 Eureka。

14. **@EnableFeignClients**：启用 Feign 客户端，用于声明和使用声明式的 HTTP 客户端。

这些是 Spring Boot 中的一些核心注解，它们用于配置、组件扫描、依赖注入、控制器声明等方面，帮助你创建和定制 Spring Boot 应用程序。根据具体的需求，你可以使用这些注解来配置你的应用程序。

## lazy-init属性是干什么用的

在Spring框架中，`lazy-init` 是一种bean的初始化方式，用于控制bean何时被实例化和初始化。当设置了 `lazy-init` 属性为 `true` 时，表示该bean将在第一次使用时才被实例化和初始化，而不是在容器启动时就立即创建。

默认情况下，Spring容器在启动时会实例化和初始化所有的singleton作用域的bean。然而，某些情况下，您可能希望在应用程序运行时根据需要延迟初始化某些bean，以提高性能和资源利用率。

使用 `lazy-init` 属性可以在某些情况下有效地减少启动时的开销，尤其是对于那些在应用程序启动时不一定会立即用到的较重量级的bean。例如，如果您有一些只在特定条件下才会被使用的bean，您可以将它们设置为延迟初始化，以减少启动时间和内存占用。

以下是一个示例，在XML配置中如何使用 `lazy-init` 属性：

```xml
<bean id="myLazyBean" class="com.example.MyLazyBean" lazy-init="true">
    <!-- Bean properties -->
</bean>
```

在注解驱动的配置中，您可以使用 `@Lazy` 注解来实现相同的效果：

```java
@Component
@Lazy
public class MyLazyBean {
    // Class definition
}
```

需要注意的是，延迟初始化的bean会在第一次访问时进行实例化和初始化，这可能会导致在访问时稍微增加一些延迟。在某些场景下，这是可以接受的，但在对于实时性要求非常高的情况下，您可能需要权衡是否使用延迟初始化。

## 在mysql中如何在添加时自动添加添加时间

在 MySQL 中，你可以通过使用 TIMESTAMP 或者 DATETIME 数据类型以及默认值来实现在添加记录时自动添加添加时间。下面是两种常见的方法：

1. 使用 TIMESTAMP 数据类型和默认值：

```sql
CREATE TABLE your_table (
    id INT PRIMARY KEY,
    data VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

在这个例子中，`created_at` 列使用了 `TIMESTAMP` 数据类型，并且默认值设置为 `CURRENT_TIMESTAMP`。这意味着在插入一条记录时，如果你没有为 `created_at` 列提供值，MySQL 会自动将当前的时间戳添加到该列。

2. 使用 DATETIME 数据类型和默认值：

```sql
CREATE TABLE your_table (
    id INT PRIMARY KEY,
    data VARCHAR(255),
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

类似地，在这个例子中，`created_at` 列使用了 `DATETIME` 数据类型，并且默认值同样设置为 `CURRENT_TIMESTAMP`。

无论你选择哪种方法，都可以实现在插入记录时自动添加时间。如果你想在以后的某个时间点更新记录的时间戳，你可以使用 `UPDATE` 语句来实现。

请注意，在 MySQL 中，`TIMESTAMP` 列会自动转换为服务器的时区，而 `DATETIME` 列则不会。这可能会影响你在处理时间戳时的预期行为，特别是在涉及不同时区的应用程序中。

## cglib动态代理中被代理类是可以被static修饰吗

在 CGLIB 动态代理中，被代理的类不能被 `static` 修饰。CGLIB 是基于字节码的代理技术，它通过生成目标类的子类来实现代理。因为 Java 中的静态方法和成员是属于类本身的，而不是属于实例的，所以无法在子类中覆盖或继承静态方法和成员。因此，CGLIB 无法代理被 `static` 修饰的方法或成员。

CGLIB 主要用于代理普通的 Java 类，而不是静态工具类或类级别的方法。如果需要对静态方法进行代理，通常需要考虑其他的代理方式，比如基于接口的 JDK 动态代理。

## 说一下Volatile关键字

Volatile是JVM提供的轻量级的同步机制，Volatile关键字可以保证并发编程三大特性（原子性、可见性、有序性）中的可见性和有序性，但是不保证原子性

## 阻塞IO，非阻塞IO

当涉及输入/输出（IO）操作时，阻塞和非阻塞是两种不同的IO处理方式。

1. 阻塞IO（Blocking IO）：
阻塞IO是指当应用程序执行IO操作时，程序会一直等待，直到IO操作完成并返回结果为止。在阻塞IO模式下，当一个IO操作被触发，程序会被阻塞，无法进行其他任务，直到IO操作完成或者出现超时等情况。这种模式通常会导致程序的性能下降，因为它会浪费时间在等待IO操作上。

2. 非阻塞IO（Non-blocking IO）：
非阻塞IO是指应用程序在执行IO操作时，会立即返回，不会等待IO操作完成。即使IO操作没有完成，应用程序也可以继续执行其他任务。在这种模式下，程序需要通过轮询或其他方式来检查IO操作是否已经完成，然后再取回结果。非阻塞IO可以提高程序的并发性和响应性，但也需要额外的处理逻辑来管理IO操作的状态。

在现代操作系统中，通常会使用异步IO来处理IO操作。异步IO是一种更高级别的IO处理方式，它允许应用程序在IO操作完成之前继续执行其他任务，而无需轮询。异步IO通常使用回调函数或者事件来处理IO完成的通知。

总之，阻塞IO和非阻塞IO是两种不同的IO处理模式，具有不同的优缺点，可以根据应用程序的需求来选择合适的方式。

## arraylist和linkedlist如何区分

`ArrayList` 和 `LinkedList` 都是 Java 集合框架中的实现，用于存储和操作数据集合。它们有不同的内部结构和性能特点，下面是它们的区别：

1. **内部结构**：
   - `ArrayList`：基于数组实现。它使用一个动态数组来存储元素，元素在内存中是连续存储的，可以通过索引快速访问。
   - `LinkedList`：基于链表实现。它使用双向链表来存储元素，每个元素都包含一个指向前一个元素和后一个元素的引用，不同元素在内存中可以是分散的。

2. **插入和删除操作**：
   - `ArrayList`：插入和删除操作需要移动元素，尤其是在列表的中间位置插入或删除元素时，需要移动后续元素，导致性能较差。
   - `LinkedList`：插入和删除操作在链表中较为高效，因为只需要调整相邻元素的引用即可，不需要像数组一样进行元素的移动。

3. **随机访问**：
   - `ArrayList`：由于元素在内存中是连续存储的，因此可以通过索引进行高效的随机访问。
   - `LinkedList`：随机访问的性能较差，因为需要从链表的头或尾开始遍历，直到找到目标元素。

4. **内存占用**：
   - `ArrayList`：每个元素占用固定大小的内存，但可能会有额外的空间浪费。
   - `LinkedList`：每个元素需要额外的内存用于存储前后引用，但没有连续内存的要求。

5. **迭代效率**：
   - `ArrayList`：在迭代访问所有元素时，由于连续存储，会比较高效。
   - `LinkedList`：迭代效率相对较低，因为需要在链表中跳转。

综上所述，选择使用 `ArrayList` 还是 `LinkedList` 取决于具体的使用场景。如果需要频繁进行插入、删除操作，或者对内存占用要求较高，可以考虑使用 `LinkedList`。如果需要频繁进行随机访问、迭代效率较高，或者数据集大小基本不变，可以考虑使用 `ArrayList`。

## hashmap能解决什么问题

`HashMap` 是 Java 集合框架中的一种实现，它是基于哈希表（Hash Table）数据结构的。`HashMap` 可以用来解决许多与映射关系相关的问题，其中包括但不限于以下几种情况：

1. **快速查找**：`HashMap` 提供了一种高效的查找机制，可以根据键（Key）来快速查找对应的值（Value）。这对于需要根据某个唯一标识来检索数据的场景非常有用，例如数据库中的主键索引。

2. **关联数据**：`HashMap` 可以用来存储键值对的映射关系，例如用于缓存、配置信息、用户会话等场景。每个键与一个值关联，可以通过键快速获取到对应的值。

3. **去重**：`HashMap` 的键是唯一的，因此可以用于去重操作。如果需要对一组数据进行去重，可以将数据作为键放入 `HashMap` 中，由于重复的键会被覆盖，最终只保留唯一的值。

4. **计数**：`HashMap` 可以用来进行计数操作。例如，可以使用键作为计数项，值表示该计数项出现的次数，这在统计词频、统计元素出现次数等场景中非常有用。

5. **缓存**：`HashMap` 可以用来实现缓存功能，将某些计算结果或数据存储在内存中，以便在后续需要时可以快速获取，避免重复计算或IO操作。

6. **映射关系**：`HashMap` 可以用来建立两组数据之间的映射关系，例如建立国家与首都的映射关系、用户名与用户信息的映射关系等。

需要注意的是，`HashMap` 在解决上述问题时，具有快速的查找和插入特性，但它不保证元素的顺序，因此在需要有序存储的情况下，可能需要使用其他实现，如 `LinkedHashMap`。同时，由于哈希表的特性，`HashMap` 在一些特定情况下可能会导致哈希冲突，需要合理设计哈希函数来避免性能问题。

## hashmap中jdk1.8的新特性

在 JDK 1.8 中，`HashMap`（以及其他相关的哈希集合实现，如 `HashSet`）进行了一些优化和改进，主要集中在减少哈希冲突和提高性能方面。以下是 `HashMap` 在 JDK 1.8 中的一些新特性和改进：

1. **红黑树优化**：当哈希桶中的链表长度过长时，JDK 1.8 引入了红黑树（TreeMap）来替代链表，以提高查找效率。这使得 `HashMap` 在处理大量数据时性能更稳定。

2. **桶分割**：在 JDK 1.8 中，`HashMap` 引入了桶分割（Bucket Splitting）的概念。在进行哈希冲突处理时，不再将所有冲突的元素都放在同一个链表中，而是将冲突的元素分割到多个链表中，减少了每个链表的长度，从而提高性能。

3. **数组扩容优化**：JDK 1.8 中改进了 `HashMap` 的数组扩容机制。扩容时不再一次性将所有元素重新哈希和分配，而是逐步迁移数据，减少了扩容时的系统开销。

4. **负载因子调整**：`HashMap` 在 JDK 1.8 中默认的负载因子由 0.75 改为了 0.75f，以减少哈希冲突和扩容的次数，提高性能。

5. **键值对迭代优化**：在 JDK 1.8 中，`HashMap` 的键值对迭代时采用了更高效的方式，减少了迭代时的内存开销和时间消耗。

总之，JDK 1.8 中的 `HashMap` 优化主要集中在减少哈希冲突、提高查找效率和扩容性能方面，使得在处理大规模数据集合时性能更好。这些优化在一定程度上改进了 `HashMap` 的性能和稳定性。

----

1.8之前中链表是采用头插法，1.8是采用尾插法，因为1.8中插入数据时需要判断链表长度

1.8中对哈希算法进行了简化，节省CPU资源

----

hashmap初始数组多长

在Java中，`HashMap` 的初始数组长度默认为 16。这意味着当你创建一个新的 `HashMap` 实例时，初始时它会分配一个长度为 16 的数组来存储键值对。

然而，需要注意的是，`HashMap` 在内部使用哈希表来存储数据，它允许自动扩容以处理更多的键值对。当存储的元素数量达到一定的阈值时，`HashMap` 会触发扩容操作。默认情况下，当存储的元素数量超过数组长度的 75%（即负载因子为 0.75）时，会触发扩容操作。扩容操作会将数组长度翻倍，同时重新计算哈希值并重新分配键值对到新的数组位置。

通过初始化数组长度为 16，`HashMap` 旨在在一般情况下提供足够的容量和性能，但如果你预计会存储大量的键值对，你可能需要在创建 `HashMap` 实例时指定初始容量，以避免在后续操作中进行频繁的扩容。例如，你可以通过以下方式来创建一个具有更大初始容量的 `HashMap`：

```java
HashMap<String, Integer> customHashMap = new HashMap<>(32);  // 使用初始容量为 32 的 HashMap
```

这样可以在一开始就提供一个适当的初始容量，以减少后续可能的扩容操作。

## Java中进程和线程如何区分

在 Java 中，进程和线程是两个并发执行的概念，它们有一些关键区别：

1. **进程（Process）**：
   - 进程是操作系统中的一个独立执行单元。每个进程都有独立的内存空间和资源，包括代码、数据、文件句柄等。
   - 进程之间是相互独立的，一个进程的崩溃不会影响其他进程。
   - 进程之间通信需要使用操作系统提供的特定机制，如管道、消息队列、套接字等。

2. **线程（Thread）**：
   - 线程是进程内的一个执行单元，多个线程可以共享同一个进程的内存空间和资源。
   - 线程之间可以相互通信，共享数据和资源。但由于共享内存，需要注意线程安全问题。
   - 线程的创建和销毁开销较小，可以更快地切换上下文，实现多任务并发。

3. **区别总结**：
   - 进程是操作系统级别的概念，具有独立的内存空间和资源；线程是进程内的执行单元，共享进程的资源。
   - 进程之间通信需要较为复杂的机制；线程之间通信相对简单，但需要注意线程安全。
   - 进程的切换开销较大，线程的切换开销相对较小。

在 Java 中，使用多线程是一种常见的方式来实现并发编程，使得程序可以同时执行多个任务，提高系统的效率和响应性。Java 提供了 `Thread` 类和 `Runnable` 接口来创建和管理线程。在 Java 中，一个进程可以包含多个线程，这些线程共享相同的 Java 虚拟机（JVM）进程。

## Java的线程是安全的吗

Java 的线程本身并不一定是安全的，因为多线程并发执行可能导致一些并发问题，如竞态条件、死锁、资源争用等。这些问题可能会导致程序的不正确行为或者数据损坏。因此，在编写多线程程序时，需要特别注意线程安全性。

线程安全性是指多线程环境下，程序可以正确地执行并保持数据的一致性。为了保证线程安全，需要采取适当的并发控制措施，常见的方法包括：

1. **互斥锁（Mutex）**：使用同步锁（如 `synchronized` 关键字）来控制多个线程对共享资源的访问，确保同一时间只有一个线程可以操作这些资源。

2. **原子操作**：使用原子操作来保证多个线程对同一个变量进行读取和修改时的安全性，Java 提供了一些原子类，如 `AtomicInteger`、`AtomicLong` 等。

3. **并发集合**：Java 提供了一些线程安全的集合类，如 `ConcurrentHashMap`、`CopyOnWriteArrayList` 等，可以在多线程环境下安全地操作集合。

4. **线程局部变量**：通过 `ThreadLocal` 来创建线程局部变量，每个线程拥有自己独立的变量副本，避免了共享资源的竞争。

5. **使用并发工具类**：Java 提供了一些并发工具类，如 `Semaphore`、`CountDownLatch`、`CyclicBarrier` 等，用于管理多线程的执行流程。

尽管有这些方法可以提高线程安全性，但在编写多线程程序时仍需谨慎，遵循一些原则：

- 尽量避免共享资源，尽量将数据封装在对象内部。
- 考虑并发控制的方式，选择适合的同步机制。
- 注意死锁和活锁问题，设计良好的锁顺序。
- 使用现有的线程安全工具和库，减少手动实现的复杂性。

总之，线程安全需要在设计和编写多线程程序时考虑，采取适当的策略和措施来保证程序在多线程环境下的正确性和可靠性。

## 介绍一下ThreadLocal

`ThreadLocal` 是 Java 标准库中的一个类，它提供了一种线程局部变量的机制。每个线程都可以独立地访问 `ThreadLocal` 创建的变量，这些变量对于不同线程是隔离的，每个线程拥有自己的变量副本，互不干扰。

`ThreadLocal` 主要用于解决多线程环境下共享变量带来的并发问题，例如多个线程共享同一个变量时可能发生的竞态条件。通过将变量声明为 `ThreadLocal`，可以确保每个线程都拥有独立的变量副本，从而避免了共享变量的竞争和同步问题。

使用 `ThreadLocal` 的步骤如下：

1. 创建 `ThreadLocal` 实例：通过实例化 `ThreadLocal` 类来创建线程局部变量。

2. 设置线程局部变量：通过 `set()` 方法设置当前线程的局部变量值。

3. 获取线程局部变量：通过 `get()` 方法获取当前线程的局部变量值。

4. 清除线程局部变量：在不需要时，通过 `remove()` 方法清除当前线程的局部变量。

以下是一个简单的示例代码，演示了如何使用 `ThreadLocal`：

```java
public class ThreadLocalExample {
    private static ThreadLocal<Integer> threadLocal = new ThreadLocal<>();

    public static void main(String[] args) {
        // 设置线程局部变量
        threadLocal.set(42);

        // 获取线程局部变量
        int value = threadLocal.get();
        System.out.println("Thread-local value: " + value);

        // 清除线程局部变量
        threadLocal.remove();
    }
}
```

需要注意的是，`ThreadLocal` 应该谨慎使用，因为它可能导致内存泄漏问题。如果不适当地使用 `ThreadLocal`，例如没有及时清除线程局部变量，那么可能会导致长时间运行的线程持有过多的变量副本，占用大量内存。因此，在使用 `ThreadLocal` 时，要确保在适当的时候清除线程局部变量，避免不必要的资源消耗。

---

ThreadLocal是一种多线程隔离机制，在多线程环境下，对于共享变量访问的安全性，一般情况下是对共享变量加锁，保证只有一个线程能对共享变量进行一个更新，而加锁会带来性能下降，ThreadLocal采用了一种空间换时间的思想也就是在在每一个线程中都有一个容器来存储共享变量的副本，每个线程只对自己的变量副本去做更新操作，这样就解决了线程安全问题，以及多线程竞争加锁的开销，共享变量的副本是存储在ThreadLocal类里面的一个成员变量ThreadLocalMap中

使用场景：

​	线程的上下文传递，在跨线程调用中可以使用ThreadLocal在不修改方法签名的情况下传递线程上下文信息

​	比如说在框架和中间件里面把请求的相关信息比如用户信息、请求ID等存储在ThreadLocal中，那么在后序的请求处理链路中都可以方便的访问这些信息

​	数据库的连接管理：每个线程可以独立管理自己的数据库连接，避免了线程之间的竞争和冲突，比如Mybatis中的SqlSession对象就使用了ThreadLocal来存储当前线程的数据库会话信息

## 数据库中的索引分为哪些？

数据库中的索引是用于提高查询效率和加快数据检索的数据结构。索引可以类比为书籍的目录，它们可以帮助数据库快速定位和访问存储在表中的数据。常见的数据库索引类型包括：

1. 主键索引（Primary Key Index）：用于唯一标识表中的每一行记录。主键索引保证了每个值都是唯一的，并且不允许NULL值。它在数据库表中只能有一个。

2. 唯一索引（Unique Index）：确保表中的每个索引列都有唯一的值，但允许NULL值。一个表可以有多个唯一索引。

3. 聚集索引（Clustered Index）：在数据库表中，每个表只能有一个聚集索引。聚集索引决定了表中数据的物理存储顺序，数据行按照索引的顺序存储在磁盘上。

4. 非聚集索引（Non-clustered Index）：非聚集索引是另一种常见的索引类型，它不会影响数据的物理存储顺序，而是创建一个单独的数据结构来加速数据的检索。一个表可以有多个非聚集索引。

5. 复合索引（Composite Index）：也称为组合索引或多列索引，它包含两个或多个列的组合，以加快查询中涉及这些列的搜索效率。

6. 全文索引（Full-Text Index）：主要用于全文搜索，允许在文本字段中进行关键词搜索。这种索引类型适用于大量文本内容的搜索，比如文章、评论等。

7. 空间索引（Spatial Index）：专门用于处理空间数据，如地理信息系统（GIS）中的地理位置数据。它可以帮助加速空间数据的查询和分析。

索引的选择取决于具体的查询需求和数据结构。适当地使用索引可以大大提高数据库的性能，但索引也会增加数据库的存储需求，并在数据更新时带来一定的开销，因此需要在索引的数量和类型上进行权衡和优化。

## 为什么添加索引后查询效率可以提高

添加索引后查询效率可以提高的原因主要有以下几点：

1. **减少数据扫描**：在没有索引的情况下，数据库查询时可能需要全表扫描，即逐行遍历整个表来寻找匹配的数据。而有了索引，数据库可以直接定位到包含匹配数据的索引项，从而避免了全表扫描，减少了数据的检索范围。

2. **提供快速定位**：索引可以看作是一种数据结构，可以帮助数据库快速定位到满足查询条件的数据块。例如，B-Tree 索引可以通过树结构进行快速的二分查找，而哈希索引则可以直接根据哈希值定位到对应的数据。

3. **支持排序和范围查询**：一些索引结构，如 B-Tree 和 B+Tree，支持有序的数据存储，这使得排序查询非常高效。同时，这些索引也能够支持范围查询，例如查找一定范围内的数据，因为索引的有序性使得范围的定位更加快速。

4. **减少 I/O 操作**：添加索引后，数据库通常可以通过索引的指引直接跳过不必要的数据块，从而减少了磁盘 I/O 操作的次数。这可以显著提高查询的效率，尤其是在大数据量和复杂查询条件的情况下。

5. **优化连接操作**：对于连接查询（JOIN），如果连接的字段上有索引，数据库可以更快地定位到匹配的记录，从而减少连接操作的开销。

需要注意的是，索引并不是没有代价的。索引需要占用额外的存储空间，且在数据插入、更新和删除时需要维护索引，可能会引入一定的性能开销。因此，在设计和使用索引时，需要权衡查询性能和更新性能，并根据实际情况进行优化。不适当的索引使用可能导致性能下降，因此需要根据数据库的查询模式和数据特点来选择合适的索引策略。

## 怎么知道数据有没有建立索引

在数据库中，你可以通过查询数据库的元数据信息来判断某个表是否有索引。不同的数据库系统可能有不同的方式来查询元数据，下面我会给出一些通用的方法示例：

1. **SQL 查询元数据**：

   使用 SQL 查询可以获取表的元数据信息，包括索引信息。以下是一些常用的 SQL 查询示例：

   - MySQL:

     ```sql
     SHOW INDEX FROM table_name;
     ```

   - PostgreSQL:

     ```sql
     SELECT indexname FROM pg_indexes WHERE tablename = 'table_name';
     ```

   - Oracle:

     ```sql
     SELECT index_name FROM all_indexes WHERE table_name = 'TABLE_NAME';
     ```

   - SQL Server:

     ```sql
     SELECT name FROM sys.indexes WHERE object_id = OBJECT_ID('table_name');
     ```

2. **使用数据库工具**：

   大多数数据库管理工具（如 MySQL Workbench、SQL Server Management Studio、Oracle SQL Developer 等）都提供了图形界面来查看表的结构和索引信息。你可以通过这些工具来直观地了解表的索引情况。

3. **编程接口**：

   如果你是在编程环境中操作数据库，很多数据库的编程接口也提供了查询元数据的方法。例如，在 Java 中，你可以使用 JDBC 的 `DatabaseMetaData` 类来查询数据库的元数据信息，包括表的索引信息。

总之，查询数据库元数据可以帮助你了解表的索引情况，从而判断数据是否已经建立索引。这对于性能优化和查询调优非常有用。不过需要注意的是，索引的存在并不一定意味着它一定被使用，有时候可能需要进一步分析查询计划来确定索引是否真正起到了作用。

## @component与@Configuration注解的区别

`@Component` 和 `@Configuration` 是 Spring 框架中两个不同的注解，用于不同的目的。它们的主要区别如下：

1. **@Component：**
   - `@Component` 是一个通用的注解，用于标记一个类为 Spring 的组件（Component）。被标记为 `@Component` 的类会被 Spring 自动扫描，并将其实例化为一个 Spring Bean。
   - 这个注解通常用于那些通用的、可重用的组件类，比如服务层、数据访问层、工具类等。
   - 通过 `@ComponentScan` 注解或者在 Spring Boot 应用中的默认扫描路径，Spring 会自动发现和注册所有被 `@Component` 标记的类为 Spring Beans。

示例：
```java
@Component
public class MyService {
    // ...
}
```

2. **@Configuration：**
   - `@Configuration` 是一个特殊的注解，用于标记一个类为 Spring 的配置类。配置类用于定义 Spring Bean 的装配、组合以及其他配置。
   - 在配置类中，你可以使用 `@Bean` 注解来定义自定义的 Spring Bean。这样的 Bean 是由开发者显式地定义和控制的，而不是由自动扫描和自动装配决定。
   - `@Configuration` 注解通常用于创建一些配置对象，比如数据源配置、第三方库的配置、特定功能的配置等。

示例：
```java
@Configuration
public class AppConfig {
    
    @Bean
    public DataSource dataSource() {
        // 定义和配置数据源 Bean
        return new DataSource();
    }
}
```

综上所述，`@Component` 用于将普通类标记为 Spring Bean，而 `@Configuration` 用于标记配置类，其中可以定义自定义的 Spring Beans。这两个注解在不同的场景下使用，但都是 Spring 框架中重要的组成部分。

## 缓存雪崩、缓存穿透、缓存击穿

![image-20230808163953462](https://cdn.jsdelivr.net/gh/yzk656/image/202308081639611.png)

![image-20230808164015328](https://cdn.jsdelivr.net/gh/yzk656/image/202308081640448.png)

缓存雪崩：比如对于Redis中的key设置的缓存失效时间是3小时，当购物期间超过三小时之后，这个首页的Redis缓存在一瞬间全部失效，导致所有的请求都打到了数据库上，造成数据库响应不及时挂掉，这个时候首页就无法提供服务了

解决方案：

​	设置缓存的失效时间，让他不要在同一时间一起失效，在设置缓存时，可以随机初始化他这个失效时间；可以把热点的key平均的分布在不同的redis节点上；还可以不设置缓存失效的时间

![image-20230808183149067](https://cdn.jsdelivr.net/gh/yzk656/image/202308081831217.png)

缓存穿透：比如一直使用ID为负数进行查询，但是我们设置ID时也是一般为正数，因此对于这种访问，redis也是直接交给MySQL去处理，但是数据库也没用这种数据，因此那种恶意用户通过脚本不断的请求这种非法数据

解决方案：

​	对于这种请求无论数据库的返回值是否是空都将其存在Redis中，这样就不会下次还访问数据库了；IP拉黑；对参数进行合法性检验，如果参数不合法直接return掉；使用布隆过滤器

![image-20230808183704734](https://cdn.jsdelivr.net/gh/yzk656/image/202308081837868.png)

缓存击穿：用户不断不断的访问热点的key，当热点key突然失效把请求打到数据库上这个过程就叫做击穿

- 缓存击穿是指针对某个热门数据项的请求无法命中缓存，导致大量请求同时访问后端存储。
- 缓存雪崩是指大量缓存数据在同一时间点过期，导致大量请求都无法命中缓存，同时访问后端存储。

## hashMap是如何扩容的

超过阈值是就进行扩容

负载因子（默认为0.75）*容量（初始默认为16）=12

新建一个更长的数组，然后把原来的数据copy一份到新数组中

## 线程池中重要的参数

线程池是一种用于管理和复用线程的机制，它可以有效地控制并发执行的线程数量，从而提高程序的性能和资源利用率。在配置线程池时，有一些重要的参数需要考虑，以确保线程池的运行符合预期。以下是一些常见的线程池参数：

1. **核心线程数（Core Pool Size）：** 这是线程池中保持活动的基本线程数量。即使这些线程没有任务可执行，也会保持活动状态。核心线程数可以避免线程的频繁创建和销毁，从而减少了资源消耗和线程创建的开销。

2. **最大线程数（Maximum Pool Size）：** 这是线程池中允许的最大线程数量。当队列中的任务数量达到一定阈值且核心线程已满时，线程池会创建新的线程，但不会超过最大线程数限制。防止线程过多造成资源耗尽。

3. **线程存活时间（Keep Alive Time）：** 当线程池中的线程数量超过核心线程数，且处于空闲状态时，这些空闲线程会根据线程存活时间来进行回收，减少资源消耗。通常配合时间单位一起使用。

4. **工作队列（Work Queue）：** 工作队列用于存储尚未执行的任务。线程池中的线程会从工作队列中获取任务进行处理。常见的工作队列类型包括无界队列（例如 `LinkedBlockingQueue`）和有界队列（例如 `ArrayBlockingQueue`），选择适合的队列类型要根据业务需求来决定。

5. **拒绝策略（Rejected Execution Policy）：** 当线程池已满且工作队列已满时，新提交的任务将会触发拒绝策略。拒绝策略决定了如何处理这些无法执行的任务。常见的策略包括丢弃任务、抛出异常、在调用者线程中执行等。

这些参数的合理设置取决于应用程序的性质、硬件环境和预期的负载情况。不同的应用场景可能需要不同的参数配置，以达到最佳的性能和资源利用。在选择线程池参数时，要综合考虑系统的并发情况、任务类型、资源限制以及对响应时间的要求等因素。

## nacos与eureka的区别

Nacos（阿里巴巴开源项目）和Eureka（Netflix开源项目）都是用于服务发现和服务注册的工具，用于在分布式系统中帮助管理和维护服务实例的信息。虽然它们的目标相似，但在实现和功能方面有一些区别。

1. **维护者和背景**:
   - Nacos：由阿里巴巴集团开发和维护，旨在提供一个全方位的动态服务发现和配置管理平台。
   - Eureka：由Netflix开发，最初是作为Netflix的云基础设施组件的一部分，用于在Netflix的分布式系统中实现服务注册和发现。

2. **服务类型**:
   - Nacos：支持服务注册、发现、配置管理和动态DNS等功能，可以用于微服务架构中的各种服务管理需求。
   - Eureka：主要专注于服务注册和发现。

3. **支持的服务实例类型**:
   - Nacos：支持各种类型的服务实例，包括基于主机名、IP地址、端口等的实例。
   - Eureka：更专注于基于主机名和端口的实例。

4. **健康检查**:
   - Nacos：支持自定义健康检查来确定服务实例的状态。
   - Eureka：在原始版本中的健康检查较为有限，但社区可能已经添加了更多功能。

5. **一致性模型**:
   - Nacos：提供了AP（可用性和分区容忍性）和CP（一致性和分区容忍性）模式的选项，以适应不同的场景需求。
   - Eureka：采用了更为宽松的 eventual consistency（最终一致性）模型。

6. **配置管理**:
   - Nacos：集成了配置管理功能，可以管理和动态更新配置信息。
   - Eureka：不提供原生的配置管理功能，但可以与其他配置管理工具集成。

7. **生态系统和扩展性**:
   - Nacos：提供了更全面的功能，包括配置管理、服务发现和动态DNS等，适用于更广泛的使用情景。
   - Eureka：主要专注于服务发现，可能需要与其他工具进行集成以满足更多需求。

总的来说，选择使用Nacos还是Eureka取决于您的项目需求和背景。如果您需要更全面的功能，特别是配置管理等，Nacos可能是更好的选择。如果您只关注基本的服务注册和发现，Eureka可能是一个简单的解决方案。考虑您的技术栈、团队熟悉度和项目需求，来做出明智的选择。请注意，技术生态系统在不断发展，有关这两个工具的信息可能会有所变化。

## hashmap扩容流程

HashMap是Java中用于存储键值对的数据结构，它通过哈希表实现。在HashMap中，哈希表由一个数组（称为桶）和一些存储在桶中的链表（或红黑树，JDK 8之后引入）组成。当存储的键值对数量逐渐增加，可能会导致哈希冲突增多，影响HashMap的性能。为了解决这个问题，HashMap会定期进行扩容操作。

HashMap的扩容流程如下：

1. **判断是否需要扩容：** HashMap会维护一个负载因子（load factor），它表示当前存储的键值对数量与桶数组长度的比值。当负载因子超过一定阈值（通常为0.75），就会触发扩容操作。

2. **创建新的桶数组：** 当需要进行扩容时，HashMap会创建一个新的更大的桶数组。

3. **重新哈希：** 扩容过程中，HashMap会遍历原有的桶数组中的每个元素，并将它们重新计算哈希值，然后放入新的桶数组中。这是为了确保键值对在新的桶数组中分布更均匀，减少哈希冲突。

4. **迁移元素：** 在重新哈希的过程中，同一个桶中的多个元素可能会被映射到新的不同的桶上。这时，HashMap需要将这些元素从旧的桶迁移到新的桶中。这包括将链表中的元素逐个移动，或者在JDK 8之后，将链表转换成红黑树（如果元素数量达到一定阈值），然后再进行迁移。

5. **更新桶数组和容量：** 所有元素迁移完成后，HashMap会更新内部的桶数组和容量信息。

6. **扩容完成：** 至此，HashMap的扩容操作就完成了。新的桶数组长度变大，可以容纳更多的键值对，从而减少了哈希冲突，提高了HashMap的性能。

需要注意的是，HashMap在扩容过程中需要进行复制和迁移元素，因此扩容会涉及一些性能开销。为了尽量减少扩容带来的影响，可以在初始化HashMap时预估存储的键值对数量，从而提前分配适当大小的桶数组。这样可以减少扩容操作的频率。

总结起来，HashMap的扩容流程包括判断是否需要扩容、创建新的桶数组、重新哈希、迁移元素、更新桶数组和容量等步骤，目的是为了保持HashMap的性能和数据分布均匀。

## 对于Hashmap何时才将链表转换成红黑树

对于hashmap，数组长度大于64或者链表长度大于8时，链表转换成红黑树

是的，您说得对。从JDK 8开始，Java中的HashMap实现在某些条件下会将链表转换成红黑树，以提高在哈希冲突情况下的查找和插入性能。

具体来说，HashMap中的链表会在以下两种情况下被转换成红黑树：

1. **链表长度过长：** 当某个桶中的链表长度超过8时，HashMap会将该链表转换成红黑树。这是因为链表长度较长时，查找操作的时间复杂度可能会较高（O(n)，n为链表长度），而红黑树的查找操作相对更加高效（O(log n)）。

2. **数组长度较大：** 当HashMap的数组长度大于64时，如果某个桶中的链表长度超过6时，也会将该链表转换成红黑树。这是为了在整体数据量较大的情况下，仍然保持较好的查找性能。

需要注意的是，一旦链表被转换成红黑树，后续的插入、查找和删除操作都会使用红黑树的操作来进行，从而提高了性能。然而，转换成红黑树也会带来一些额外的开销，因为红黑树的操作相对复杂，占用的内存也更多。

这个优化策略的目标是在不同的数据量情况下都能够保持HashMap的高效性能，同时避免链表过长时的性能问题。

# 2023-08-13

## 线程池中提交一个任务的流程是怎样的？

![image-20230813094403639](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813094403639.png)

![image-20230813094703453](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813094703453.png)

## 线程池中有几种状态，分别是如何变化的

![image-20230813100727248](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813100727248.png)

![image-20230813101322527](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813101322527.png)

## 如何停止一个线程

![image-20230813101517636](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813101517636.png)

因为对于reentrantLock锁的unlock是在for循环后执行的，但是for循环并没有执行完，因此并不会执行unlock方法

建议使用interrupt方法去停止线程，同时可以在线程中声明一些逻辑代码去停止线程

![image-20230813102745246](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813102745246.png)

## 线程池的核心线程数、最大线程数该如何设置

![image-20230813103507050](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813103507050.png)

![image-20230813103516175](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813103516175.png)

![image-20230813113949449](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813113949449.png)

![image-20230813114801219](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813114801219.png)

## tomcat默认最大连接数

Tomcat 8 版本默认的最大连接数为 200，最大线程数为 200。这意味着在默认情况下，Tomcat 最多能够同时处理 200 个请求。在实际部署中，您可以通过调整 Tomcat 的配置参数，如连接数、线程池大小等，来提高同时处理的请求数。

如果您需要更大的并发处理能力，您可以根据实际情况调整 Tomcat 的配置，以适应您的应用需求。请注意，调整配置需要谨慎进行，以避免资源过度占用或其他性能问题。在进行任何配置更改之前，建议您详细了解 Tomcat 的配置参数和其对应的影响。

请注意，上述信息基于我所知道的截止日期为2021年9月。如果在此之后有关于 Tomcat 的新变化或更新，请您查阅最新的文档或资源以获取准确的信息。

---

但是线程数也并不是越大越好

下图是进行压测比较（针对设置的不同的最大连接数）

![image-20230813115228538](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813115228538.png)

## 如何理解Java并发中的可见性

使用Volatile关键字修饰变量

![image-20230813115515697](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813115515697.png)

![image-20230813115530751](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813115530751.png)

## 如何理解Java并发中的原子性

![image-20230813120841684](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813120841684.png)

![image-20230813120939145](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813120939145.png)

![image-20230813121034097](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813121034097.png)

## 如何理解Java并发中的有序性

![image-20230813121340353](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813121340353.png)

![image-20230813121529641](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813121529641.png)

![image-20230813121627085](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813121627085.png)

## Java死锁如何避免

![image-20230813132407693](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813132407693.png)

## hashmap扩容机制

![image-20230813133455270](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813133455270.png)

## 说一下hashmap的put方法

![image-20230813134123291](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813134123291.png)

## Jdk1.7到jdk1.8，hashmap发生了哪些变化

![image-20230813135650462](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813135650462.png)

## concurreentHashMap的扩容机制

 <img src="https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813152539676.png" alt="image-20230813152539676" style="zoom:150%;" />

第二条也就是辅助迁移

## ReentrantLock中tryLock和lock方法的区别

![image-20230813171234227](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813171234227.png)

## ReentrantLock中tryLock的应用场景

`ReentrantLock` 是 Java 中提供的一个可重入锁，与传统的 `synchronized` 关键字相比，它提供了更多的灵活性和功能。`tryLock` 是 `ReentrantLock` 提供的一个方法，它可以用于尝试获取锁，但不会阻塞线程，而是会立即返回一个结果。

`tryLock` 方法有几个常见的应用场景：

1. **避免死锁：** 通过在尝试获取多个锁时使用 `tryLock`，可以在获取锁失败时及时释放已经获得的锁，避免发生死锁。例如，如果一个线程需要同时获得多个资源的锁，在获取其中一个锁失败时，可以释放已经获取的锁，避免造成死锁情况。

2. **超时等待：** `tryLock` 方法可以指定一个超时时间，在指定时间内尝试获取锁，如果获取成功则继续执行，如果超时未能获取到锁，可以进行其他处理或尝试其他逻辑，避免线程一直阻塞。

3. **轮询获取锁：** 在某些场景中，可以使用 `tryLock` 进行轮询，即在一段时间内反复尝试获取锁，如果获取不到则进行其他处理，而不是一直阻塞线程。

4. **避免长时间等待：** 如果一个线程在等待获取锁的时间较长，可能会影响整体性能，使用 `tryLock` 可以在获取锁失败时及时返回，避免长时间的等待。

需要注意的是，`tryLock` 方法返回一个 `boolean` 值，表示是否成功获取到锁。如果获取成功，需要在适当的时候释放锁，以避免资源泄漏。

总之，`tryLock` 方法适用于那些需要尝试获取锁但不希望一直阻塞线程的场景，它可以提供更多的控制和灵活性，用来解决一些复杂的并发问题。

## Hashmap的扩容是双倍扩容吗

是的，Java 中的 HashMap 在发生扩容时采用的是双倍扩容策略。

当 HashMap 中的元素数量达到阈值时，HashMap 将会触发扩容操作，以便维持其性能。在扩容过程中，HashMap 的容量会翻倍，即扩容后的容量是扩容前容量的两倍。这个扩容操作涉及到重新计算每个元素在新的容量下的索引位置，以确保元素分布更加均匀。

双倍扩容策略在一定程度上能够减少扩容操作的频率，因为每次扩容都会涉及到重新分配内存、重新计算索引等操作，可能会影响性能。通过双倍扩容，HashMap 能够在一定程度上平衡内存开销和性能。不过，在某些情况下，如果预知数据量会非常大，也可以在创建 HashMap 时提前指定一个较大的初始容量，以减少扩容次数。

需要注意的是，尽管双倍扩容可以减少扩容次数，但在某些情况下，如果 HashMap 中的元素数量远远超过初始容量，仍然可能会导致扩容操作造成较大的性能开销。因此，在选择初始容量时，需要根据具体的使用情况和性能需求进行权衡。

##  ReentrantLock中的公平锁和非公平锁的底层实现

![image-20230813175915665](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813175915665.png)

## Sychronized的偏向锁 、轻量级锁、重量级锁

![image-20230813214223962](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813214223962.png)

## Sychronized和ReentrantLock的区别

![image-20230813215332706](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813215332706.png)

## ThreadLocal的底层原理

![](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230813223025429.png)

## 并发、并行、串行之间的区别

![image-20230814004536507](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814004536507.png)

## 对守护线程的理解

![image-20230814004800731](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814004800731.png)

## 说说对线程安全的理解

![image-20230814004932705](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814004932705.png)

## 谈谈你对AQS的理解、AQS是如何实现可重入锁

![image-20230814005130020](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814005130020.png)

## 线程池的底层工作原理

![image-20230814005450692](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814005450692.png)

## 线程池为什么是先添加队列而不是先创建最大线程

![image-20230814005837483](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814005837483.png)

## 线程之间是如何进行通讯的

![image-20230814010136727](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814010136727.png)

一个进程之间的线程可以通过共享内存进行通讯；不同进程之间的线程可以通过网络进行通讯

## 如果你提交任务时，线程池队列已满，这时会发生什么？

![image-20230814010448050](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814010448050.png)

## 简述线程池原理、FixedThreadPool用的阻塞队列

![image-20230814010631120](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814010631120.png)

## Volatile关键字，他是如何保证可见性、有序性

![image-20230814010939310](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230814010939310.png)

# 2023-08-15

## 多线程中的核心线程与非核心线程是如何区分的

在多线程编程中，通常有一个线程池（ThreadPool）来管理线程的创建和回收。线程池中的线程可以分为核心线程（Core Threads）和非核心线程（Non-Core Threads），它们有一些区别和特点。

核心线程（Core Threads）：
1. 核心线程是线程池中最初创建的线程数量，它们会一直存在，不会被销毁，除非线程池被显式地关闭。
2. 核心线程负责处理任务队列中的任务，如果任务队列中有任务，核心线程会立即执行任务。
3. 核心线程数量在线程池的初始化时被设置，一般情况下保持不变，除非显式地调用线程池的设置方法进行更改。

非核心线程（Non-Core Threads）：
1. 非核心线程是在线程池中可创建的额外线程，当核心线程都在处理任务并且任务队列中有未处理的任务时，非核心线程会被创建来帮助处理这些任务。
2. 非核心线程数量通常有一个上限，称为线程池的最大线程数。一旦达到最大线程数，不会再创建新的线程。
3. 如果非核心线程在一段时间内没有执行任务，线程池可以根据一些策略来回收这些线程，以减少资源占用。

总结：
核心线程是线程池中最初创建的线程，一直存在，负责执行任务队列中的任务；非核心线程是在需要时额外创建的线程，用于处理任务，但有一定的上限和回收机制。

请注意，具体的多线程库和编程语言可能会有不同的实现和策略，上述描述是一般情况下的概念性解释。

## 线程池的线程数最小是核心线程数吗？会出现线程数小于核心线程数的情况吗

是的，线程池的线程数最小值通常等于核心线程数。核心线程数是线程池中最初创建的线程数量，它们会一直存在，不会被销毁，除非线程池被显式地关闭。这些核心线程负责处理任务队列中的任务。

在一些情况下，线程池的线程数可能会小于核心线程数，但这通常是由于线程池的特定配置或调整策略造成的。例如，在一些实现中，可能允许临时的、非核心的线程数少于核心线程数，以便在负载较轻时减少资源占用。

但总体而言，核心线程数应该是线程池的最小线程数，即使非核心线程在某些情况下可能被回收或减少。核心线程数的存在保证了线程池始终有一定数量的线程可以立即执行任务，从而提供了更快的响应能力。

## 线程池是如何实现线程的复用的

线程池通过实现线程的复用来提高多线程应用程序的性能和效率。线程的创建和销毁是比较昂贵的操作，线程池的主要目标之一就是减少这种开销。以下是线程池如何实现线程的复用的一般流程：

1. **线程池初始化：** 在创建线程池时，会指定核心线程数、最大线程数、任务队列等参数。线程池会在初始化阶段创建核心线程，这些线程会一直存在，等待执行任务。

2. **任务提交：** 当应用程序提交一个任务给线程池执行时，线程池会首先尝试将任务分配给一个空闲的核心线程。如果核心线程都在忙碌，任务会被放入任务队列中等待执行。

3. **任务队列：** 任务队列是线程池的一个关键部分。它用于暂时存储等待执行的任务。如果核心线程都在执行任务，而任务队列还有未处理的任务，线程池会将这些任务暂存在队列中，等待核心线程空闲时执行。

4. **非核心线程的创建：** 如果核心线程都在处理任务并且任务队列已满，线程池可能会创建非核心线程来帮助处理任务。非核心线程会执行等待队列中的任务。

5. **线程的复用：** 一旦线程执行完一个任务，它会被返回到线程池中，而不是被销毁。这样，这些线程可以继续被复用来执行其他任务，避免了频繁地创建和销毁线程的开销。

6. **线程的回收：** 一些线程池实现会根据一定的策略来回收非核心线程，以防止线程数量无限增长。这些策略可以包括线程空闲超时时间、最大线程数限制等。

通过上述流程，线程池实现了线程的复用，使得多个任务可以共享同一组线程来执行，从而降低了线程创建和销毁的开销，提高了多线程应用程序的性能和效率。

## Java中如何创建线程池

在 Java 中，你可以使用 `java.util.concurrent` 包提供的 `ExecutorService` 接口及其实现类来创建线程池。以下是一些创建线程池的常见方式：

1. **使用 `Executors` 工厂方法：**
`Executors` 类提供了一些工厂方法来创建不同类型的线程池。这是最简单的创建线程池的方式，但在某些情况下可能不够灵活，因为它隐藏了一些配置选项。

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class ThreadPoolExample {
    public static void main(String[] args) {
        // 创建一个固定大小的线程池
        ExecutorService executor = Executors.newFixedThreadPool(5);

        // 提交任务给线程池执行
        executor.submit(() -> {
            // 任务逻辑
            System.out.println("Task executed by thread: " + Thread.currentThread().getName());
        });

        // 关闭线程池
        executor.shutdown();
    }
}
```

2. **使用 `ThreadPoolExecutor`：**
`ThreadPoolExecutor` 是 `ExecutorService` 接口的一个实现类，它提供了更详细的线程池配置选项，可以更精确地控制线程池的行为。

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.ThreadPoolExecutor;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.ArrayBlockingQueue;

public class ThreadPoolExample {
    public static void main(String[] args) {
        int corePoolSize = 2;
        int maxPoolSize = 5;
        long keepAliveTime = 60L;
        int queueCapacity = 10;

        ExecutorService executor = new ThreadPoolExecutor(
            corePoolSize,
            maxPoolSize,
            keepAliveTime,
            TimeUnit.SECONDS,
            new ArrayBlockingQueue<>(queueCapacity)
        );

        executor.submit(() -> {
            System.out.println("Task executed by thread: " + Thread.currentThread().getName());
        });

        executor.shutdown();
    }
}
```

在上述示例中，`corePoolSize` 表示核心线程数，`maxPoolSize` 表示最大线程数，`keepAliveTime` 表示非核心线程的最大存活时间，`queueCapacity` 表示任务队列的容量。

无论使用哪种方式，一般都需要在任务执行完毕后关闭线程池，以释放资源。使用 `shutdown()` 方法关闭线程池会等待已提交的任务执行完毕后再关闭线程池，而使用 `shutdownNow()` 方法会尝试立即关闭线程池。

## 分布式锁的实现方式

分布式锁是在分布式系统中用来协调不同节点或进程之间访问共享资源的一种机制。它可以保证在分布式环境下，同一时刻只有一个节点能够获取到锁，从而防止资源竞争和数据不一致问题。以下是一些常见的分布式锁的实现方式：

1. **基于数据库的分布式锁：**
   可以使用数据库的事务和锁机制来实现分布式锁。常见的做法是在数据库中创建一个表，使用行级锁或者乐观锁来控制对共享资源的访问。获取锁时，向数据库插入一条记录或者更新某个字段，释放锁时删除对应的记录或者更新字段。

2. **基于缓存的分布式锁：**
   使用分布式缓存系统如Redis或ZooKeeper来实现分布式锁。通过在缓存中设置某个键的值作为锁标识，获取锁时尝试设置该键的值，成功则获取锁，释放锁时删除对应的键。

3. **基于ZooKeeper的分布式锁：**
   ZooKeeper是一个分布式协调服务，它可以用来实现分布式锁。可以创建一个有序临时节点作为锁的标识，所有节点按照顺序创建节点并尝试获取锁，最小节点的节点持有锁，其他节点按序等待。

4. **基于公共资源的分布式锁：**
   使用共享的外部资源，如文件系统或数据库，作为锁的标识。所有节点通过竞争对该资源的访问来获取锁，类似于文件锁。

5. **基于算法的分布式锁：**
   使用分布式算法来实现分布式锁，如Chubby算法、Raft协议等。这些算法可以保证在分布式系统中实现一致性的锁机制。

需要注意的是，分布式锁的实现要考虑到分布式系统的复杂性和性能影响，需要谨慎设计和测试。不同的实现方式适用于不同的场景，选择合适的分布式锁方案取决于具体的需求和架构。

## undolog、binlog、redolog之间的区别

`undolog`、`binlog` 和 `redolog` 都是与数据库系统相关的日志，用于维护数据的一致性、持久性和恢复能力，但它们在功能和用途上有一些区别。

1. **Undo Log (`undolog`)：**
   - `undolog` 是用于支持事务的回滚操作和读一致性的日志，也称为回滚日志。
   - 在数据库中，当进行数据更新操作（如插入、更新、删除）时，会首先将被修改的数据复制一份到 `undolog` 中，然后再进行实际的修改。如果事务回滚，可以通过 `undolog` 中的信息将数据还原到事务开始之前的状态。
   - `undolog` 通常用于实现数据库的 MVCC（多版本并发控制）机制，以支持并发事务处理和读一致性。

2. **Binary Log (`binlog`)：**
   - `binlog` 是一种二进制格式的日志，用于记录数据库中的写操作，如插入、更新、删除等。
   - 主要用于数据库的主从复制。在主数据库上记录的 `binlog` 可以传输到从数据库上，从而使从数据库能够重放主数据库上的写操作，保持数据的一致性。
   - `binlog` 可以用于备份和恢复数据库，也可以用于实现数据库的高可用和灾难恢复。

3. **Redo Log (`redolog`)：**
   - `redolog` 是用于保障数据库事务的持久性的日志，也称为事务日志。
   - 在数据库中，当进行数据更新操作时，会将这些操作记录到 `redolog` 中，然后再进行实际的修改。如果数据库崩溃或发生故障，可以通过 `redolog` 中的信息重新执行操作，从而恢复到事务提交前的状态。
   - `redolog` 的作用是确保已提交的事务在数据库故障时不会丢失，从而保障数据库的一致性和持久性。

总结：
- `undolog` 用于支持事务回滚和读一致性。
- `binlog` 用于主从复制、备份和恢复。
- `redolog` 用于保障事务的持久性和故障恢复。

这些日志在数据库系统中共同协作，确保了数据的完整性、一致性和持久性，同时提供了高可用性和灾难恢复的能力。

## Java中futuretask是干嘛的

`FutureTask`是Java中用于表示一个可以异步执行的任务（Task）的类，它实现了`Future`和`Runnable`接口。`Future`表示一个可能还没有完成的计算，而`Runnable`表示一个可以在单独的线程中执行的任务。

`FutureTask`允许你将一个计算包装成一个可取消并且可以获取结果的异步任务。通常情况下，你可以将一个`Callable`对象传递给`FutureTask`，然后将`FutureTask`提交给`ExecutorService`（线程池）执行。

主要特点和用途包括：

1. **异步执行：** 你可以将一个任务交给`FutureTask`，然后继续执行其他操作，而不需要等待任务完成。

2. **获取结果：** 通过调用`get()`方法，你可以获取任务的计算结果。如果任务还没有完成，调用`get()`会阻塞，直到任务完成并返回结果。

3. **取消任务：** 你可以调用`cancel()`方法来取消任务的执行。这在某些情况下是很有用的，特别是当你希望终止一个长时间运行的任务。

4. **监视任务状态：** `FutureTask`提供了方法来查询任务是否已经完成、是否被取消等状态。

5. **并发控制：** `FutureTask`可以在多线程环境中使用，帮助你管理多个任务的并发执行和结果获取。

以下是一个简单的示例代码，展示了如何使用`FutureTask`：

```java
import java.util.concurrent.*;

public class FutureTaskExample {
    public static void main(String[] args) {
        Callable<Integer> callableTask = () -> {
            // 模拟一个耗时计算
            Thread.sleep(2000);
            return 42;
        };

        FutureTask<Integer> futureTask = new FutureTask<>(callableTask);

        // 创建线程池并提交任务
        ExecutorService executor = Executors.newSingleThreadExecutor();
        executor.submit(futureTask);

        // 在这里可以执行其他操作，不需要等待任务完成

        try {
            // 获取任务结果，如果任务还没有完成，此处会阻塞
            Integer result = futureTask.get();
            System.out.println("Task result: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }

        // 关闭线程池
        executor.shutdown();
    }
}
```

在这个例子中，`FutureTask`用来包装一个耗时计算，我们可以在后台执行这个任务，然后在需要的时候获取其结果。这种机制在需要进行异步计算，同时又需要控制和获取计算结果的情况下非常有用。

## 如何保证T1、T2、T3顺序执行

![image-20230815224317148](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230815224317148.png)

![image-20230815225853182](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230815225853182.png)

![image-20230816103237743](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230816103237743.png)

![image-20230816150434992](https://cdn.jsdelivr.net/gh/yzk656/image/img/image-20230816150434992.png)

## 使用countdownlatch实现T1、T2、T3顺序执行

`CountDownLatch` 是 Java 多线程编程中的一个工具类，用于控制线程的执行顺序。通过它，你可以等待多个线程执行完毕后再继续执行下面的操作。在你的情况下，你想要实现 T1、T2、T3 顺序执行，可以使用 `CountDownLatch` 来实现。

以下是一个使用 `CountDownLatch` 实现 T1、T2、T3 顺序执行的示例代码：

```java
import java.util.concurrent.CountDownLatch;

public class Main {
    public static void main(String[] args) {
        CountDownLatch latchT1 = new CountDownLatch(1);
        CountDownLatch latchT2 = new CountDownLatch(1);

        Thread t1 = new Thread(() -> {
            System.out.println("T1 is running");
            // T1 执行完毕后，释放 T2
            latchT1.countDown();
        });

        Thread t2 = new Thread(() -> {
            try {
                // 等待 T1 执行完毕
                latchT1.await();
                System.out.println("T2 is running");
                // T2 执行完毕后，释放 T3
                latchT2.countDown();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        });

        Thread t3 = new Thread(() -> {
            try {
                // 等待 T2 执行完毕
                latchT2.await();
                System.out.println("T3 is running");
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        });

        t1.start();
        t2.start();
        t3.start();
    }
}
```

在这个示例中，我们创建了两个 `CountDownLatch`，一个用于 T1 到 T2 的通信，另一个用于 T2 到 T3 的通信。T1 在执行完毕后释放 T2，T2 在执行完毕后释放 T3，从而保证了 T1、T2、T3 的顺序执行。

记得在实际应用中处理异常和线程的关闭等情况。

## countDown方法是什么意思

`CountDownLatch` 类中的 `countDown()` 方法用于减少计数器的值。计数器在初始化时指定一个初始值，然后可以通过调用 `countDown()` 方法逐渐减少计数器的值。当计数器的值减少到零时，等待该计数器的线程将被释放，可以继续执行。

具体来说，`CountDownLatch` 的 `countDown()` 方法的作用是：

1. 将计数器的值减1。
2. 如果减少后的计数器值为0，则唤醒所有等待该计数器的线程，使它们可以继续执行。

在你的问题中，我们使用了两个 `CountDownLatch`，分别用于控制 T1 到 T2 的顺序和 T2 到 T3 的顺序执行。在 T1 和 T2 执行完毕后，通过调用 `countDown()` 方法来减少计数器的值，从而释放等待的线程。

## 一个用于 T1 到 T2 的通信，另一个用于 T2 到 T3 的通信这句话是什么意思

抱歉，我可能没有表达清楚。让我重新解释一下。

在前面提供的示例中，我创建了两个 `CountDownLatch` 对象，分别命名为 `latchT1` 和 `latchT2`。这两个 `CountDownLatch` 对象的作用是帮助线程之间进行通信，确保它们按照特定的顺序执行。

1. `latchT1`：这个 `CountDownLatch` 对象用于控制 T1 到 T2 的通信。在示例代码中，T1 执行完毕后会调用 `latchT1.countDown()` 方法，将 `latchT1` 的计数器减少。而在 T2 的线程中，通过调用 `latchT1.await()` 方法，等待计数器变为0，即等待 T1 执行完毕后才能继续执行。

2. `latchT2`：这个 `CountDownLatch` 对象用于控制 T2 到 T3 的通信。在示例代码中，T2 执行完毕后会调用 `latchT2.countDown()` 方法，将 `latchT2` 的计数器减少。而在 T3 的线程中，通过调用 `latchT2.await()` 方法，等待计数器变为0，即等待 T2 执行完毕后才能继续执行。

通过这种方式，我们确保了线程 T1、T2 和 T3 按照所需的顺序执行，即先执行 T1，然后执行 T2，最后执行 T3。这种通信机制能够帮助线程之间协调工作，以实现特定的执行顺序。

## await方法的作用

`await()` 方法是 `CountDownLatch` 类中的一个方法，用于使当前线程等待，直到计数器的值减少到零。当调用 `await()` 方法时，如果计数器的值不为零，当前线程将被阻塞，直到计数器的值变为零为止，然后线程将被唤醒继续执行。

在你的情况中，我们使用了 `await()` 方法来实现线程之间的协调，以确保它们按照特定的顺序执行。在示例代码中：

- T2 线程在执行之前会调用 `latchT1.await()`，这意味着 T2 线程会等待，直到 `latchT1` 的计数器变为零（即 T1 线程执行完毕并调用了 `latchT1.countDown()`）。
- 同样，T3 线程在执行之前会调用 `latchT2.await()`，这意味着 T3 线程会等待，直到 `latchT2` 的计数器变为零（即 T2 线程执行完毕并调用了 `latchT2.countDown()`）。

通过这种方式，`await()` 方法帮助实现了线程之间的等待和唤醒操作，确保它们在特定的条件下按照顺序执行，以达到你所期望的结果。

## 通过线程池来实现

```java
package class18;

import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class ThreadPoolExample {
    public static void main(String[] args) {
        ExecutorService threadPool = Executors.newFixedThreadPool(1);
        threadPool.execute(new Runnable() {
            @Override
            public void run() {
                System.out.println("T1线程开始执行");
            }
        });

        threadPool.execute(new Runnable() {
            @Override
            public void run() {
                System.out.println("T2线程开始执行");
            }
        });

        threadPool.execute(new Runnable() {
            @Override
            public void run() {
                System.out.println("T3线程开始执行");
            }
        });
    }
}
```

## execute与submit的区别

在Java中，`execute`和`submit`都是用于将任务提交给线程池执行的方法，但它们在一些细节上有一些区别。这两个方法都属于`ExecutorService`接口，而`ExecutorService`是线程池的主要接口。

1. `execute` 方法：
`execute` 方法用于提交一个 `Runnable` 任务给线程池执行，它没有返回值（`void`）。当你只关心任务的执行，而不需要获取任务的执行结果时，可以使用 `execute` 方法。示例代码如下：

```java
ExecutorService executor = Executors.newFixedThreadPool(5);
executor.execute(() -> {
    // 任务代码
});
```

2. `submit` 方法：
`submit` 方法用于提交一个 `Callable` 或 `Runnable` 任务给线程池执行，并返回一个 `Future` 对象，你可以通过这个 `Future` 对象获取任务的执行结果、取消任务等。因此，`submit` 方法更加灵活，适用于需要获取任务结果或进行任务控制的情况。示例代码如下：

```java
ExecutorService executor = Executors.newFixedThreadPool(5);
Future<String> future = executor.submit(() -> {
    // 任务代码
    return "Task completed!";
});
```

你可以使用 `Future` 对象来获取任务的执行结果：

```java
try {
    String result = future.get(); // 阻塞，直到任务完成并返回结果
    System.out.println(result);
} catch (InterruptedException | ExecutionException e) {
    e.printStackTrace();
}
```

总结：
- 如果你只关心任务的执行，并不需要获取任务的返回结果，可以使用 `execute` 方法。
- 如果你需要获取任务的返回结果、取消任务或者进行其他任务控制，可以使用 `submit` 方法，并通过返回的 `Future` 对象来操作。

无论你选择哪种方法，都是根据具体的需求来决定的。

## 线程的创建

线程的创建方式只有一种：就是Thread类的start方法，然后调用JVM的start方法，然后通过CPU的调度回调到run方法，对于那些继承Thread、重写runable、callable都只是定义的run方法不同

## redis的数据类型

Redis（Remote Dictionary Server）是一种开源的、高性能的键值对存储数据库。它支持多种数据类型，以下是Redis的主要数据类型：

1. String（字符串）：最基本的数据类型，可以存储任何类型的数据，如文本、二进制数据等。

2. List（列表）：有序的字符串列表，可以进行头部和尾部的插入和删除操作，常用于实现队列和栈。

3. Set（集合）：无序的字符串集合，不允许重复元素，支持交集、并集、差集等集合操作。

4. Sorted Set（有序集合）：与普通集合类似，每个成员关联一个分数（score），用于排序，适用于排行榜等应用。

5. Hash（哈希表）：类似于关联数组，可以存储多个键值对，适合存储对象属性。

6. Bitmaps（位图）：可以进行位级别的操作，适用于一些统计和布隆过滤器等应用。

7. HyperLogLog（基数估计算法）：用于估计集合中不重复元素的数量，占用很小的空间。

8. Geospatial（地理位置）：支持存储地理坐标，可以进行距离计算和范围查询。

9. Streams（流）：类似于日志的数据结构，支持有序的事件流处理。

这些数据类型使得Redis适用于各种不同的应用场景，如缓存、队列、计数器、实时统计等。不同的数据类型在Redis中有对应的命令操作，可以灵活地处理不同的数据需求。

## Redis快的原因

以下是Redis快的原因：

A. 基于内存操作，客户端数据操作不需要跟磁盘交互。
B. Redis自己支持多种底层数据结构，比如skiplist、sds，操作快。
C. 命令执行单线程、同时通信采用多路复用模型。

这些因素都有助于使Redis成为一种高性能的键值存储数据库。选项D是关于数据管理和持久化的，虽然与性能有关，但不是Redis快速的主要原因之一。

## skiplist、sds数据结构是什么

Skiplist（跳跃表）和SDS（简单动态字符串）是Redis使用的两种底层数据结构，用于支持不同的功能和性能需求。

1. Skiplist（跳跃表）：
Skiplist是一种有序数据结构，用于实现有序集合（Sorted Set）数据类型。它通过在数据层级之间创建一个"跳跃"层，以快速进行元素的插入、删除和查找操作。Skiplist的插入和查找操作时间复杂度为O(log n)，在某些情况下可以比平衡二叉树更高效。Redis使用跳跃表作为Sorted Set的底层实现，以支持有序集合的高效操作。

2. SDS（简单动态字符串）：
SDS是一种动态字符串数据结构，用于存储字符串数据类型。它可以根据字符串的长度自动扩展和收缩内存，减少了内存分配和拷贝的开销，提高了字符串操作的性能。SDS还可以存储二进制数据，不仅限于文本字符串。Redis使用SDS作为字符串数据类型的底层实现，这使得字符串操作在Redis中非常高效。

这两种底层数据结构的设计和实现使得Redis在处理不同类型的数据和操作时都能获得出色的性能和效率。

## 关于Redis过期策略

A. 惰性过期，即当key被访问时才会去检查是否过期，对内存不友好，对CPU友好。
B. 定期过期的时间间隔默认是100ms触发一次，也可以通过redis.conf配置文件中的hz来进行配置。
D. 过期策略是为了删除已经过期的数据。

选项C中的描述不准确，定期过期并不是每隔100ms扫描所有的key，然后删除过期的key。实际上，定期过期会以配置的频率对一部分key进行扫描和删除操作，而不是扫描全部的key。

# 2023-08-17

## spring是什么，特点，注解有那些

Spring是一个开源的Java应用框架，它提供了一种全面的编程和配置模型，用于构建现代化的企业级应用程序。Spring框架的核心目标是简化应用程序的开发，提高代码的可重用性和可维护性，并促进松耦合的设计和测试。Spring提供了许多模块和功能，用于处理各种应用程序层面的任务，包括但不限于依赖注入、AOP（面向切面编程）、事务管理、数据访问、Web开发等。

Spring的一些特点包括：

1. **依赖注入（DI）和控制反转（IoC）：** Spring框架通过依赖注入的方式来管理组件之间的依赖关系，将对象的创建和依赖关系的管理交由框架来处理，从而实现控制反转。

2. **面向切面编程（AOP）：** Spring支持面向切面编程，可以将横切关注点（如日志、事务、安全性等）从主要业务逻辑中分离出来，提高了代码的模块化和可维护性。

3. **声明式事务管理：** Spring提供了声明式的事务管理，可以通过注解或配置来管理数据库事务，简化了事务的管理和编码。

4. **灵活的数据访问：** Spring支持多种数据访问技术，包括JDBC、ORM（如Hibernate、JPA）、NoSQL等，使数据访问更加灵活和便捷。

5. **集成多种视图技术：** Spring支持多种视图技术，如JSP、Freemarker、Velocity等，用于构建Web应用程序。

6. **轻量级和非侵入性：** Spring框架的设计哲学是轻量级和非侵入性的，不强制应用程序采用特定的编程模型，可以逐渐引入和使用Spring的各种功能。

7. **模块化设计：** Spring框架由多个模块组成，可以根据应用程序的需求选择性地引入不同的模块。

一些常用的Spring注解包括：

- `@Component`：用于将类标记为Spring容器中的组件，让Spring自动扫描并注册这些组件。
- `@Autowired`：用于自动注入依赖，通常用于构造函数、属性或方法上。
- `@Service`、`@Repository`、`@Controller`：这些注解是`@Component`的特殊变种，用于指定不同类型的组件。
- `@Scope`：用于指定Bean的作用域，如单例、原型等。
- `@Value`：用于注入属性值。
- `@Configuration`、`@Bean`：用于定义配置类和Bean，支持Java配置方式。
- `@Aspect`、`@Pointcut`、`@Before`、`@After`：用于AOP相关的注解。

这只是一小部分Spring框架的特点和注解，Spring框架拥有丰富的功能和模块，用于支持各种应用程序的开发需求。 



## 关于redis的淘汰策略，下列说话正确的是

。

正确答案:A,B,D

解析:
C.redis的淘汰算法没有FIFO。只有lru、lfu、random、ttl、noeviction

## Redis哨兵机制实现故障转移时，选举从节点变成主节点的因素有（）
[多选]

A.断开连接时长
B.优先级排序（replica-priority配置）
C.数据偏移量
D.进程ID

答案是:ABCD

解析:
ABCD都是从节点选举成为主节点的考虑因素

# 并发编程

## Lock和synchronized的区别

1. 他俩都是用于解决线程安全问题的一个工具
2. synchronized是Java中的一个同步关键字，而Lock是JUC包里面提供的一个接口，其中有一个著名的ReentrantLock实现类

# 2023-08-23

## SpringBoot使用ThreadLocal保存每次请求的用户信息

ThreadLocal是Thread的局部变量，用于编多线程程序，对解决多线程程序的并发问题有一定的启示作用。

一、ThreadLocali简介
ThreadLocal叫做线程变量，意思是ThreadLocal中填充的变量属于当前线程，该变量对其他线程而言是隔离的，也就是说该变量是当前

线程独有的变量。ThreadLocali为变量在每个线程中都创建了一个副本，那么每个线程可以访问自己内部的副本变量。

ThreadLoal变量，线程局部变量，同一个ThreadLocal所包含的对象，在不同的Thread中有不同的副本。这里有几点需要注意：

因为每个Thread内有自己的实例副本，且该副本只能由当前Thread使用。这是也是ThreadLocal命名的由来。
既然每个Thread有自己的实例副本，且其它Thread不可访问，那就不存在多线程间共享的问题。
ThreadLocal提供了线程本地的实例。它与普通变量的区别在于，每个使用该变量的线程都会初始化一个完全独立的实例副本。
ThreadLocal变量通常被private static修饰。当一个线程结束时，它所使用的所有ThreadLocal相对的实例副本都可被回收。

总的来说，ThreadLocal适用于每个线程需要自己独立的实例且该实例需要在多个方法中被使用，也即变量在线程间隔离而在方法或类间共享的场景

github地址：https://github.com/yzk656/ThreadLocalDemo

流程：

定义一个UserThreadLocal类，定义一个`private static final ThreadLocal<User> USER_INFO_THREAD_LOCAL = new ThreadLocal<>();`通时定义一个get、set、clear静态方法

定义一个拦截器LoginInterceptor实现HandlerInterceptor接口

这样就随时随地可以使用这些方法，同时随时访问该线程中的包含的对象

## 介绍一下Spring的ioc和aop流程

Spring框架是一个广泛用于Java应用程序开发的框架，它提供了多种功能，包括IoC（Inversion of Control，控制反转）和AOP（Aspect-Oriented Programming，面向切面编程）。下面是IoC和AOP在Spring中的基本流程：

**IoC（控制反转）流程：**

1. **定义Bean：** 在Spring中，你需要定义要管理的各种组件、服务或对象，这些都被称为"Bean"。通常，你可以通过XML配置、注解或Java代码来定义Bean。

2. **配置IoC容器：** Spring的IoC容器是一个负责实例化、配置和管理Bean的容器。你需要配置IoC容器，告诉它如何创建和管理Bean。

3. **Bean的创建和注入：** 当应用程序启动时，IoC容器会根据你的配置创建Bean实例。它会解析Bean之间的依赖关系，并将依赖的Bean注入到需要它们的地方。

4. **应用程序使用Bean：** 应用程序可以通过从IoC容器中获取Bean实例来使用它们。你不再需要自己实例化和管理Bean，IoC容器会负责这些工作。

**AOP（面向切面编程）流程：**

1. **定义切面：** 切面是一个包含横切关注点（如日志、事务管理）的模块化单元。你需要定义切面，以指定在哪些地方应用横切关注点。

2. **创建通知：** 在切面中，你需要定义各种通知，如前置通知、后置通知、环绕通知等。通知是在特定连接点（例如方法调用、异常抛出）上执行的操作。

3. **定义切点：** 切点是一个表达式，指定了在哪些连接点应用通知。切点定义了何时触发通知。

4. **将切面应用到Bean：** 使用切点表达式，你可以将切面应用到特定的Bean方法上。这样，当方法被调用时，切面中定义的通知会被触发。

总的来说，IoC和AOP是Spring框架中的两个核心概念。IoC通过将对象的创建和管理交给框架，降低了组件之间的耦合度。AOP允许你将横切关注点从主要业务逻辑中分离出来，通过切面在特定连接点上应用通知来实现。这些特性共同使得Spring应用程序更具可维护性、可扩展性和可重用性。



## Springboot的启动方式有几种

Spring Boot提供了多种启动方式，适用于不同的开发和部署场景。以下是一些常见的Spring Boot启动方式：

1. **使用Java命令行启动：** 最常见的方式是通过Java命令行来启动Spring Boot应用程序。你可以使用`java -jar`命令来运行生成的可执行JAR文件。这是一种简单且独立的方式，适用于将应用程序部署到生产环境或本地开发环境。

2. **使用Maven或Gradle插件启动：** Spring Boot提供了Maven和Gradle插件，可以直接在构建工具中运行应用程序。通过运行类似于`mvn spring-boot:run`（Maven）或`gradle bootRun`（Gradle）的命令，你可以在开发过程中快速启动应用程序。

3. **使用Servlet容器启动：** 你可以将Spring Boot应用程序打包成WAR文件，并将其部署到外部Servlet容器（如Tomcat、Jetty或Undertow）中运行。这种方式适用于需要与其他Servlet或Java EE应用程序进行集成的情况。

4. **使用Spring Boot CLI启动：** Spring Boot CLI是一个命令行工具，允许你使用Groovy脚本编写和运行Spring Boot应用程序。这对于快速原型开发和编写简单的命令行应用程序非常有用。

5. **使用集成开发环境（IDE）启动：** 你可以在集成开发环境（如Eclipse、IntelliJ IDEA）中运行Spring Boot应用程序。通过右键单击主应用程序类中的`main`方法并选择“Run”或“Debug”，可以在IDE中启动应用程序。

6. **使用Docker容器启动：** 将Spring Boot应用程序打包到Docker容器中，然后在任何支持Docker的环境中运行。这种方式有助于实现应用程序的容器化部署和管理。

7. **使用Spring Cloud启动（微服务场景）：** 如果你在构建微服务架构，可以使用Spring Cloud来协调和管理多个Spring Boot微服务应用程序的启动和通信。

无论选择哪种启动方式，Spring Boot都旨在简化开发和部署流程，并提供了灵活的选项以适应不同的使用情景。具体的选择取决于你的项目需求、团队偏好以及部署环境。

## Set集合特点

在Java中，Set是一种集合类型，它继承自Collection接口，表示一组不重复元素的集合。Set集合有以下几个特点：

1. **无重复元素：** Set集合中不能包含重复的元素，即集合中的元素是唯一的。如果试图向Set中添加重复元素，添加操作将会被忽略。

2. **无序性：** Set集合没有指定元素的顺序，即集合中的元素没有特定的排列顺序。因此，不能通过索引来访问Set中的元素。

3. **不允许基于索引的访问：** 由于Set没有指定元素的顺序，因此不能通过索引来访问集合中的元素，只能通过迭代器或其他遍历方式来遍历集合。

4. **高效的查找操作：** Set集合通常基于哈希表实现，这使得查找操作非常高效。由于元素的唯一性，可以使用哈希算法来快速确定元素是否存在于集合中。

5. **添加和删除元素：** 通过添加操作（例如`add()`方法）可以向Set集合中添加元素，而通过删除操作（例如`remove()`方法）可以从Set中移除元素。

6. **不保证特定的顺序：** Set集合的实现类（如HashSet、LinkedHashSet、TreeSet等）在元素的存储和迭代时可能会有不同的顺序。例如，HashSet没有保证元素的存储顺序，而LinkedHashSet会保留元素的插入顺序，TreeSet会对元素进行排序。

7. **允许null元素：** 大多数Set实现允许存储一个null元素，但需要注意某些实现可能不支持。

常见的Set实现类包括：

- **HashSet：** 基于哈希表实现，不保证元素的存储顺序，允许存储null元素。
- **LinkedHashSet：** 基于哈希表和链表实现，保留元素的插入顺序。
- **TreeSet：** 基于红黑树实现，对元素进行排序，元素必须是可比较的。
- **EnumSet：** 专门用于存储枚举类型的集合，基于位向量实现，效率高。

总之，Set集合在处理不重复元素的场景下非常有用，可以根据需要选择不同的实现类以满足特定的需求。

## collection和collections的区别

`Collection` 和 `Collections` 是 Java 中两个不同的类或接口，它们有着不同的作用和用途。

1. **Collection：**
   `Collection` 是 Java 集合框架中的根接口，它是所有集合类的基础接口。它定义了一组通用的方法，用于操作和管理一组对象。`Collection` 接口表示一个对象的集合，这些对象可以是重复的（如 `List`）或不重复的（如 `Set`）。

   常见的 `Collection` 子接口和实现类包括：`List`、`Set`、`Queue` 等。每个子接口或实现类都有特定的用途和行为。

2. **Collections：**
   `Collections` 是 Java 提供的一个实用类，包含了一系列静态方法，用于操作和处理集合类（`Collection` 接口的实现类）。它提供了一些算法、排序、查找等方法，用于对集合进行操作。

   `Collections` 类中的方法都是静态方法，不需要创建 `Collections` 的实例，而是直接使用类名来调用。这些方法包括对集合的排序、查找最大最小值、对集合的元素进行随机化等。

总结：
- `Collection` 是一个接口，定义了各种集合类的基本行为和方法，它是集合框架的核心部分。
- `Collections` 是一个实用类，提供了一系列静态方法，用于操作和处理集合类的对象。这些方法可以用于排序、查找、线程安全操作等。

示例：
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class CollectionAndCollectionsExample {
    public static void main(String[] args) {
        // 使用 Collection 接口和 ArrayList 类
        List<Integer> list = new ArrayList<>();
        list.add(3);
        list.add(1);
        list.add(2);

        // 使用 Collections 类中的方法对集合进行操作
        Collections.sort(list); // 对列表进行排序
        int maxValue = Collections.max(list); // 获取最大值
        int minValue = Collections.min(list); // 获取最小值

        System.out.println("Sorted list: " + list);
        System.out.println("Max value: " + maxValue);
        System.out.println("Min value: " + minValue);
    }
}
```

## Springboot在Controller层常用注解

在Spring Boot的Controller层，使用注解可以定义请求处理的逻辑、路由映射以及其他相关行为。以下是在Controller层常用的一些注解：

1. **@RestController：**
   用于声明一个控制器类，该类中的所有方法都会返回JSON格式的数据，不需要额外的 `@ResponseBody` 注解。

2. **@Controller：**
   声明一个控制器类，通常用于返回视图（HTML页面）。方法返回的字符串会被解析为视图名称。

3. **@RequestMapping：**
   用于映射请求路径到控制器方法。可以指定HTTP方法、请求路径、参数等。在Spring 4.3版本之后，推荐使用更具体的注解如 `@GetMapping`、`@PostMapping`、`@PutMapping`、`@DeleteMapping`等来代替。

4. **@GetMapping、@PostMapping、@PutMapping、@DeleteMapping：**
   分别用于将HTTP GET、POST、PUT、DELETE请求映射到控制器方法，简化了 `@RequestMapping` 的用法。

5. **@PathVariable：**
   用于从URL路径中提取参数值，将参数值绑定到方法参数上。

6. **@RequestParam：**
   用于获取请求参数的值，可以设置参数名、默认值等。

7. **@RequestBody：**
   用于接收HTTP请求的请求体，并将其转化为方法参数对象。

8. **@ResponseBody：**
   用于将方法返回的对象转化为HTTP响应体，通常用于返回JSON数据。

9. **@RequestHeader：**
   用于获取HTTP请求头的值，将值绑定到方法参数上。

10. **@ModelAttribute：**
    用于将请求参数绑定到模型对象中，通常用于在表单提交时将数据绑定到实体类。

11. **@SessionAttribute：**
    用于将模型属性绑定到会话中，以便多个请求之间共享数据。

12. **@SessionAttributes：**
    用于指定哪些模型属性需要存储在会话中。

13. **@Validated：**
    用于启用参数校验，可以与校验注解如 `@NotNull`、`@Size` 等一起使用。

14. **@ExceptionHandler：**
    用于定义全局的异常处理方法，可以捕获处理Controller中抛出的异常。

15. **@RestControllerAdvice：**
    用于定义全局的异常处理和响应封装，通常与 `@ExceptionHandler` 一起使用。

这些注解可以根据不同的业务需求和场景进行灵活的组合和使用，帮助你快速构建功能强大的Spring Boot应用程序。

## String、StringBuffer、StringBuilder之间的区别

在Java中，`String`、`StringBuffer` 和 `StringBuilder` 都用于处理字符串，但它们在性能、线程安全性和使用方式等方面存在一些区别。以下是它们之间的主要区别：

1. **String：**
   - `String` 是不可变的，一旦创建就不能被修改。每次对 `String` 进行操作，都会创建一个新的 `String` 对象，原始的 `String` 对象不会改变。
   - 因为不可变性，`String` 适用于字符串常量或不经常修改的情况。

2. **StringBuffer：**
   - `StringBuffer` 是可变的，它允许对字符串进行修改，而不会每次都创建新的对象。
   - `StringBuffer` 是线程安全的，它的方法都是同步的，适合在多线程环境下使用。
   - 由于同步操作，`StringBuffer` 的性能可能会受到一些影响，适合在多线程环境或需要频繁修改字符串的情况下使用。

3. **StringBuilder：**
   - `StringBuilder` 与 `StringBuffer` 类似，也是可变的，但是它不保证线程安全性。
   - `StringBuilder` 比 `StringBuffer` 更快，因为它没有同步操作，适合在单线程环境下使用。
   - 在不需要考虑多线程问题的情况下，推荐使用 `StringBuilder`。

使用示例：

```java
String str = "Hello";
str = str + " World"; // 创建了新的String对象，原始对象不变

StringBuffer stringBuffer = new StringBuffer("Hello");
stringBuffer.append(" World"); // 原始对象被修改

StringBuilder stringBuilder = new StringBuilder("Hello");
stringBuilder.append(" World"); // 原始对象被修改
```

总结：
- 如果字符串不会频繁修改，或者需要在多线程环境中使用，可以使用 `String` 或 `StringBuffer`。
- 如果需要频繁修改字符串且不涉及多线程，推荐使用 `StringBuilder`，因为它性能更高。
- 在Java 5 之后引入了 `StringBuilder`，其主要目的是提供高效的字符串拼接操作，但是不保证线程安全。

## final和finally关键字的区别

`final` 和 `finally` 是Java中两个完全不同的关键字，它们用于不同的用途，没有直接的关联。

1. **final：**
   - `final` 是一个关键字，用于修饰类、方法、变量等。
   - 当用于类时，表示该类不能被继承，即它是一个最终类，不能有子类。
   - 当用于方法时，表示该方法不能被子类重写（覆盖）。
   - 当用于变量时，表示该变量的值不能被修改，即它是一个常量。

示例：
```java
final class FinalClass {
    // 类不能被继承
}

class SubClass extends FinalClass {
    // 编译错误，无法继承final类
}

class Parent {
    final void finalMethod() {
        // 该方法不能被子类重写
    }
}

class Child extends Parent {
    // 编译错误，无法重写final方法
}

class Example {
    final int value = 10; // 常量，值不能被修改
}
```

2. **finally：**
   - `finally` 是一个关键字，用于定义在异常处理代码块中的一个语句块。
   - 不管是否发生异常，`finally` 中的代码块总会执行。它通常用于确保资源的释放或清理操作。

示例：
```java
try {
    // 尝试执行可能抛出异常的代码
} catch (Exception e) {
    // 处理异常
} finally {
    // 无论是否发生异常，都会执行此代码块
}
```

总结：
- `final` 用于表示最终性：最终类、最终方法、最终变量。
- `finally` 用于定义在异常处理中必定执行的代码块，不受是否发生异常影响。

## mybatisplus常用的注解

MyBatis-Plus（简称MP）是基于MyBatis的增强工具，提供了一些方便的注解来简化数据库操作的编码。以下是MyBatis-Plus常用的一些注解：

1. **@TableName：**
   用于将实体类与数据库表进行映射。可以指定表名，也可以根据驼峰命名规则自动生成。

2. **@TableField：**
   用于将实体类的属性与数据库表的字段进行映射。可以设置字段名、是否为主键、是否为自增、插入和更新策略等。

3. **@TableId：**
   用于标识实体类中的主键属性，并与数据库表的主键字段进行映射。

4. **@Version：**
   用于乐观锁的实现，指定一个字段作为版本号。

5. **@EnumValue：**
   用于枚举类型与数据库字段值的映射。

6. **@TableLogic：**
   用于逻辑删除的实现，标识逻辑删除字段。

7. **@KeySequence：**
   用于设置Oracle数据库中序列的名称，配合主键自增策略使用。

8. **@SqlParser：**
   用于设置 SQL 解析注入器，常用于多租户等场景。

9. **@SqlParserConfig：**
   用于设置全局的 SQL 解析注入器配置。

10. **@SqlValue：**
    用于设置 SQL 语句中的值，用于解决某些数据库差异问题。

11. **@Insert、@Update、@Select、@Delete：**
    分别用于指定自定义的新增、更新、查询、删除 SQL 语句。

12. **@Results、@Result：**
    用于配置查询的结果映射关系，类似于 MyBatis 中的 ResultMap。

13. **@Param：**
    用于指定方法参数与 SQL 语句中的参数映射关系。

14. **@DS：**
    用于多数据源场景，指定数据源名称。

这些注解可以帮助你在使用MyBatis-Plus时更便捷地进行数据库操作，减少手动编写 SQL 语句的工作量。当然，除了注解外，MyBatis-Plus还提供了很多其他便捷的功能，如Wrapper查询、条件构造器、分页等。

## mybatisplus如何自定义sql

MyBatis-Plus允许你通过注解或XML文件来自定义SQL语句。这里将分别介绍两种方法：

### 1. 使用注解自定义SQL：

你可以在Mapper接口的方法上使用注解来定义自定义的SQL语句。

```java
import org.apache.ibatis.annotations.Param;
import com.baomidou.mybatisplus.core.mapper.BaseMapper;
import org.apache.ibatis.annotations.Mapper;

@Mapper
public interface MyEntityMapper extends BaseMapper<MyEntity> {
    @Select("SELECT * FROM my_table WHERE column = #{value}")
    List<MyEntity> customSelect(@Param("value") String value);

    @Update("UPDATE my_table SET column = #{value} WHERE id = #{id}")
    int customUpdate(@Param("id") Long id, @Param("value") String value);
}
```

### 2. 使用XML文件自定义SQL：

另一种方法是使用XML文件来定义自定义SQL，这是更灵活和可维护的方式。

在Mapper接口中引用XML文件：

```java
import com.baomidou.mybatisplus.core.mapper.BaseMapper;
import org.apache.ibatis.annotations.Mapper;

@Mapper
public interface MyEntityMapper extends BaseMapper<MyEntity> {
    // 此处不需要定义方法体
}
```

然后，在相同包路径下，创建与Mapper接口同名的XML文件 `MyEntityMapper.xml`：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.example.mapper.MyEntityMapper">

    <select id="customSelect" resultType="MyEntity">
        SELECT * FROM my_table WHERE column = #{value}
    </select>

    <update id="customUpdate" parameterType="map">
        UPDATE my_table SET column = #{value} WHERE id = #{id}
    </update>

</mapper>
```

然后你就可以在Java代码中调用这些自定义SQL方法：

```java
@Service
public class MyEntityService {

    @Autowired
    private MyEntityMapper myEntityMapper;

    public List<MyEntity> customSelect(String value) {
        return myEntityMapper.customSelect(value);
    }

    public int customUpdate(Long id, String value) {
        Map<String, Object> map = new HashMap<>();
        map.put("id", id);
        map.put("value", value);
        return myEntityMapper.customUpdate(map);
    }
}
```

使用XML文件来自定义SQL语句通常更灵活，尤其是当SQL逻辑比较复杂时，同时也有利于SQL的管理和维护。

## mybatis如何进行多参数传递

在 MyBatis 中进行多参数传递有多种方式，这里将介绍几种常用的方法：

### 1. 使用 `@Param` 注解：

在方法参数上使用 `@Param` 注解，可以将参数映射到SQL语句中的具体位置。

```java
@Mapper
public interface MyEntityMapper {
    List<MyEntity> findByParams(@Param("param1") String param1, @Param("param2") int param2);
}
```

在 XML 文件中使用 `#{param1}` 和 `#{param2}` 引用这些参数。

### 2. 使用 Map 传递参数：

你可以将多个参数封装到一个 Map 中，然后将该 Map 作为参数传递给方法。

```java
@Mapper
public interface MyEntityMapper {
    List<MyEntity> findByParams(Map<String, Object> params);
}
```

在 XML 文件中使用 `#{param1}`、`#{param2}` 作为 Map 的键来引用这些参数。

### 3. 使用 `@Param` 和 Map 结合：

结合上述两种方式，你可以在方法参数上使用 `@Param` 注解来为 Map 的键命名。

```java
@Mapper
public interface MyEntityMapper {
    List<MyEntity> findByParams(@Param("params") Map<String, Object> params);
}
```

在 XML 文件中使用 `#{params.param1}`、`#{params.param2}` 来引用这些参数。

### 4. 使用 JavaBean：

如果有一个 JavaBean 对象，它的属性与方法参数一一对应，你可以直接传递 JavaBean 对象作为方法参数。

```java
@Mapper
public interface MyEntityMapper {
    List<MyEntity> findByParams(ParamBean paramBean);
}
```

在 XML 文件中使用 `#{param1}`、`#{param2}` 来引用 JavaBean 的属性。

总之，在 MyBatis 中进行多参数传递的关键是正确地映射参数到 SQL 语句中，你可以根据自己的喜好和业务需求选择适合的方式。

## session和cookie的区别

Session和Cookie是在Web开发中常用的两种机制，用于管理用户状态和跟踪用户行为。它们有一些区别，下面我会详细介绍它们之间的差异：

1. **数据存储位置**:
   - **Cookie**: Cookie是存储在用户浏览器中的小段文本数据，通过在HTTP响应头中设置Set-Cookie标头来创建。浏览器会在后续的HTTP请求中将这些Cookie信息自动包含在请求头中，从而将数据发送回服务器。
   - **Session**: Session数据是存储在服务器端的。通常，服务器会为每个用户创建一个唯一的会话，会话数据存储在服务器的内存或持久性存储中（例如数据库）。

2. **数据安全性**:
   - **Cookie**: 由于Cookie存储在用户的浏览器中，存在一定的安全风险。虽然可以设置Cookie的属性来增加安全性（如HttpOnly和Secure），但仍然可能受到跨站脚本攻击（XSS）等威胁。
   - **Session**: 会话数据存储在服务器上，相对较安全，不容易受到客户端攻击。然而，会话劫持仍然可能发生，需要采取措施来防止此类攻击。

3. **存储容量**:
   - **Cookie**: 每个域名下的Cookie数量和每个Cookie的大小都是有限的，通常每个域名下的Cookie总容量也是有限的（一般几十KB）。
   - **Session**: 理论上，服务器上的会话数据可以更大，但实际容量受到服务器硬件和配置的限制。

4. **生命周期**:
   - **Cookie**: 可以设置Cookie的过期时间，使其在一定时间后失效。也可以创建会话Cookie，它在用户关闭浏览器时自动失效。
   - **Session**: 会话数据的生命周期通常由服务器管理。会话可以在一段时间内保持活动状态（通过设置会话超时时间），或者在用户关闭浏览器后自动失效。

5. **跨页面通信**:
   - **Cookie**: 由于存储在客户端，Cookie可以在不同页面之间共享数据。但是受到浏览器同源策略的限制。
   - **Session**: 会话数据存储在服务器上，不同页面之间可以通过会话ID来共享数据。

综上所述，Cookie主要用于在客户端存储少量数据，适用于跨页面状态维护和用户跟踪，而Session更适合在服务器端存储用户会话数据，用于安全性较高的用户状态管理。在实际开发中，开发者需要根据需求和安全性要求来选择使用Cookie还是Session。

## jwt是什么

JWT代表JSON Web Token，是一种用于在网络应用间安全传输信息的开放标准（RFC 7519）。它通过在信息中嵌入数字签名或加密信息，以保证信息的完整性和安全性。JWT通常用于身份验证和信息交换，特别适用于分布式系统和单点登录（SSO）场景。

一个JWT由三个部分组成，通过点号（.）分隔开来：

1. **Header（头部）**: 包含了关于生成的JWT的元数据信息，如令牌类型（JWT）和所使用的签名算法（例如HMAC SHA256或RSA）。

2. **Payload（负载）**: 包含了需要传递的信息，如用户ID、角色等。Payload的内容可以自定义，但建议避免存放敏感信息，因为Payload可以被解码（Base64解码）而不需要密钥。

3. **Signature（签名）**: 使用头部指定的签名算法和密钥，对头部和负载进行签名。这个签名用于验证消息的完整性和身份认证。

JWT的工作流程通常如下：

1. **生成Token**：服务器根据用户的身份信息和其他必要的数据生成一个JWT。

2. **传输Token**：服务器将生成的JWT返回给客户端，在HTTP头部的Authorization字段中或作为请求参数放置。

3. **验证Token**：客户端将收到的JWT存储下来，将其附加到后续的请求中，或按需发送给服务器。

4. **验证和解码**：服务器收到JWT后，首先会验证签名以确保JWT的完整性。然后对Payload进行解码，获取其中的信息以进行身份认证和授权。

5. **处理请求**：服务器根据解码后的信息来处理请求，执行相应的操作。

JWT的优点包括：
- 轻量级：JWT是一种紧凑的数据格式，适合于网络传输。
- 自包含：JWT包含了自身的信息和签名，不需要在服务器端存储会话信息。
- 分布式系统友好：JWT适用于分布式和跨域环境，因为无需在服务器端存储会话状态。

然而，需要注意的是，由于JWT的信息是可解码的，因此不应将敏感信息存储在Payload中，应该将敏感信息进行加密或通过其他安全手段处理。

---

jwt token：

头部:
{
  "alg": "HS256",
  "typ": "JWT"
}
载体 -- 存放有用户信息:
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
签名:
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret
)

base64UrlEncode(header) . base64UrlEncode(payload) . HMACSHA256(base64UrlEncode(header)+"."+base64UrlEncode(payload),secret))

## Java序列化是什么

Java序列化（Serialization）是一种将Java对象转换为字节流的过程，以便于在网络上传输、存储到文件或持久化到数据库等。序列化的主要目的是将对象的状态保存下来，以便在需要时可以重新创建该对象。

在Java中，对象序列化是通过实现`java.io.Serializable`接口来实现的。该接口是一个标记接口，没有定义任何方法，仅仅是一个标志，告诉Java虚拟机这个类可以被序列化。当一个类实现了`Serializable`接口后，就可以使用Java的序列化机制将对象转换为字节流，或者从字节流中反序列化出对象。

序列化的基本过程如下：

1. 创建一个实现了`Serializable`接口的Java类。
2. 创建一个`ObjectOutputStream`对象，将其连接到一个输出流，如文件流或网络输出流。
3. 使用`ObjectOutputStream`的`writeObject()`方法将Java对象写入输出流。这将触发对象的序列化。
4. 在接收端，如果要反序列化对象，需要创建一个`ObjectInputStream`对象，将其连接到输入流。
5. 使用`ObjectInputStream`的`readObject()`方法从输入流中读取字节并反序列化成对象。

需要注意的是，不是所有的Java对象都可以被序列化。以下情况可能导致序列化问题：

- 对象的类没有实现`Serializable`接口。
- 对象包含不支持序列化的成员变量，这些成员变量可能引用了不可序列化的对象。
- 对象包含了不可序列化的匿名内部类。

另外，虽然Java的序列化提供了一种简单的方式来保存和传输对象，但也存在一些问题，例如：
- 序列化后的字节流可能会随着类的结构变化而失效。
- 序列化产生的字节流可能较大，影响传输效率和存储空间。
- 序列化机制可能存在安全风险，因为反序列化过程中可能会执行恶意代码。

在实际开发中，如果需要在不同系统间传输对象，或者需要将对象持久化到文件或数据库中，需要仔细考虑序列化的使用，并可能选择其他序列化库或格式来满足特定需求。

## 数据库的乐观锁与悲观锁

乐观锁和悲观锁是数据库并发控制的两种常见策略，用于处理多个事务同时访问和修改数据库数据时可能出现的问题。它们的主要思想和应用场景不同。

**悲观锁**：

悲观锁假设在大部分情况下，数据会发生冲突，因此在读取或修改数据时，会将数据进行锁定，防止其他事务对其进行修改。这种方式的代价在于，如果一个事务持有锁的时间较长，其他需要访问这个数据的事务可能会被阻塞，导致性能下降。

一种常见的悲观锁应用是使用数据库提供的`SELECT ... FOR UPDATE`语句，在读取数据时就对数据进行了锁定，只有在释放锁之后其他事务才能进行修改。悲观锁可以保证数据的一致性，但会对并发性能造成影响。

**乐观锁**：

乐观锁则假设数据的冲突较少，多个事务可以同时读取和修改同一个数据，但在提交修改时会检查数据是否被其他事务修改过，从而避免脏数据的写入。通常，乐观锁基于版本控制的机制。每个数据记录都有一个版本号，事务在读取数据时会获取当前版本号，然后在更新时检查版本号是否一致，如果一致才会提交更新，否则会放弃更新并进行重试。

在关系数据库中，通常使用额外的列来记录版本信息，例如“版本号”或“时间戳”字段。在NoSQL数据库或分布式系统中，也可以使用类似的机制来实现乐观锁。

乐观锁允许更高的并发性，因为读取时不会对数据进行锁定。但是，需要开发人员编写额外的代码来处理版本检查和冲突处理，以及处理因为版本不一致而导致的重试。

在选择悲观锁还是乐观锁时，需要考虑数据库的并发性能需求以及数据一致性的要求。

## 跨域

跨域（Cross-Origin）指的是在 Web 应用中，一个域（或者协议、端口）的 JavaScript 请求访问了另一个域的资源。在浏览器的同源策略（Same-Origin Policy）下，这种跨域请求通常受到限制，以防止潜在的安全风险。

同源策略要求：

- **协议相同**：跨域请求的协议必须和当前页面的协议相同。
- **域名相同**：跨域请求的域名必须和当前页面的域名相同。
- **端口相同**：跨域请求的端口号必须和当前页面的端口号相同。

由于同源策略的限制，一些常见的情况会被视为跨域请求：

- 域名不同：例如，从 example.com 的页面向 api.example.net 发起请求。
- 协议不同：例如，从 https 的页面向 http 发起请求。
- 端口不同：例如，从 8080 端口的页面向 8000 端口发起请求。

为了克服跨域问题，可以采用以下方法：

1. **JSONP（JSON with Padding）**：通过动态创建`<script>`标签，利用浏览器对跨域请求`<script>`标签不受同源策略限制的特性，实现跨域数据获取。不过，JSONP 只支持 GET 请求，并且存在一些安全性问题。

2. **CORS（Cross-Origin Resource Sharing）**：通过服务器设置响应头，允许指定域名的请求跨域访问资源。使用 CORS，可以支持各种类型的 HTTP 请求，并提供更好的安全性。

3. **代理服务器**：在同源的服务器上设置代理，让该代理服务器去请求其他域上的资源，然后再将结果返回给前端。这种方式需要在服务器端进行设置。

4. **WebSocket**：WebSocket 协议本身支持跨域通信，不受同源策略的限制。

5. **前后端分离架构**：将前端和后端部署在不同的域名下，通过后端提供的 API 接口来进行数据交互，避免直接在前端发起跨域请求。

要选择适合的解决方案，需要根据具体的情况和安全需求来决定。

## 讲一下快排

当使用Java实现快速排序时，你可以按照前面提供的伪代码来编写实际的Java代码。以下是一个简单的Java实现示例：

```java
public class QuickSort {

    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pivotIndex = partition(arr, low, high);
            quickSort(arr, low, pivotIndex - 1);
            quickSort(arr, pivotIndex + 1, high);
        }
    }

    public static int partition(int[] arr, int low, int high) {
        int pivot = arr[high];
        int i = low - 1;
        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                swap(arr, i, j);
            }
        }
        swap(arr, i + 1, high);
        return i + 1;
    }

    public static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    public static void main(String[] args) {
        int[] arr = {10, 7, 8, 9, 1, 5};
        int n = arr.length;

        quickSort(arr, 0, n - 1);

        System.out.println("Sorted array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

在这个示例中，`quickSort`方法对数组进行排序，`partition`方法将数组分割为两部分，`swap`方法用于交换数组中的元素。在 `main` 方法中，你可以替换示例数组为你自己的数据，然后运行程序以查看排序结果。

请注意，这只是一个简单的示例，实际应用中可能需要更多的优化和错误处理。

## JWT

在进行单点登录时，一般会采用将用户ID存储到Cookie中一份，然后将信息存储在Session中一份，这个Session一般是放在服务端应用程序内存中的，cookie可以根据ID去Session中那到自己的用户信息，从而实现单点登录

登录时，将ID信息存储在Cookie中一份，将对应的对象存储在Session中

![image-20230828184808661](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308281848749.png)

>  JSESSIONID是什么

`JSESSIONID`是Java Servlet容器中用于跟踪用户会话的一种标准方式。它是一个用于唯一标识用户会话的会话标识符。当用户通过浏览器访问使用Java Servlet技术的Web应用时，Servlet容器会为每个用户创建一个唯一的`JSESSIONID`，并将其保存在一个名为`JSESSIONID`的Cookie中，随后的每个请求都会自动包含这个`JSESSIONID`。

`JSESSIONID`的工作过程如下：

1. **会话创建**：当用户首次访问使用Java Servlet技术的Web应用时，Servlet容器会为用户创建一个新的会话，并生成一个唯一的`JSESSIONID`。

2. **Cookie设置**：Servlet容器将生成的`JSESSIONID`写入一个名为`JSESSIONID`的Cookie，然后将这个Cookie包含在响应中返回给浏览器。浏览器会在后续的请求中自动将这个Cookie发送给服务器。

3. **会话跟踪**：当浏览器发送请求到服务器时，服务器可以通过解析请求中的`JSESSIONID` Cookie来识别用户会话。这使得服务器能够跟踪用户的状态和数据，即使HTTP是一种无状态协议。

4. **会话销毁**：会话可以在一定时间内保持活动状态，也可以在用户关闭浏览器或会话超时后自动失效。失效的会话和相应的`JSESSIONID`将被清除。

总之，`JSESSIONID`是用于在Java Servlet容器中管理和跟踪用户会话的机制。它使得服务器能够在无状态的HTTP协议下实现会话状态的管理，从而为Web应用提供更丰富的功能和用户体验。

> 有JSESSIONID，为什么还需要cookie

`JSESSIONID`是会话标识符，用于在服务器端跟踪用户会话状态。而Cookie是一种在客户端存储数据的机制，它可以在浏览器和服务器之间传递数据。虽然`JSESSIONID`可以存储在Cookie中，但Cookie的作用不仅仅局限于存储会话标识符。

以下是一些原因，解释为什么还需要使用Cookie：

1. **存储其他信息**：除了`JSESSIONID`之外，可能还需要存储其他与用户相关的信息，例如用户的偏好设置、购物车内容、浏览历史等。这些信息可以存储在Cookie中，以便在浏览器和服务器之间传递。

2. **客户端状态管理**：某些应用可能需要在客户端维护一些状态信息，以减轻服务器的负担。Cookie可以用于存储这些状态信息，从而避免在每次请求时都向服务器查询。

3. **持久登录**：在用户登录后，可以使用Cookie存储登录凭证或令牌，以便在用户关闭浏览器后再次打开时保持登录状态。

4. **第三方服务集成**：许多第三方服务（如分析、广告等）需要在客户端存储标识符或配置信息，这些信息可以通过Cookie来传递。

5. **本地缓存**：某些情况下，Cookie可以用于在客户端缓存数据，以减少对服务器的请求。

需要注意的是，由于Cookie存储在客户端，所以存在一些安全性和隐私问题。在使用Cookie时，应该遵循最佳实践，确保存储的数据不涉及敏感信息，并遵循隐私政策。同时，Cookie也需要考虑浏览器的同源策略以及跨站脚本攻击（XSS）等安全问题。

---

并且JSESSIONID是存储在cookie中

对于分布式应用的话，如果还采用session存储信息的话，可能还需要解决session共享机制，这样就太复杂了

![image-20230828195106208](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308281951301.png)

---

使用jwt后，认证还是后端进行认证，但是存储并不是后端进行存储了，而是保存在浏览器端

![image-20230828195422468](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308281954537.png)

![image-20230828195518358](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308281955440.png)

![image-20230829002546812](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308290025894.png)

> jwt中签名是后端给的吗？

是的，JWT（JSON Web Token）中的签名通常是由后端生成的。

JWT由三部分组成：头部（Header）、负载（Payload）和签名（Signature）。签名是为了确保JWT的完整性和安全性而添加的。

在生成JWT时，后端会先创建头部和负载，然后使用指定的加密算法（如HMAC、RSA等）将头部和负载进行签名。签名的生成通常需要使用密钥（秘钥），只有持有正确密钥的一方才能验证签名的合法性。这个签名将与JWT一起发送给客户端。

客户端在接收到JWT后，可以通过解码头部和负载来查看JWT的内容。然后，客户端可以使用与后端共享的密钥，来验证JWT的签名是否与解码后的内容一致，以确认JWT的完整性和真实性。

总之，JWT的签名是由后端生成的，用于保护JWT的内容不被篡改。验证签名需要后端提供的密钥，以确保客户端能够验证JWT的合法性。

---

因为这个签名是服务端给的，因此对于不同的服务端给的签名不同，因此如果你的头部和负载被修改了，如果你没有密钥你是任务法生成对应的签名的，就会导致头部+负载+服务端密钥``！=``提供的签名

![image-20230829004643804](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308290105012.png)

![image-20230829011041884](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308290110972.png)

![image-20230829011218447](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308290112537.png)

```java
package com.example.jwt;

import com.auth0.jwt.JWT;
import com.auth0.jwt.JWTVerifier;
import com.auth0.jwt.algorithms.Algorithm;
import com.auth0.jwt.interfaces.DecodedJWT;
import com.auth0.jwt.interfaces.Verification;
import org.junit.jupiter.api.Test;
import org.springframework.boot.test.context.SpringBootTest;

import java.util.Calendar;
import java.util.HashMap;
import java.util.Objects;

@SpringBootTest
class JwtApplicationTests {

    @Test
    void contextLoads() {
        HashMap<String, Object> hashMap = new HashMap<>();
        Calendar instance = Calendar.getInstance();
        instance.add(Calendar.SECOND,60);

        String token = JWT.create()
                .withHeader(hashMap)
                .withClaim("username", "yzk")
                .withClaim("userId",11)
                .withExpiresAt(instance.getTime())
                .sign(Algorithm.HMAC256("ads!@#$%^"));

        System.out.println(token);
    }

    @Test
    public void test(){
        //创建验证对象
        JWTVerifier jwtVerifier = JWT.require(Algorithm.HMAC256("ads!@#$%^")).build();
        DecodedJWT verify = jwtVerifier.verify("eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2OTMyNzM1NjQsInVzZXJJZCI6MTEsInVzZXJuYW1lIjoieXprIn0.2lCLM4K7jQgjUyVMNwTrP4n2uQpBj2x7RikMQTVZ2jw");

        System.out.println(verify.getClaim("userId").asInt());
//        System.out.println(verify.getClaims().get("username"));
//        System.out.println(verify.getClaims().get("userId").asInt());
    }

}
```

> 编写成对应的工具类

```java
package com.example.jwt.utils;

import com.auth0.jwt.JWT;
import com.auth0.jwt.JWTCreator;
import com.auth0.jwt.algorithms.Algorithm;
import com.auth0.jwt.interfaces.DecodedJWT;

import java.util.Calendar;
import java.util.HashMap;
import java.util.Map;

public class JWTUtils {
    private static final String SIGN="!@#$%^^*&*";

    public static String getToken(Map<String,String> map){
        HashMap<String, Object> hashMap = new HashMap<>();
        Calendar instance = Calendar.getInstance();
        instance.add(Calendar.DATE,7);//默认7天过期

        //创建jwt builder
        JWTCreator.Builder builder = JWT.create();
        map.forEach((k,v)->{
            builder.withClaim(k,v);
        });
        //指定令牌过期时间和签名
        String token = builder.withExpiresAt(instance.getTime())
                .sign(Algorithm.HMAC256(SIGN));

        return token;
    }

    /**
     * 验证token
     * @param token
     */
    public static DecodedJWT verify(String token){
        return JWT.require(Algorithm.HMAC256(SIGN)).build().verify(token);
    }

    /**
     * 获取token信息
     */
//    public static DecodedJWT getTokenInfo(String token){
//        DecodedJWT verify = JWT.require(Algorithm.HMAC256(SIGN)).build().verify(token);
//        return verify;
//    }
}
```

![image-20230830132749266](C:\Users\27939\AppData\Roaming\Typora\typora-user-images\image-20230830132749266.png)

## @Accessors(chain = true)这个注解是干嘛的

`@Accessors(chain = true)` 是一种在Java类中使用的注解，通常与Lombok库一起使用。Lombok是一个Java库，它通过自动生成代码来简化Java类的开发，减少样板代码的编写。`@Accessors(chain = true)` 注解是Lombok中的一个特性，用于生成链式方法调用的代码。

链式方法调用是一种编程风格，通过在每个方法调用之后返回对象本身，从而允许在一行代码中连续调用多个方法。这在构建复杂对象或配置对象属性时很有用，因为它可以使代码更加紧凑和可读。

使用`@Accessors(chain = true)`注解后，Lombok会自动生成符合链式调用风格的setter方法。这意味着你可以在单行中设置对象的多个属性，而不必每次都写一个新的方法调用。

以下是一个使用`@Accessors(chain = true)`注解的简单示例：

```java
import lombok.Data;
import lombok.experimental.Accessors;

@Data
@Accessors(chain = true)
public class Person {
    private String firstName;
    private String lastName;
    private int age;
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person()
            .setFirstName("John")
            .setLastName("Doe")
            .setAge(30);
        
        System.out.println(person.getFirstName());
        System.out.println(person.getLastName());
        System.out.println(person.getAge());
    }
}
```

在这个示例中，`@Data`注解生成了getter和setter方法，而`@Accessors(chain = true)`注解使得在单行中链式调用了多个setter方法来设置对象的属性。

总之，`@Accessors(chain = true)`注解可以使代码更加简洁，提高可读性，并且是Lombok库中非常实用的一个功能。

## @Transactional(propagation = Propagation.SUPPORTS)注解的作用

在Spring框架中，`@Transactional(propagation = Propagation.SUPPORTS)` 注解用于定义一个方法的事务传播行为。事务传播行为指定了在一个方法调用中如何处理已经存在的事务。

具体来说，`@Transactional(propagation = Propagation.SUPPORTS)` 注解的作用如下：

1. **事务传播行为设置：** 该注解用于标记一个方法应该在一个已经存在的事务中运行。如果调用该方法的时候已经有一个事务在运行，那么方法会在该事务内运行；如果没有事务在运行，那么方法会在没有事务的环境下运行。

2. **没有事务的情况下执行：** 如果当前没有事务在运行，使用 `Propagation.SUPPORTS` 传播行为的方法会在没有事务的情况下正常执行，不会创建新的事务。

3. **与事务隔离级别无关：** 该注解主要关注事务传播行为，与事务隔离级别无关。如果在调用 `@Transactional(propagation = Propagation.SUPPORTS)` 注解标记的方法时，已经存在一个事务，那么该方法将在该事务的隔离级别下运行。

使用示例：

```java
import org.springframework.transaction.annotation.Propagation;
import org.springframework.transaction.annotation.Transactional;

@Service
public class MyService {

    @Transactional(propagation = Propagation.SUPPORTS)
    public void doSomething() {
        // 在此方法中，如果已经存在事务，则在该事务内运行，如果没有事务，则在没有事务的环境下运行
        // 执行业务逻辑
    }
}
```

需要注意的是，`@Transactional(propagation = Propagation.SUPPORTS)` 注解通常用于那些不需要强制在事务内运行的方法。它适用于读取操作或不需要事务控制的非核心业务逻辑。如果方法需要在事务内运行，并且如果没有事务就创建一个新的事务，那么可以使用其他传播行为，如 `Propagation.REQUIRED`。

 ## 使用与不使用这个注解的区别

使用 `@Transactional(propagation = Propagation.SUPPORTS)` 注解和不使用它之间的区别在于方法在事务上下文中的行为。让我们来看看使用和不使用这个注解的区别：

**使用 `@Transactional(propagation = Propagation.SUPPORTS)` 注解：**

1. **已有事务情况下：** 如果当前已经存在一个事务（即调用该方法的上层方法已经在事务内），方法会在该事务上下文中运行。如果上层方法在事务中抛出异常，事务会根据事务管理器的配置进行回滚。

2. **无事务情况下：** 如果当前没有事务在运行，方法会在非事务上下文中运行。即使方法内部发生异常，也不会触发回滚操作。

**不使用 `@Transactional(propagation = Propagation.SUPPORTS)` 注解：**

1. **无论是否有事务：** 方法会根据自己的事务传播行为来运行。如果方法内部抛出异常，根据事务传播行为和事务管理器的配置，可能会触发回滚操作。

总之，使用 `@Transactional(propagation = Propagation.SUPPORTS)` 注解可以确保方法在有事务的情况下运行在该事务内，而在没有事务的情况下也能正常运行，而不会创建新的事务。而不使用这个注解，方法的事务行为将根据事务传播行为的设置和事务上下文的存在情况而变化。选择使用哪种方式取决于你的业务需求，是否需要在事务内运行，以及是否需要读取操作等。

## resultType="com.example.jwt.entity.User" 对于这种可以不写全限定类名吗

在 MyBatis 中，`resultType` 属性用于指定 SQL 查询返回的结果类型。如果你希望指定一个结果类型，通常情况下是需要写全限定类名的。这是因为不写全限定类名可能会导致 MyBatis 无法正确解析结果类型。

例如，假设你有一个 `com.example.jwt.entity.User` 类，如果你不写全限定类名，MyBatis 可能无法找到正确的类来映射结果。因此，为了确保 MyBatis 能够正确解析结果类型，建议始终写上全限定类名。

以下是一个示例：

```xml
<select id="getUserById" resultType="com.example.jwt.entity.User">
    SELECT * FROM users WHERE id = #{id}
</select>
```

在这个示例中，我们明确指定了 `resultType` 为 `com.example.jwt.entity.User`，以确保 MyBatis 正确地映射查询结果到该实体类。

如果你不想写全限定类名，还有另一种方式是使用 `typeAliases` 配置来为类添加别名。你可以在 MyBatis 的配置文件中配置别名，然后在 SQL 映射中使用别名来指定结果类型，这样就不需要写全限定类名了。

例如：

```xml
<!-- 在 MyBatis 配置文件中配置别名 -->
<typeAliases>
    <package name="com.example.jwt.entity"/>
</typeAliases>
```

然后在 SQL 映射中使用别名：

```xml
<select id="getUserById" resultType="User">
    SELECT * FROM users WHERE id = #{id}
</select>
```

请注意，尽管使用别名可以让你在 SQL 映射中不写全限定类名，但仍然建议在 `resultType` 属性中使用全限定类名，以避免可能的混淆和错误。·

## 可以在yml文件中设置吗

是的，你可以在 MyBatis 的配置文件中使用 YAML 格式来配置 MyBatis 相关的内容，包括别名配置。以下是在 YAML 配置文件中设置类型别名的示例：

```yaml
mybatis:
  type-aliases-package: com.example.jwt.entity
```

在这个示例中，`type-aliases-package` 配置项用于指定包名，MyBatis 将会自动为该包中的所有类创建别名。这样，在你的 SQL 映射中，你可以直接使用类名来指定结果类型，而不需要写全限定类名。

```xml
<select id="getUserById" resultType="User">
    SELECT * FROM users WHERE id = #{id}
</select>
```

需要注意的是，MyBatis 的配置项名称在 YAML 中要遵循驼峰式写法，与在 XML 中的标签名相对应。在上述示例中，`type-aliases-package` 配置项对应于 XML 配置中的 `<typeAliases>` 标签。

如果你的 MyBatis 配置比较复杂，你也可以将整个 MyBatis 配置放在 YAML 文件中，然后在 Spring Boot 的配置文件中引用该 YAML 文件：

```yaml
mybatis:
  config-location: classpath:mybatis-config.yml
```

在 `mybatis-config.yml` 文件中，你可以包含 MyBatis 的所有配置，包括类型别名、插件、数据源等。

总之，是的，你可以使用 YAML 格式在 Spring Boot 中配置 MyBatis 的类型别名，以及其他 MyBatis 相关的配置。

## 如何将token返回给浏览器端并储存

将 Token 返回给浏览器并储存通常涉及到使用 Cookie 或者 Web Storage（LocalStorage 或 SessionStorage）来保存 Token。下面我将为你解释这两种方法的实现方式：

1. **使用 Cookie：**
   使用 Cookie 是一种常见的方法，它允许将数据存储在浏览器端并在每个 HTTP 请求中发送给服务器。要将 Token 存储在 Cookie 中，你可以通过服务器将 Token 附加到响应的 Set-Cookie 头部中，然后浏览器会自动将 Cookie 存储。这样，在后续的请求中，浏览器会自动将 Cookie 信息包含在请求头中。

   在 Spring Boot 中，你可以使用 Spring Security 的功能来生成 Token 并将其放入 Cookie 中。以下是一个简单的示例：

   ```java
   import org.springframework.security.core.Authentication;
   import org.springframework.security.core.userdetails.UserDetails;
   import org.springframework.security.web.authentication.AuthenticationSuccessHandler;
   import javax.servlet.ServletException;
   import javax.servlet.http.Cookie;
   import javax.servlet.http.HttpServletRequest;
   import javax.servlet.http.HttpServletResponse;
   import java.io.IOException;
   
   public class CustomAuthenticationSuccessHandler implements AuthenticationSuccessHandler {
       @Override
       public void onAuthenticationSuccess(HttpServletRequest request, HttpServletResponse response, Authentication authentication) throws IOException, ServletException {
           UserDetails userDetails = (UserDetails) authentication.getPrincipal();
           
           // 生成 Token，这里只是一个示例，实际场景可能使用其他方式生成 Token
           String token = generateToken(userDetails.getUsername());
           
           // 将 Token 放入 Cookie
           Cookie cookie = new Cookie("token", token);
           cookie.setPath("/");
           response.addCookie(cookie);
           
           // 重定向到主页或其他需要跳转的页面
           response.sendRedirect("/home");
       }
       
       // 生成 Token 的逻辑，这里只是一个示例
       private String generateToken(String username) {
           // 实现生成 Token 的逻辑
           return "your_generated_token";
       }
   }
   ```

2. **使用 Web Storage（LocalStorage 或 SessionStorage）：**
   Web Storage 提供了一种在浏览器端存储数据的方式，可以在浏览器会话中持久保存数据。与 Cookie 不同，Web Storage 数据不会在每个请求中自动发送到服务器。要将 Token 存储在 Web Storage 中，你可以使用 JavaScript 代码将 Token 存储在 LocalStorage 或 SessionStorage 中，并在需要时读取。

   在浏览器端的 JavaScript 中，你可以使用以下代码将 Token 存储在 LocalStorage 中：

   ```javascript
   // 存储 Token 到 LocalStorage
   localStorage.setItem('token', 'your_token_here');
   ```

   如果想要使用 SessionStorage，可以将上述代码中的 `localStorage` 替换为 `sessionStorage`。

无论你选择使用 Cookie 还是 Web Storage，都需要在前后端之间建立相应的逻辑来生成 Token、将 Token 返回给浏览器，并在需要时从浏览器中读取 Token。这只是一个简单的示例，实际实现可能会根据你的项目结构和需求有所不同。
