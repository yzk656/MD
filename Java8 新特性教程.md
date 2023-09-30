# Java8 新特性教程

## Stream 流

`Map` 不支持 `Stream` 流。`Stream` 流支持同步执行，也支持并发执行。

### Filter过滤

首先，我们创建一个 `List` 集合：

```java
List<String> stringCollection = new ArrayList<>();
stringCollection.add("ddd2");
stringCollection.add("aaa2");
stringCollection.add("bbb1");
stringCollection.add("aaa1");
stringCollection.add("bbb3");
stringCollection.add("ccc");
stringCollection.add("bbb2");
stringCollection.add("ddd1");
```

`Filter` 的入参是一个 `Predicate`, 上面已经说到，`Predicate` 是一个断言的中间操作，它能够帮我们筛选出我们需要的集合元素。它的返参同样 是一个 `Stream` 流，我们可以通过 `foreach` 终端操作，来打印被筛选的元素：

```java
stringCollection
    .stream()
    .filter((s) -> s.startsWith("a"))
    .forEach(System.out::println);

// "aaa2", "aaa1"
```

==注意==：`foreach` 是一个终端操作，它的返参是 `void`, 我们无法对其再次进行流操作。

### Sorted排序

`Sorted` 同样是一个中间操作，它的返参是一个 `Stream` 流。另外，我们可以传入一个 `Comparator` 用来自定义排序，如果不传，则使用默认的排序规则。

```java
stringCollection
    .stream()
    .sorted()
    .filter((s) -> s.startsWith("a"))
    .forEach(System.out::println);

// "aaa1", "aaa2"

        stringCollection.stream()
                .filter(s->s.startsWith("a"))
                .sorted((o1,o2)->o2.compareTo(o1))
                .forEach(System.out::println);
```

需要注意，`sorted` 不会对 `stringCollection` 做出任何改变，`stringCollection` 还是原有的那些个元素，且顺序不变：

System.out.println(stringCollection); // ddd2, aaa2, bbb1, aaa1, bbb3, ccc, bbb2, ddd1

### Map 转换

中间操作 `Map` 能够帮助我们将 `List` 中的每一个元素做功能处理。例如下面的示例，通过 `map` 我们将每一个 `string` 转成大写：

```java
stringCollection
    .stream()
    .map(String::toUpperCase)
    .sorted((a, b) -> b.compareTo(a))
    .forEach(System.out::println);

// "DDD2", "DDD1", "CCC", "BBB3", "BBB2", "AAA2", "AAA1"
```

另外，我们还可以做对象之间的转换，业务中比较常用的是将 `DO`（数据库对象） 转换成 `BO`（业务对象） 。

### Match 匹配

顾名思义，`match` 用来做匹配操作，它的返回值是一个 `boolean` 类型。通过 `match`, 我们可以方便的验证一个 `list` 中是否存在某个类型的元素。

```java
// 验证 list 中 string 是否有以 a 开头的, 匹配到第一个，即返回 true
boolean anyStartsWithA =
    stringCollection
        .stream()
        .anyMatch((s) -> s.startsWith("a"));

System.out.println(anyStartsWithA);      // true

// 验证 list 中 string 是否都是以 a 开头的
boolean allStartsWithA =
    stringCollection
        .stream()
        .allMatch((s) -> s.startsWith("a"));

System.out.println(allStartsWithA);      // false

// 验证 list 中 string 是否都不是以 z 开头的,
boolean noneStartsWithZ =
    stringCollection
        .stream()
        .noneMatch((s) -> s.startsWith("z"));

System.out.println(noneStartsWithZ);      // true
```

### Count 计数

`count` 是一个终端操作，它能够统计 `stream` 流中的元素总数，返回值是 `long` 类型。

```java
// 先对 list 中字符串开头为 b 进行过滤，让后统计数量
long startsWithB =
    stringCollection
        .stream()
        .filter((s) -> s.startsWith("b"))
        .count();

System.out.println(startsWithB);    // 3
```

### Reduce

`Reduce` 中文翻译为：*减少、缩小*。通过入参的 `Function`，我们能够将 `list` 归约成一个值。它的返回类型是 `Optional` 类型。

```java
Optional<String> reduced =
    stringCollection
        .stream()
        .sorted()
        .reduce((s1, s2) -> s1 + "#" + s2);

reduced.ifPresent(System.out::println);
// "aaa1#aaa2#bbb1#bbb2#bbb3#ccc#ddd1#ddd2"
```

### Map 集合

前面已经提到过 `Map` 是不支持 `Stream` 流的，因为 `Map` 接口并没有像 `Collection` 接口那样，定义了 `stream()` 方法。但是，我们可以对其 `key`, `values`, `entry` 使用 流操作，如 `map.keySet().stream()`, `map.values().stream()` 和 `map.entrySet().stream()`.

另外, JDK 8 中对 `map` 提供了一些其他新特性:

```java
Map<Integer, String> map = new HashMap<>();

for (int i = 0; i < 10; i++) {
    // 与老版不同的是，putIfAbent() 方法在 put 之前，
    // 会判断 key 是否已经存在，存在则直接返回 value, 否则 put, 再返回 value
    map.putIfAbsent(i, "val" + i);
}

// forEach 可以很方便地对 map 进行遍历操作
map.forEach((key, value) -> System.out.println(value));
```

==forEach 可以很方便地对 map 进行遍历操作==

``` java
map.forEach((key, value) -> System.out.println(value));
```

除了上面的 `putIfAbsent()` 和 `forEach()` 外，我们还可以很方便地对某个 `key` 的值做相关操作：

```java
// computeIfPresent(), 当 key 存在时，才会做相关处理
// 如下：对 key 为 3 的值，内部会先判断值是否存在，存在，则做 value + key 的拼接操作
map.computeIfPresent(3, (num, val) -> val + num);
map.get(3);             // val33

// 先判断 key 为 9 的元素是否存在，存在，则做删除操作
map.computeIfPresent(9, (num, val) -> null);
map.containsKey(9);     // false

// computeIfAbsent(), 当 key 不存在时，才会做相关处理
// 如下：先判断 key 为 23 的元素是否存在，不存在，则添加
map.computeIfAbsent(23, num -> "val" + num);
map.containsKey(23);    // true

// 先判断 key 为 3 的元素是否存在，存在，则不做任何处理
map.computeIfAbsent(3, num -> "bam");
map.get(3);             // val33
```

关于删除操作，JDK 8 中提供了能够新的 `remove()` API:

```java
map.remove(3, "val3");
map.get(3);             // val33

map.remove(3, "val33");
map.get(3);             // null
```

如上代码，只有当给定的 `key` 和 `value` 完全匹配时，才会执行删除操作。

关于添加方法，JDK 8 中提供了带有默认值的 `getOrDefault()` 方法：

```java
// 若 key 42 不存在，则返回 not found
map.getOrDefault(42, "not found");  // not found
```

对于 `value` 的合并操作也变得更加简单：

```java
// merge 方法，会先判断进行合并的 key 是否存在，不存在，则会添加元素
map.merge(9, "val9", (value, newValue) -> value.concat(newValue));
map.get(9);             // val9

// 若 key 的元素存在，则对 value 执行拼接操作
map.merge(9, "concat", (value, newValue) -> value.concat(newValue));
map.get(9);             // val9concat
```





