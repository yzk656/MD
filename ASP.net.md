# ASP.net

## CSS

> 总结

![image-20220922202810187](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942634.png)

外部样式表：导链接

内部样式表：写进style标签中

内联样式表，写进元素内



```
body{font-size:12px;}``*{font-szie:12px;}
```

以上两个代码的作用是完全一样的，因为font-size属性是居右继承性的。但是大家还是要明白它们的原理是不一样的，*选择器确实是选择了每一个元素并且把它们的字体大小设置为12px，body则是通过继承将字体设置为12px的。



将图片作为背景：background-image:url("url")



调整背景图像大小

```
background-size: 400px;
```



背景简写

```
background:url("img_tree.png") no-repeat top right;
```



使用margin属性居中对齐某个元素

```
margin:auto
```



将 div 的边距设置为“25px”：值得就是盒子之间的距离



轮廓：outline



1.text-align:center 设置文本或img标签等一些内联对象（或与之类似的元素）的居中。

2.margin:0 auto 设置[块元素](https://so.csdn.net/so/search?q=块元素&spm=1001.2101.3001.7020)（或与之类似的元素）的居中。



去除下划线

```
a{
	text-decoration:none;
}
```



标题格式 h 和段落p的大写不一样

```
        h1{
            text-transform:uppercase;
        }
        p{
            text-transform: capitalize;
        }
```



首行缩进

```
  text-indent: 20px;
```



修改字体类型

```
 font-family: "JetBrains Mono";
```



将字体转换成斜体

```
font-style: italic;
```



调整字体大小

```
font-size:20px;
```

*任意浏览器的默认字体高都是16px。所有未经调整的浏览器都符合: 1em=16px。那么12px=0.75em,10px=0.625em。为了简化font-size的换算，需要在css中的body选择器中声明Font-size=62.5%，这就使em值变为 16px\*62.5%=10px, 这样12px=1.2em, 10px=1em, 也就是说只需要将你的原来的px数值除以10，然后换上em作为单位就行了。*



将字体转换成粗体

```
font-weight:bold;
```

font-family，font-style，font-variant，font-weight，font-size，font

font-family（字体族）: “Arial”、“Times New Roman”、“宋体”、“黑体”等;
font-style（字体样式）: normal（正常）、italic（斜体）或oblique（倾斜）;
font-variant (字体变化): normal（正常）或small-caps（小体大写字母）;
font-weight (字体浓淡): 是normal（正常）或bold（加粗）。有些浏览器甚至支持采用100到900之间的数字（以百为单位）;
font-size（字体大小）: 可通过多种不同单位（比如像素或百分比等）来设置, 如：12xp，12pt，120%，1em

如果用 font 属性的话，就可以把几个样式进行简化，减少书的情况；font 属性的值应按以下次序书写(各个属性之间用空格隔开)：

顺序：font-style | font-variant | font-weight | font-size | line-height | font-family



超链接的四种状态是：

①a:link {color:#FF0000;}/* 未被访问的链接 */

②a:visited {color:#00FF00;}/* 已被访问的链接 */

③a:hover {color:#FF00FF;}/* 鼠标指针移动到链接上 */

④a:active {color:#0000FF;}/* 正在被点击的链接 */

```
<style>
    /* mouse over link */
    a:hover {
        color: red;
    }

    /* selected link */
    a:active {
        color: blue;
    }

    a:link{
        color: red;
    }
    a:visited{
        color:blue;
    }
</style>
```



删除下划线

```
a:link {
    text-decoration:none;
}
```



改变列表样式

```
ul{
    list-style-type:square;
}
ol{
    list-style-type:upper-roman;
}
```



将图片设置为列表样式

```
list-style-image:url("sqpurple.gif");
```





使用 list-style 属性：将无序列表标记设置为 "img_marker.png"，备用样式为 "circle"，并在内容流中显示标记。

```
list-style:circle inside url("img_marker.png");
```



清楚列表样式

```
list-style-type:none;
```



边框合并

```
border-collapse:collapse;
```



元素中的文本右对齐

```
text-align:right;
```



隐藏元素占用空间

```
visibility:hidden;
```

隐藏元素，不占用空间

```
display:none;
```



将列表转换成内联元素

```
li{
    display:inline;
}
```

将元素转换成块级元素

```
display:block;
```



关于fixed属性，在什么情况下需要用，怎么用，首先，我们应该先了解下fixed属性的说明：fixed总是以body为定位时的对象，总是根据浏览器的窗口来进行元素的定位，通过"left"、 "top"、 "right"、 "bottom" 属性进行定位。

```
h1 {
    color: red;
    position: fixed;
    top:50px;
    right: 50px;
}
```



相对于窗口/框架边缘：position：fixed

相对于元素：position：relative

相对于HTML 页面：position：absolute

z-index 属性设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。

但是在有滚动条后，**fixed始终会在定好的位置不动，而absolute会随参照对象元素的宽高变化为移动**。 一般fixed用在遮盖层和固定在页面某个位置（固定在顶端的菜单栏 / 弹出框居中显示 / 页面两侧的广告位等）



添加滚动条：溢出：overflow

```
overflow:scroll;
```

隐藏溢出文本

```
overflow:hidden;
```

添加水平滚动条

```
overflow-x:scroll;
```





元素居中对齐

```
margin:0 auto;
```

元素定位到右侧

            position: absolute;
            right: 0;



水平居中

text-align：center

垂直居中

![image-20220930141807906](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942752.png)

使用background-reapeat：能够节省流量，用小的组成大的



mouseout:不论鼠标指针离开被选元素还是任何子元素，都会触发 mouseout 事件。
mouseleave: 只有在鼠标指针离开被选元素时，才会触发 mouseleave 事件。



transparent:透明色



background-position

![image-20221011101203500](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942797.png)

box-sizing

### [属性值](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-sizing#属性值)

- `content-box`

	默认值，标准盒子模型。[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 与 [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height) 只包括内容的宽和高，不包括边框（border），内边距（padding），外边距（margin）。注意：内边距、边框和外边距都在这个盒子的外部。比如说，`.box {width: 350px; border: 10px solid black;}` 在浏览器中的渲染的实际宽度将是 370px。尺寸计算公式：`width` = 内容的宽度`height` = 内容的高度宽度和高度的计算值都不包含内容的边框（border）和内边距（padding）。

- `border-box`

	[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 和 [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height) 属性包括内容，内边距和边框，但不包括外边距。这是当文档处于 Quirks 模式 时 Internet Explorer 使用的[盒模型](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)。注意，填充和边框将在盒子内 , 例如， `.box {width: 350px; border: 10px solid black;}` 导致在浏览器中呈现的宽度为 350px 的盒子。内容框不能为负，并且被分配到 0，使得不可能使用 border-box 使元素消失。尺寸计算公式：`width` = border + padding + 内容的宽度`height` = border + padding + 内容的高度





输入框默认显示内容

placeholder 属性规定可描述输入字段预期值的简短的提示信息（比如：一个样本值或者预期格式的短描述）。 该提示会在用户输入值之前显示在输入字段中。 注意：placeholder 属性适用于下面的input 类型：text、search、url、tel、email 和password





background-position可以加入background速记模式

![image-20221011162122728](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942439.png)



![image-20221011162110504](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942932.png)





边框透明化

```
border: 1px solid transparent;
```

边框的线可以去掉

```
outline:none
```





> let

**`let`** 语句声明一个块级作用域的局部变量，并可以初始化为一个值（可选）。



> [JavaScript 中 let 是不是比 var 好？](https://segmentfault.com/q/1010000022889200)



我认为是**淘汰关系**

let 的特点

1. 块级作用域（var function 回调的都是最后一次）
2. 声明前不可以使用（undefined）





> 立即执行函数

```javascript
(function() {
  // 块级作用域
  for (var i = 0; i < 5; i++) {
    console.log(i);
  }
})();
console.log(i);

复制代码
```

上述代码中当解析到`console.log(i);`时，会报错ReferenceError: i is not defined，这是因为它访问的变量是在IIFE内部定义的，在外部访问不到。

在es5以前，为了防止变量定义外泄，IIFE是个非常有效的方式，这样也不会导致闭包相关的内存问题，因为不存在对这个匿名函数的引用。因此，只要函数执行完毕，其作用域链就可以被销毁。

> IIFE的全称为Immediately Invoked Function Expression，翻译过来就是立即调用函数表达式。


作者：神奇的程序员
链接：https://juejin.cn/post/6953256240969760781
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

在进行innerHTML拼接时，使用的`` 而不是单引号

























### CSS语法

![image-20220907195256484](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942352.png)

在此例中，所有 <p> 元素都将居中对齐，并带有红色文本颜色：

```html
p {
  color: red;
  text-align: center;
}
```

### CSS选择器

我们可以将 CSS 选择器分为五类：

- 简单选择器（根据名称、id、类来选取元素）
- [组合器选择器](https://www.w3school.com.cn/css/css_combinators.asp)（根据它们之间的特定关系来选取元素）
- [伪类选择器](https://www.w3school.com.cn/css/css_pseudo_classes.asp)（根据特定状态选取元素）
- [伪元素选择器](https://www.w3school.com.cn/css/css_pseudo_elements.asp)（选取元素的一部分并设置其样式）
- [属性选择器](https://www.w3school.com.cn/css/css_attribute_selectors.asp)（根据属性或属性值来选取元素）

> 元素选择器

在这里，页面上的所有 <p> 元素都将居中对齐，并带有红色文本颜色：

```
p {
  text-align: center;
  color: red;
}
```

> id选择器

id 选择器使用 HTML 元素的 id 属性来选择特定元素。

元素的 id 在页面中是唯一的，因此 id 选择器用于选择一个唯一的元素！

要选择具有特定 id 的元素，请写一个井号（＃），后跟该元素的 id。

这条 CSS 规则将应用于 id="para1" 的 HTML 元素：

```
#para1 {
  text-align: center;
  color: red;
}
```

> 类选择器

类选择器选择有特定 class 属性的 HTML 元素。

如需选择拥有特定 class 的元素，请写一个句点（.）字符，后面跟类名。

在此例中，所有带有 class="center" 的 HTML 元素将为红色且居中对齐：

```
.center {
  text-align: center;
  color: red;
}
```

在这个例子中，只有具有 class="center" 的 <p> 元素会居中对齐：

```
p.center {
  text-align: center;
  color: red;
}
```

在这个例子中，<p> 元素将根据 class="center" 和 class="large" 进行样式设置：

```
<p class="center large">这个段落引用两个类。</p>
```

**注意：**类名不能以数字开头！

> CSS通用选择器

通用选择器（*）选择页面上的所有的 HTML 元素。

下面的 CSS 规则会影响页面上的每个 HTML 元素：

```
* {
  text-align: center;
  color: blue;
}
```

> 分组选择器

```
h1 {
  text-align: center;
  color: red;
}

h2 {
  text-align: center;
  color: red;
}

p {
  text-align: center;
  color: red;
}
```

最好对选择器进行分组，以最大程度地缩减代码。

如需对选择器进行分组，请用逗号来分隔每个选择器。

```
h1, h2, p {
  text-align: center;
  color: red;
}
```

### CSS使用

有三种插入样式表的方法：

- 外部 CSS
- 内部 CSS
- 行内 CSS

> 外部CSS

通过使用外部样式表，您只需修改一个文件即可改变整个网站的外观！

每张 HTML 页面必须在 head 部分的 <link> 元素内包含对外部样式表文件的引用。

外部样式在 HTML 页面 <head> 部分内的 <link> 元素中进行定义：

```
<!DOCTYPE html>
<html>
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

外部样式表可以在任何文本编辑器中编写，并且必须以 .css 扩展名保存。

外部 .css 文件不应包含任何 HTML 标签。

"mystyle.css" 是这样的：

```
body {
  background-color: lightblue;
}

h1 {
  color: navy;
  margin-left: 20px;
}
```

**注意：**请勿在属性值和单位之间添加空格（例如 `margin-left: 20 px;`）。正确的写法是：`margin-left: 20px;`

> 内部CSS

如果一张 HTML 页面拥有唯一的样式，那么可以使用内部样式表。

内部样式是在 head 部分的 <style> 元素中进行定义。

内部样式在 HTML 页面的 <head> 部分内的 <style> 元素中进行定义：

```
<!DOCTYPE html>
<html>
<head>
<style>
body {
  background-color: linen;
}

h1 {
  color: maroon;
  margin-left: 40px;
} 
</style>
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

> 行内CSS

行内样式（也称内联样式）可用于为单个元素应用唯一的样式。

如需使用行内样式，请将 style 属性添加到相关元素。style 属性可包含任何 CSS 属性。

行内样式在相关元素的 "style" 属性中定义：

```
<!DOCTYPE html>
<html>
<body>

<h1 style="color:blue;text-align:center;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>

</body>
</html>
```

> 多个样式表

如果在不同样式表中为同一选择器（元素）定义了一些属性，则将使用最后读取的样式表中的值。

```
h1 {
  color: navy;
}
```

然后，假设某个*内部样式表*也为 <h1> 元素设置了如下样式：

```
h1 {
  color: orange;    
}
```

如果内部样式是在链接到外部样式表*之后*定义的，则 <h1> 元素将是橙色：

```
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
<style>
h1 {
  color: orange;
}
</style>
</head>
```

不过，如果在链接到外部样式表*之前*定义了内部样式，则 <h1> 元素将是深蓝色：

```
<head>
<style>
h1 {
  color: orange;
}
</style>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

### CSS注释

位于 `<style>` 元素内的 CSS 注释，以 `/*` 开始，以 `*/` 结束：

从 HTML 教程中，您学习到可以使用 `<!--...-->` 语法在 HTML 源代码中添加注释。

### CSS颜色

> CSS背景色

```
    <h1 style="background-color:DodgerBlue">China</h1>
    <h1 style="background-color:Tomato">China</h1>
```

![image-20220908235918946](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942250.png)

> 文本颜色

```
<h1 style="color:DodgerBlue">China</h1>
<h1 style="color:Tomato">China</h1>
```

![image-20220909000056454](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942776.png)

> 边框颜色

```
<h1 style="border:2px solid DodgerBlue">China</h1>
```

![image-20220909000454262](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942049.png)

### CSS背景

**CSS 背景属性用于定义元素的背景效果。**

`background-color` 属性指定元素的背景色。

> 不透明度/透明度

opacity 属性指定元素的不透明度/透明度。取值范围为 0.0 - 1.0。值越低，越透明：

![image-20220909001356357](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942640.png)

![image-20220909001404315](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942178.png)

### CSS背景图像

`background-image` 属性指定用作元素背景的图像。

默认情况下，图像会重复，以覆盖整个元素。

注意：css和images放在不同的文件夹下，如何让css 引用image？

[vscode](https://so.csdn.net/so/search?q=vscode&spm=1001.2101.3001.7020)中如果css.css和图片各自放在同级目录下的不同目录里的话css样式中访问图片的路径就是../来返回css.css样式的上一级目录
然后再写图片的路径

![这里写图片描述](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942585.png)

![image-20220909002616889](https://cdn.jsdelivr.net/gh/yzk656/image/202212241942795.png)

![image-20220909002556458](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943647.png)

### CSS 背景重复

默认情况下，`background-image` 属性在水平和垂直方向上都重复图像。

某些图像应只适合水平或垂直方向上重复，否则它们看起来会很奇怪，如下所示：

```
            background-image:url("../image/Sea.png");
            background-repeat:repeat-x;
```

![image-20220909003033927](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943832.png)

```
background-image:url("../image/Sea.png");
background-repeat:repeat-y;
```

![image-20220909003051228](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943194.png)

`background-repeat` 属性还可指定只显示一次背景图像：

![image-20220909003155401](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943243.png)

`background-position` 属性用于指定背景图像的位置。

```
background-image:url("../image/Sea.png");
background-repeat:no-repeat;
background-position:right top;
```

![image-20220909003315683](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943009.png)

### CSS背景附着

`background-attachment` 属性指定背景图像是应该滚动还是固定的（不会随页面的其余部分一起滚动）：

```
body {
  background-image: url("tree.png");
  background-repeat: no-repeat;
  background-position: right top;
  background-attachment: fixed;
}
```

指定背景图像应随页面的其余部分一起滚动：

```
body {
  background-image: url("tree.png");
  background-repeat: no-repeat;
  background-position: right top;
  background-attachment: scroll;
}
```

### CSS背景简写

CSS background - 简写属性

如需缩短代码，也可以在一个属性中指定所有背景属性。它被称为简写属性。

而不是这样写：

```
body {
  background-color: #ffffff;
  background-image: url("tree.png");
  background-repeat: no-repeat;
  background-position: right top;
}
```

使用简写属性在一条声明中设置背景属性：

```
body {
  background: #ffffff url("tree.png") no-repeat right top;
}
```

- background-color
- background-image
- background-repeat
- background-attachment
- background-position

属性值之一缺失并不要紧，只要按照此顺序设置其他值即可。请注意，在上面的例子中，我们没有使用 background-attachment 属性，因为它没有值。

```
           background:DodgerBlue url("../image/Sea.png") no-repeat fixed;
```

![image-20220909063325385](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943506.png)

### CSS边框

CSS `border` 属性允许您指定元素边框的样式、宽度和颜色。

`border-style` 属性指定要显示的边框类型。

允许以下值：

- `dotted` - 定义点线边框
- `dashed` - 定义虚线边框
- `solid` - 定义实线边框
- `double` - 定义双边框
- `groove` - 定义 3D 坡口边框。效果取决于 border-color 值
- `ridge` - 定义 3D 脊线边框。效果取决于 border-color 值
- `inset` - 定义 3D inset 边框。效果取决于 border-color 值
- `outset` - 定义 3D outset 边框。效果取决于 border-color 值
- `none` - 定义无边框
- `hidden` - 定义隐藏边框

`border-style` 属性可以设置一到四个值（用于上边框、右边框、下边框和左边框）。

```
<h1 style="border:2px solid DodgerBlue;border-style: dotted">China</h1>
```

如果采用元素内部署，不同的属性之间可以通过分号`;`进行连接

### CSS边框宽度

`border-width` 属性指定四个边框的宽度。

可以将宽度设置为特定大小（以 px（像素）、pt（物理像素）、cm、em（格） 计），也可以使用以下三个预定义值之一：thin、medium 或 thick：

```
p.one {
  border-style: solid;
  border-width: 5px;
}

p.two {
  border-style: solid;
  border-width: medium;
}

p.three {
  border-style: dotted;
  border-width: 2px;
} 

p.four {
  border-style: dotted;
  border-width: thick;
}
```

![image-20220909155604349](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943673.png)

### CSS边框颜色

`border-color` 属性用于设置四个边框的颜色。

可以通过以下方式设置颜色：

- name - 指定颜色名，比如 "red"
- HEX - 指定十六进制值，比如 "#ff0000"
- RGB - 指定 RGB 值，比如 "rgb(255,0,0)"
- HSL - 指定 HSL 值，比如 "hsl(0, 100%, 50%)"
- transparent

```
p.one {
  border-style: solid;
  border-color: red;
}

p.two {
  border-style: solid;
  border-color: green;
}

p.three {
  border-style: dotted;
  border-color: blue;
}
```

![image-20220909155824325](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943507.png)

### CSS边框各边

> CSS边框-单独的边

```
p {
  border-top-style: dotted;
  border-right-style: solid;
  border-bottom-style: dotted;
  border-left-style: solid;
}
```

> 不同的边框样式

```
p {
  border-style: dotted solid;
}
```

如果 `border-style` 属性设置四个值：

border-style: dotted solid double dashed;

- 上边框是虚线
- 右边框是实线
- 下边框是双线
- 左边框是虚线

如果 `border-style` 属性设置三个值：

border-style: dotted solid double;

- 上边框是虚线
- 右和左边框是实线
- 下边框是双线

如果 `border-style` 属性设置两个值：

border-style: dotted solid;

- 上和下边框是虚线
- 右和左边框是实线

如果 `border-style` 属性设置一个值：

border-style: dotted;

- 四条边均为虚线

==注意：==

上例中使用的是 `border-style` 属性。但 `border-width` 和 `border-color` 也同样适用。

### CSS简写边框属性

就像您在上一章中所见，处理边框时要考虑许多属性。

为了缩减代码，也可以在一个属性中指定所有单独的边框属性。

`border` 属性是以下各个边框属性的简写属性：

- `border-width`
- `border-style`（必需）
- `border-color`

```
p {
  border: 5px solid red;
}
```

您还可以只为一个边指定所有单个边框属性：

```
p {
  border-left: 6px solid red;
  background-color: lightgrey;
}
```

==注意：==

不同的属性之间用空格隔开

![image-20220909161133232](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943962.png)

![image-20220909161138160](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220909161138160.png)

### 圆角边框

 `border-radius` 属性用于向元素添加圆角边框：

==注意：==

注意radius，不是radious

```
border-radius:10px;
```

![image-20220909172415923](https://cdn.jsdelivr.net/gh/yzk656/image/202212241943859.png)

### CSS 外边距

CSS `margin` 属性用于在任何定义的边框之外，为元素周围创建空间。

通过 CSS，您可以完全控制外边距。有一些属性可用于设置元素每侧（上、右、下和左）的外边距。

margin同样有简写属性

> auto

您可以将 margin 属性设置为 `auto`，以使元素在其容器中水平居中。

然后，该元素将占据指定的宽度，并且剩余空间将在左右边界之间平均分配。

使用 `margin: auto`：

```
div {
  width: 300px;
  margin: auto;
  border: 1px solid red;
}
```

> inherit

本例使 <p class="ex1"> 元素的左外边距继承自父元素（<div>）：

使用 inherit 值：

```
div {
  border: 1px solid red;
  margin-left: 100px;
}

p.ex1 {
  margin-left: inherit;
}
```

### 盒子模型

![image-20220914163839124](https://cdn.jsdelivr.net/gh/yzk656/image/202212241946265.png)

![image-20220914163948342](https://cdn.jsdelivr.net/gh/yzk656/image/202212241946903.png)

![image-20220914164803896](https://cdn.jsdelivr.net/gh/yzk656/image/202212241946047.png)

![image-20220914165147911](https://cdn.jsdelivr.net/gh/yzk656/image/202212241946287.png)

### 弹性盒子模型

![image-20220914165257524](https://cdn.jsdelivr.net/gh/yzk656/image/202212241946246.png)

![image-20220914165316822](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220914165316822.png)

![image-20220914170108428](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220914170108428.png)

![image-20220914170129173](https://cdn.jsdelivr.net/gh/yzk656/image/202212241946199.png)

![image-20220914181057074](https://cdn.jsdelivr.net/gh/yzk656/image/202212241946112.png)

![image-20220914181306677](https://cdn.jsdelivr.net/gh/yzk656/image/202212241946126.png)

![image-20220914181700856](https://cdn.jsdelivr.net/gh/yzk656/image/202212241946782.png)

![image-20220914182213978](https://cdn.jsdelivr.net/gh/yzk656/image/202212241947330.png)

### 文档流

![image-20220914182421470](https://cdn.jsdelivr.net/gh/yzk656/image/202212241948193.png)

![image-20220914183338381](https://cdn.jsdelivr.net/gh/yzk656/image/202212241948346.png)

![image-20220914183516829](https://cdn.jsdelivr.net/gh/yzk656/image/202212241948258.png)

![image-20220914183533509](https://cdn.jsdelivr.net/gh/yzk656/image/202212241948210.png)

### 浮动

![image-20220914183748486](https://cdn.jsdelivr.net/gh/yzk656/image/202212241948889.png)

![image-20220914183758231](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949891.png)

![image-20220914183921706](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949915.png)

   



![image-20220914205205492](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949563.png)

![image-20220914205309874](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949200.png)

==注意：==如果都是脱离文档流就不会出现压盖情况

### 清除浮动

主要用于处理不方便设置高度等情况

![image-20220914205849999](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949250.png)

![image-20220914205933420](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949004.png)

![image-20220914211444019](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949002.png)

![image-20220914211451094](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949155.png)

清除高度后造成高度塌陷：

![image-20220914211558307](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949059.png)

![image-20220914211544807](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949875.png)

![image-20220914211923080](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949229.png)



再重新开个框子

![image-20220914213813809](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949972.png)

![image-20220914213816702](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949282.png)

![image-20220914213948445](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949412.png)

![image-20220914214108352](https://cdn.jsdelivr.net/gh/yzk656/image/202212241949306.png)

![image-20220914214115889](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950517.png)

![image-20220914214239587](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950828.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950884.png)

清除浮动

![image-20220914214356409](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950143.png)

![image-20220914214421945](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950500.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950388.png)

overflow清除浮动

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950147.png)

![image-20220914220716343](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950869.png)

> 伪对象方式

![image-20220914220812649](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950956.png)



![image-20220914221105545](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950732.png)

![image-20220914221116065](https://cdn.jsdelivr.net/gh/yzk656/image/202212241950350.png)

添加进里面后

![image-20220914221339047](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952208.png)

![image-20220914221346031](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220914221346031.png)

![image-20220914221808259](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952392.png)

### 定位

![image-20220914221832156](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952629.png)

![image-20220914221837706](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952676.png)





![image-20220915084019804](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952854.png)

> 绝对定位

绝对定位是脱离文档流的

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952878.png)

每一个绝对定位都是一层

![image-20220915093347558](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952817.png)

> 固定定位

固定定位不会随着页面的滚动而滚动；绝对定位会随着页面的滚动而滚动

![image-20220915095539880](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952733.png)

![image-20220915095757691](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952240.png)

![image-20220915100454458](https://cdn.jsdelivr.net/gh/yzk656/image/202212241952071.png)

![image-20220915100510481](https://cdn.jsdelivr.net/gh/yzk656/image/202212241956663.png)

> z-index

![image-20220915100851463](https://cdn.jsdelivr.net/gh/yzk656/image/202212241956649.png)

![image-20220915101210430](https://cdn.jsdelivr.net/gh/yzk656/image/202212241956021.png)

![image-20220915102302036](https://cdn.jsdelivr.net/gh/yzk656/image/202212241956242.png)

### CSS新特性

![image-20220915102613186](https://cdn.jsdelivr.net/gh/yzk656/image/202212241956774.png)

 ![image-20220915104440788](https://cdn.jsdelivr.net/gh/yzk656/image/202212241956655.png)

语法：text-shadow:w-shadow h-shadow blur color;

w-shadow：水平方向的距离 （必须有的：支持负值）

h-shadow：垂直方向的距离 （必须有的：支持负值）

blur：阴影的模糊程度，可选 （不支持负值）

color：阴影的颜色

![image-20220915110749586](https://cdn.jsdelivr.net/gh/yzk656/image/202212241956069.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241956550.png)



 ![image-20220915110418961](https://cdn.jsdelivr.net/gh/yzk656/image/202212241956303.png)

![image-20220915112139301](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957805.png)

### 动画

![image-20220915112304630](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957398.png)

![image-20220915112259422](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220915112259422.png)

![image-20220915112352113](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957024.png)

![image-20220915112550096](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957014.png)

![image-20220915112658020](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957071.png)

![image-20220915113237634](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957355.png)

![image-20220915121158262](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957264.png)

当鼠标滑到某个位置时进行颜色变化

```
div{
    width: 200px;
    height: 200px;
    background-color: pink;
    animation:my_anim 3s linear 0 infinite ;
}
div:hover{
    background-color: cornsilk;
}
```

![image-20220915114533731](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957040.png)

```
div{
    width: 200px;
    height: 200px;
    background-color: pink;
    animation:my_anim 3s linear 0s infinite ;
}
div:hover{
    animation-play-state: paused;
}

@keyframes my_anim{
    0%{
        width: 200px;
        background-color: #F29B9B;
    }

    50%{
        width: 400px;
        background-color: #ada0ff;
    }
    100%{
        width: 200px;
        background-color: #F29B9B;
    }
}
```

> 呼吸灯

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box{
            width:500px;
            height:400px;
            margin:40px auto;
            background-color:#2b92d4;
            border-radius:5px;
            box-shadow:0 1px 2px rgba(0,0,0,.3);
            animation: breathe 1s ease-in-out infinite alternate;
        }

        @keyframes breathe{
            0%{
                opacity:0.2;
                box-shadow:0 1px 2px rgba(255,255,255,0.1)
            }
            50%{
                opacity:0.5;
                box-shadow:0 1px 2px rgba(18,190,84,0.76)
            }
            100%{
                opacity: 1;
                box-shadow: 0 1px 30px rgba(59, 255, 255, 1)
            }
        }
    </style>
</head>
<body>
    <div class="box">

    </div>
</body>
</html>
```

![image-20220915121857796](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957640.png)

### 媒体查询

![image-20220915234112917](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957384.png)

![image-20220915234207682](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957167.png)

![image-20220915235227581](https://cdn.jsdelivr.net/gh/yzk656/image/202212241957312.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1,use-scalable=no">
    <style>
        .box{
          width: 300px;
          height: 300px;
          background-color:red;
        }

        @media screen and (max-width:768px){
            .box{
                background-color:greenyellow;
            }
            .p1{
                display:none;
            }
            .p2{
                display:none;
            }
        }

        @media screen and (min-width: 768px) and (max-width:992px){
            .box{
                background-color: #F29B9B;
            }
            .p1{
                display:none;
            }
            .p2{
                display:block;
            }
        }
        
        @media screen and (min-width: 992px) {
            .box{
                background-color: blueviolet;
            }
            .p1{
                display:block;
            }
            .p2{
                display:block;
            }
        }

    </style>
</head>
<body>
    <div class="box"></div>
    <p class="p1">哈哈哈</p>
    <p class="p2">嘻嘻嘻</p>
</body>
</html>
```

### 雪碧图

![image-20220916001524103](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958465.png)

![image-20220916001716038](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958097.png)

 ```
 <!DOCTYPE html>
 <html lang="en">
 <head>
     <meta charset="UTF-8">
     <title>Title</title>
     <style>
         .icon1{
           display: block;;
           width: 45px;
           height: 70px;
           background-image:url(01.png);
           border:1px solid red;
           background-position:-289px -62px;
         }
         .icon2{
             display: block;;
             width: 45px;
             height: 70px;
             background-image:url(01.png);
             border:1px solid red;
             background-position:-17px 0;
         }
     </style>
 </head>
 <body>
     <span class="icon1"></span>
     <span class="icon2"></span>
 </body>
 </html>
 ```

![image-20220916004235526](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958595.png)





### 字体图标

![image-20220916074150466](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958371.png)



![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958378.png)

==注意：==class后面可以跟多个类标签

### blockquote

在此标签内可以显示空格

![image-20221009230150151](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958240.png)

### 字体水平对齐方式

text-align

在CSS中，使用text-align属性控制文本的水平方向的对齐方式：左对齐、居中对齐、右对齐

### 字体垂直对齐方式

vertical-align：center

### 标题栏

标题左侧添加图片

将图片后缀改为`ico` ,在head标签中添加`<link rel="shortcut icon" href="地址"/>`

### 为什么把Script标签放在body结束标签之后html结束标签之前？

之所以将脚本放在正文之后，是为了防止它影响HTML的其他部分。如果放在前面，脚本可能需要很长时间才能影响后续内容的呈现，或者当脚本执行出现问题时，后续内容的解析就会中断。这是个人的理解。请专家来鉴定。

### src和href的区别

href是Hypertext Reference的简写，表示超文本引用，指向网络资源所在位置。 src是source的简写，目的是要把文件下载到html页面中去

### 水平居中

`margin:0  auto`

上下靠内容撑开就行



## JavaScript

### JavaScript简介

![image-20220916195539296](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958362.png)



![image-20220916195951422](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958080.png)

### JavaScript语句与标识符

![image-20220916200749904](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958081.png)

### 变量

![image-20220917070351797](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958962.png)

![image-20220917070357905](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958035.png)

### JavaScript引入到文件

![image-20220917070449030](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958633.png)

![image-20220917070500656](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958609.png)

![image-20220917071037009](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958866.png)

### JavaScript注释与输出方式

![image-20220917071445500](https://cdn.jsdelivr.net/gh/yzk656/image/202212241958881.png)

![image-20220917071943944](https://cdn.jsdelivr.net/gh/yzk656/image/202212241959750.png)

### 数据类型

![image-20220917072118777](https://cdn.jsdelivr.net/gh/yzk656/image/202212241959454.png)

![image-20220917072134508](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220917072134508.png)

![image-20220917072232006](https://cdn.jsdelivr.net/gh/yzk656/image/202212241959447.png)

![image-20220917072503519](https://cdn.jsdelivr.net/gh/yzk656/image/202212241959762.png)

![image-20220917073010234](https://cdn.jsdelivr.net/gh/yzk656/image/202212241959602.png)

![image-20220917073230675](https://cdn.jsdelivr.net/gh/yzk656/image/202212241959625.png)

### typeof运算符

![image-20220917073404513](https://cdn.jsdelivr.net/gh/yzk656/image/202212241959675.png)

 ![image-20220917075214492](https://cdn.jsdelivr.net/gh/yzk656/image/202212242005605.png)

![image-20220917075511952](https://cdn.jsdelivr.net/gh/yzk656/image/202212242005826.png)

![image-20220917075548386](https://cdn.jsdelivr.net/gh/yzk656/image/202212242005490.png)



### 运算符之算数运算符

![image-20220917075711367](https://cdn.jsdelivr.net/gh/yzk656/image/202212242005947.png)

### 运算符之赋值运算符

![image-20220917080258558](https://cdn.jsdelivr.net/gh/yzk656/image/202212242005092.png)



### 运算符之比较运算符

![image-20220917080552600](https://cdn.jsdelivr.net/gh/yzk656/image/202212242005436.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242006054.png)



### 运算符之布尔运算符

![image-20220917081023846](https://cdn.jsdelivr.net/gh/yzk656/image/202212242006114.png)

![image-20220917082145204](https://cdn.jsdelivr.net/gh/yzk656/image/202212242006637.png)

### charAt()

![image-20220917191306786](https://cdn.jsdelivr.net/gh/yzk656/image/202212242006069.png)

![image-20220917191745682](https://cdn.jsdelivr.net/gh/yzk656/image/202212242006028.png)

![image-20220917191814654](https://cdn.jsdelivr.net/gh/yzk656/image/202212242006516.png)

### concat

![image-20220917191838822](https://cdn.jsdelivr.net/gh/yzk656/image/202212242006237.png)

![image-20220917192207909](https://cdn.jsdelivr.net/gh/yzk656/image/202212242006388.png)

![image-20220917192345145](https://cdn.jsdelivr.net/gh/yzk656/image/202212242007519.png)

![image-20220917192606035](https://cdn.jsdelivr.net/gh/yzk656/image/202212242007189.png)

### substring

![image-20220917192908898](https://cdn.jsdelivr.net/gh/yzk656/image/202212242007413.png)

### substr

![image-20220917195801026](https://cdn.jsdelivr.net/gh/yzk656/image/202212242007807.png)

![image-20220917205715868](https://cdn.jsdelivr.net/gh/yzk656/image/202212242007482.png)

### indexof

![image-20220917205801268](https://cdn.jsdelivr.net/gh/yzk656/image/202212242007663.png)

### trim

![image-20220917210636827](https://cdn.jsdelivr.net/gh/yzk656/image/202212242007904.png)

![image-20220917210704302](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008774.png)

### split

![image-20220917211221123](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008942.png)

![image-20220917211614578](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008974.png)

### 数组

![image-20220917215046829](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008000.png)

![image-20220917215144679](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220917215144679.png)

![image-20220917215420514](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008281.png)

![image-20220917215922097](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008760.png)

### 数组的遍历

![image-20220917220311015](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008102.png)

### 数组静态方法Array.isArray()

![image-20220917220724789](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008880.png)

![image-20220917233401749](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008790.png)

### 数组方法 push pop

![image-20220917233726529](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008287.png)

### 数组方法 shift()/unshift()

![image-20220917234244866](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008150.png)

![image-20220917234638885](https://cdn.jsdelivr.net/gh/yzk656/image/202212242008358.png)

### 数组方法 join()

![image-20220917234959249](https://cdn.jsdelivr.net/gh/yzk656/image/202212242009360.png)

![image-20220917235245923](https://cdn.jsdelivr.net/gh/yzk656/image/202212242009093.png)

### 数组方法 concat

![image-20220917235705508](https://cdn.jsdelivr.net/gh/yzk656/image/202212242009222.png)

### 数组方法 reverse()

![image-20220918085121539](https://cdn.jsdelivr.net/gh/yzk656/image/202212242009429.png)

### 数组方法 indexOf()

![image-20220918090244640](https://cdn.jsdelivr.net/gh/yzk656/image/202212242009648.png)

### 函数

![image-20220918090900080](https://cdn.jsdelivr.net/gh/yzk656/image/202212242009393.png)

![image-20220918092202016](https://cdn.jsdelivr.net/gh/yzk656/image/202212242010876.png)

### 对象

![image-20220918092751626](https://cdn.jsdelivr.net/gh/yzk656/image/202212242010802.png)

![image-20220918092741019](https://cdn.jsdelivr.net/gh/yzk656/image/202212242010138.png)

![image-20220918093307997](https://cdn.jsdelivr.net/gh/yzk656/image/202212242010684.png)

### Math对象

![image-20220918093426628](https://cdn.jsdelivr.net/gh/yzk656/image/202212242010285.png)

![image-20220918093435183](https://cdn.jsdelivr.net/gh/yzk656/image/202212242010930.png)

![image-20220918093817083](https://cdn.jsdelivr.net/gh/yzk656/image/202212242010620.png)

![image-20220918094052177](https://cdn.jsdelivr.net/gh/yzk656/image/202212242010883.png)

### Date对象

![image-20220918094524142](https://cdn.jsdelivr.net/gh/yzk656/image/202212242010552.png)

![image-20220918094702440](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220918094702440.png)

![image-20220918094818501](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220918094818501.png)

![image-20220918095849970](https://cdn.jsdelivr.net/gh/yzk656/image/202212242014736.png)

### DOM概述

![image-20220919000944767](https://cdn.jsdelivr.net/gh/yzk656/image/202212242014564.png)

![image-20220919001125583](https://cdn.jsdelivr.net/gh/yzk656/image/202212242014847.png)

![image-20220919001210892](https://cdn.jsdelivr.net/gh/yzk656/image/202212242014897.png)

![image-20220919001314594](https://cdn.jsdelivr.net/gh/yzk656/image/202212242014856.png)

![image-20220919001559710](https://cdn.jsdelivr.net/gh/yzk656/image/202212242015225.png)

### doucument对象__方法/获取元素

![image-20220919001841189](https://cdn.jsdelivr.net/gh/yzk656/image/202212242015741.png)

![image-20220919002103255](https://cdn.jsdelivr.net/gh/yzk656/image/202212242015937.png)

```
      <div>
        hello1
      </div>
      <div>
          hello2
      </div>
      <script>
          var  div1=document.getElementsByTagName("div")[0];
          div1.innerHTML="hello world"
      </script>
```

![image-20220919002830587](https://cdn.jsdelivr.net/gh/yzk656/image/202212242015339.png)

```
          var text=document.getElementsByClassName("text")[0];
          text.innerHTML="hello"
```

![image-20220919003250899](https://cdn.jsdelivr.net/gh/yzk656/image/202212242015856.png)

```
var name=document.getElementsByName("login");
          console.log(name);
```



![image-20220919003458509](https://cdn.jsdelivr.net/gh/yzk656/image/202212242015293.png)

```
var root=document.getElementById("root")//由于属性ID是唯一的，因此不存在集合的情况，因此是Element，没s
          console.log(root);
```

![image-20220919004039283](https://cdn.jsdelivr.net/gh/yzk656/image/202212242015721.png)

```
          var nav=document.querySelector(".nav");//参数是选择器
          console.log(nav);
```

![image-20220919004616430](https://cdn.jsdelivr.net/gh/yzk656/image/202212242015175.png)

```
          var nav=document.querySelectorAll(".nav")[1];
          console.log(nav);
```

### document对象__方法/创建元素

![image-20220919005306262](https://cdn.jsdelivr.net/gh/yzk656/image/202212242015011.png)

![image-20220919130648022](https://cdn.jsdelivr.net/gh/yzk656/image/202212242016300.png)

```
        var text=document.createElement("p");

        var content=document.createTextNode("我是文本");
        console.log(content);

        //appendChild：将内容或者子元素放进容器中
        text.appendChild(content);
        console.log(text);
```

![image-20220919130657342](https://cdn.jsdelivr.net/gh/yzk656/image/202212242016370.png)

```
        var id=document.createAttribute("id");
        id.value="root";
        console.log(id);
```

```
        var id=document.createAttribute("id");
        id.value="root";
        text.setAttributeNode(id);
        console.log(text);
```

元素是内置的关键字  p等

属性是经常在标签中进行定义

标签 是 head、body这样的

setAttributeNode是只有属性才有的，其他的都是使用appendChild

```
        var container=document.getElementById("container");
        container.appendChild("")
        console.log(container);
```

### Element属性_对象_

![image-20220919144324856](https://cdn.jsdelivr.net/gh/yzk656/image/202212242016178.png)

![image-20220919144419751](https://cdn.jsdelivr.net/gh/yzk656/image/202212242016528.png)

```
		var root=document.getElementById("root");
        root.id="roots";
        console.log(root);

        root.className="boxs box1";
```

![image-20220919171534124](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018519.png)

```
        console.log(root.classList.add("mybox"));
        root.classList.remove("box");

        if(root.classList.contains("box1")){
            console.log("有");
        }else {
            console.log("没有");
        }
```

![image-20220919172238825](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018836.png)

```
        //没有大家好，就进行读取元素中的内容
		console.log(root.innerHTML="大家好");
```

```
        console.log(root.innerText="www");
```

```
        //没有大家好，就进行读取元素中的内容
		console.log(root.innerHTML="大家好");

        console.log(root.innerText="www");

        //innerHTML与innerText的区别：
        /**
         * innerHTML可以识别标签
         * innerText会把标签识别成1个字符串
         */

        var str="<a href='https://www.itbaizhan.com'>百战</a>";
        root.innerHTML=str;
        root.innerText=str;
```

![image-20220919192052001](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018596.png)

### Element 获取元素位置

![image-20220919192137240](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018054.png)

![image-20220919192720749](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018222.png)

```
        var box=document.getElementById("box");
        console.log(box.clientWidth);
        console.log(box.clientHeight);

        //获取视口高度
        console.log(document.documentElement.clientHeight);
        //获取页面的高度（内容的高度）
        console.log(document.body.clientHeight);
```

![image-20220919195617206](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018136.png)

```
        console.log(box.scrollWidth);
        console.log(box.scrollHeight);

        console.log(document.documentElement.scrollHeight);
        console.log(document.body.scrollHeight);

        console.log(document.documentElement.scrollTop);
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
          *{
              padding: 0;
              margin:0;
          }

        .box{
            width: 200px;
            height: 200px;
            background-color: red;
            margin:100px;
        }

        .root{
            width: 500px;
            height: 500px;
            background-color: #999;
            margin:50px;
            position: relative;
        }
    </style>
</head>
<body>
    <div class="root">
      <div class="box" id="box"></div>
    </div>

    <script>
        var box=document.getElementById("box");
        console.log(box.offsetLeft);
        console.log(box.offsetTop);
    </script>
</body>
</html>
```

![image-20220919220917314](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018780.png)

子元素导致父元素出现高度塌陷margin



外边距合并现象
如果两个div上下排列，给上面div设置margin-bottom，给下面div设置margin-top，那么两个margin会发生合并现象，会取较大的margin值。
注意：左右不会发生 外边距合并现象
上下塌陷现象
一个大盒子 中包含一个小盒子，给小盒子设置一个margin-top，大盒子会一起向下平移。
注意：margin左右没有塌陷现象



###  CSS操作

![image-20220919221516485](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018215.png)

 ![image-20220919223709426](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018141.png)

```
        var box=document.getElementById("box");
        //box.setAttribute("style","width:200px;height:200px;background-color:red;");

        // box.style.width="300px";
        // box.style.height="300px";
        // box.style.backgroundColor="red";

        box.style.cssText="width:200px;height:200px;background-color:red";
        
```

### 事件处理程序

![image-20220920165340948](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018421.png)

```
<body>
    <button onclick="clickHandle()">按钮</button>

    <script>
    	// HTML事件：缺点：HTML和js没有分开
        function clickHandle(){
          console.log("点击了按钮");
        }
    </script>
</body>
```

> DOM0级事件

```
<body>
    <button id="btn">按钮</button>

    <script>
        //DOM0事件：优点：HTML和js是分离的
        //缺点：无法同时添加多个事件
        var btn=document.getElementById("btn");
        
        //出现多个事件时，第一个事件会被第二个覆盖
        btn.onclick=function (){
            console.log("点击了");
        }
        btn.onclick=function (){
            console.log("点击了2");
        }

    </script>
</body>
```

> DOM2级事件

```
<body>
    <button id="btn">按钮</button>


    <script>
    	//优点：DOM2：优点事件不会被覆盖
        var btn=document.getElementById("btn");

        btn.addEventListener("click",function (){
            console.log("点击了");
        });
    </script>
</body>
```

![image-20220920170435697](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018748.png)

### 事件类型之鼠标事件

![image-20220920194857947](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018927.png)

![image-20220920194931217](https://cdn.jsdelivr.net/gh/yzk656/image/202212242018503.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .box1{
            width: 100px;
            height: 100px;
            background-color: red;
        }
        .box2{
          width: 100px;
          height: 100px;
          background-color: green;
        }
        .box3{
          width: 100px;
          height: 100px;
          background-color: blueviolet;
        }
        .box4{
          width: 100px;
          height: 100px;
          background-color:palegoldenrod;
        }
        .box5{
          width: 100px;
          height: 100px;
          background-color:olivedrab;
        }
    </style>
</head>
<body>
    <button id="btn1">单击</button>
    <button id="btn2">双击</button>
    <button id="btn3">鼠标按下</button>
    <button id="btn4">鼠标抬起</button>
    <div id="btn5" class="box1"></div>
    <div id="btn6" class="box2"></div>
    <div id="btn7" class="box3"></div>
    <div id="btn8" class="box4"></div>
    <div id="btn9" class="box5"></div>

    <script>
        var btn1=document.getElementById("btn1");
        var btn2=document.getElementById("btn2");
        var btn3=document.getElementById("btn3");
        var btn4=document.getElementById("btn4");
        var btn5=document.getElementById("btn5");
        var btn6=document.getElementById("btn6");
        var btn7=document.getElementById("btn7");
        var btn8=document.getElementById("btn8");
        var btn9=document.getElementById("btn9");
        btn1.onclick=function (){
            console.log("单击事件");
        }

        btn2.ondblclick=function (){
            console.log("双击事件");
        }

        btn3.onmousedown=function (){
          console.log("鼠标落下事件");
        }

        btn4.onmouseup=function (){
          console.log("鼠标抬起事件");
        }

        btn5.onmousemove=function (){
          console.log("鼠标移动事件");
        }

        btn6.onmouseenter=function (){
          console.log("鼠标进入事件");
        }

        btn7.onmouseleave=function (){
          console.log("鼠标离开事件");
        }

        btn8.onmouseover=function (){
          console.log("鼠标进入事件");
        }

        btn9.onmouseout=function (){
          console.log("鼠标离开事件");
        }
    </script>
</body>
</html>
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
      .root{
        width: 300px;
        height: 300px;
        background-color: green;
      }
      .box{
        width: 100px;
        height: 100px;
        background-color:red;
      }
    </style>
</head>
<body>
    <div class="root" id="root">
      <div class="box" id="box"></div>
    </div>
    <script>
      //mouseenter\mouseleave和mouseover\mouseout区别

      var root=document.getElementById("root");
      var box=document.getElementById("box");

      // root.onmouseenter=function (){
      //   console.log("鼠标进入");
      // }

      root.onmouseover=function (){
        console.log("鼠标进入");
      }
      
      


    </script>
</body>
</html>
```

### Event事件对象

![image-20220920203937332](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019382.png)

![image-20220920204022040](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220920204022040.png)

![image-20220920204500770](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220920204500770.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <button id="btn">按钮</button>


    <script>
      var btn=document.getElementById("btn");
      //Event事件对象 其实就是参数
      btn.onclick=function(event){
        event.target.innerHTML="点击之后";
        console.log(event.type);
      }
    </script>
</body>
</html>
```

![image-20220920205535645](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019836.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <button id="btn">按钮</button>
    <a href="https://itbaizhan.com" id="it">百战</a>

    <script>
      var btn=document.getElementById("btn");
      //Event事件对象 其实就是参数
      btn.onclick=function(event){
        event.target.innerHTML="点击之后";
        console.log(event.type);
      }

      var it=document.getElementById("it");
      it.onclick=function (event){
          event.preventDefault();
          console.log("点击了A");
      }


    </script>
</body>
</html>
```



![image-20220920210200410](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019302.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
      .root{
        width: 200px;
        height: 200px;
        background-color: #999999;
      }
      .box{
        width: 100px;
        height: 100px;
        background-color: red;
      }
    </style>
</head>
<body>
    <div class="root" id="root">
      <div class="box" id="box"></div>
    </div>

    <script>
      var root=document.getElementById("root");
      var box=document.getElementById("box");

      root.onclick=function (){
        console.log("root");
      }

      box.onclick=function (e){
        e.stopPropagation();
         console.log("box");
      }
    </script>
</body>
</html>
```

### 事件类型之键盘事件



![image-20220920212149912](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019164.png)

```
<body>
    <input type="text" id="username">

    <script>
        var username=document.getElementById("username");
        username.onkeydown=function (e){
            console.log("按下了");
         }
         username.onkeyup=function (){
            console.log(e.target.value);
         }
         //数字和字母是有值的，其他的是无值的
         username.onkeypress=function (){
             console.log("press");
         }
    </script>
</body>
```

![image-20220921155055260](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019381.png)

  enter键的keycode是13

 ```
         var password=document.getElementById("password");
         password.onkeyup=function (e){
             //keycode代表每个按键的唯一标识
             if(e.keyCode==13)
             console.log("开始搜索");
         }
 ```

### 事件类型之表单事件

![image-20220921160056442](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019998.png)

 ```
     <input type="text" id="username">
 
     <script>
       var username=document.getElementById("username");
       username.oninput=function (e){
         console.log(e.target.value);
       }
     </script>
 ```

![image-20220921161056340](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019205.png)

```
username.onselect=function (){
  console.log("选中了")
}
```

![image-20220921161244340](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019303.png)

```
//回车或者失去焦点才会触发
password.onchange=function (e){
  console.log(e.target.value);
}
```

![image-20220921161651154](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019782.png)

```
<body>
    <form action="服务器地址" id="my_form" onsubmit="submit_handle">
        <input type="text" name="username">
        <button id="rest_btn">重置</button>
        <button>提交表单</button>
    </form>

    <script>
        var rest_btn=document.getElementById("rest_btn");
        var my_form=document.getElementById("my_form");
        rest_btn.onclick=function (){
            my_form.reset();//触发在表单上：清空表单
        }

        function submit_handle(){
            console.log("想做的事");
        }
    </script>
</body>
```

### 事件代理

![image-20220921163530275](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019606.png)

![image-20220921164033014](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019822.png)

```
<body>
    <ul id="list">
      <li>列表1</li>
      <li>列表2</li>
        <p>sldk</p>
    </ul>

    <script>
      var list=document.getElementById("list");
      // list.onclick=function (){
      //   console.log("点击了");
      // }

      list.addEventListener("click",function (e){
          if(e.target.tagName==="LI")
              console.log(e.target.innerHTML);
      });
    </script>
</body>
```

**![image-20220921182111491](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019159.png)**

### 定时器之setTimeout（）

![image-20220921182159115](https://cdn.jsdelivr.net/gh/yzk656/image/202212242019662.png)

![image-20220921182216618](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220921182216618.png)

```
<script>
  setTimeout(function (){
    console.log("大家好，3s后执行");
  },3000);
</script>
```

![image-20220921182611491](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020606.png)

![image-20220921182639701](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020086.png)

   

```
var name="iven";
var user={
  name:"itbaizhan",
  getName:function (){
    var that=this;//对于当前位置的this值得是user里面的name
    //this永远指向当前调用者
    setTimeout(function (){
      console.log(that.name);
    },1000);
  }
}

user.getName();
```

![image-20220921183852266](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020671.png)

```
timer=setTimeout(function (){
  console.log("大家好，3s后执行");
},3000);

//取消定时器
clearTimeout(timer);
```

### 定时器值setInterval（）

![image-20220921184137536](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020159.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
      .some_div{
        width: 100px;
        height: 100px;
        background-color: red;
      }
    </style>
</head>
<body>
    <div class="some_div" id="some_div"></div>

    <script>
      var div =document.getElementById("some_div");
      //透明度：opacity：取值为0-1
      var opacity=1;
      var fade=setInterval(function (){
        opacity-=0.05;
        div.style.opacity=opacity;
        if(opacity<=0) clearInterval(fade);
      },60);
    </script>
</body>
</html>
```



### 防抖

![image-20220921203833885](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020663.png)

![image-20220921204807325](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020431.png)

![image-20220921204844620](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020853.png)

 ![image-20220921210122994](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020453.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
      h3{
        height: 400px;
      }
    </style>
</head>
<body>
    <h3>1</h3>
    <h3>2</h3>
    <h3>3</h3>
    <h3>4</h3>
    <h3>5</h3>
    <h3>6</h3>


    <script>

      function debounce(fn,delay){
          var timer=null;
          return function (){
              if(timer){
                  clearTimeout(timer);
              }
              timer=setTimeout(fn,delay);
          }
      }
      //滚动事件
      window.onscroll=debounce(scroll_handle,200);


      // function  scroll_handle(){
      //   console.log("页面滚动了")
      // }

      function  scroll_handle(){
        var scrollTop=document.documentElement.scrollTop;
        console.log(scrollTop);
      }
    </script>
</body>
</html>
```

### 节流（throttle）

![image-20220921210336037](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020776.png)

![image-20220921210615143](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020168.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        h3{
            height: 400px;
        }
    </style>
</head>
<body>
<h3>1</h3>
<h3>2</h3>
<h3>3</h3>
<h3>4</h3>
<h3>5</h3>
<h3>6</h3>


<script>

    function throttle(fn,delay){
        var valid = true;
        return function (){
            if(!valid){
                return false;
            }
            valid=false;
            setTimeout(function (){
                fn();
                valid=true;
            },delay);
        }
    }

    //滚动事件
    window.onscroll = throttle(scroll_handle,2000);

    function scroll_handle() {
        var scrollTop = document.documentElement.scrollTop;
        console.log(scrollTop);
    }
</script>
</body>
</html>
```

![image-20220921211818463](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020808.png)

>  水果库存

html代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link href="css_01.css" rel="stylesheet">
    <script type="text/javascript" src="js_01.js"></script>
    <title>Title</title>
</head>
<body>
    <div id="div_container">
        <div id="div_fruit_list">
          <table id="tbl_fruit">
            <tr>
              <th>名称</th>
              <th>单价</th>
              <th>数量</th>
              <th>小计</th>
              <th>操作</th>
            </tr>

            <tr onmouseover="show_background_color()" onmouseout="clear_background_color()">
              <td>苹果</td>
              <td onmouseover="show_hand()">12</td>
              <td>20</td>
              <td>240</td>
              <td><img src="images/delete.png" class="image_delete"/></td>
            </tr>

            <tr onmouseover="show_background_color()" onmouseout="clear_background_color()">
              <td >西瓜</td>
              <td onmouseover="show_hand()">3</td>
              <td>20</td>
              <td>60</td>
              <td><img src="images/delete.png" class="image_delete"/></td>
            </tr>

            <tr onmouseover="show_background_color()" onmouseout="clear_background_color()">
              <td>菠萝</td>
              <td onmouseover="show_hand()">4</td>
              <td>25</td>
              <td>100</td>
              <td><img src="images/delete.png" class="image_delete"/></td>
            </tr>

            <tr onmouseover="show_background_color()" onmouseout="clear_background_color()">
              <td>榴莲</td>
              <td onmouseover="show_hand()">3</td>
              <td>30</td>
              <td>90</td>
              <td><img src="images/delete.png" class="image_delete"/></td>
            </tr>

            <tr onmouseover="show_background_color()" onmouseout="clear_background_color()">
              <td>总计</td>
              <td colspan="4"></td>
            </tr>
          </table>
        </div>
    </div>
</body>
</html>
```

css代码

```css
*{
    /**
        通配符解决浏览器边缘问题
     */
    margin: 0;
    padding: 0;
}
/**
    设置删除图标大小
 */
.image_delete{
    width: 15px;
    height: 15px;
}
/**
    设置最外层边框大小
 */
#div_container{
    width: 1600px;
    height: 780px;
    background: #f1fff2;
}
/**
    设置层边框大小
 */
#div_fruit_list{
    width: 700px;
    height: 200px;
    margin-top:200px;
    margin-left:300px;
    position: absolute;
    border:0px solid black;
}
#tbl_fruit{
    width: 500px;
    height: 150px;
    margin-top: 10px;
    margin-left: 10px;
    position: absolute;
    text-align: center;
}
#tbl_fruit,#tbl_fruit tr th,#tbl_fruit tr td{
    border: 1px solid black;
    border-collapse: collapse;
    font-family: "JetBrains Mono";
    color: violet;
}
```

js代码

```js
//鼠标悬浮：颜色变化
function show_background_color() {
    if (event && event.srcElement && event.srcElement.tagName == "TD") {
        var td = event.srcElement;
        var tr = td.parentElement;
        tr.style.backgroundColor="navy"

        var tds=tr.cells;
        for(var i=0;i<tds.length;i++)
            tds[i].style.color="white"
    }
}
//恢复颜色
function clear_background_color(){
    if(event&&event.srcElement&&event.srcElement.tagName=="TD"){
        var td=event.srcElement;
        var tr=td.parentElement;
        tr.style.backgroundColor="transparent"

        var tds=tr.cells;
        for(var i=0;i<tds.length;i++)
            tds[i].style.color="violet";
    }
}
//悬浮显示手势
function show_hand(){
    if(event&&event.srcElement&&event.srcElement.tagName=="TD"){
        var td=event.srcElement;
        td.style.cursor="pointer";
    }
}
```

js进行优化

```js
window.onload=function (){
    var table_fruit=document.getElementById("tbl_fruit");
    var rows=table_fruit.rows;
    for(var i=0;i<rows.length;i++){
        var tr=rows[i];
        //将事件与动作进行绑定，而不是执行，因此是不带小括号的
        tr.onmouseover=show_background_color;
        tr.onmouseout=clear_background_color;
        var cells=tr.cells;
        var price_id=cells[1];
        price_id.onmouseover=show_hand;
    }
}
//鼠标悬浮：颜色变化
function show_background_color() {
    if (event && event.srcElement && event.srcElement.tagName == "TD") {
        var td = event.srcElement;
        var tr = td.parentElement;
        tr.style.backgroundColor="navy"

        var tds=tr.cells;
        for(var i=0;i<tds.length;i++)
            tds[i].style.color="white"
    }
}
//恢复颜色
function clear_background_color(){
    if(event&&event.srcElement&&event.srcElement.tagName=="TD"){
        var td=event.srcElement;
        var tr=td.parentElement;
        tr.style.backgroundColor="transparent"

        var tds=tr.cells;
        for(var i=0;i<tds.length;i++)
            tds[i].style.color="violet";
    }
}
//悬浮显示手势
function show_hand(){
    if(event&&event.srcElement&&event.srcElement.tagName=="TD"){
        var td=event.srcElement;
        td.style.cursor="pointer";
    }
}
```



元素节点是1，文本节点是3

![image-20221001163809052](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020856.png)



边框的宽度不发生改变

给`table`加`table-layout: fixed;`



失去焦点后进行更新

```
input.onblur=update_price;
```

获取值

```
var price_id=tds[1].innerText;
```

使盒子居中

```
margin: 0 auto;
```

使边框圆角

```
border-radius:5px;
```

元素的名字的获取

```
if(tr&&tr.tagName=="TR"){
```

行：row ；列:col



更新内容

```js
window.onload=function (){
    var table_fruit=document.getElementById("tbl_fruit");
    var rows=table_fruit.rows;
    for(var i=0;i<rows.length;i++){
        var tr=rows[i];
        //将事件与动作进行绑定，而不是执行，因此是不带小括号的
        tr.onmouseover=show_background_color;
        tr.onmouseout=clear_background_color;
        var cells=tr.cells;
        var price_id=cells[1];
        price_id.onmouseover=show_hand;

        price_id.onclick=edit_price;
    }
}
//鼠标悬浮：颜色变化
function show_background_color() {
    if (event && event.srcElement && event.srcElement.tagName == "TD") {
        var td = event.srcElement;
        var tr = td.parentElement;
        tr.style.backgroundColor="navy"

        var tds=tr.cells;
        for(var i=0;i<tds.length;i++)
            tds[i].style.color="white"
    }
}
//恢复颜色
function clear_background_color(){
    if(event&&event.srcElement&&event.srcElement.tagName=="TD"){
        var td=event.srcElement;
        var tr=td.parentElement;
        tr.style.backgroundColor="transparent"

        var tds=tr.cells;
        for(var i=0;i<tds.length;i++)
            tds[i].style.color="violet";
    }
}
//悬浮显示手势
function show_hand(){
    if(event&&event.srcElement&&event.srcElement.tagName=="TD"){
        var td=event.srcElement;
        td.style.cursor="pointer";
    }
}
function edit_price(){
    if(event&&event.srcElement&&event.srcElement.tagName=="TD"){
        var price_id=event.srcElement;
        if(price_id&&price_id.firstChild.nodeType==3){
            var old_price=price_id.innerText;
            price_id.innerHTML="<input type='text' size='4'/>";
            var input=price_id.firstChild;
            if(input.tagName=="INPUT"){
                input.value=old_price;
                input.select();
                input.onblur=update_price;
            }
        }
    }
}
function update_price(){
    if(event&&event.srcElement&&event.srcElement.tagName=="INPUT"){
        var input=event.srcElement;
        var new_price=input.value;
        var price_id=input.parentElement;
        price_id.innerText=new_price;

        //更新小计
        update_xj(price_id.parentElement);
    }
}
function update_xj(tr){
    if(tr&&tr.tagName=="TR"){
        var tds=tr.cells;
        var price=tds[1].innerText;
        var count=tds[2].innerText;
        var xj=parseInt(price)*parseInt(count);
        tds[3].innerText=xj;

        update_zj();
    }
}

function update_zj(){
    var table_fruit=document.getElementById("tbl_fruit");
    var rows= table_fruit.rows;
    var sum=0;
    for(var i=1;i<rows.length-1;i++){
        var tr=rows[i];
        var xj=parseInt(tr.cells[3].innerText);
        sum=sum+xj;
    }
    rows[rows.length-1].cells[1].innerText=sum;
}
```





表格具有删除行的方法

行具有获得当前行在表格中的位置

```
var table_fruit=document.getElementById("tbl_fruit");
table_fruit.deleteRow(tr.rowIndex);
```

## js滚动图













# School_ASP.net

![image-20220824085332796](https://cdn.jsdelivr.net/gh/yzk656/image/202212242020399.png)

![image-20220824090737697](../../../AppData/Roaming/Typora/typora-user-images/image-20220824090737697.png)

## HTML

![image-20220824094032124](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021846.png)

```java
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<!--
    单标记：hr、br
    width:500px/50%
    双标记：body、h1-6
-->
<body>
    <h1>算法</h1>
    SDK分类法搜<br/>
    <hr width="50%" color="red" size="6"/>
    SDK分类法搜
</body>
</html>
```

![image-20220826143200883](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021322.png)

> 特殊字符

空格:& nbsp

小于：&lt，&gt

> 列表

    * ol：有序列表
    * li：代表数字
    * type:代表排序的类型
    * start:代表从第几个字符开始【1,2,3】
    
    * ul:无序列表
    * type：圆圈、方块

disc在无序列表中是 点 

> 图片

图片的路径的选择尽量使用相对路径：便于在其他电脑上显示

alter：图片显示错误时，显示想要显示的内容

title：鼠标放在图片上想要显示的内容

> 表格

td：table data

cellpadding:单元格与内容之间的距离

cellspaceing：单元格之间的距离

![image-20220831093937352](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021593.png)

> 超链接

```
<a href="" target="_blank" ></a>
```

_blank -- 在新窗口中打开链接
_parent -- 在父窗体中打开链接
_self -- 在当前窗体打开链接,此为默认值
_top -- 在当前窗体打开链接，并替换当前的整个窗体([框架](https://so.csdn.net/so/search?q=框架&spm=1001.2101.3001.7020)页)

#：空连接

> 滚动

```html
<marquee direction="left" srcollamount="3" behavior="alternate" onmouseover="this.stop()" onmouseout="this.start()">
    计算机与信息工程学院
</marquee>
```

> 插入

```html
<embed src="" width="" height=""/>
```

> 构架

<frameset rows=”行数” cols=”列数”>

​       <frame src=”文件路径” name=”框架名称”/>

</frameset>

需要删除body

准备：

![image-20220902163514273](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021818.png) 

![image-20220902163526382](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021914.png)

效果：

![image-20220902163451243](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021364.png)

> 表单

单行文本框<input type="text">

密码框：<input type="password">

单选框：<input type="rdio" value="" checked="checked"/>

复选框：<input type="checkbox" value="" checked="checked"/>

浏览框：<input type="file"/>

列表框：<select>

​					<option>

​					</option>

​				<select/>

文本框：<textarea rows="" cols=""></textarea>

按钮：<input type="button" value=""></input>

表单外框：<fieldset><legend>注册界面</legend><fieldset>

![image-20220907091559689](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021410.png)

## CSS

> 知识

规定文本块中首行文本的缩进：text-indent



[CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) 的属性 **`vertical-align`** 用来指定行内元素（inline）或表格单元格（table-cell）元素的垂直对齐方式。行内式用标记的style写样式

：；【属性：属性值；属性：属性值；】



css中图片作为背景

```
        #p1{
            text-indent:2em;
            background-img:url("Header.jpg");
        }
```



background-attachment 属性设置背景图像是否固定或者随着页面的其余部分滚动。

| 值      | 描述                                                    |
| :------ | :------------------------------------------------------ |
| scroll  | 默认值。背景图像会随着页面其余部分的滚动而移动。        |
| fixed   | 当页面的其余部分滚动时，背景图像不会移动。              |
| inherit | 规定应该从父元素继承 background-attachment 属性的设置。 |









> 下划线

text-decoration-style 属性规定线条如何显示。

语法：

```
text-decoration-style: solid|double|dotted|dashed|wavy|initial|inherit;
```

属性值：

solid 默认值。线条将显示为单线。

double 线条将显示为双线。

dotted 线条将显示为点状线。

dashed 线条将显示为虚线。

wavy 线条将显示为波浪线。

initial 设置该属性为它的默认值。

inherit 从父元素继承该属性。

![image-20220907112055271](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021803.png)

多个属性之间可以通过`;`隔开

![image-20220909145529922](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021281.png)



```
/**
并集选择器，将选择器用逗号间隔
 */
p,h3,div{
    color: red;
    font-size: 20px;
}
```

交集选择器：

![image-20220914085643412](https://cdn.jsdelivr.net/gh/yzk656/image/202212242021059.png)

后代选择器

```
p span{
    color: red;
}
div span{
    color: beige;
}
```

> 盒子模型

![image-20220914092214526](https://cdn.jsdelivr.net/gh/yzk656/image/202212242022428.png)

1. 边框：border

   三个属性：border-color：颜色；border-width：粗细；border-style：线型（solid dotted）

   属性值得简写

   ```
   border-color: red;   	  /*四个边为红色*/	
   border-color: red blue;   /*红色*/	
   border-color: red;        /*四个边为红色*/	
   border-color: red;         /*四个边为红色*/	
   ```

![image-20220914094156605](https://cdn.jsdelivr.net/gh/yzk656/image/202212242022014.png)

![image-20220916141638057](https://cdn.jsdelivr.net/gh/yzk656/image/202212242022306.png)

![image-20220916141655533](https://cdn.jsdelivr.net/gh/yzk656/image/202212242022724.png)



```
/**
    使用通配选择器清除浏览器固有格式
 */
*{
    margin: 0;
    padding: 0;
}
```

> 盒子之间的关系

1. 块级元素block：他总是以一个块的形式表现出来，并且跟同级兄弟块依次竖直排列，左右撑满，如div、ul li ol  h3 table

​		![image-20220916143535838](https://cdn.jsdelivr.net/gh/yzk656/image/202212242022060.png)





 2. 行内元素inline 对于【】文字这类元素各个字母之间横向排列，到最右端自动换行:span

    ![image-20220916143750940](https://cdn.jsdelivr.net/gh/yzk656/image/202212242022868.png)

> 盒子在标准流中的定位规则

1. 行内元素

   ![image-20220916145004047](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220916145004047.png)

   ![image-20220916144932851](https://cdn.jsdelivr.net/gh/yzk656/image/202212242022036.png)

   

2. 块级元素

   ![image-20220916144848205](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220916144848205.png)

![image-20220916144504689](https://cdn.jsdelivr.net/gh/yzk656/image/202212242023803.png)

> 盒子的浮动

floa属性：默认是none，即标准流，如果将float属性设置为left、right。元素就会向其父元素的左侧或右侧紧靠，同时默认情况下，例子不再，而是根据盒子的内容决定

        .father div{
          background-color: #F29B9B;
        }



对于外边相同的，里边不同的

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .father{
            border:1px solid red;
        }
        .father div{
          background-color: #F29B9B;
        }
    </style>
</head>
<body>
    <div class="father">
      <div class="son1">1</div>
      <div class="son2">2</div>
      <div class="son3">3</div>
    </div>

</body>
</html>
```

 ![image-20220921092000952](https://cdn.jsdelivr.net/gh/yzk656/image/202212242023331.png)

box1和box2的左侧是重合的，当box1浮动时，就脱离了标准流，box2占用了原来的位置，只是box2的内容是紧靠box1来显示的

![image-20220921093418748](https://cdn.jsdelivr.net/gh/yzk656/image/202212242023004.png)

![image-20220921093549926](https://cdn.jsdelivr.net/gh/yzk656/image/202212242023329.png)

![image-20220921093707399](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220921093707399.png)

![image-20220921094222178](https://cdn.jsdelivr.net/gh/yzk656/image/202212242023654.png)

七、盒子的定位

position有四个属性：

static：默认排版方式，即标准流模式

relative：相对定位

absolute：绝对定位

fixed：固定定位

1. relative相对定位：没有脱离标准流

	以标准流的排版方式为基础，使盒子相对于它原本的位置偏移指定的距离，相对定位的盒子仍在标准流中，他后面的盒子仍以标准流方式对待他

	![ ](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220923142247731.png)

	![image-20220923142727342](https://cdn.jsdelivr.net/gh/yzk656/image/202212242024492.png)

	新->旧

	![image-20220923142934977](https://cdn.jsdelivr.net/gh/yzk656/image/202212242024399.png)

	```
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	    <style>
	        .father{
	            border: 1px solid red;
	        }
	        .father div{
	            border: 1px solid blue;
	            background-color: #2b92d4;
	        }
	        .son1{
	            position: relative;
	            left: 100px;
	            top: 100px;
	        }
	        .son2{
	            position: relative;
	            left: 40px;
	            bottom: 20px;
	        }
	    </style>
	</head>
	<body>
	    <div class="father">
	        <div class="son1">box1</div>
	        <div class="son2">box2</div>
	    </div>
	</body>
	</html>
	```

2. 绝对定位：absolute：从标准流脱离出来了

	![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242024336.png)

	```
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	    <style>
	        .father{
	            border: 1px solid red;
	            height: 200px;
	        }
	        .father div{
	            border: 1px solid blue;
	            background-color: #2b92d4;
	        }
	        .son1{
	            position: absolute;
	            right: 80px;
	            bottom: 80px;
	        }
	        .son2{
	            position: absolute;
	            left: 80px;
	            bottom: 80px;
	        }
	    </style>
	</head>
	<body>
	    <div class="father">
	        <div class="son1">box1</div>
	        <div class="son2">box2</div>
	        <div class="son3">box3</div>
	    </div>
	</body>
	</html>
	```

3. 固定定位：fixed

	![image-20220928085516196](https://cdn.jsdelivr.net/gh/yzk656/image/202212242024982.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212242024702.png)



![image-20220928094106668](https://cdn.jsdelivr.net/gh/yzk656/image/202212242024757.png)

==缩写==

![image-20220930144907119](https://cdn.jsdelivr.net/gh/yzk656/image/202212242024847.png)

> 链接 伪类

![image-20220930150005159](https://cdn.jsdelivr.net/gh/yzk656/image/202212242024295.png)

> 按钮式水平导航条

## 动态网站

1. AutoPostBack 属性用于设置或返回当用户选择列表控件中的项目时是否发生自动回发。

如果此属性设置为 TRUE，则启用自动回发，否则为 FALSE。默认为假。

2. 想对哪个部件进行事件处理时，可以之间双击部件，进入部件的方法设计



## 问题1：

![image-20221109104959965](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221109104959965.png)

1. https://www.microsoft.com/zh-CN/download/details.aspx?id=13255
2. ![image-20221109105132941](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221109105132941.png)
3. 重启vs

![image-20221112193944361](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112193944361.png)

![image-20221112194538850](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112194538850.png)

![image-20221112195120778](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112195120778.png)

![image-20221112195133727](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112195133727.png)

![image-20221112195431138](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112195431138.png)

![image-20221112200116942](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112200116942.png)

![image-20221112201508912](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112201508912.png)

![image-20221112201839402](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112201839402.png)

![image-20221112202533685](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112202533685.png)

![image-20221112203118998](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112203118998.png)

![image-20221112214728265](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112214728265.png)

![image-20221112214739967](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112214739967.png)

![image-20221112215148446](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221112215148446.png)













## webform

```
        <asp:Repeater ID="Repeater1" runat="server">
```

里面`HeaderTemplate`和`ItemTemplate`和`AlternatingItemTemplateAlternatingItemTemplate`和`FooterTemplate`

使用`<%#Eval ("sno") %>`进行绑定数据



在进行数据库连接时

先导入类：

```
using System.Data;
using System.Data.OleDb;
```

模板：

```asp
//连接
OledbCoonection  coon =new OledbConnection("provider=microsoft.ace.oledb.12.0;data source="+Server.MapPath="app_data//stu.accdb");
//命令
String sql="";
OledbCommand cmd=new OledbCommand(sql,coon);
//桥梁
OledbDataAdapter adp=new OledbDataAdapter(cmd);
//虚拟数据库
DataSet ds=new DataSet();
//填充
adp.Fill(ds,"aaa");
//赋值
Repeater1.DataSource=ds.Tables["aaa"].DefaultView;
//绑定动作
Repeater1.DataBind();
```

##  Repeater与GridView区别

1、Repeater 控件

用于显示被绑定在该控件上的项目的重复列表。
Repeater 控件可被绑定到数据库表、XML 文件或者其他项目列表

2、GridView 控件

这个控件相对来说更熟悉一点，重构合作的时候都会用到；

优点：功能强大，提供分页，编辑，删除，选择等功能，使用方便，直接拖拽到需要使用的界面上，建立新的数据源，设置相对应（按照自我需求）的属性，就能够进行数据的操作，而且还不用费劲的进行分页；

不足：模板已经定制好，不如Repeater使用灵活；



加载时自动注焦`TextBox1.Focus();`



取前8条数据：`select top 8 * from message_ss`



`IsPostBack()`是判断是否是第一加载，因为又是点击控件会重新加载，因此，通过if语句来避免再次尽心加载



在使用类时，需要进行实例化`data_operate mydo = new data_operate();`



在类中进行数据库连接时，Sever不能使用，因此MapPath()就报废了，此时：

`data source=|DataDirectory|jsj.accdb`



只显示日期：`<span><%#Eval ("messages_datetime","{0:d}")%>`



aspx.cs中使用类对象，把sql语句给类，类返回一个表`DataTable`可以赋值给DataSource，赋值后再使用DataBind()进行绑定







转换成动态网站后就不能直接点击list1等aspx文件，因为这样会得不到参数，就会运行失败

![image-20221125165307123](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221125165307123.png)

![image-20221125174729439](https://cdn.jsdelivr.net/gh/yzk656/image/image-20221125174729439.png)

