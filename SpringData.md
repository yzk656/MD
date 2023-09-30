## 什么是Spring Data

![image-20230924093301865](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309240933986.png)

![image-20230830185417196](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301854275.png)

![auto-orient,1](https://img-mid.csdnimg.cn/release/static/image/mid/ask/317705494946128.png?x-oss-process=image/auto-orient,1)

针对不同的存储方式，有不同的模板对象，来进行数据存储操作

![image-20230830185822101](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301858148.png)

![image-20230830191241700](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301912756.png)

![image-20230830191417173](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301914210.png)

## JPA的介绍及JDBC关系

![image-20230830191724867](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301917914.png)

![image-20230830194319454](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301943499.png)

![image-20230830194341923](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301943953.png)

![image-20230830194527757](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301945816.png)

## JPA、Hibernate、MyBatis关系

![image-20230830194810997](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301948089.png)

![image-20230830195029470](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301950532.png)

![image-20230830195153535](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301951584.png)

![image-20230830195702699](https://cdn.jsdelivr.net/gh/yzk656/image/img/202308301957734.png)

> @GeneratedValue(strategy = GenerationType.IDENTITY)是什么意思

`@GeneratedValue` 注解与 JPA（Java Persistence API）一起使用，用于指定实体类中主键字段的生成策略。`@GeneratedValue` 注解通常与 `@Id` 注解一起使用，因为它是用于指定主键生成方式的。

`@GeneratedValue` 注解具有一个 `strategy` 属性，该属性用于指定主键生成策略。其中，常见的策略包括：

1. **GenerationType.IDENTITY:** 使用数据库的自增长策略来生成主键。这通常适用于支持自动增长的数据库，如 MySQL 的 AUTO_INCREMENT。

2. **GenerationType.SEQUENCE:** 使用数据库的序列来生成主键。在一些数据库系统中，例如 Oracle，可以使用序列生成唯一的主键值。

3. **GenerationType.TABLE:** 使用一个特定的数据库表来存储主键的当前值。这种方式比较灵活，但性能可能较差。

4. **GenerationType.AUTO:** 由持久化提供程序自动选择适当的生成策略。

示例代码：

```java
@Entity
public class Product {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    
    // Getters and setters
}
```

在上面的示例中，`@GeneratedValue(strategy = GenerationType.IDENTITY)` 表示主键将使用数据库的自增长策略来生成。这意味着当插入一条新记录时，数据库会自动分配一个唯一的主键值给 `id` 字段。

总之，`@GeneratedValue` 注解与其指定的生成策略一起，用于确定主键字段如何在数据库中生成唯一的值。不同的生成策略适用于不同的数据库系统和需求。

> # Hibernate - hibernate.cfg.xml配置文件

```java
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
        "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
        "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
        <!-- 配置数据库连接信息 -->
        <property name="connection.driver_class">com.mysql.jdbc.Driver</property>
        <property name="connection.url">jdbc:mysql://localhost:3306/springdata_jpa?characterEncoding=UTF-8</property>
        <property name="connection.username">root</property>
        <property name="connection.password">yzk</property>

        <!-- 会在日志中记录sql 默认false-->
        <property name="show_sql">true</property>
        <!--是否格式化sql 默认false-->
        <property name="format_sql">true</property>
        <!--表生成策略
            默认none   不自动生成
            update    如果没有表会创建，有会检查更新
            create    创建-->
        <property name="hbm2ddl.auto">update</property>
        <!-- 配置方言：选择数据库类型 -->
        <property name="dialect">org.hibernate.dialect.MySQL57InnoDBDialect</property>

        <!--指定哪些pojo 需要进行ORM映射-->
        <mapping class="com.tuling.pojo.Customer"></mapping>
    </session-factory>
</hibernate-configuration>
```

简写

```java
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
        "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
        "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">
<hibernate-configuration>

    <session-factory>

        <!-- Hibernate 连接数据库的基本信息 -->
        <property name="connection.username">root</property>
        <property name="connection.password">yzk</property>
        <property name="connection.driver_class">com.mysql.jdbc.Driver</property>
        <property name="connection.url">jdbc:mysql:///springdata_jpa</property>

        <!-- Hibernate 的基本配置 -->
        <!--允许显示sql语句-->
        <property name="show_sql">true</property>
        <property name="format_sql">true</property>
        <property name="hbm2ddl.auto">update</property>
        <!--配置方言，选择数据库类型-->
        <property name="dialect">org.hibernate.dialect.MySQL5InnoDBDialect</property>

        <!--映射方式-->
        <mapping class="com.yzk.pojo.Customer"></mapping>

    </session-factory>

</hibernate-configuration>
```

出现报错了

> java.lang.IllegalStateException: Cannot get a connection as the driver manager is not properly initialized
> 	at org.hibernate.engine.jdbc.connections.internal.DriverManagerConnectionProviderImpl.getConnection(DriverManagerConnectionProviderImpl.java:172)
> 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator$ConnectionProviderJdbcConnectionAccess.obtainConnection(JdbcEnvironmentInitiator.java:180)
> 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:68)
> 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:35)
> 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:101)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:237)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:214)
> 	at org.hibernate.engine.jdbc.internal.JdbcServicesImpl.configure(JdbcServicesImpl.java:51)
> 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.configureService(StandardServiceRegistryImpl.java:107)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:246)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:214)
> 	at org.hibernate.engine.jdbc.connections.internal.BasicConnectionCreator.convertSqlException(BasicConnectionCreator.java:116)
> 	at org.hibernate.engine.jdbc.connections.internal.DriverConnectionCreator.makeConnection(DriverConnectionCreator.java:41)
> 	at org.hibernate.engine.jdbc.connections.internal.BasicConnectionCreator.createConnection(BasicConnectionCreator.java:58)
> 	at org.hibernate.engine.jdbc.connections.internal.DriverManagerConnectionProviderImpl$PooledConnections.addConnections(DriverManagerConnectionProviderImpl.java:341)
> 	at org.hibernate.engine.jdbc.connections.internal.DriverManagerConnectionProviderImpl$PooledConnections.<init>(DriverManagerConnectionProviderImpl.java:260)
> 	at org.hibernate.engine.jdbc.connections.internal.DriverManagerConnectionProviderImpl$PooledConnections.<init>(DriverManagerConnectionProviderImpl.java:238)
> 	at org.hibernate.engine.jdbc.connections.internal.DriverManagerConnectionProviderImpl$PooledConnections$Builder.build(DriverManagerConnectionProviderImpl.java:379)
> 	at org.hibernate.engine.jdbc.connections.internal.DriverManagerConnectionProviderImpl.buildPool(DriverManagerConnectionProviderImpl.java:98)
> 	at org.hibernate.engine.jdbc.connections.internal.DriverManagerConnectionProviderImpl.configure(DriverManagerConnectionProviderImpl.java:73)
> 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.configureService(StandardServiceRegistryImpl.java:107)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:246)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:214)
> 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.buildJdbcConnectionAccess(JdbcEnvironmentInitiator.java:145)
> 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:66)
> 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:35)
> 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:101)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:237)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:214)
> 	at org.hibernate.id.factory.internal.DefaultIdentifierGeneratorFactory.injectServices(DefaultIdentifierGeneratorFactory.java:152)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.injectDependencies(AbstractServiceRegistryImpl.java:286)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:243)
> 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:214)
> 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:176)
> 	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:127)
> 	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.build(MetadataBuildingProcess.java:86)
> 	at org.hibernate.boot.internal.MetadataBuilderImpl.build(MetadataBuilderImpl.java:479)
> 	at org.hibernate.boot.internal.MetadataBuilderImpl.build(MetadataBuilderImpl.java:85)
> 	at org.hibernate.boot.MetadataSources.buildMetadata(MetadataSources.java:202)
> 	at com.tuling.test.HibernateTest.init(HibernateTest.java:30)
> 	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
> 	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
> 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
> 	at java.lang.reflect.Method.invoke(Method.java:498)
> 	at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:59)
> 	at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12)
> 	at org.junit.runners.model.FrameworkMethod.invokeExplosively(FrameworkMethod.java:56)
> 	at org.junit.internal.runners.statements.RunBefores.invokeMethod(RunBefores.java:33)
> 	at org.junit.internal.runners.statements.RunBefores.evaluate(RunBefores.java:24)
> 	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
> 	at org.junit.runners.BlockJUnit4ClassRunner$1.evaluate(BlockJUnit4ClassRunner.java:100)
> 	at org.junit.runners.ParentRunner.runLeaf(ParentRunner.java:366)
> 	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:103)
> 	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:63)
> 	at org.junit.runners.ParentRunner$4.run(ParentRunner.java:331)
> 	at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:79)
> 	at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:329)
> 	at org.junit.runners.ParentRunner.access$100(ParentRunner.java:66)
> 	at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:293)
> 	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
> 	at org.junit.runners.ParentRunner.run(ParentRunner.java:413)
> 	at org.junit.runner.JUnitCore.run(JUnitCore.java:137)
> 	at com.intellij.junit4.JUnit4IdeaTestRunner.startRunnerWithArgs(JUnit4IdeaTestRunner.java:69)
> 	at com.intellij.rt.junit.IdeaTestRunner$Repeater$1.execute(IdeaTestRunner.java:38)
> 	at com.intellij.rt.execution.junit.TestsRepeater.repeat(TestsRepeater.java:11)
> 	at com.intellij.rt.junit.IdeaTestRunner$Repeater.startRunnerWithArgs(IdeaTestRunner.java:35)
> 	at com.intellij.rt.junit.JUnitStarter.prepareStreamsAndStart(JUnitStarter.java:232)
> 	at com.intellij.rt.junit.JUnitStarter.main(JUnitStarter.java:55)

解决办法：https://cloud.tencent.com/developer/ask/sof/810916

我今天也遇到了这个问题，我把mysql-connector-java的包升级到了8.0.23，它工作得很好

> Springdatajpa和jpa和hibernate的关系

Spring Data JPA（Java Persistence API）和 Hibernate 是 Java 领域中与持久性相关的技术和框架。它们之间的关系可以描述如下：

1. **JPA（Java Persistence API）**：
   - JPA 是 Java EE（Enterprise Edition）规范的一部分，用于定义了一种标准的持久性编程模型。
   - JPA 提供了一种将对象映射到关系型数据库的方式，允许开发者通过简单的注解来描述实体类和关系。
   - JPA 不是具体的实现，而是一种规范，它定义了一系列接口和规则，以便不同的持久性框架（例如 Hibernate、EclipseLink 等）可以实现这些接口并提供 JPA 的实现。

2. **Hibernate**：
   - Hibernate 是一个流行的开源的 JPA 实现，它是一个强大的 ORM（对象关系映射）框架。
   - Hibernate 实现了 JPA 规范，并提供了许多额外的功能和性能优化，以便更方便地进行数据库交互和对象-关系映射。
   - Hibernate 提供了自定义查询语言（HQL）、一级缓存、事务管理等功能。

3. **Spring Data JPA**：
   - Spring Data JPA 是 Spring 生态系统的一部分，它简化了使用 JPA 进行数据访问的开发任务。
   - Spring Data JPA 构建在 JPA 的基础之上，提供了一种更简单的方式来编写 JPA 存储库（Repositories）。
   - 开发者可以通过定义接口并继承 Spring Data JPA 提供的基础接口，自动获得常见的 CRUD（创建、读取、更新、删除）操作，无需编写具体的实现代码。
   - Spring Data JPA 还提供了查询方法的自动生成、分页、排序、复杂查询等功能。

因此，关系可以总结为：

- Hibernate 是 JPA 的一种实现，它实现了 JPA 规范，并提供了额外的功能。
- Spring Data JPA 利用 JPA 和 Hibernate（或其他 JPA 实现）来简化数据访问层的开发，它是在 Spring Framework 的基础上构建的，为开发者提供了更便捷的数据持久化解决方案，尤其是在 Spring 应用程序中。

![image-20230903230419056](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309032304193.png)

![image-20230904072420926](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309040724022.png)

## 第二周

顶层接口都是Repository，CrudRepository继承Repository接口，而排序分页的在PagingAndSortingRepository接口中，它继承CrudRepository接口。JpaRepository接口继承PagingAndSortingRepository接口





##   @Query("select * from Customer where custName=:custName")    List<Customer> findCustomerByCustName(@Param("custName") String custName); 这个注解是与sql语句中的具名函数进行绑定的还是有方法里面的参数进行绑定的

这个`@Query`注解是与SQL语句中的具名参数进行绑定的，而不是与方法参数进行绑定。

在您提供的示例中，SQL查询字符串中使用了具名参数`:custName`，并通过`@Param("custName")`注解将该参数绑定到方法的参数`custName`上。这意味着在运行时，Spring Data JPA会查找SQL查询中具名参数`:custName`的值，并将其与方法参数`custName`的值进行匹配。这样，您可以在SQL查询中引用`custName`参数的值，而不必直接将方法参数传递给查询。

例如，如果您调用`findCustomerByCustName("John")`，Spring Data JPA将会在SQL查询中将`:custName`替换为"John"，然后执行查询以查找具有指定`custName`的顾客。

总结一下，`@Query`注解中的具名参数与方法参数之间建立了绑定关系，这允许您在SQL查询中使用方法参数的值。





## 那对于sql语句中的表名是与数据库中的表名一样还是要与类的名字一样

在Spring Data JPA中，通常情况下，SQL查询中的表名应该与数据库中的实际表名一致，而不是与实体类的名字一样。这是因为实体类的名字可以与表名不同，通过`@Table`注解来指定表的名称，以允许不同的映射。默认情况下，如果没有提供`@Table`注解，Spring Data JPA会假定表名与实体类名相同。

下面是一个示例，展示如何在实体类上使用`@Table`注解来指定不同于类名的表名：

```java
@Entity
@Table(name = "customers")
public class Customer {
    // ...
}
```

在上述示例中，实体类`Customer`与表名"customers"关联，而不是与类名"Customer"关联。

总之，通常情况下，建议在SQL查询中使用实际数据库中的表名，而不是依赖于默认的实体类名。这样可以更灵活地管理数据库表的映射，允许您在需要时指定不同的表名。如果没有特殊需求，使用默认的实体类名作为表名通常是一个不错的选择。

![image-20230909210351463](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309092103557.png)







如果你要是使用JPQL的话就可以使用那些类的属性作为字段值

```
@Query(value = "From Customer c where c.custName=:custName")
List<Customer> findCustomerByCustName(@Param("custName") String custName);
```



如果你要是使用的原生SQL，就无法使用这些类的属性



## 为什么jpql不支持插入操作，为什么要这么设计

JPQL（Java Persistence Query Language）是一种用于执行查询操作的查询语言，它是Java Persistence API（JPA）的一部分。JPQL主要设计用于从数据库中检索数据，而不是执行插入、更新或删除等修改操作。这种设计有几个原因：

1. **分离查询和修改操作的关注点**：JPA的设计理念之一是将查询和修改操作的关注点分离。查询通常用于检索数据，而修改操作用于更改数据。这种分离有助于提高代码的可维护性和可读性，并降低错误发生的风险。

2. **遵循对象关系映射（ORM）原则**：JPA的主要目标之一是将关系数据库中的数据映射到对象模型中。查询操作通常涉及从数据库中检索数据并将其映射到实体类的对象，这是ORM的主要用途。插入、更新和删除操作更多地涉及到将数据从对象模型同步到数据库中，这是ORM的另一个方面。

3. **事务的控制**：插入、更新和删除操作通常需要与事务一起使用，以确保数据的一致性和完整性。JPQL的查询通常也可以在事务中执行，但这两者之间存在不同的执行语境和要求。通过分离查询和修改操作，可以更容易地管理事务。

虽然JPQL本身不支持插入、更新或删除操作，但JPA提供了其他方式来执行这些操作。通常，您可以使用JPA的`EntityManager`接口的`persist()`、`merge()`和`remove()`方法来执行插入、更新和删除操作，这些方法会与实体对象一起工作，并处理相应的数据库操作。

总之，JPQL的设计目标是提供一种强大的查询语言，用于从数据库中检索数据，并与JPA的ORM机制紧密集成。插入、更新和删除等修改操作通常通过其他JPA机制来执行，以确保代码的可维护性和事务的管理。





![image-20230909211340959](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309092113050.png)

![image-20230909212718066](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309092127117.png)

```
/**
 * 修改
 */
@Transactional
@Modifying
@Query(value = "update customer set cust_name=:custName where cust_id=:id",nativeQuery = true)
int updateCustomer(@Param("custName")String custName,@Param("id")Long id);
```

要加在对应的数据层的方法上



![image-20230910001404614](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309100014765.png)

![image-20230910001615821](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309100016900.png)

![image-20230910001740189](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309100017292.png)

## 在jpa中findByCustName与findCustNameBy的区别

在Spring Data JPA中，`findByCustName` 和 `findCustNameBy` 这两种方法命名方式的区别在于它们的查询方法签名以及用法约定。

1. **findByCustName**：
   - 这是Spring Data JPA的默认命名约定。命名以`findBy`开头，后面跟着实体类的属性名（驼峰命名法）。
   - 这种方法签名表示您想要根据 `CustName` 属性的值进行查询，并且返回的结果是与该属性匹配的实体对象（通常是一个实体的列表，因为可能有多个匹配项）。
   - 示例：`List<Customer> findByCustName(String custName)`，将返回所有`CustName`属性与给定`custName`值匹配的`Customer`实体对象。

2. **findCustNameBy**：
   - 这种方法命名方式相对不太常见。命名以`find`开头，后面跟着要检索的属性名（驼峰命名法），然后跟着`By`。
   - 这种方法签名表示您想要根据 `CustName` 属性的值进行查询，并且返回的结果是该属性的值（通常是一个单一的值，而不是实体对象）。
   - 示例：`String findCustNameByCustomerId(Long customerId)`，将返回与给定`customerId`匹配的`CustName`属性的值。

总的来说，`findByCustName`通常用于返回与属性匹配的实体对象，而`findCustNameBy`用于返回与属性匹配的属性值。选择使用哪种方式取决于您的查询需求以及您希望从查询中返回的数据类型。在大多数情况下，`findBy`约定更常见，因为它允许您从数据库中检索完整的实体对象。  

之前写JPQL语句是之所以使用第二章方式就是为了与第一种方式区别开





![image-20230910004749278](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309100047374.png)

![image-20230910010020236](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309100100326.png)

![image-20230910010141918](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309100101990.png)

![image-20230910010455174](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309100104230.png)

withmatcher会让withignoreCase失效





![](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309101031895.png)

![image-20230910103139464](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309101031504.png)



## 单向一对一

![image-20230910143059614](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309101430727.png)

![image-20230910144457128](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309101444193.png)

![image-20230910152115907](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309101521971.png)

![image-20230910152945819](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309101529872.png)

## 双向一对一

`mappedBy` 是 Java 持久化（如使用 JPA 或 Hibernate）中的一个重要注解属性，用于建立双向关联关系（Bidirectional Relationships）时的映射。它通常用在实体类的注解中，用于指定在双向关联中，哪个属性应该被用作关系的拥有方。

在双向关联中，一般有两个实体类，一个拥有关系的一方称为"拥有方"（Owning Side），另一个被关系所包含的一方称为"被拥有方"（Inverse Side）。拥有方通常包含外键信息，负责维护关联关系的数据库表结构，而被拥有方通常不包含外键信息。

`mappedBy` 的作用是告诉框架在双向关联中，被拥有方的哪个属性应该与拥有方的属性进行映射。这样做有以下好处：

1. 避免了重复的外键列：如果不使用 `mappedBy`，双向关联中通常会生成两个外键列，一个在拥有方，一个在被拥有方。通过指定 `mappedBy`，你可以告诉框架只在拥有方生成外键列，避免了重复的列。

2. 明确关联关系：使用 `mappedBy` 可以明确地指定双向关联的关系，防止出现不一致的情况。

示例：

假设有两个实体类 `Author` 和 `Book`，它们之间是一对多的关系，一个作者可以有多本书，但一本书只属于一个作者。在 `Author` 类中，你可以这样定义：

```java
@Entity
public class Author {
    // ...
    @OneToMany(mappedBy = "author")
    private List<Book> books;
    // ...
}
```

在 `Book` 类中，你可以这样定义：

```java
@Entity
public class Book {
    // ...
    @ManyToOne
    @JoinColumn(name = "author_id")
    private Author author;
    // ...
}
```

在上述示例中，`mappedBy` 属性告诉框架，在 `Author` 类中，`books` 属性用来维护与 `Book` 实体的关联关系，并且在 `Book` 类中，`author` 属性用来表示与 `Author` 实体的关联关系。这样可以确保关联关系的一致性，并且避免了不必要的外键列。

## 那你这个例子中谁是外键

在我提供的例子中，外键是在 `Book` 实体的 `author` 属性上定义的。具体来说，`@JoinColumn(name = "author_id")` 注解指定了外键的名称为 "author_id"，并且这个外键连接到了 `Author` 实体的主键，因此 `Book` 实体的 `author` 属性表示了与 `Author` 实体之间的外键关系。

简而言之，`Book` 实体中的 `author` 属性表示了外键列，并且这个外键用来关联 `Book` 表与 `Author` 表。这是因为一本书（`Book`）通常会有一个作者（`Author`），所以 `Book` 表中的外键用来指向 `Author` 表中的相关记录。

## 什么是外键约束

外键约束（Foreign Key Constraint）是关系型数据库中的一种重要约束，用于维护表与表之间的引用完整性（Referential Integrity）。它定义了一个表中的字段（外键）与另一个表中的字段（主键）之间的关系，确保了数据的一致性和有效性。外键约束的主要作用包括以下几点：

1. 引用完整性（Referential Integrity）：外键约束确保了在引用表中存在的数据也在关联表中存在，从而防止了无效的引用关系。这意味着如果在关联表中尝试插入一个引用表中不存在的值，数据库会拒绝这个操作。

2. 数据一致性：外键约束确保了表之间的关联关系保持一致，从而防止了数据的不一致和矛盾。它确保了关联表中的数据与引用表中的数据相匹配。

3. 数据完整性：外键约束可以防止在关联表中插入无效或不符合关联规则的数据，从而提高了数据的完整性。

4. 级联操作：外键约束可以定义级联操作，例如当引用表中的数据被删除或更新时，可以自动执行相关的操作，如级联删除或级联更新。这有助于维护数据的一致性和完整性。

外键约束通常用于建立表与表之间的关联关系，其中一个表的某个字段引用另一个表的主键。例如，一个订单表可以有一个指向客户表的客户ID的外键，这表示订单与客户之间存在关联。

在创建外键约束时，通常需要指定以下信息：

- 外键字段：定义关联的字段，它们是引用表中的外键。
- 主键表：定义被引用的表，通常是主键表。
- 主键字段：定义被引用表中的主键字段，外键将引用这些字段。
- 级联操作：定义在删除或更新主键表记录时要执行的操作，如级联删除或级联更新。

外键约束是数据库设计中的重要概念，它有助于维护数据的完整性和一致性，同时支持表与表之间的关联关系。不同的数据库管理系统（如MySQL、Oracle、SQL Server等）可能对外键约束的实现有些许差异，但核心概念是相似的。



外键<=>主键

多<=>1

多的那一方插入别人的主键信息

```java
@Entity
@Getter
@Setter
@ToString
@Table(name = "customer")
public class Customer {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "cust_id")
    public Long custId;

    @Column(name = "cust_name", length = 20)
    public String custName;

    @Column(name = "cust_address", length = 20)
    public String custAddress;

    //单向关联
    /**
     * cascade：设置关联操作
     * All：所有持久化操作
     * persist：只有插入才会修改关联操作
     * merge：只有修改才会执行关联操作
     * remove：只有删除才会关联操作
     * fetch:是否设置成懒加载
     * orphanRemoval:当外键设置为空时就会删除关联表所对应的信息
     * mappedBy:将外键约束交给另一方维护
     * mappedBy: 另一方关联属性名
     */
    @OneToOne(mappedBy = "customer",cascade = CascadeType.ALL,fetch = FetchType.LAZY,orphanRemoval = true)
    /*设置外键的字段名*/
    @JoinColumn(name = "account_id")
    public Account account;
}




@Data
@Entity
@Table(name = "tb_account")
public class Account {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String username;

    private String password;

    @OneToOne
    @JoinColumn(name = "customer_id")
    private Customer customer;
}

```



在你提供的代码中，外键是在 `Account` 表中定义的，具体是在 `customer_id` 列上。这是因为 `Account` 表中的 `@JoinColumn(name = "customer_id")` 注解定义了一个外键列，该列引用了 `Customer` 表的主键，因此 `Account` 表中的 `customer` 列表示了与 `Customer` 表之间的外键关系。

换句话说，`Account` 表是关联关系的拥有方（Owning Side），它包含了与 `Customer` 表之间的外键关系。而 `Customer` 表是被关联方（Inverse Side），它包含了与 `Account` 表之间的单向关联，但没有定义外键列，因为外键列在 `Account` 表中维护。

![image-20230910181707141](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309101817236.png)

## Spring-Data-JPA 提示:java.lang.StackOverflowError

根据Debug模式，代码错误最终定位在com.zzg.entity.Article.toString() 方法，堆栈相关信息如上截图。

结合google 结果，分析结果如下：System.out.println("author=" + author);会调用Author类中toString()方法，toString()方法会触发author属性的懒加载，便会去调用Article类的toString()方法，Article()类中的toString()方法，会触发articleList属性的懒加载，接着会调用Author类中的toString()方法。以上就是循环引用的过程。

解决办法：将@Data注解去掉，换成@Setter、@Getter、@EqualsAndHashCode注解。我们自己重写Article类的toString()方法。

## 多对多

![image-20230910203639629](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309102036741.png)

## 审计

![image-20230910222017463](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309102220554.png)

![image-20230910222233170](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309102222238.png)
