---
title: Js基本语法

copyright: true
date: 2020-6-4 12:15:15

toc: true
tags: [HTML,Js基本语法]
categories: [网页技术,JavaScript-JS]
declare: true

---



## JavaScript

---

### 1.Js概述

#### 1.1 JavaScript的诞生

> JavaScript 诞生于 1995 年。
>
> 由Netscape(网景公司)的程序员Brendan Eich(布兰登)与Sun公司联手开发一门脚本语言,  最初名字叫做Mocha，1995年9月改为LiveScript。
>
> 12月，Netscape公司与Sun公司（Java语言的发明者）达成协议，后者允许将这种语言叫做JavaScript。
>
> 1996年3月， Netscape公司的浏览器Navigator2.0浏览器正式内置了JavaScript脚本语言.  此后其他主流浏览器逐渐开始支持JavaScript. 

<!--more--> 

#### 1.2 js版本

> JavaScript这种语言的基本语法结构是由ECMAScript来标准化的, 所以我们说的JavaScript版本一般指的是ECMAScript版本.

#### 1.3 js的优势

> 目前苹果公司的Safari, 谷歌的Chrome,微软的IE等几乎全部浏览器都支持JavaScript, 基于JavaScript开发的库和框架数不胜数, 例如: jQuery,Angular, React等…

> JavaScript将在前端和服务器端(Node.js)有更好的发展

#### 1.4 js用途

用途： 表单校验  开发网站  动画效果 +  移动端app + 游戏

javascript必须依赖于HTML 

​	边解释边执行，不需要编译 --- 速度慢

  浏览器中默认内置了javascript的解释程序

 <!--more--> 

#### 1.5.JavaScript特点

1. 安全性 （不允许直接访问本地硬盘），它可以做的就是**信息的动态交互**。  
2. 跨平台性  （只要是可以解释Js的**浏览器**都可以执行，和平台无关。）  

#### 1.6.JavaScript与Java不同

1. JS是 Netscape公司的产品，Java是Sun公司的产品  
2. JS是基于对象，Java是面向对象。
3.  JS只需解释就可以执行，Java需要先编译成字节码文件，再执行。
4. JS是弱类型，Java是强类型。

<!-- **强类型语言**，当你定义一个变量是某个类型，如果不经过代码显式转  换（强制转化）过，它就永远都是这个类型，如果把它当做其他类   型来用，就会报错

 **弱类型语言**，你想把这个变量当做什么类型来用，就当做什么类型来用，语言的解析器会自动（隐式）转换。-->

### 2.JavaScript内容

一个完整的JavaScript实现是由以三个不同部分组成

> javascript = ECMAScript + BOM + DOM

1. ECMAScript     核心
2. DOM           使用JS操作网页   文档对象模型
3. BOM           使用JS操作浏览器   浏览器对象模型

### 3.JS 与 HTML 和 CSS 的不同

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


- console.log()：控制台输出
- 输出到页面元素
  - innerHTML：双标签输出
  - value：表单输出
```

### 3.注释

```
html <!-- 注释的内容 -->
css的注释 /*注释的内容*/
javascript： // 单行注释  /* */多行注释  
```

### 4.声明变量

```html
//var：关键字，
var 变量名 = 数据；
js中 声明变量只用 var 可以存储任意数据类型的数据 number boolean string array
可重复 变量名 但后面会覆盖前面
不建议省略var
```

#### 4.1 js 规范

- JS变量的命名规范（规定）
  - 变量名必须是数字,字母,下划线`_`和美元符`$`组成;
  - 第一个字符不能为数字
  - 不能使用关键字或保留字
- 代码可读性（约定）
  - 标识符区分大小写，如：age和Age是不同的变量。但强烈不建议用同一个单词的大小写区分两个变量。
  - 变量命名尽量遵守驼峰原则: myStudentScore
  - 变量命名尽量见名知意
  - 保持代码缩进
  - JS语句的末尾尽量写上分号;
  - 运算符两边都留一个空格, 如 `var n = 1 + 2`;
  - 注释
    - 单行注释：//注释内容
    - 多行注释（和CSS注释一样）
      - `/*注释内容*/`
      - 多行注释不能嵌套



### 5.数据类型

```html
typeof + 变量名； 可查看变量的数据类型
		document.write("10数据类型是" + (typeof 10) + "<br/>"); 
```

#### 5.1 值类型

* number 数字
  * NaN：是一个特殊的值，即非数值(Not a Number)，转换类型失败的计算值（如：1-"1a"）

* string 字符串 （用引号【单/双引号】括起来的内容）

* boolean 布尔 （true，false）

#### 5.2 引用

Object：对象

- Array：数组 
- Function：函数
- RegExp：正则
- Date：日期

#### 5.3 特殊数据类型

- Null
  - null ，通过id获取不到元素时则得到 null
- Undefined
  - undefined，声明变量但不赋值则得到 undefined 

### 6.字符串转换为数字

#### 6.1parseInt

```html
parseInt(string index)  将字符串转换为整数
```

| 参数   | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| string | 必需。要被解析的字符串。                                     |
| radix  | 可选。表示要解析的数字的基数。该值介于 2 ~ 36 之间。如果省略该参数或其值为 0，则数字将以 10 为基础来解析。如果它以 “0x” 或 “0X” 开头，将以 16 为基数。如果该参数小于 2 或者大于 36，则 parseInt() 将返回 NaN。 |

```js
parseInt("10");			//返回 10
parseInt("19",10);		//返回 19 (10+9)
parseInt("11",2);		//返回 3 (2+1)
parseInt("17",8);		//返回 15 (8+7)
parseInt("1f",16);		//返回 31 (16+15)
```

#### 6.2 paseFloat

> paseFloat(string) 转换为小数

| 参数     | 描述                     |
| -------- | ------------------------ |
| *string* | 必需。要被解析的字符串。 |

```js
parseFloat("10")               //返回 10
parseFloat("10.00")            //返回 10
parseFloat("10.33")            //返回 10.33
parseFloat("34 45 66")         //返回 34
parseFloat(" 60 ")             //返回 60
parseFloat("40 years")         //返回 40
parseFloat("He was 40")        //返回 NaN
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

> - 基本数据类型转换：利用内置函数进行转换


| 值(a)     | 转换为 | 字符串String(a) | 数字Number(a) | 布尔值Boolean(a) |
| --------- | ------ | --------------- | ------------- | ---------------- |
| undefined | =>     | \"undefined\"   | NaN           | false            |
| null      | =>     | \"null\"        | 0             | false            |
| true      | =>     | \"true\"        | 1             |                  |
| false     | =>     | \"false\"       | 0             |                  |
| \"\"      | =>     |                 | 0             | false            |
| \"1.2\"   | =>     |                 | 1.2           | true             |
| \"one\"   | =>     |                 | NaN           | true             |
| 0         | =>     | \"0\"           |               | false            |
| -0        | =>     | \"0\"           |               | false            |
| NaN       | =>     | \"NaN\"         |               | false            |
| 1         | =>     | \"1\"           |               | true             |

> - 隐式转换
>   如果运算不能进行下去，内部就会尝试进行数据类型的转换
>   支持隐式转换的运算：逻辑运算、关系运算、算术运算

6.3  isNaN(x)

> isNaN() 函数用于检查其参数是否是非数字值

	javascript提供一个IsNaN的方法让我们判断该字符串是否是 一个数字。
		 is not a  number  不是一个数字。
		不是一个数字返回true，是一个数字返回false.
		document.write(isNaN(123) + "<br/>");   // false
		document.write(isNaN("abc123"));		// true
NaN -- > Not a Number 判断字符串是否不是一个数字 是数字为false 不是数字为 true

> 检查数字是否非法：

```js
isNaN(123);            //返回 false
isNaN(-1.23);          //返回 false
isNaN(5-2);            //返回 false
isNaN(0);              //返回 false
isNaN("Hello");        //返回 true
isNaN("2005/12/12");   //返回 true
```



### 7.运算符

```html
+加  -减  *乘  /除  %取余  
逻辑运算符 : 没有单个 | 和 &
 || 有true为true 
 && 有false为 false

 三元运算 	布尔表达式 ? 值1T : 值2F
条件 ? 条件成立代码 : 条件不成立代码
var a=20;
var b = 50;
var sum = a>b ? a-b : a+b;

Infinity 表示无穷大 --> 6/0
```

### 8.控制

if 和 switch 条件判断  和 java 语法 相同

* 1. 在javascript中的 if 语句 的条件不单止可以写布尔表达式，还可以写任何的数据。  

     number 非 0 为 true         0 为 false

     string    非 空 为 true         空  /  null  为 false

     undefined  为 false

     NaN 给变量赋值 表示不参与运算

  2.  在 javascript 中 switch 判断里 可以跟其他类型   



```
if(条件1){
    //条件1成立(返回true)时，执行这里的代码，忽略以下代码
}else if(条件2){
    //条件2成立(返回true)时，执行这里的代码，忽略以下代码
}
...
else{
    //以上条件都不成立(都返回false)时，执行这里的代码
}
```



```
switch(值) {
    case value1: //要求value1与值恒等
        //如果表达式的值恒等于value1，代码从这里开始执行
        break;
    case value2:
        //如果表达式的值恒等于value2，代码从这里开始执行
        break;
    case value3: 
        //如果表达式的值恒等于value3，代码从这里开始执行
        break;
    case value4: 
        //如果表达式的值恒等于value4，代码从这里开始执行
        break;
    default: 
        //如果以上条件都不成立，默认执行这里的代码
}
```



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
函数表达式(赋值式)
function add(a,b){ return a + b;}
function 函数名(形参列表){   函数体;	}

关键字声明（声明式）：
格式：`function 函数名(){}`
function sum(){}
```

匿名函数： 没有名字的函数就叫匿名函数

```
function(){}
```



* 1.在javascript中   定义形参不可用 var 声明
* 2.函数没有返回值  ， 若函数返回数据给调用者 ，直接 返回
* 3.没有函数重载，重名会 后  覆盖 前

**所有从文本框中获取的值都是字符串类型**

   &nbsp; “ &nbsp ; ”表示空格

#### 10.1函数的执行

1. 手动调用:
   `sum();`
2. 事件驱动:
   格式：元素.事件 = 函数名;
   `buton.onclick = sum;`

#### 10.2  声明提前

- 函数声明提前
- 变量声明提前
  声明但没有赋值的变量默认为undefined

```
function test(){
    console.log(a);
    var a=20;
}
test() ==> 会得到什么信息？
```

#### 10.3 作用域

>俗称“使用范围”，即能够使用某个变量的范围，分<全局作用域>和<局部作用域>

>- 全局变量与局部变量
>  - 全局变量：在全局作用域下声明的变量，可以在任意地方中使用，作用范围比较大，我们称为全局变量
>  - 局部变量：在函数内（局部作用域）声明的变量，只在函数中可以使用，作用范围较小，我们称之为局部变量
>- 变量的访问规则
>  - 就近原则（如查找变量a）：
>    - 使用变量a时先从当前函数查找，如果当前函数有变量a则使用;
>    - 如果当前函数无变量a,则往父级函数查找，如果找到则使用，并停止查找;
>    - 如果在父级函数还是无法找到，则继续往上一层函数查找，以此类推，直到最顶层(全局作用域)，如果还是没找到，则报not defined错误;
>  - 作用域链：每个函数在定义时就形成了局部作用域，如果存在多个函数嵌套，他们之间就会建立起某种联系，直到全局作用域，这种联系称之为作用域链。当函数访问变量时，根据就近原则在这个作用域链中从内到外查询变量。

10.4 闭包

> 闭包是js开发惯用的技巧，什么是闭包？**闭包指的是：能够访问另一个函数作用域的变量的函数**。清晰的讲：闭包就是一个函数，这个函数能够访问其他函数的作用域中的变量。eg:

```
  function outer() {
       var  a = '变量1'
       var  inner = function () {
              console.info(a)
       }
      return inner    // inner 就是一个闭包函数，因为他能够访问到outer函数的作用域
  }
```



### 11.字符串

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

#### 11.2 字符串的属性和方法

##### 11.2.1 属性

> - length: 表示字符串的长度，只读（只能读取）

##### 11.2.2 字符串的获取方法

> - charAt(3) //获取下标为3的字符

##### 11.2.3 字符串的查找替换方法

> - indexOf/lastIndexOf(keyword [,startIndex])  从开头/尾部向后查找字符串`keyword`第一次出现的位置,如果没找到返回-1
> - search(str|regExp) 查找字符串第一次出现的位置

> 与indexOf的区别：search方法支持正则表达式

> - match(str|regExp) 匹配字符串，返回一个数组
>   index:匹配字符所在的索引
>   input:表示整个字符串的引用
> - replace(str|regExp,'') 替换字符串 	
>   这里的替换只能执行一次，不能够进行全局匹配，如果需要全局匹配，则应使用正则表达式

##### 11.2.4 字符串的截取方法

> - substring(start[,end])：不包括end所在字符，end省略表示截取到最后
> - substr(start[,len])：支持负数，len为截取的数量
> - slice(start[,end]) ：截取start到end(不包括end)的字符串，支持负数

##### 11.2.5 字符串分割

> - split(分割符)：根据分割字符，把字符串拆分成数组

##### 11.2.6 字符串大小写转换

> - toLowerCase()：转换成小写
> - toUpperCase()：转换成大写

##### 11.2.7 ECMAscript5新增

> - str[3]//通过下标获取
> - trim()：删除前后所有空格，返回新的字符串

##### 11.2.8 编码与字符集(了解)

> - charCodeAt(3) //获取下标为3的字符的ASCII(American Standard Code for * Information Interchange) == > unicode编码
> - String.fromCharCode(94) //编码转换成字符

> [ascii码, GBK及Unicode由来]
> 字符编码是计算机技术的基石，想要熟练使用计算机，就必须懂得一点字符编码的知识。

### 12.Date 时间  对象

```javascript
var date = new Date();//获取当前系统的时间
getFullYear() 年
getMonth() 月
getData()	日

getDay()  0-6:星期天-星期六 获取星期

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

#### 12.1 日期处理

- getTime()/setTime()：获取/修改某个日期自1970年1月1日0时以来的毫秒数
- toLocaleDateString();  以特定地区格式显示年、月、日
- toUTCString();  转换成UTC时间

**ES5方法**

> - Date.parse("2015-08-24")//返回指定日期距1970-1-1零时的毫秒数

> PS：转换格式默认支持2015-08-24或2015/08/24

> - Date.now();//返回执行这行代码时距1970-1-1零时的毫秒数

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

