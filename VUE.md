# VUE

## VUE简介

![image-20230709172551392](https://cdn.jsdelivr.net/gh/yzk656/image/202307091725518.png)

## VUE API风格

![image-20230709173256313](https://cdn.jsdelivr.net/gh/yzk656/image/202307091732361.png)

![image-20230709173339407](https://cdn.jsdelivr.net/gh/yzk656/image/202307091733474.png)

![image-20230709173352875](https://cdn.jsdelivr.net/gh/yzk656/image/202307091733935.png)

![image-20230709173358425](https://cdn.jsdelivr.net/gh/yzk656/image/202307091733488.png)

![image-20230709173752714](https://cdn.jsdelivr.net/gh/yzk656/image/202307091737775.png)

## VUE开发前准备

![image-20230709174150015](https://cdn.jsdelivr.net/gh/yzk656/image/202307091741053.png)

![image-20230709175554349](https://cdn.jsdelivr.net/gh/yzk656/image/202307091755436.png)

## 模板语法

![image-20230921000939308](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210009430.png)

## 条件渲染

![image-20230921001143057](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210011102.png)

![image-20230921001315899](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210013950.png)

![image-20230921001517203](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210015247.png)

![image-20230921001544089](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210015167.png)

## 列表渲染

![image-20230921001842456](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210018519.png)

在vue中的v-for为什么必须指定:key="item.id"



在Vue.js中使用`v-for`指令时，为每个被迭代的元素指定`:key`是为了帮助Vue更高效地更新和重新渲染DOM。这是Vue中的一个重要优化技巧，它有助于Vue跟踪每个被迭代元素的身份，从而减少不必要的DOM操作，提高性能。

以下是为什么必须指定`:key`的原因：

1. 识别唯一性：`key`属性帮助Vue识别每个迭代元素的唯一性。Vue使用这些`key`来确定哪些元素已经被添加、删除或移动，以便在更新DOM时做出精确的决策。

2. 避免重新渲染问题：如果没有指定`:key`，Vue会使用默认的迭代索引作为元素的标识符。但这会导致一个问题，即当数据数组重新排序或元素数量发生变化时，Vue可能会错误地重新渲染相同的元素，因为它们具有相同的索引，而不是识别它们的内容或身份。这会导致不必要的性能开销，也可能引发意外的UI问题。

3. 提高性能：通过指定`:key`，Vue能够更快速地确定元素的变化，从而减少不必要的DOM操作。这可以显著提高应用程序的性能，尤其是在处理大量数据或复杂列表时。

通常情况下，`:key`应该设置为具有唯一性的值，例如元素的ID或其他唯一标识符。这可以确保Vue能够准确地跟踪元素的变化并进行高效的更新。

示例：
```vue
<template>
  <ul>
    <li v-for="item in items" :key="item.id">{{ item.name }}</li>
  </ul>
</template>
```

在上面的示例中，`:key`被设置为`item.id`，以确保每个元素都有唯一的标识符，从而使Vue能够正确地跟踪和更新元素。

![image-20230921002753878](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210027953.png)

## 事件处理

![image-20230921002925424](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210029481.png)

![image-20230921003333127](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210033195.png)

![image-20230921003833124](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309210038185.png)

## 表单绑定

![image-20230921210730642](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212107731.png)

![image-20230921210743288](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212107351.png)

![image-20230921211130971](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212111031.png)

## 组件

![image-20230921211325221](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212113291.png)

![image-20230921211622007](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212116053.png)

![image-20230921212006481](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212120538.png)

## Props组件之间的交互

![image-20230921220427340](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212204403.png)

![image-20230921220451405](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212204463.png)

==<my-component :title="title" :age="age" :names="names"></my-component> 对于这个组件，传给子组件的是：names还是“names”==

在Vue.js中，当你在模板中使用冒号（v-bind）或简写冒号来传递属性时，传递的是JavaScript表达式的值，而不是字符串。因此，对于你提供的这个组件：

```html
<my-component :title="title" :age="age" :names="names"></my-component>
```

你传递给子组件的是`names`变量的值，而不是字符串“names”。

如果你想传递一个字符串“names”而不是变量的值，你应该将属性值用引号括起来，像这样：

```html
<my-component :title="title" :age="age" :names="'names'"></my-component>
```

这样，子组件将会收到一个名为“names”的字符串作为属性值。



==这个names是变量吗？为什么使用双引号引起来==

我明白你的疑惑，让我澄清一下：

在你提供的代码中，`:names="names"` 中的 `names` 不是一个字符串，而是一个变量名，它引用了当前 Vue 实例中的 `names` 变量的值。这意味着，子组件将接收到 `names` 变量的值作为属性值，而不是字符串。

如果你想将字符串“names”传递给子组件，你应该在引号中包含它，如下所示：

```html
<my-component :title="title" :age="age" :names="'names'"></my-component>
```

这里的 `:names="'names'"` 将把字符串“names”传递给子组件作为属性值，而不是引用变量 `names` 的值。

所以，如果你的目标是传递一个字符串而不是变量值，那么使用双引号或单引号将字符串括起来是正确的做法。



==所以说父组件中：names绑定的是子组件的属性？==

是的，你理解得正确。在Vue.js中，通过使用属性绑定语法（`:属性名`）将数据传递给子组件时，你实际上是在将父组件中的属性值绑定到子组件的属性上。

在你的示例中，这行代码：

```html
<my-component :title="title" :age="age" :names="names"></my-component>
```

绑定了父组件中的 `title`、`age` 和 `names` 属性到子组件的相应属性上。这意味着子组件可以通过属性来访问这些值。

在子组件中，你可以像这样声明这些属性，以便 Vue.js 知道要接收哪些属性值：

```vue
<script>
export default {
  props: {
    title: String,
    age: Number,
    names: Array
  }
}
</script>
```

现在，子组件就能够访问 `title`、`age` 和 `names` 这些属性，并在模板中使用它们。父组件中的这些属性的值将会传递给子组件，并在子组件中进行渲染或处理。



==注意：==

```
names:{
  type:Array,
  //数组和对象必须要使用函数来接收
  default:function (){
    return []
  }
}
```

## 自定义书简组件交互

![image-20230921223330920](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212233994.png)

## 组件生命周期

![image-20230921232002924](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212320982.png)

![image-20230921232055819](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212320862.png)

![image-20230921234611359](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212346407.png)

![image-20230921234657560](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212346595.png)

## Vue引入第三方

![image-20230921234834012](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212348060.png)

![image-20230921235432544](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212354601.png)

![image-20230921235714197](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309212357248.png)

## Axios网络请求

![image-20230922074047760](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309220740824.png)

![image-20230922074151639](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309220741699.png)

![image-20230922075621450](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309220756491.png)

![image-20230922075408177](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309220754247.png)

![image-20230922080304391](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309220803456.png)

## Axios网络请求封装

![image-20230922210335786](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222103893.png)

![image-20230922233025078](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222330159.png)

![image-20230922233404904](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222334942.png)

## 网络请求跨域解决方案

![image-20230922233537307](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222335383.png)

![image-20230922233555701](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222335746.png)

![image-20230922234043037](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222340071.png)

解决跨域请求时这个'/api'是固定的吗

在你的webpack配置中，'/api' 是一个代理路径，用于指示要被代理到目标服务器的请求。这个'/api'路径不是固定的，你可以根据你的需要自定义这个路径，只要确保它与你在前端代码中实际发起的请求路径匹配即可。

例如，如果你希望将所有以'/data'开头的请求代理到目标服务器，你可以这样配置：

```javascript
module.exports = defineConfig({
  transpileDependencies: true,
  devServer: {
    proxy: {
      '/data': { // 这里使用 '/data' 作为代理路径
        target: "http://iwenwiki.com",
        changeOrigin: true
      }
    }
  }
})
```

然后，在你的前端代码中，当你发起请求时，请求路径需要以'/data'开头，例如：

```javascript
axios.get('/data/some-endpoint')
  .then(response => {
    // 处理响应
  })
  .catch(error => {
    // 处理错误
  });
```

这样配置的好处是你可以根据需要灵活地定义代理路径，以适应不同的后端服务接口。

## Vue引入路由配置

![image-20230922234514021](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222345067.png)

![image-20230922235514834](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222355895.png)

![image-20230922235525730](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222355766.png)

![image-20230922235519898](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222355951.png)

什么是重定向

重定向是网络通信中的一个重要概念，它指的是当一个资源或页面请求到达服务器时，服务器返回一个指示客户端去请求不同资源或页面的响应。重定向用于在客户端和服务器之间导航或跳转到不同的 URL 或资源，通常有以下几种用途：

1. **页面跳转重定向**：在网页开发中，重定向经常用于将用户从一个 URL 地址自动导航到另一个URL地址。这可以用于实现页面的跳转、用户登录后的重定向等。

2. **URL重写**：有时候，服务器会将请求的 URL 重写为不同的 URL，以实现一些特定的逻辑或提供友好的 URL。这通常用于美化 URL 或使其更易于理解。

3. **域名重定向**：域名重定向是将一个域名导向到另一个域名的过程。这常用于将多个域名指向同一个网站，或者将一个域名导向到另一个主要域名。

4. **HTTP到HTTPS重定向**：为了增强安全性，网站通常会将HTTP请求重定向到HTTPS，以确保数据在传输过程中加密。

5. **临时重定向和永久重定向**：HTTP协议使用不同的状态码来表示不同类型的重定向。例如，状态码302表示临时重定向，状态码301表示永久重定向。永久重定向告诉客户端将来的请求应该直接发送到新的 URL，而临时重定向则只是告诉客户端暂时跳转到新的 URL，以后可能还会有其他操作。

6. **重定向链**：有时候，多个重定向可以组成一个重定向链，其中一个URL会重定向到另一个URL，然后再重定向到另一个URL，以此类推。

总之，重定向是一种常见的网络技术，用于导航或跳转到不同的资源或地址，以满足各种不同的需求，如页面跳转、URL美化、安全性增强等。在Web开发和网络通信中，重定向扮演着重要的角色。

![image-20230922235830005](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309222358066.png)

## 路由传递参数

![image-20230923110516894](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231105032.png)

## 嵌套路由配置

![image-20230923113727339](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231137421.png)

![image-20230923113930093](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231139151.png)

![image-20230923114129877](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231141960.png)

## Vue状态管理（Vuex）

![image-20230923115437221](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231154297.png)

![image-20230923115815480](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231158560.png)

![image-20230923120526102](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231205165.png)

## Vuex状态管理核心

![image-20230923130228319](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231302388.png)

![image-20230923130727998](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231307099.png)

![image-20230923131157235](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231311322.png)

## Vue3新特性1

![image-20230923155715789](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231557853.png)

![image-20230923161212291](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231612369.png)

![image-20230923163141333](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231631396.png)

![image-20230923163300854](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231633944.png)

## Vue3新特性2

![image-20230923165410759](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231654838.png)

![image-20230923165616535](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231656616.png)

![image-20230923165803484](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231658540.png)

在vue中props传递值和provide传递值的区别

在Vue.js中，`props` 和 `provide/inject` 都是用于在组件之间传递数据的机制，但它们之间有一些重要的区别。

1. **Props**:
   - `props` 是一种从父组件向子组件传递数据的方式。你可以在子组件的标签中使用 `v-bind` 来绑定父组件的数据到子组件的属性上。
   - 数据是单向流动的，只能从父组件传递到子组件，子组件不能直接修改 `props` 中的数据。
   - 适用于将数据从父组件传递给子组件，通常用于将组件的配置选项传递给子组件。

```vue
// 父组件
<template>
  <child-component :message="parentMessage"></child-component>
</template>

<script>
export default {
  data() {
    return {
      parentMessage: 'Hello from parent!'
    };
  }
};
</script>

// 子组件
<template>
  <div>{{ message }}</div>
</template>

<script>
export default {
  props: ['message']
};
</script>
```

2. **Provide/Inject**:
   - `provide/inject` 是一种高级特性，用于在祖先组件和后代组件之间建立一个"依赖注入"的关系。祖先组件可以通过 `provide` 提供数据，而后代组件可以通过 `inject` 注入这些数据。
   - 数据是双向的，后代组件可以修改注入的数据，但要注意慎用，因为这可能会引起不可预料的副作用。
   - 适用于在多层嵌套的组件中共享数据，例如全局状态管理或者主题配置。

```vue
// 祖先组件
<template>
  <div>
    <grandparent-component></grandparent-component>
  </div>
</template>

<script>
export default {
  provide: {
    sharedData: 'Data from ancestor'
  }
};
</script>

// 父组件
<template>
  <div>
    <child-component></child-component>
  </div>
</template>

<script>
export default {};
</script>

// 后代组件
<template>
  <div>
    <p>{{ injectedData }}</p>
    <button @click="updateData">Update Data</button>
  </div>
</template>

<script>
export default {
  inject: ['sharedData'],
  data() {
    return {
      injectedData: this.sharedData
    };
  },
  methods: {
    updateData() {
      this.injectedData = 'Updated Data';
    }
  }
};
</script>
```

总之，`props` 用于从父组件向子组件传递数据，而 `provide/inject` 用于在祖先组件和后代组件之间共享数据。你应该根据你的具体需求来选择使用哪种方式。如果只需要简单的数据传递，使用 `props` 即可；如果需要在多层次的组件中共享数据，使用 `provide/inject` 可能更合适。

## Vue3加载Element-plus

![image-20230923172145844](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231721938.png)

![image-20230923172307025](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231723092.png)

![image-20230923172500652](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231725743.png)

![image-20230923172611950](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231726006.png)

c

![image-20230923172644898](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231726972.png)

![image-20230923172941335](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231729417.png)

![image-20230923173025253](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231730332.png)

![image-20230923173201030](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309231732079.png)
