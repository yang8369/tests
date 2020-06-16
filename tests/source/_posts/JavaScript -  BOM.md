---
title: BOM浏览器对象模型

copyright: true
date: 2020-6-5 12:15:15

toc: true
tags: [JS,BOM]
categories: [网页技术,JavaScript-BOM]
declare: true

---



## BOM

### 1.BOM基本

bom(Browser Object Model) 浏览器对象模型

浏览器对象模型 把 浏览器 的 各个部分 都用了 一个对象 进行描述，若操作浏览器，则可以通过 浏览器对象模型 的 对象 进行操作

window对象  代表了一个新开的窗口

location对象 代表了地址栏的对象

screen对象  代表了整个屏幕的对象

<!--more--> 

### 2.window对象

document history location frames screen navigator

**常用属性**

- 浏览器窗口尺寸
  innerWidth/innerHeight, //表示浏览器窗口"可视区域"尺寸
  outerWidth/outerHeight //表示整个浏览器窗口的尺寸
- 滚动相关
  - scrollX/scrollY //获取浏览器窗口滚动条滚动过的距离
  - scrollTo(x,y) //指定滚动位置
  - scrollBy(xnum,ynum) //设置基于当前位置滚动的距离，可以为负数

 window**常用方法**

* open("href","_blank","location:no,toolbar=no") 		打开一个新的窗口
  * href  跳转 的 页面 地址 
  * _blank 打开一个新的窗口  或 _self 在自身打开一个窗口
  * location 地址栏  toolbar 工具栏
* resizeTo("height","width")    将窗口的大小改为指定的 **高度** 和 **宽度**
* moveTo("x","y") 将窗口的左上角的 屏幕位置 移动到指定的 x 和 y 位置
  * 基于屏幕左上角为坐标原点  绝对位置
* moveBy("x","y") 相对于原来的窗口移动指定的x、y值。  
  * 基于原窗口的左上角为坐标原点  相对位置

##### **延迟与定时器**

* setInterval("function()",times)    每经过指定毫秒值后就会执行指定的代码
  * 方法名 + 时间 （毫秒）   
* clearTimeout(timeoutID)：清除指定id标识的延迟操作
* clearInterval()        据一个任务的 ID 取消 的 定时任务  
* setTimeout()         经过指定毫秒值后执行指定 的代码**一次**  

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<input type="button"  value="打开一个新的窗口" onclick="TestOpen()"/>
		<input type="button"  value="改变窗口大小" onclick="TestResizeTo()"/>
		<input type="button"  value="移动窗口-绝对" onclick="TestMoveTo()"/>
		<input type="button"  value="移动窗口-相对" onclick="TestMoveBy()"/>
		<input type="button"  value="停止打开新窗口" onclick="TestClearInterval()"/>
	</body>
	<script>
		function TestOpen(){
			window.open("baidu.html","_self","location=no,toolbar=no");
		}
		function TestResizeTo(){
			window.resizeTo("500","500");
		}
		function TestMoveTo(){
			window.moveTo("0","400");
		}
		function TestMoveBy(){
			//window.moveBy("100","200");
			for(var i=0;i<9;i++){
								window.moveBy(50,0);//右移
								window.moveBy(0,50);//下移
								window.moveBy(-50,0);//左移
								window.moveBy(0,-50);//上移
							}

		}
		// var id = window.setInterval("TestOpen()",3000);
        
		// function TestClearInterval(){
		// 	window.clearInterval(id);
		// }
        
		//window.setTimeout("TestOpen()",1000);
		
	</script>
</html>

```

### 3.事件

#### 3.1 事件

事件是可以被JavaScript侦测到的行为。网页中的每个元素都可以产生某些可以触发JavaScript函数的事件

> 格式：节点.on+事件名 = 事件处理函数;

```
div.onclick = function(){}
```

#### 3.2鼠标事件

* 鼠标点击相关
  * onclick  鼠标单机触发的事件
  * ondblclick  鼠标双击触发的事件
  * onmousedown     鼠标按钮被按下。
  * onmouseup  鼠标位于对象上且释放鼠标按钮时
  * onmouseover     鼠标移到某元素之上。
  
  * onmouseout  鼠标指针移除对象边界时
  * onmousemove  鼠标划进对象时触发
  * onmouseenter      在鼠标光标从元素外部移动到元素范围之内时触发。这个事件不冒泡
  * onmouseleave      在位于元素上方的鼠标光标移动到元素范围之外时触发。这个事件不冒泡，
  * oncontextmenu   鼠标右键菜单展开时触发。
  
* 键盘事件

  - onkeydown       某个键盘按键被按下。
  - onkeyup         某个键盘按键被松开。
  - onkeypress      键盘<字符键>被按下,而且如果按住不放的话，会重复触发此事件。

* 表单事件
  * onbluer 对象失去鼠标焦点
  * ondocus 对象获取鼠标焦点
  * onchange 当选中区的内容发生改变的时候
  * onsubmit 表单被提交后触发
  * oninput     输入字符时触发
  * onreset     重置按钮被点击。
  * onselect     输入框文本被选中。
  
* UI事件
  * onresize        窗口或框架被重新调整大小。
  * **onload**  在浏览器完成加载后  立即 触发 
  * onscroll      滚动时触发。

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<!-- onload="testOnload()" -->
	<body  >
			<form onsubmit="testOnsubmit()">
		<span id = "spanNode"></span>
		用户名： <input type = "text" onblur="testOnblur()" onfocus="testOnfocus()" onchange="testOnchange()" />
		<input type="submit" value="提交" />
		</form>
		<select onchange="testOnchange()">
			<option>郑州</option>
			<option>安阳</option>
			<option>重庆</option>
		</select>
		<hr />
		<input type = "button" value = "点击" onclick="testClick()"/>
		<input type = "button" value = "双点击" ondblclick="testDbclick()"/>
		<input type = "button" value = "按下鼠标" onmousedown="testMousedown()"/>
		<input type = "button" value = "释放鼠标" onmouseup="testMouseup()"/>
		<input type = "button" value = "鼠标移出" onmouseout="testMouseout()"/>
		<input type = "button" value = "鼠标移入" onmousemove="testMousemove()"/>
	</body>
	<script>
		 var spanNode = document.getElementById("spanNode");
		 function testClick(){
			 spanNode.innerHTML = "单击";	 
		 }
		 function testDbclick(){
			  spanNode.innerHTML = "双击";
		 }
		 
		 function testMousedown(){
			 spanNode.innerHTML = "按下鼠标";
		 }
		function testMouseup(){
			 spanNode.innerHTML = "释放鼠标";
		}
		function testMouseout(){
			spanNode.innerHTML = "鼠标出去了";
		}
		function testMousemove(){
			spanNode.innerHTML = "鼠标进来了";
		}
		
		function testOnblur(){
			spanNode.innerHTML = "失去焦点".fontcolor("red");
		}
		function testOnfocus(){
			spanNode.innerHTML = "获得焦点".fontcolor("green");
		}
		function testOnchange(){
			spanNode.innerHTML = "内容改变".fontcolor("blue");
		}
		function testOnload(){
			window.open("6-3/baidu.html","_blank");
		}
		 function testOnsubmit(){
			 alert("表单提交了");
		 }
	</script>
</html>
```



### 4.location对象

* 由 JRE （ JavaScript runtime engine  ）自动创建， 包含有关当前的URL信息
* 方法
  * 属性
    * http://127.0.0.1:8848/js/location.html
    * href  网址链接 http://127.0.0.1:8848/js/location.html
    * hostname 地址  127.0.0.1
    * host 当前页面的链接   127.0.0.1:8848
    * port 端口  8848
    * protocol 协议   http:
  * reload()方法
    * location.reload() 刷新当前页面

* 属性：
  - hash		设置或返回从井号 (#) 开始的 URL（锚）==>哈希值。
  - href		设置或返回完整的 URL。
  - search	设置或返回从问号 (?) 开始的 URL（查询部分）。

encodeURI();//转码
decodeURI();//解码



### 5.screen对象

screen 对象是由 JRE 自动创建的，包含有关的客户机显示的信息

* avaliHeight  排除任务栏 的 屏幕高度
* avaliwidth  排除任务栏 的 屏幕宽度
* height  不排除任务栏 的 屏幕高度
* width  不排除任务栏 的 屏幕宽度

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
	</body>
	<script >
		document.write("获取系统屏幕的工作区高度 " + screen.availHeight + "<br>");
		document.write("获取系统屏幕的工作区宽度 " + screen.availWidth + "<br>");
		document.write("获取系统屏幕的高度 " + screen.height + "<br>");
		document.write("获取系统屏幕的宽度 " + screen.width + "<br>");
	</script>
</html>
```

### 6.history

history(重要): 历史对象,包含窗口的浏览历史，可以实现后退

- 属性：
  - length	返回浏览器历史列表中的 URL 数量。
- 方法：
  - back()	加载 history 列表中的前一个 URL。
  - forward()	加载 history 列表中的下一个 URL。
  - go()	加载 history 列表中的某个具体页面，支持负数。

```javascript
history.go(2);//向前两个页面
history.go(-2);//后退两个页面
```



### 7.点餐案例

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<center>
		<body onload="eat()" >
			<span id = "food"></span>
			<hr />	
			<input type="button" style="font-size: 50px;"  value="暂停" onclick="stop()"/>
			<input type="button" style="font-size: 50px;"  value="继续" onclick="start()"/>
		</body>
	</center>
	<script> 
	function eat(){
		var arr = ["炒面","土豆","胡萝卜","千张","酸辣白菜"];
		var index = Math.floor(Math.random() * arr.length);
		var code = arr[index];
		
		var spanNode = document.getElementById("food");
		spanNode.innerHTML = code;	
		spanNode.style.fontSize = "124px";
		spanNode.style.color = "red";
		spanNode.style.backgroundColor = "yellow";
	}
	var id = null;
	function start(){
		id = window.setInterval("eat()" , 100);
	}	
	function stop(){
		window.clearInterval(id);
	}
	</script>
</html>
```



