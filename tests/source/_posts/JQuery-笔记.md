---
title: JQuery异步请求

copyright: true
date: 2020-6-8 12:15:15

toc: true
tags: [ajax,JQuery]
categories: [网页技术,JavaScript-JQuery]
declare: true


---



## JQuery 异步请求

### 1.引言

#### 1.1 jQuery概述

> jQuery是一个快速、简洁的JavaScript代码库。jQuery设计的宗旨是“Write Less，Do More”，即倡导写更少的代码，做更多的事情。它封装JavaScript常用的功能代码，提供一种简便的JavaScript操作方式，优化HTML文档操作、事件处理、动画设计和Ajax交互。

#### 1.2 jQuery特点

> - 具有独特的链式语法。
> - 支持高效灵活的CSS选择器。
> - 拥有丰富的插件。
> - 兼容各种主流浏览器，如IE 6.0+、FF 1.5+、Safari 2.0+、Opera 9.0+等。

#### 1.3 为什么要用jQuery

> - 目前网络上有大量开源的 JS 框架, 但是 jQuery 是目前最流行的 JS 框架，而且提供了大量的扩展。很多大公司都在使用 jQuery， 例如：Google、Microsoft、IBM、Netflix

<!--more--> 

### 2.下载导入

#### 2.1官网下载

 从官网下载 jQuery 库：https://jquery.com/download/ 

导入（/web/js目录下）:

```html
<head>
	<script src="jquery-1.12.2.min.js"></script>
</head>
```

#### 2.2 CDN引用

##### 2.2.1 什么是CDN？

> CDN的全称是Content Delivery Network，即[内容分发网络](https://baike.baidu.com/item/内容分发网络/4034265) , 使用户就近获取所需内容，降低网络拥塞，**提高用户访问响应速度和命中率**。

##### 2.2.2 官网

 官网： 

```html
<script src="https://code.jquery.com/jquery-3.5.1.min.js"></script> 
```

##### 2.2.3常见 CDN

> 百度 CDN

```html
<head>
	<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js">
	</script>
</head>
```

> 新浪 CDN

```html
<head>
	<script src="http://lib.sinaapp.com/js/jquery/2.0.2/jquery-2.0.2.min.js">
	</script>
</head>
```

> Google CDN

```html
<head>
	<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js">
	</script>
</head>
```

> Microsoft CDN

```html
<head>
	<script src="http://ajax.htmlnetcdn.com/ajax/jQuery/jquery-1.10.2.min.js">
	</script>
</head>
```

#### 2.3 JQuery 命名冲突解决

多个JS库很有可能会导致 jQuery 命名冲突，解决办法：

```html
var jq=$.noConflict(); // 使用自定义的名称：比如 jq 来代替 $ 符号。
```

### 3、jQuery语法【`重点`】

#### 3.1 基本使用

> + [$(匿名函数)]()：表示页面DOM加载完毕，则执行，比onload事件执行早，并且可以写多个。$是jQuery函数的简写。

```html
<body>
	 <script>
    	$(function(){  alert("欢迎使用jQuery1");   });
        $(function(){  alert("欢迎使用jQuery2");   })
     </script>
</body>
```

> -  [$(selector).action()]()：通过选取 HTML 元素，并对选取的元素执行某些操作。
>    - 选择符（selector）表示"查找" HTML 元素
>    - jQuery 的 action() 执行对元素的操作

```html
- $(this).hide() - 隐藏当前元素
- $("p").hide() - 隐藏所有 <p> 元素
- $("p.test").hide() - 隐藏所有 class="test" 的 <p> 元素
- $("#test").hide() - 隐藏所有 id="test" 的元素
<html>
  <head>
     <script src="jquery-1.12.2.min.js"></script>
  </head>
</html>
<body>	
     <p>窗前明月光</p>
     <p>疑是地上霜</p>
     <p>举头望明月</p>
     <p>低头思故乡</p>
	 <script>
    	$("p").hide();
        $("p.test").hide(); 
		$("#test").hide();
     </script>
</body>
```

#### 3.2 jQuery选择器

 参考手册：https://www.w3school.com.cn/jquery/jquery_ref_selectors.asp 

> - 元素选择器：jQuery 元素选择器基于元素名选取元素。

**基本选择器**：

- id选择器：`$("#id");`
- 类选择器：`$(".className");`
- 标签选择器：`$("标签名");`
- 通配符选择器：`$("*");`

**② 层次选择器**：
从父子关系和胸弟关系来进行选择页面节点。

- `$("a b");` a节点的所有后代节点b都被选中
- `$("a > b");` a节点的所有子节点b都被选中
- `$("a + b");` a节点之后的第一个胸弟节点b
- `$("a ~ b");` a节点之后的所有胸弟节点b

**③ 过滤选择器**：
【基本过滤】从位置的角度来对页面的标签进行过滤选择。

- `$("tagName:first");` 选择第一个tagName标签
- `$("tagName:last");` 选择最后一个tagName标签
- `$("tagName:eq(2)");` 选择脚标为2的tagName标签
- `$("tagName:gt(2)");` 选择脚标大于2的tagName标签
- `$("tagName:lt(2)");` 选择脚标小于2的tagName标签

【内容过滤】节点值是否为空，节点值是否包含指定的字符串。

- `$("tagName:empty");` tagName节点中没有子元素(文本元素,其他子元素)
- `$("tagName:contains('aaa')");` tagName节点是否包含指定字符串
- `$("tagName:has(.one)");` tagName节点是否包含class为one的tagName元素

【属性过滤】从节点的属性来过滤筛选节点:有无属性,属性值等于,不等于,包含,多重过滤。

- `$("tagName[id]")` :tagName节点是否包含id属性
- `$("tagName[id='cc']")` : tagName节点属性值是否为cc
- `$("tagName[id!='cc']")` :tagName节点属性值是否不为cc
- `$("tagName[id^='cc']")` :tagName节点属性值是否以cc为开头
- `$("tagName[id$='cc']")` :tagName节点属性值是否以cc为结尾
- `$("tagName[title*='cc']")` :tagName节点属性值是否包含cc
- `$("tagName[title*='cc'][name='ee'][id!='ff']")` : tagName节点属性值title是否包含cc,属性值name是否为ee,id属性是否不是ff

> 属性过滤的下标从 0 开始，因为拿到的是个数组。

【子元素过滤】选择父元素下的子元素(第1个,最后1个,第几个子元素) 。语法中的空格不能少。

- `$("tagName :first‐child")` :tagName节点下的第一个子节点
- `$("tagName :last‐child")` :tagName节点下的最后一个子节点
- `$("tagName :nth‐child(2)")` :tagName节点下的第二个子节点
- `$("tagName :only-child")` :tagName如果只有一个子元素，就选中该子元素

> tagName 后的空格不能少； 子元素过滤器下标从 1 开始；



> - 示例：在页面中选取所有 <p> 元素

```javascript
$(document).ready(function(){
  $("button").click(function(){
    $("p").hide();
  });
});
```

> -  id选择器：jQuery #id 选择器通过 HTML 元素的 id 属性选取指定的元素。
>
> -  页面中元素的 id 应该是唯一的，所以您要在页面中选取唯一的元素需要通过 #id 选择器。通过 id 选取元素语法如下：

```javascript
$(document).ready(function(){
  $("button").click(function(){
    $("#test").hide();
  });
});
```

> - class选择器：jQuery 类选择器可以通过指定的 class 查找元素。
>
> - 语法如下：

```javascript
$(document).ready(function(){
  $("button").click(function(){
    $(".test").hide();
  });
});
```

#### 3.3 jQuery事件及常用事件方法

 参考手册：https://www.w3school.com.cn/jquery/jquery_ref_events.asp 

jQuery 是为处理 HTML 事件而特别设计的，更恰当且更易维护的代码规则：

- 所有 jQuery 代码置于事件处理函数中；
- 所有事件处理函数置于文档就绪事件处理器中；
- jQuery 代码置于单独的 .js 文件中；
- 如果存在名称冲突，则重命名 jQuery 库。

> - 什么是事件？
>   - 页面对不同访问者的响应叫做事件。
> - 事件处理程序指的是当 HTML 中发生某些事件时所调用的方法。
> - 实例：
>   - 在元素上移动鼠标。
>   - 选取单选按钮
> - 点击元素：在事件中经常使用术语"触发"（或"激发"）例如： "当您按下按键时触发 keypress 事件"。
>   常见 DOM 事件：

| 鼠标事件   | 键盘事件 | 表单事件 | 文档/窗口事件 |
| ---------- | -------- | -------- | ------------- |
| click      | keypress | submit   | load          |
| dblclick   | keydown  | change   | resize        |
| mouseenter | keyup    | focus    | scroll        |
| mouseleave |          | blur     | unload        |

> - ######  jQuery 事件方法语法：
>
>
> - 在 jQuery 中，大多数 DOM 事件都有一个等效的 jQuery 方法。
>   - 页面中指定一个点击事件：

```javascript
$("p").click();
```

> 下一步是定义什么时间触发事件。您可以通过一个事件函数实现：

```javascript
$("p").click(function(){
    // 动作触发后执行的代码!!
});
```

+ [总结：也就是说，不传参数是点击，传参数是设置事件。]()

> - 常用的 jQuery 事件方法
> - $(document).ready() 方法允许我们在文档完全加载完后执行函数。该事件方法在 [jQuery 语法](http://www.runoob.com/jquery/jquery-syntax.html) 章节中已经提到过。

> - click()：当按钮点击事件被触发时会调用一个函数。
> - 该函数在用户点击 HTML 元素时执行。

在下面的实例中，当点击事件在某个 <p> 元素上触发时，隐藏当前的 <p> 元素：

```javascript
$("p").click(function(){
  $(this).hide();
});
```

> - dblclick()：当双击元素时，会发生 dblclick 事件。
>
> - dblclick() 方法触发 dblclick 事件，或规定当发生 dblclick 事件时运行的函数：

```javascript
$("p").dblclick(function(){
  $(this).hide();
});
```

> - mouseenter()：当鼠标指针穿过元素时，会发生 mouseenter 事件。
> - mouseenter() 方法触发 mouseenter 事件，或规定当发生 mouseenter 事件时运行的函数：

```javascript
$("#p1").mouseenter(function(){
    alert('您的鼠标移到了 id="p1" 的元素上!');
});
```

> - mouseleave()：当鼠标指针离开元素时，会发生 mouseleave 事件。
>
> - mouseleave() 方法触发 mouseleave 事件，或规定当发生 mouseleave 事件时运行的函数：

```javascript
$("#p1").mouseleave(function(){
    alert("再见，您的鼠标离开了该段落。");
});
```

> - mousedown()：当鼠标指针移动到元素上方，并按下鼠标按键时，会发生 mousedown 事件。
>
> - mousedown() 方法触发 mousedown 事件，或规定当发生 mousedown 事件时运行的函数：

```javascript
$("#p1").mousedown(function(){
    alert("鼠标在该段落上按下！");
});
```

> - mouseup()：当在元素上松开鼠标按钮时，会发生 mouseup 事件。
>
> - mouseup() 方法触发 mouseup 事件，或规定当发生 mouseup 事件时运行的函数：

```javascript
$("#p1").mouseup(function(){
    alert("鼠标在段落上松开。");
});
```

> - hover()：hover()方法用于模拟光标悬停事件。
>
> - 当鼠标移动到元素上时，会触发指定的第一个函数(mouseenter);当鼠标移出这个元素时，会触发指定的第二个函数(mouseleave)。

```javascript
$("#p1").hover(
    function(){
        alert("你进入了 p1!");
    },
    function(){
        alert("拜拜! 现在你离开了 p1!");
    }
);
```

> - focus()：当元素获得焦点时，发生 focus 事件。
>
> - 当通过鼠标点击选中元素或通过 tab 键定位到元素时，该元素就会获得焦点。
>   focus() 方法触发 focus 事件，或规定当发生 focus 事件时运行的函数：

```javascript
$("input").focus(function(){
  $(this).css("background-color","#cccccc");
});
```

> - blur()：当元素失去焦点时，发生 blur 事件。
>
> - blur() 方法触发 blur 事件，或规定当发生 blur 事件时运行的函数：

```javascript
$("input").blur(function(){
  $(this).css("background-color","#ffffff");
});
```

#### 3.4 **JS 与 jQuery 事件对比**：

```html
<script>
    // js 事件方式一
    function fn1() {
        alert("点击111");
    }
    window.onload = function () {
        // js 事件方式二
        document.getElementById("btn1").onclick = function () {
            alert("点击222");
        };
        // jQuery 事件
        $("#btn2").click(function () {
            alert("点击333");
        });
    }
</script>
<button onclick="fn1()">点击1</button>
<button id="btn1">点击2</button>
<button id="btn2">点击3</button>
```

**jQuery 事件绑定的两种方式**：

```html
<script>
    $(function () { // 监听页面加载完成
        // jQuery 事件绑定方式1
        $("#btn1").click(function () {
            console.log("点击111！！！");
        });
        // jQuery 事件绑定方式2
        $("#btn2").bind("click", function () {
           console.log("点击222！！！")
        });
    });
</script>
```

**监听页面加载完成**：

```html
<script>
    // js 方式
    window.onload = function () {
        // 页面加载完成操作
    };

    // jQuery方式
    $(document).ready(function () {
        // 页面加载完成操作
    });

    // jQuery简化
    $(function () {
        // 页面加载完成操作
    });
</script>
```

使用：`输入框的获取/失去焦点默认值点击事件`

```html
<script>
    $(function () {
        var username = $("#username");
        username.focus(function () {
            console.log("默认值时，获取焦点，置空");
            if (username.attr("placeholder") === "请输入用户名") {
                username.attr("placeholder", "");
            }
        });

        username.blur(function () {
            console.log("空时，失去焦点，设值默认值");
            if (username.attr("placeholder") === "") {
                username.attr("placeholder", "请输入用户名");
            }
        });
    });
</script>
<input type="text" name="username" id="username" placeholder="请输入用户名">
```

### 四、jQuery效果

---

#### 4.1 隐藏显示

> hide()：可以使用 hide() 将元素隐藏

```javascript
$("#hide").click(function(){
  $("p").hide();
});
```

> show()： 您可以使用show()将元素显示

```javascript
$("#show").click(function(){
  $("p").show();
});
```

> - toggle()：通过 jQuery，您可以使用 toggle() 方法来切换 hide() 和 show() 方法。
> - 显示被隐藏的元素，并隐藏已显示的元素。

```javascript
$("button").click(function(){
  $("p").toggle();
});
```

> 事实上，这三种方法都是有两个参数的：

```javascript
$(selector).hide(speed,callback);
$(selector).show(speed,callback);
$(selector).toggle(speed,callback);
```

> - 可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。
>
> - 可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

#### 4.2 淡入淡出

> - 通过 jQuery，您可以实现元素的淡入淡出效果。
> - jQuery 拥有下面四种 fade 方法：
>   - fadeIn()
>   - fadeOut()
>   - fadeToggle()
>   - fadeTo()

> jQuery fadeIn() 方法：jQuery fadeIn() 用于淡入已隐藏的元素。

```javascript
$(selector).fadeIn(speed,callback);
```

> - 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。.
>
> - 可选的 callback 参数是 fading 完成后所执行的函数名称。
> - 下面的例子演示了带有不同参数的 fadeIn() 方法：

```javascript
$("button").click(function(){
  $("#div1").fadeIn();
  $("#div2").fadeIn("slow");
  $("#div3").fadeIn(3000);
});
```

> jQuery fadeOut() 方法用于淡出可见元素。

```javascript
$(selector).fadeOut(speed,callback);
```

> - 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> - 可选的 callback 参数是 fading 完成后所执行的函数名称。
> - 下面的例子演示了带有不同参数的 fadeOut() 方法：

```javascript
$("button").click(function(){
  $("#div1").fadeOut();
  $("#div2").fadeOut("slow");
  $("#div3").fadeOut(3000);
});
```

> - jQuery fadeToggle() 方法可以在 fadeIn() 与 fadeOut() 方法之间进行切换。
>
> - 如果元素已淡出，则 fadeToggle() 会向元素添加淡入效果。
> - 如果元素已淡入，则 fadeToggle() 会向元素添加淡出效果。

```javascript
$(selector).fadeToggle(speed,callback);
```

> - 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> - 可选的 callback 参数是 fading 完成后所执行的函数名称。
> - 下面的例子演示了带有不同参数的 fadeToggle() 方法：

```javascript
$("button").click(function(){
  $("#div1").fadeToggle();
  $("#div2").fadeToggle("slow");
  $("#div3").fadeToggle(3000);
});
```

> jQuery fadeTo() 方法允许渐变为给定的不透明度（值介于 0 与 1 之间）。

```javascript
$(selector).fadeTo(speed,opacity,callback);
```

> - 必需的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> - fadeTo() 方法中必需的 opacity 参数将淡入淡出效果设置为给定的不透明度（值介于 0 与 1 之间）。
> - 可选的 callback 参数是该函数完成后所执行的函数名称。
> - 下面的例子演示了带有不同参数的 fadeTo() 方法：

```javascript
$("button").click(function(){
  $("#div1").fadeTo("slow",0.15);
  $("#div2").fadeTo("slow",0.4);
  $("#div3").fadeTo("slow",0.7);
});
```

#### 4.3 滑动

> - 通过 jQuery，您可以在元素上创建滑动效果。jQuery 拥有以下滑动方法：
>   - slideDown()
>   - slideUp()
>   - slideToggle()
> - jQuery slideDown() 方法用于向下滑动元素。

```javascript
$(selector).slideDown(speed,callback);
```

> - 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> - 可选的 callback 参数是滑动完成后所执行的函数名称。
>
> - 下面的例子演示了 slideDown() 方法：

```javascript
$("#flip").click(function(){
  $("#panel").slideDown();
});
```

> jQuery slideUp() 方法用于向上滑动元素。

```javascript
$(selector).slideUp(speed,callback);
```

> - 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> - 可选的 callback 参数是滑动完成后所执行的函数名称。
>
> - 下面的例子演示了 slideUp() 方法：

```javascript
$("#flip").click(function(){
  $("#panel").slideUp();
});
```

> - jQuery slideToggle() 方法可以在 slideDown() 与 slideUp() 方法之间进行切换。
>
> - 如果元素向下滑动，则 slideToggle() 可向上滑动它们。
>
> - 如果元素向上滑动，则 slideToggle() 可向下滑动它们。

```javascript
$(selector).slideToggle(speed,callback);
```

> - 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> - 可选的 callback 参数是滑动完成后所执行的函数名称。
>
> - 下面的例子演示了 slideToggle() 方法：

```javascript
$("#flip").click(function(){
  $("#panel").slideToggle();
});
```

#### 4.4 动画

> animate() 方法：jQuery animate() 方法用于创建自定义动画。

```javascript
$(selector).animate({params},speed,callback);
```

> - 必需的 params 参数定义形成动画的 CSS 属性。
>
> - 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> - 可选的 callback 参数是动画完成后所执行的函数名称。
>
> - 下面的例子演示 animate() 方法的简单应用。它把 <div> 元素往右边移动了 250 像素：

```javascript
$("button").click(function(){
  $("div").animate({left:'250px'});
});
```

> -  操作多个属性
>
> -  请注意，生成动画的过程中可同时使用多个属性：

```javascript
$("button").click(function(){
  $("div").animate({
    left:'250px',
    opacity:'0.5',
    height:'150px',
    width:'150px'
  });
});
```

> - 可以用 animate() 方法来操作所有 CSS 属性吗？
>
> - 是的，几乎可以！不过，需要记住一件重要的事情：当使用 animate() 时，必须使用 Camel 标记法书写所有的属性名，比如，必须使用 paddingLeft 而不是 padding-left，使用 marginRight 而不是 margin-right，等等。
>
> - 同时，色彩动画并不包含在核心 jQuery 库中。
>
> - 如果需要生成颜色动画，您需要从 [jquery.com](http://jquery.com/download/) 下载 [颜色动画](http://plugins.jquery.com/color/) 插件。
>
> - 也可以定义相对值（该值相对于元素的当前值）。需要在值的前面加上 += 或 -=：

```javascript
$("button").click(function(){
  $("div").animate({
    left:'250px',
    height:'+=150px',
    width:'+=150px'
  });
});
```

> 预定义的值：您甚至可以把属性的动画值设置为 "show"、"hide" 或 "toggle"：

```javascript
$("button").click(function(){
  $("div").animate({
    height:'toggle'
  });
});
```

> - 使用队列功能：默认地，jQuery 提供针对动画的队列功能。
>
> - 这意味着如果您在彼此之后编写多个 animate() 调用，jQuery 会创建包含这些方法调用的"内部"队列。然后逐一运行这些 animate 调用。

```javascript
$("button").click(function(){
  var div=$("div");
  div.animate({height:'300px',opacity:'0.4'},"slow");
  div.animate({width:'300px',opacity:'0.8'},"slow");
  div.animate({height:'100px',opacity:'0.4'},"slow");
  div.animate({width:'100px',opacity:'0.8'},"slow");
});
```

> 下面的例子把 <div> 元素往右边移动了 100 像素，然后增加文本的字号：

```javascript
$("button").click(function(){
  var div=$("div");
  div.animate({left:'100px'},"slow");
  div.animate({fontSize:'3em'},"slow");
});
```

#### 4.5 停止动画

> - jQuery stop() 方法用于停止动画或效果，在它们完成之前。
>
> - stop() 方法适用于所有 jQuery 效果函数，包括滑动、淡入淡出和自定义动画。

```javascript
$(selector).stop(stopAll,goToEnd);
```

> - 可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。
>
> - 可选的 goToEnd 参数规定是否立即完成当前动画。默认是 false。
>
> - 因此，默认地，stop() 会清除在被选元素上指定的当前动画。
>
> - 下面的例子演示 stop() 方法，不带参数：

```javascript
$("#stop").click(function(){
  $("#panel").stop();
});
```

#### 4.6 Callback

> - 许多 jQuery 函数涉及动画。这些函数也许会将 *speed* 或 *duration* 作为可选参数。
>
> - 例子：*$("p").hide("slow")*
>
> - speed* 或 *duration* 参数可以设置许多不同的值，比如 "slow", "fast", "normal" 或毫秒。

```javascript
$("button").click(function(){
  $("p").hide("slow",function(){
    alert("段落现在被隐藏了");
  });
});
```

> 以下实例没有回调函数，警告框会在隐藏效果完成前弹出：

```javascript
$("button").click(function(){
  $("p").hide(1000);
  alert("段落现在被隐藏了");
});
```

#### 4.7 链式编程

> - 直到现在，我们都是一次写一条 jQuery 语句（一条接着另一条）。
>
> - 不过，有一种名为链接（chaining）的技术，允许我们在相同的元素上运行多条 jQuery 命令，一条接着另一条。
>
> - **提示：** 这样的话，浏览器就不必多次查找相同的元素。
> - 如需链接一个动作，您只需简单地把该动作追加到之前的动作上。
>
> - 下面的例子把 css()、slideUp() 和 slideDown() 链接在一起。"p1" 元素首先会变为红色，然后向上滑动，再然后向下滑动：

```javascript
$("#p1").css("color","red").slideUp(2000).slideDown(2000);
```

> - 如果需要，我们也可以添加多个方法调用。
>
> - **提示：**当进行链接时，代码行会变得很差。不过，jQuery 语法不是很严格；您可以按照希望的格式来写，包含换行和缩进。
>
> - 如下书写也可以很好地运行：

```javascript
$("#p1").css("color","red")
  .slideUp(2000)
  .slideDown(2000);
```

### 五、 jQuery DOM操作【`重点`】

---

#### 5.1 捕获

> - jQuery 拥有可操作 HTML 元素和属性的强大方法。
> - jQuery 中非常重要的部分，就是操作 DOM 的能力。
> - jQuery 提供一系列与 DOM 相关的方法，这使访问和操作元素和属性变得很容易。
> - 三个简单实用的用于 DOM 操作的 jQuery 方法：
>   - text() - 设置或返回所选元素的文本内容
>   - html() - 设置或返回所选元素的内容（包括 HTML 标记）
>   - val() - 设置或返回表单字段的值
> - 下面的例子演示如何通过 jQuery text() 和 html() 方法来获得内容：



> -  内容操作： 
>   - `.html("html content")` : 设置/获取标签内容，解析 html 标签，相当于 .innerHTML
>   - `.text("text content")` : 设置/获取标签内容，不解析 html 标签，相当于 .innerText
>   - `.val(string)` : 多用于 input 元素，设置/获取 value 属性，相当于 .value
> - 属性操作：
>   - `.attr("属性名", "属性值")` : 获取/设置元素的属性，相当于 .setAttribute()
>   - `.removeAttr("属性名")` : 删除属性，相当于 .removeAttirbute()
>
>  使用：`获取第2个li节点的title属性和文本内容` 

```javascript
<script>
    // 获取第2个 li 的 title 属性值
    function getTitle1() {
        // 基本过滤器：下标取值
        alert( $("li:eq(1)").attr("title") );
    }
    function getTitle2() {
        // 子元素过滤器：子元素下标
        alert( $("ul :nth-child(2)").attr("title") );
    }
    // 获取第 2 个 li 的文本内容
    function getText() {
        alert( $("li:eq(1)").html() );
    }
</script>
<ul>
    <li title="xg">西瓜</li>
    <li title="hmg">哈密瓜</li>
    <li title="hfl">黑凤梨</li>
</ul>
<br>
<button onclick="getTitle1()">获取1</button>
<button onclick="getTitle2()">获取2</button>
<button onclick="getText()">获取3</button>
```

#### 5.2 设置

> - 我们将使用前一章中的三个相同的方法来设置内容：
>   - text() - 设置或返回所选元素的文本内容
>   - html() - 设置或返回所选元素的内容（包括 HTML 标记）
>   - val() - 设置或返回表单字段的值
> - 下面的例子演示如何通过 text()、html() 以及 val() 方法来设置内容：

```javascript
$("#btn1").click(function(){
    $("#test1").text("Hello world!");
});
$("#btn2").click(function(){
    $("#test2").html("<b>Hello world!</b>");
});
$("#btn3").click(function(){
    $("#test3").val("Hello world!");
});
```

> - 上面的三个 jQuery 方法：text()、html() 以及 val()，同样拥有回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。
>
> - 下面的例子演示带有回调函数的 text() 和 html()：

```javascript
$("#btn1").click(function(){
    $("#test1").text(function(i,origText){
        return "旧文本: " + origText + " 新文本: Hello world! (index: " + i + ")"; 
    });
});
 
$("#btn2").click(function(){
    $("#test2").html(function(i,origText){
        return "旧 html: " + origText + " 新 html: Hello <b>world!</b> (index: " + i + ")"; 
    });
});
```

> - jQuery attr() 方法也用于设置/改变属性值。
>
> - 下面的例子演示如何改变（设置）文本中 color属性的值：

```javascript
$("button").click(function(){
  $("#font1").attr("color","red");
});
```

#### 5.3 添加元素

> - 我们将学习用于添加新内容的四个 jQuery 方法：
>   - append() - 在被选元素的结尾插入内容
>   - prepend() - 在被选元素的开头插入内容
>   - after() - 在被选元素之后插入内容
>   - before() - 在被选元素之前插入内容
> - jQuery append() 方法在被选元素的结尾插入内容。

```javascript
$("p").append("追加文本");
```

> jQuery prepend() 方法在被选元素的开头插入内容。

```javascript
$("p").prepend("v文本");
```

> - 在上面的例子中，我们只在被选元素的开头/结尾插入文本/HTML。
>
> - 不过，append() 和 prepend() 方法能够通过参数接收无限数量的新元素。可以通过 jQuery 来生成文本/HTML（就像上面的例子那样），或者通过 JavaScript 代码和 DOM 元素。
>
> - 在下面的例子中，我们创建若干个新元素。这些元素可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建。然后我们通过 append() 方法把这些新元素追加到文本中（对 prepend() 同样有效）：

```javascript
function appendText()
{
    var txt1="<p>文本。</p>";              // 使用 HTML 标签创建文本
    var txt2=$("<p></p>").text("文本。");  // 使用 jQuery 创建文本
    var txt3=document.createElement("p");
    txt3.innerHTML="文本。";               // 使用 DOM 创建文本 text with DOM
    $("body").append(txt1,txt2,txt3);        // 追加新元素
}
```

> - jQuery after() 方法在被选元素之后插入内容。
>
> - jQuery before() 方法在被选元素之前插入内容。

```javascript
$("img").after("在后面添加文本");
 
$("img").before("在前面添加文本");
```

> - after() 和 before() 方法能够通过参数接收无限数量的新元素。可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建新元素。
>
> - 在下面的例子中，我们创建若干新元素。这些元素可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建。然后我们通过 after() 方法把这些新元素插到文本中（对 before() 同样有效）：

```javascript
function afterText()
{
    var txt1="<b>I </b>";                    // 使用 HTML 创建元素
    var txt2=$("<i></i>").text("love ");     // 使用 jQuery 创建元素
    var txt3=document.createElement("big");  // 使用 DOM 创建元素
    txt3.innerHTML="jQuery!";
    $("img").after(txt1,txt2,txt3);          // 在图片后添加文本
}
```

#### 5.4 删除元素

> - 如需删除元素和内容，一般可使用以下两个 jQuery 方法：
>   - remove() - 删除被选元素（及其子元素）
>   - empty() - 从被选元素中删除子元素

```javascript
$("#div1").remove();
$("#div1").empty();
```

> - jQuery remove() 方法也可接受一个参数，允许您对被删元素进行过滤。
>
> - 该参数可以是任何 jQuery 选择器的语法。
>
> - 下面的例子删除 class="italic" 的所有 <p> 元素：

```javascript
$("p").remove(".italic");
```

#### 5.5 CSS类

> - jQuery 拥有若干进行 CSS 操作的方法。我们将学习下面这些：
>   - addClass() - 向被选元素添加一个或多个类
>   - removeClass() - 从被选元素删除一个或多个类
>   - toggleClass() - 对被选元素进行添加/删除类的切换操作
>   - css() - 设置或返回样式属性
> - 下面的样式表将用于本页的所有例子：

```css
.important
{
    font-weight:bold;
    font-size:xx-large;
}
.blue
{
	color:blue;
}
```

> 下面的例子展示如何向不同的元素添加 class 属性。当然，在添加类时，您也可以选取多个元素：

```javascript
$("button").click(function(){
  $("h1,h2,p").addClass("blue");
  $("div").addClass("important");
});
```

> 您也可以在 addClass() 方法中规定多个类：

```javascript
$("button").click(function(){
  $("body div:first").addClass("important blue");
});
```

> 下面的例子演示如何在不同的元素中删除指定的 class 属性：

```javascript
$("button").click(function(){
  $("h1,h2,p").removeClass("blue");
});
```

> 下面的例子将展示如何使用 jQuery toggleClass() 方法。该方法对被选元素进行添加/删除类的切换操作：

```javascript
$("button").click(function(){
  $("h1,h2,p").toggleClass("blue");
});
```

#### 5.6 css()方法

> - css() 方法设置或返回被选元素的一个或多个样式属性。
>
> - 如需返回指定的 CSS 属性的值，请使用如下语法：

```javascript
css("propertyname");
```

> 下面的例子将返回首个匹配元素的 background-color 值：

```javascript
$("p").css("background-color");
```

> 如需设置指定的 CSS 属性，请使用如下语法：

```javascript
css("propertyname","value");
```

> 下面的例子将为所有匹配元素设置 background-color 值：

```javascript
$("p").css("background-color","yellow");
```

> 如需设置多个 CSS 属性，请使用如下语法：

```javascript
css({"propertyname":"value","propertyname":"value",...});
```

> 下面的例子将为所有匹配元素设置 background-color 和 font-size：

```javascript
$("p").css({"background-color":"yellow","font-size":"200%"});
```

#### 5.7 尺寸

> - jQuery 提供多个处理尺寸的重要方法：
>   - width()	
>   - height()
>   - innerWidth()
>   - innerHeight()
>   - outerWidth()
>   - outerHeight()

|         尺寸         |
| :------------------: |
| ![1](Pictures/1.png) |



> - width() 方法设置或返回元素的宽度（不包括内边距、边框或外边距）。
>
> - height() 方法设置或返回元素的高度（不包括内边距、边框或外边距）。
>
> - 下面的例子返回指定的 &lt;div&gt; 元素的宽度和高度：

```javascript
$("button").click(function(){
  var txt="";
  txt+="div 的宽度是: " + $("#div1").width() + "</br>";
  txt+="div 的高度是: " + $("#div1").height();
  $("#div1").html(txt);
});
```

> - innerWidth() 方法返回元素的宽度（包括内边距）。
>
> - innerHeight() 方法返回元素的高度（包括内边距）。
>
> - 下面的例子返回指定的 &lt;div&gt; 元素的 inner-width/height：

```javascript
$("button").click(function(){
  var txt="";
  txt+="div 宽度，包含内边距: " + $("#div1").innerWidth() + "</br>";
    txt+="div 高度，包含内边距: " + $("#div1").innerHeight();
  $("#div1").html(txt);
});
```

> - outerWidth() 方法返回元素的宽度（包括内边距和边框）。
>
> - outerHeight() 方法返回元素的高度（包括内边距和边框）。
>
> - 下面的例子返回指定的 &lt;div&gt; 元素的 outer-width/height：

```javascript
$("button").click(function(){
  var txt="";
  txt+="div 宽度，包含内边距和边框: " + $("#div1").outerWidth() + "</br>";
  txt+="div 高度，包含内边距和边框: " + $("#div1").outerHeight();
  $("#div1").html(txt);
});
```

### 六、jQuery遍历

---

 参考手册：https://www.w3school.com.cn/jquery/jquery_ref_traversing.asp 

#### 6.1 遍历

> - jQuery 遍历，意为"移动"，用于根据其相对于其他元素的关系来"查找"（或选取）HTML 元素。以某项选择开始，并沿着这个选择移动，直到抵达您期望的元素为止。
>
> - 下图展示了一个家族树。通过 jQuery 遍历，您能够从被选（当前的）元素开始，轻松地在家族树中向上移动（祖先），向下移动（子孙），水平移动（同胞）。这种移动被称为对 DOM 进行遍历。

#### 6.2 祖先 jQuery parent() 方法

> - parent() 方法返回被选元素的直接父元素。
>
> - 该方法只会向上一级对 DOM 树进行遍历。
>
> - 下面的例子返回每个 span 元素的直接父元素：

```javascript
$(document).ready(function(){
  $("span").parent();
});
```

> - parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (html)。
>
> - 下面的例子返回所有 span 元素的所有祖先：

```javascript
$(document).ready(function(){
  $("span").parents();
});
```

> - 您也可以使用可选参数来过滤对祖先元素的搜索。
>
> - 下面的例子返回所有 span  元素的所有祖先，并且它是 url 元素：

```javascript
$(document).ready(function(){
  $("span").parents("ul");
});
```

> - parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。
>
> - 下面的例子返回介于 span  与 di v 元素之间的所有祖先元素：

```javascript
$(document).ready(function(){
  $("span").parentsUntil("div");
});
```

#### 6.3 后代 jQuery children() 方法

> - children() 方法返回被选元素的所有直接子元素。
>
> - 该方法只会向下一级对 DOM 树进行遍历。
>
> - 下面的例子返回每个div 元素的所有直接子元素：

```javascript
$(document).ready(function(){
  $("div").children();
});
```

> - 您也可以使用可选参数来过滤对子元素的搜索。
>
> - 下面的例子返回类名为 "a" 的所有 p 元素，并且它们是 div 的直接子元素：

```javascript
$(document).ready(function(){
  $("div").children("p.a");
});
```

> - find() 方法返回被选元素的后代元素，一路向下直到最后一个后代。
>
> - 下面的例子返回属于 div 后代的所有 span 元素：

```javascript
$(document).ready(function(){
  $("div").find("span");
});
```

> 下面的例子返回 div 的所有后代：

```javascript
$(document).ready(function(){
  $("div").find("*");
});
```

#### 6.4 同胞 jQuery siblings() 方法

> - siblings() 方法返回被选元素的所有同胞元素。
>
> - 下面的例子返回 h2 的所有同胞元素：

```javascript
$(document).ready(function(){
  $("h2").siblings();
});
```

> - 您也可以使用可选参数来过滤对同胞元素的搜索。
>
> - 下面的例子返回属于 h2 的同胞元素的所有 p 元素：

```javascript
$(document).ready(function(){
  $("h2").siblings("p");
});
```

> - next() 方法返回被选元素的下一个同胞元素。
>
> - 该方法只返回一个元素。
>
> - 下面的例子返回h2的下一个同胞元素：

```javascript
$(document).ready(function(){
  $("h2").next();
});
```

> - nextAll() 方法返回被选元素的所有跟随的同胞元素。
>
> - 下面的例子返回 h2 的所有跟随的同胞元素：

```javascript
$(document).ready(function(){
  $("h2").nextAll();
});
```

> - nextUntil() 方法返回介于两个给定参数之间的所有跟随的同胞元素。
>
> - 下面的例子返回介于 h2 与 h6 元素之间的所有同胞元素：

```javascript
$(document).ready(function(){
  $("h2").nextUntil("h6");
});
```

> - prev()方法取得一个包含匹配的元素集合中每一个元素紧邻的前一个同辈元素的元素集合
> - 下面的例子返回 h2 的下一个同胞元素

```javascript
$(document).ready(function(){
  $("h2").prev();
});
```

> prevAll() 方法查找当前元素之前所有的同辈元素
>
> prevUntil() 方法查找当前元素之前所有的同辈元素，直到遇到匹配的那个元素为止

#### 6.5 过滤 jQuery first() 方法

> - first() 方法返回被选元素的首个元素。
>
> - 下面的例子选取首个div 元素内部的第一个 p 元素：

```javascript
$(document).ready(function(){
  $("div p").first();
});
```

> - last() 方法返回被选元素的最后一个元素。
>
> - 下面的例子选择最后一个div 元素中的最后一个 p 元素：

```javascript
$(document).ready(function(){
  $("div p").last();
});
```

> - eq() 方法返回被选元素中带有指定索引号的元素。
>
> - 索引号从 0 开始，因此首个元素的索引号是 0 而不是 1。下面的例子选取第二个p 元素（索引号 1）：

```javascript
$(document).ready(function(){
  $("p").eq(1);
});
```

> - filter() 方法允许您规定一个标准。不匹配这个标准的元素会被从集合中删除，匹配的元素会被返回。
>
> - 下面的例子返回带有类名 "url" 的所有p 元素：

```javascript
$(document).ready(function(){
  $("p").filter(".url");
});
```

> - not() 方法返回不匹配标准的所有元素。
>
> - 提示：not() 方法与 filter() 相反。
> - 下面的例子返回不带有类名 "url" 的所有p元素：

```javascript
$(document).ready(function(){
  $("p").not(".url");
});
```

### 七、jQuery AJAX

---

 参考手册：https://www.w3school.com.cn/jquery/jquery_ref_ajax.asp 

- $(selector).**load**(url,data,callback) 把远程数据加载到被选的元素中
- $.**ajax**(options) 把远程数据加载到 XMLHttpRequest 对象中
- $.**get**(url,data,callback,type) 使用 HTTP GET 来加载远程数据
- $.**post**(url,data,callback,type) 使用 HTTP POST 来加载远程数据
- $.**getJSON**(url,data,callback) 使用 HTTP GET 来加载远程 JSON 数据
- $.**getScript**(url,callback) 加载并执行远程的 JavaScript 文件

> 参数说明：
> @selector, jQuery 元素选择器语法
> @url, 被加载的数据的 URL（地址）
> @data, 发送到服务器的数据的键/值对象
> @callback, 当数据被加载时，所执行的函数
> @type, 被返回的数据的类型 (html,xml,json,jasonp,script,text)
> @options, 完整 AJAX 请求的所有键/值对选项

#### 7.1 jQuery AJAX简介

> - AJAX = 异步 JavaScript 和 XML（Asynchronous JavaScript and XML）。
>
> - 简短地说，在不重载整个网页的情况下，AJAX 通过后台加载数据，并在网页上进行显示。
>
> - 使用 AJAX 的应用程序案例：谷歌地图、腾讯微博、优酷视频、人人网等等。

#### 7.2 get和post方法

> $.get() 方法通过 HTTP GET 请求从服务器上请求数据。

```javascript
$.get(URL,callback);
```

> - 必需的 *URL* 参数规定您希望请求的 URL。
>
> - 可选的 *callback* 参数是请求成功后所执行的函数名。
>
> - 下面的例子使用 $.get() 方法从服务器上的一个文件中取回数据：

```javascript
$("button").click(function(){
  $.get("demo_test.php",function(data){
    alert("数据: " + data );
  });
});
```

> - $.post() 方法通过 HTTP POST 请求从服务器上请求数据。
>   - $.post(*URL,data,callback*);
>   - 必需的 *URL* 参数规定您希望请求的 URL。
>   - 可选的 *data* 参数规定连同请求发送的数据。
>   - 可选的 *callback* 参数是请求成功后所执行的函数名。
> - 下面的例子使用 $.post() 连同请求一起发送数据：

```javascript
$("button").click(function(){
    $.post("/try/ajax/demo_test_post.jsp",
    {
        name:"百度",
        url:"http://www.baidu.com"
    },
        function(data){
        alert("数据: \n" + data );
    });
});
```

#### 7.3 ajax()方法

> - jQuery 底层 AJAX 实现。简单易用的高层实现见 $.get, $.post 等。$.ajax() 返回其创建的 XMLHttpRequest  对象。大多数情况下你无需直接操作该函数，除非你需要操作不常用的选项，以获得更多的灵活性。
> - 最简单的情况下，$.ajax()可以不带任何参数直接使用

#### 7.4案例 

Demo：`验证用户名是否存在，给出合适的提示` 

简单步骤

因为要涉及到数据库查询 先需要一个核心对象 

var xhr = new XMLHttpRequest();

这个对象提供了一系列用于 打开请求  发送请求  接收响应等方法 

用于实现 异步刷新的操作

我们要去数据库中查询  前端页面是和控制器连接的 
所以我们现在需要一个控制器路径 

var url = "/StuManage/checkNameServlet?stuName="+stuNameValue;

//1.请求方式 get或者post
//2.请求路径
//3.是否是异步的 true表示异步

xhr.open("get",url,true);
xhr.send();

//onreadystatechange 这个属性表示我们的请求状态码 
回调函数  返回请求所调用的函数
xhr.onreadystatechange = function (){
				//readyState 请求状态码
				//0.表示请求未初始化
				//1.表示与服务器建立连接
				//2.服务器接收请求
				//3.服务器处理请求
				//4.服务器处理请求完成并且响应就绪
          	//status 404 500 505 401 201 200 ok						
			//xhr.readyState == 4 && xhr.status == 200 表示请求处理完成 并且响应ok
		if(xhr.readyState == 4 && xhr.status == 200){
			var resText = xhr.responseText;//接收到控制器返回给我们的字符串 

}

​		

 regist.jsp 

```jsp
<script>
    function checkUsername() {
        var username = $("#username").val();
        // post 异步请求
        $.post("${pageContext.request.contextPath}/checkUsername",{
            "username":username,
        }, function (data) {
            console.log(data);
            if (data.flag) {
                // 用户名可用
                $("#span").html("√ 用户名可用");
                $("button[type='submit']").attr("disabled", false); //使能按钮
            } else {
                $("#span").html("* 用户名已存在");
                $("button[type='submit']").attr("disabled", true); //禁用按钮
            }
        }, "json");
    }
</script>
<form action="${pageContext.request.contextPath}/regist" method="post">
    账户：<input type="text" name="username" id="username" onchange="checkUsername()">
    <span id="span"></span><br>
    密码：<input type="text" name="password" id="password"> <br>
    <button type="submit">注册</button>
</form>
```

 CheckUsernameServlet.java 

```java
@WebServlet(name = "CheckUsernameServlet", urlPatterns = "/checkUsername")
public class CheckUsernameServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        request.setCharacterEncoding("utf-8");
        String username = request.getParameter("username");
        UserService userService = new UserServiceImpl();
        try {
            boolean flag = userService.checkUsername(username);
            String msg = flag ? "用户名可用" : "用户名已存在";
            Map<String, Object> map = new HashMap<>();
            map.put("flag", flag);
            map.put("msg", msg);

            JsonUtils.writeJsonStr(response, map);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doPost(request, response);
    }
}
```

 UserServiceImpl.java 

```java
public class UserServiceImpl implements UserService {
    private UserDao userDao = new UserDaoImpl();
    @Override
    public boolean checkUsername(String username) throws Exception {
        return userDao.checkUsername(username) == null;
    }
}
```



### 八、其他

---

#### 8.1 jQuery noConflict方法

> - 正如您已经了解到的，jQuery 使用 $ 符号作为 jQuery 的简写。
>
> - 如果其他 JavaScript 框架也使用 $ 符号作为简写怎么办？
>
> - 其他一些 JavaScript 框架包括：MooTools、Backbone、Sammy、Cappuccino、Knockout、JavaScript MVC、Google Web Toolkit、Google Closure、Ember、Batman 以及 Ext JS。
>
> - 其中某些框架也使用 $ 符号作为简写（就像 jQuery），如果您在用的两种不同的框架正在使用相同的简写符号，有可能导致脚本停止运行。
>
> - jQuery 的团队考虑到了这个问题，并实现了 noConflict() 方法。
>
> - noConflict() 方法会释放对 $ 标识符的控制，这样其他脚本就可以使用它了。
>
> - 当然，您仍然可以通过全名替代简写的方式来使用 jQuery：

```javascript
$.noConflict();
jQuery(document).ready(function(){
  jQuery("button").click(function(){
    jQuery("p").text("jQuery 仍然在工作!");
  });
});
```

> 您也可以创建自己的简写。noConflict() 可返回对 jQuery 的引用，您可以把它存入变量，以供稍后使用。请看这个例子：

```javascript
var jq = $.noConflict();
jq(document).ready(function(){
  jq("button").click(function(){
    jq("p").text("jQuery 仍然在工作!");
  });
});
```

> 如果你的 jQuery 代码块使用 $ 简写，并且您不愿意改变这个快捷方式，那么您可以把 $ 符号作为变量传递给 ready 方法。这样就可以在函数内使用 $ 符号了 - 而在函数外，依旧不得不使用 "jQuery"：

```
$.noConflict();
jQuery(document).ready(function($){
  $("button").click(function(){
    $("p").text("jQuery 仍然在工作!");
  });
});
```

