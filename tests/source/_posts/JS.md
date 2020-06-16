---

title: JS入门笔记

copyright: true
date: 2020-6-4 12:15:15

toc: true
tags: [HTML,JS]
categories: [网页技术,JS]
declare: true
---



## JavaScript

### 1.基本简介

>用途： 表单校验 + 动画效果 + 游戏

​    javascript必须依赖于HTML 

​	边解释边执行，不需要编译 --- 速度慢

  浏览器中默认内置了javascript的解释程序

 <!--more--> 

### 2.JavaScript特点

1. 安全性 （不允许直接访问本地硬盘），它可以做的就是**信息的动态交互**。  
2. 跨平台性  （只要是可以解释Js的**浏览器**都可以执行，和平台无关。）  

### 3.JavaScript与Java不同

1. JS是 Netscape公司的产品，Java是Sun公司的产品  
2. JS是基于对象，Java是面向对象。
3.  JS只需解释就可以执行，Java需要先编译成字节码文件，再执行。
4. JS是弱类型，Java是强类型。

<!-- **强类型语言**，当你定义一个变量是某个类型，如果不经过代码显式转  换（强制转化）过，它就永远都是这个类型，如果把它当做其他类   型来用，就会报错

 **弱类型语言**，你想把这个变量当做什么类型来用，就当做什么类型来用，语言的解析器会自动（隐式）转换。-->

### 4.JavaScript内容

一个完整的JavaScript实现是由以三个不同部分组成

1. ECMAScript    
2. DOM           使用JS操作网页  
3. BOM           使用JS操作浏览器  

### 5.JS 与 HTML 和 CSS 的不同

html: 负责了一个页面的结构. 

css: 负责了一个页面的样式。  

 javascript： 负责与用户进行交互。



## JavaScript基础

### 1.引入

```html
1.直接用标签写
	<script type = "text/javascript"> js代码; </script>

2.引入js（不可在html中再写js）
	<script src = "1.js" type ="text/javascript"></script>
```

### 2.常用的函数

```javascript
alter("显示的内容"); //弹出框
confirm("确认删除？");//确定为true 取消为false
prompt("请输入你的名字");//确定返回 输入的内容  否则 返回 null
document.write("数据");//向页面输出数据。。。
```

### 3.注释

```
html <!-- 注释的内容 -->
css的注释 /*注释的内容*/
javascript： // 单行注释  /* */多行注释  
```

### 4.声明变量

```html
var 变量名 = 数据；
js中 声明变量只用 var 可以存储任意数据类型的数据 number boolean string array
可重复 变量名 但后面会覆盖前面
不建议省略var
```

### 5.数据类型

```html
typeof + 变量名； 可查看变量的数据类型
		document.write("10数据类型是" + (typeof 10) + "<br/>");  number
number 数字
string 字符串
boolean 布尔
undefined 表示未定义的变量
```

### 6.字符串转换为数字

```html
parseInt()  将字符串转换为整数
paseFloat() 转换为小数
```

```javascript
	var a = "12";
			a = 12.64;
			a = "123abc123"; 
var b = parseInt(a);
			document.write("结果：" + b + "<br/>");---123
/* parseInt方法如果接收的字符串含有非数字的字符，那么parseInt方法会从字符串的首个字符开始寻找，一直找到非数字字符为止，然后就使用前面的数字字符转换成数字，
```

```javascript
var c = "3.14";
			c = parseFloat(c);
			document.write("结果：" + c + "<br/>");
```

```javascript
	javascript提供一个IsNaN的方法让我们判断该字符串是否是 一个数字。
		 is not a  number  不是一个数字。
		不是一个数字返回true，是一个数字返回false.
		document.write(isNaN(123) + "<br/>");   // false
		document.write(isNaN("abc123"));		// true
NaN -- > Not a Number 判断字符串是否不是一个数字 是数字为false 不是数字为 true
```

### 7.运算符

```html
+加  -减  *乘  /除  %取余  
逻辑运算符 : 没有单个 | 和 &
 || 有true为true 
 && 有false为 false
 三目运算符 ： 	布尔表达式 ? 值1T : 值2F
Infinity 表示无穷大 --> 6/0
```

### 8.控制

if 和 switch 条件判断

* 1. 在javascript中的 if 语句 的条件不单止可以写布尔表达式，还可以写任何的数据。  

     number 非 0 为 true         0 为 false

     string    非 空 为 true         空  /  null  为 false

     undefined  为 false

     NaN 给变量赋值 表示不参与运算

  2.  在 javascript 中 switch 判断里 可以跟其他类型   

### 9.循环

* while

  ```HTML
  while(判断的条件){
  		循环体内容	
  		}
  ```

* do-while

  ```html
  do{
  	循环语句；
  			}while(判断条件);
  ```

* for

  ```html
  for(初始化语句; 判断的条件 ; 循环后的语句){
  					循环体语句；	
  				}
  ```

  ```html
  <script type="text/javascript">
  		//打印九九乘法表
  	for (var i = 1; i <= 9; i++) {
  		for (var j = 1; j <= i; j++) {
  		document.write(i + "*" + j + "=" + (i * j) + "&nbsp;&nbsp;");
  			}
  			document.write("<br/>");
  		}
  </script>
  ```

### 10.函数的定义

java 中 的 函数 定义 为 

```java
public int add(int a, int b){}
```

在 js 中

```javascript
function add(a,b){ return a + b;}

function 函数名(形参列表){   函数体;	}
```

* 1.在javascript中   定义形参不可用 var 声明
* 2.函数没有返回值  ， 若函数返回数据给调用者 ，直接 返回
* 3.没有函数重载，重名会 后  覆盖 前

**所有从文本框中获取的值都是字符串类型**

   &nbsp; “ &nbsp ; ”表示空格

### 11.String对象

```javascript
创建字符串类型
1 new String("字符串的内容");
2 var str = "字符串的内容"；
```

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<script>
		var str1 = new String("hello");
		var str2 = new String("hello");
		document.write("str1和str2是否相等" + (str1.toString() == str2.toString()) + "<br>" + "<br>");  //true
		
		//给该字符串添加一个a标签，并且添加name属性,属性值为five 
		document.write("第五章".anchor("five")+ "<br>"); //返回顶部
		
		//charAt返回的是索引值对应的字符的码值
		document.write("abc".charAt(0)+ "<br>");   //a
		
		//fontcolor()给字符串添加font标签，然后设置color的属性值。
		document.write("第六章".fontcolor("red") + "<br>");   //字体为红色
		
		//indexOf()指定字符串第一次索引的值
		document.write("abahekkosadajafsja".indexOf("hekko") + "<br>");  //3
		
		//给文本添加一个i标签，把文本设置成斜体
		document.write("第五章".italics()+ "<br>");  // 
		
		//给文本添加一个a标签
		document.write("百度".link("www.baidu.com")+ "<br>");
		
		//将文本中 返回根据 正则表达式 进行文字替换 后的字符串的复制
		document.write("明天讲html".replace("html","DOM编程")+ "<br>"); //明天讲DOM编程
		
		//第一个表示下标，第二个表示长度
		document.write("abcdef".substr(1,3)+ "<br>");  //bcd
		
		//第一个表示开始的下标，第二个表示结束的下标（包前不包后）
		document.write("abcdedg".substring(1,3)+ "<br>");  // bc
	
		var str = "我们-大家-好";
		var arr = str.split("-");  //切割 获取" - "
		for(var index = 0; index < arr.length; index++){
			document.write(arr[index] + ","); //我们,大家,好,
			}
		document.write("<br/>");
		document.write("abc".toUpperCase()+ "<br>");  //大写
		document.write("ABC".toLowerCase()+ "<br>");  //小写
	</script>
	<body>
		<div style="height: 1000px;">		
		</div>
		<a href="#five">返回顶部</a>
	</body>
</html>
```



### 12.Date对象

```javascript
var date = new Date();//获取当前系统的时间
getFullYear() 年
getMonth() 月
getData()	日
getHours()	时
getMinutes()	分
getSeconds()	秒
```

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		当前系统时间： <span  id="time"> </span>
	</body>
	<script type="text/javascript">
			var date = new Date();//获取当前系统的时间
			document.write("<br>");
			document.write("年：" + date.getFullYear() + "<br>");
			document.write("月：" + (date.getMonth()+1)+ "<br>");
			document.write("日：" + date.getDate()+ "<br>");
			document.write("时：" + date.getHours()+ "<br>");
			document.write("分：" + date.getMinutes()+ "<br>");
			document.write("秒：" + date.getSeconds()+ "<br>");
			//xxxx年yy月dd日 hh:mm:ss
			document.write("当前时间是：" + date.getFullYear() + "年" + (date.getMonth()+1) +"月"+ date.getDate() +"日" + date.getHours() +"时" + date.getMinutes() +"分" + date.getSeconds()+"秒"+ "<br>");
			
			function getCurrentTime(){
				//获取当前的系统时间
				var date = new Date();
				//把当前系统时间拼成我指定的格式。
				var timeInfo = date.getFullYear() + "年" + (date.getMonth()+1) +"月"+ date.getDate() +"日" + date.getHours() +"时" + date.getMinutes() +"分" + date.getSeconds()+"秒";
				//找span对象
				var spanObj = document.getElementById("time");
				//设置span标签的内容
				spanObj.innerHTML=timeInfo.fontcolor("red");
			}
			getCurrentTime();
			//定时方法
			//setInterval 第一个参数为方法，第二个参数为间隔刷新时间
			window.setInterval("getCurrentTime()",1000);
	</script>
</html>
```



### 13. Math对象

```
ceil() 向上取整
floor()  向下取整
random()  随机数
round()  四舍五入
```

```javascript
document.write("向上取整： " + Math.ceil(3.14) + "<br>");  //4
document.write("向下取整： " + Math.floor(3.14) + "<br>");  //3
document.write("随机数： " + Math.random() + "<br>");    //0<= ~ <1
document.write("四舍五入： " + Math.round(3.14) + "<br>");//3
```

### 14. 数组对象

创建数组

1. var 变量名 = newArray(); 
2. var 变量名 = new Array(长度);
3. var 变量名 = new Array(" 元素1","元素2"...  );
4. var 变量名 = [" 元素1","元素2"... ];

方法

- pop()          移除数组中的最后一个元素并返回该元素  
- push()        将新元素添加到一个数组中，并返回数组的新长度值。
- reverse()     翻转数组的元素  
- shift()          删除第一个元素并返回：  

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<script>
		var arr = new Array();  //创建一个长度为0的数组
		var arr1 = new Array(12); //创建一个长度为12的数组
		arr1[100] = 14;
		document.write("arr1长度：" + arr1.length + "<br>");
        
		var arr2 = new Array("狗蛋","发财","铁子");
		//创建给定数组指定元素创建数组的对象
		document.write("arr2长度：" + arr2.length +"<br>")
		
		var arr3 = ["富贵","富强","富明"];
		document.write(arr3 + "<br>");
	
        
		document.write("移除 arr 数组中最后一个元素 " + arr3.pop() + "<br>");
        
		//arr3.push("尔康");
		document.write("添加一个元素 " +  arr3.push("尔康") + "<br>"+ "数组为:"+ arr3 + "<br>");
		
		arr3.reverse();
		document.write(arr3 + "<br>");
		
		arr3.shift();
		document.write(arr3 + "<br>");
	</script>
	<body>
	</body>
</html>

```





### 15.自定义对象

1. javascript没有类的概念，只要有函数即可创建对象  

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<script>
		//1 无参
		function Person(){}
			var p = new Person(); //创建一个Person对象
			p.id = 110;
			p.name = "狗娃";
		document.write(p.id +"---" + p.name);
				
		//2 带参
		function Person(id,name){
			this.id = id;
			this.name = name;
			this.say = function(){
				alert(name + "嘿嘿");
			}
		}
		var p1 = new Person(110,"狗剩");//创建对象
		document.write(p1.id +  "---" + p1.name );
        
	 	//3 Object函数创建对象
		var p2 = new Object();
		p2.id = 110;
		p2.name = "铁蛋";
		document.write(p2.id + "---" + p2.name)
		
		//4 字面量
		var p3 = {
			id : 110,
			name :"富贵",
			say:function(){
				alert(this.name + " 嘿嘿 ");
			}
		}
		p3.say();
		document.write(p3.id + "---" +p3.name)		
	</script>
	<body>
	</body>
</html>
```



### 16.js中（面试题）

**!=，==，!==，===的用法和区别**

!=   和 ==   数值 和 字符串 判断时先将**字符串** 转换 为 **数值**  ，再进行判断

!==  和  ===  判断时   先 判断 **数据类型** 再判断 数值 

!==  数据类型相同，值相同 为 false

=== 数据类型相同，值相同 为 true

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<script type="text/javascript">
		// != == = === !==
		var num = 1;
		var str = '1';
		var test = 1;
		document.write( "test : "+ test  + " == " + " num : "+ num  + " &nbsp;"+ 
                       (test == num) + "<br>");
		document.write("test : "+ test  + " == " + " num : "+ num  + " &nbsp;"+
                       (test === num )+ "<br>");
		document.write("test : "+ test  + " == " + " num : "+ num  + " &nbsp;"+ 
                       (test !== num) + "<br>");
		document.write("num : "+ num  + " == " + " str : "+ str  + " &nbsp;" + 
                       (num == str) + "<br>");
		document.write("num : "+ num  + " == " + " str : "+ str  + " &nbsp;" +
                       (num != str )+ "<br>");
		document.write("num : "+ num  + " == " + " str : "+ str  + " &nbsp;" + 
                       (num === str) + "<br>");
		document.write("num : "+ num  + " == " + " str : "+ str  + " &nbsp;" +
                       (num !== str) + "<br>");
	</script>
	<body>
	</body>
</html>
```

> test : 1 == num : 1  true
>test : 1 == num : 1  true
>test : 1 == num : 1  false
>num : 1 == str : 1  true
>num : 1 == str : 1  false
>num : 1 == str : 1  false
>num : 1 == str : 1  true 

```
var b = null;
var d = undefined;
b ==  d  T 
b === d  F
```



## BOM

### 1.BOM基本

bom(Browser Object Model) 浏览器对象模型

浏览器对象模型 把 浏览器 的 各个部分 都用了 一个对象 进行描述，若操作浏览器，则可以通过 浏览器对象模型 的 对象 进行操作

window对象  代表了一个新开的窗口

location对象 代表了地址栏的对象

screen对象  代表了整个屏幕的对象

### 2.window对象

 window常用方法

* open("href","_blank","location:no,toolbar=no") 		打开一个新的窗口
  * href  跳转 的 页面 地址 
  * _blank 打开一个新的窗口  或 _self 在自身打开一个窗口
  * location 地址栏  toolbar 工具栏
* resizeTo("height","width")    将窗口的大小改为指定的 **高度** 和 **宽度**
* moveTo("x","y") 将窗口的左上角的 屏幕位置 移动到指定的 x 和 y 位置
  * 基于屏幕左上角为坐标原点  绝对位置
* moveBy("x","y") 相对于原来的窗口移动指定的x、y值。  
  * 基于原窗口的左上角为坐标原点  相对位置
* setInterval("function()",times)    每经过指定毫秒值后就会执行指定的代码
  * 方法名 + 时间 （毫秒）   
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

### 3.常用事件

* 鼠标点击相关
  * onclick  鼠标单机触发的事件
  * ondblclick  鼠标双击触发的事件
  * onmouseup  鼠标位于对象上且释放鼠标按钮时
* 鼠标移动相关
  * onmouseout  鼠标指针移除对象边界时
  * onmousemove  鼠标划进对象时触发
* 焦点相关
  * onbluer 对象失去鼠标焦点
  * ondocus 对象获取鼠标焦点
* 其他
  * onchange 当选中区的内容发生改变的时候
  * **onload**  在浏览器完成加载后  立即 触发 
  * onsubmit 表单被提交后触发

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



### 6.点餐案例

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

## DOM

* Document Object Model  文档对象模型
* Dom 描绘了一个层次化的树，允许开发人员添加、删除、修改页面的某一部分 
* 浏览器在解析HTML页面标记的时候，是将HTML页面中的每一个标记按照顺序在内存中组件一颗DOM树，按照树的结构将页面显示在浏览器窗口中



### 1.节点层次

  HTML网页是可以看做是一个树状的结构，如下：

  html

   |-- head

   |   |-- title

   |   |-- meta

   |   ...

   |-- body

   |   |-- div

   |   |-- form

   |   |   |-- input

   |   |   |-- textarea

   ...  ...  ...

document

​    代表当前页面的整个文档树。

  访问属性

​    all   所有标签

​    images  所有img标签

​    links  所有a标签

### 2.document入门

* 一个html页面被浏览器加载的时候，浏览器就会对整个html页面上的所有标签都会创建一个对应的对象进行描述，我在浏览器上看到的信息只不过就是这些html对象的属性信息而已。我们只要能找到对应的对象操作对象的属性，则可以改变浏览器当前显示的内容。
* //nodeName：节点名称  

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<img src =  "" alt="这是图片1 " />
		<img src = "" alt="这是图片2" />
		<img src = "" alt="这是图片3" />
		<input type="button" value="设置图片" onclick="setImg()"/>
		
		<a href="#">百度</a>
		<a href="#">百度</a>
		<a href="#">百度</a>
		<input type="button" value="设置a标签" onclick="setLink()"/>
	</body>
	<script>
		function setImg(){
			var images = document.images;
			for(var i = 0 ; i < images.length;i++){
				images[i].src="img/www.jpg";
				images[i].height = 100;
				images[i].width = 100;
			}
		}
		function setLink(){
			var link = document.links;
			for(var i = 0 ; i < link.length;i++){
				link[i].href="http://www.baidu.com";
			}
			
		}
        //获取当前页面所有标签对象
		document.write("<br>")
		var all = document.all;
		for(var i = 0; i < all.length; i++){
			document.write(all[i].nodeName+"---");
		}	
	</script>
</html>
```

### 3.根据html标签的属性来找节点

* 通过html元素的标签属性找节点。
  * document.getElementById("html元素的id属性值") 
  *  document.getElementsByTagName("标签名") 
  * document.getElementsByName("html元素的name属性值")
  *  document.getElementsByClassName("html元素的class属性值")
*  返回的是一个数组  

```html
	<body>
		用户名：<input type="text" id = "username" />
		<input type="button" value="设置用户名" onclick="setUserName()" />
		<hr />
		<img src=""  alt="这是图片1"/>
		<img src=""  alt="这是图片2" class="imgs"/>
		<img src=""  alt="这是图片3" class="imgs"/>
		<input type="button" value="设置图片" onclick="setImg()" />
		<hr />
		<div>div标签1</div>
		<div>div标签2</div>
		<div>div标签3</div>
		<input type="button" value="设置div" onclick="setDivs()" />
		<hr />
		<span name = "span">span标签1</span>
		<span name = "span">span标签2</span>
		<span name = "span">span标签3</span>
		<input type="button" value="设置span" onclick="setSpan()" />
	</body>
	
	<script>
			function setUserName(){
				 var username  = document.getElementById("username");
				 username.value = "赵四";
			}
			
			function setImg(){
				var imges = document.getElementsByClassName("imgs");
				for(var i = 0 ; i < imges.length; i++){
					imges[i].src = "img/www.jpg";
					imges[i].width=200;
					imges[i].height=200;	
				}
			}
			
			function setDivs(){
				var divs = document.getElementsByTagName("div");
				for(var i = 0 ; i < divs.length; i++){
					divs[i].innerHTML="div标签".fontcolor("red");
				}
			}
			
			function setSpan(){
				var span = document.getElementsByName("span");
				for(var i = 0 ; i < span.length ; i++){
					span[i].innerHTML = "span标签".fontcolor("red");
				}
			}
	</script>
```

### 4.练

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<script>
		function checkAll(){
			var items = document.getElementsByName("item");
			var allNode  = document.getElementsByName("all")[0];
			for(var i = 0;i < items.length ;i++){
				items[i].checked = allNode.checked;
			}
		}
		function getSum(){
			var items = document.getElementsByName("item");
			var sum = 0;
			for(var i = 0 ; i < items.length; i++){
				if (items[i].checked)
				sum += parseInt(items[i].value);
		}
		var smid = document.getElementById("sumid");
		smid.innerHTML = ("&nbsp;&nbsp;&nbsp;&yen;" + sum).fontcolor("green");
			}
	</script>
	<body>
			<div>商品列表</div>
			<input type="checkbox" name="item" value="3000" />笔记本电脑3000元<br />
			<input type="checkbox" name="item" value="3000" />笔记本电脑3000元<br />
			<input type="checkbox" name="item" value="3000" />笔记本电脑3000元<br />
			<input type="checkbox" name="item" value="3000" />笔记本电脑3000元<br />
			<input type="checkbox" name="item" value="3000" />笔记本电脑3000元<br />
			<input type="checkbox" name="item" value="3000" />笔记本电脑3000元<br />
			
			<input type="checkbox" name="all" onclick="checkAll()" />全选/不选<br />
			
			<input type="button" value="总金额: " onclick="getSum()" />
			
			<span id = "sumid"></span>
	</body>
</html>
```

### 5.通过节点关系找标签

* 通过关系(父子关系、兄弟关系)找标签。
  * parentNode  获取当前元素的父节点。
  * childNodes  获取当前元素的所有下一级子元素。
  * firstChild  获取当前节点的第一个子节点。
  *  lastChild  获取当前节点的最后一个子节点。

* nextSibling   获取当前节点的下一个节点。（获取当前节点相邻的下一个平级节点）
* previousSibling 获取当前节点的上一个节点。（获取当前节点相邻的上一个平级节点）
* 我们可以通过标签的类型进行判断筛选：
  * 文本节点的类型： 3
  * 注释的节点类型： 8 
  * 标签节点的类型： 1




### 6.创建节点，插入节点

* 每个节点都包含的信息的，这些属性是：
  * nodeType 节点类型
  * nodeName 节点名称
  * nodeValue节点值

      元素类型 节点类型 

      元素   1   就是标签元素，例<div>..</div>

     文本   3   标签元素中的文本

     注释   8    表示为注释

* nodeName   nodeName 属性含有某个节点的名称。
  * 元素节点的 nodeName 是标签名称 
  *  属性节点的 nodeName 是属性名称 
  *  文本节点的 nodeName 永远是 #text 
  * 文档节点的 nodeName 永远是 #document 

* nodeValue
  * 对于文本节点，nodeValue 属性是所包含的文本。
  *  对于属性节点，nodeValue 属性是属性值。
  * 对于注释节点，nodeValue 属性注释内容。
  *  nodeValue 属性对于文档节点和元素节点是不可用的。

*  创建节点、设置节点的属性。
  * document.createElement("标签名")		创建新元素节点
  * elt.setAttribute("属性名", "属性值")	设置属性
  * elt.appendChild(e)		添加元素到elt中最后的位置

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<input type="button" onclick="add()" value="添加" />
	</body>
	<script>
		var num  = 1;
		function add(){
			var inputNode = document.createElement("input");  //创建 标签名字的节点。
			//setAttribute:设置节点的属性
			inputNode.setAttribute("type", "button");
			inputNode.setAttribute("value", "按钮" + num);	
			num++;			 
			 var bodyNode = document.getElementsByTagName("body")[0];
			 bodyNode.appendChild(inputNode);
		}
	 </script>
</html>
```

### 7.添加附件

* 插入目标元素的位置 

  * elt.**insertBefore**(newNode, childNode);     

    		添加到elt中，childNode之前。

      注意： elt必须是childNode的直接父节点。

* 删除指定的子节点 

    elt.removeChild(child)             

    注意： elt必须是child的直接父节点。


   ```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<table>
			<tbody>
				<tr>
					<td><input type="file" /></td>
					<td><a href="#" onclick="del(this)"> 删除附件 </a> </td>
				</tr>
				<tr id = "lastrow">
					<td colspan="2">
						<input onclick="addFile()" type ="button" value="添加附件"/>
					</td>
				</tr>
			</tbody>
		</table>
	</body>
	<script>
		//添加附件
		function addFile(){
			//获取表格节点对象
			var table = document.getElementsByName("table")[0];
			//创建tr标签节点对象
			var trnode = document.createElement("tr");
			trnode.innerHTML = "<td><input type = 'file'/></td><td><a href='#' onclick='del(this)'> 删除附件 </a></td>";
		
		//获取父节点 tbody
		var tbody = document.parentNode("tbody")[0];
		//获取要插入的字节点
		 var lastrow = document.getElementById("lastrow");
		//添加数据
		tbody.insertBefore(trnode,lastrow);
		}
		function del(delfile){
			var tbody = document.getElementsByTagName("tbody")[0];
			var del  = delfile.parentNode.parentNode;
			tbody.removeChild(del);
		}
	</script>
</html>
   ```

### 8.城市联动框

* selectedIndex 选择索引

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
			省份<select id = "province" onchange="showCity()">
				<option>省份</option>
				<option>河南</option>
				<option>山东</option>
				<option>安徽</option>
			</select>城市
			<select id = "city">
				<option>城市</option>
			</select>
	</body>
	<script>
		function showCity(){
			//维护一个二维数组存储省份对应的城市
			var citys = [[],["洛阳","郑州","三门峡"],["青岛","日照","烟台"],["广州","汕头","深圳"]];
			//获取省份对应的节点
			var provinceNodes = document.getElementById("province");
			//获取省份选中的选项
			var index = provinceNodes.selectedIndex;
			//获取对应的城市
			var datas = citys[index];
			//找到city节点
			var citynode = document.getElementById("city");
			//先清空city框所有option
			var citychild = citynode.childNodes;
			for(var i = 0; i < citychild.length;){
				citynode.removeChild(citychild[i]);
			}
			//设置options的个数。
			//citynode.options.length = 1;
			//遍历对应的所有城市然后创建对应的option添加到city上。
			for(var i = 0; i < datas.length;i++){
				var op = document.createElement("option");
				op.innerHTML = datas[i];
				citynode.appendChild(op);
			}
		}
	</script>
</html>
```



### 9.正则验证From表单  

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<form action="success.html" method="get" onsubmit="return checkAll()">
			<table border="1px" width="50%" align="center" cellpadding="3px" cellspacing="0px">
			<tr>
				<td width="25%">姓名：</td>
				<td>
					<input type="text" name = "userName" id="userName" onblur="checkName()" />
					<span id = "userId"></span>
				</td>
			</tr>
			<tr>
				<td>密码：</td>
				<td>
					<input type="password" name="pwd" id="pwd" onblur="checkPass()" />
					<span id = "passId"></span>
				</td>
			</tr>
			<tr>
				<td>确认密码：</td>
				<td>
					<input type="password" name="ensurepwd" id="ensurepwd" onblur="ensurePass()" />
					<span id = "ensure"></span>
				</td>
			</tr>
			<tr>
				<td>邮箱：</td>
				<td>
					<input type="text" name="email" id="email" onblur="checkEmail()" />
					<span id="emailspan"></span>
				</td>
			</tr>
			<tr>
				<td>性别：</td>
				<td>
					<input type="radio" checked="true" name="gender" id= "male" value="male" />
					男
					<input type="radio" checked="true" name="gender" value="female" />
					女
				</td>
			</tr>
			<tr>
				<td>爱好：</td>
				<td>
					<input type="checkbox" name="like" /> eat
					<input type="checkbox" name="like" /> sleep
					<input type="checkbox" name="like" /> play
					<span id = "hobbyspan"></span>
				</td>
			</tr>
			<tr>
				<td>城市：</td>
				<td>
					<select name="city" id="city">
						<option value="">请选择</option>
						<option value="bj">北京</option>
						<option value="sh">上海</option>
						<option value="gz">广州</option>
					</select>
				</td>
			</tr>
			<tr>
				<td>自我介绍</td>
				<td>				
					<textarea cols="15" rows="5" name="myInfo" id="myInfo"></textarea>
				</td>
			</tr>
			<tr align="center">
				<td colspan="2">
					<input type="submit" />
				</td>
			</tr>
			</table>
		</form>
	</body>
	<script>
        //
		function checkName(){
			var inputNode = document.getElementById("userName").value;
			var spanNode = document.getElementById("userId");
			var reg = /^[a-z][0-9]{7}$/i;
			if(reg.test(inputNode)){
				spanNode.innerHTML = "√".fontcolor("green");
				return true;
			}else{
				spanNode.innerHTML = "格式不对".fontcolor("red");
				return false;
			}
		}
		
		function checkEmail(){
			var email = document.getElementById("email").value;
			var spanNode = document.getElementById("emailspan");
			var reg = /^[a-z0-9]\w+@[a-z0-9]+(\.[a-z]{2,3}){1,2}$/i;
			if(reg.test(email)){
				spanNode.innerHTML = "√".fontcolor("green");
				return true;
			}else{
				spanNode.innerHTML = "格式不对".fontcolor("red");
				return false;
			}
		}
		function checkAll(){
			var userName = checkName();
			var email = checkEmail();
			if(userName && email){
				return true;
			}else{
				return false;
			}
		}
	</script>
</html>
```



## 正则表达式

/^$/

位置：^   $

次数 

* /*/    0 或 多个
* /+/    1 个 多个
* /?/     0 或 1个



