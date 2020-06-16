---
title: DOM文档对象模型

copyright: true
date: 2020-6-6 11:27:15

toc: true
tags: [HTML,DOM]
categories: [网页技术,JavaScript-DOM]
declare: true

---



## DOM

* Document Object Model  文档对象模型
* Dom 描绘了一个层次化的树，允许开发人员添加、删除、修改页面的某一部分 
* 浏览器在解析HTML页面标记的时候，是将HTML页面中的每一个标记按照顺序在内存中组件一颗DOM树，按照树的结构将页面显示在浏览器窗口中

<!--more--> 

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
    * 返回元素节点对象，如果id不存在返回null
  * document.getElementsByTagName("标签名") 
    *  返回类数组，如果tagname不存在返回空数组[]
  * document.getElementsByName("html元素的name属性值")
  * 返回类数组，如果name属性不存在返回空数组[]
  * document.getElementsByClassName("html元素的class属性值")
    *  返回类数组，如果类名不存在返回空数组[]
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
* 兄弟
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
  * 属性节点的 nodeName 是属性名称 
  * 文本节点的 nodeName 永远是 #text 
  * 文档节点的 nodeName 永远是 #document

* nodeValue

  * 对于文本节点，nodeValue 属性是所包含的文本。
  * 对于属性节点，nodeValue 属性是属性值。
  * 对于注释节点，nodeValue 属性注释内容。
  * nodeValue 属性对于文档节点和元素节点是不可用的

#### 6.1创建节点、设置节点的属性。

* 创建：
  - document.createElement()      创建一个元素节点
  - document.createTextNode()     创建一个文本节点
  - document.createAttribute()    创建一个属性节点（几乎不用）
* 插入：
  - parent.appendChild()    向节点的子节点列表的结尾添加新的子节点
  - parent.insertBefore(new,node)   在指定的子节点node前插入新的子节点new。
  - ele.setAttributeNode(attrNode)  在指定元素中插入一个属性节点（几乎不用）

> 对页面已存在节点的处理

> - 复制
>   - cloneNode(boolean)      复制节点，为true是深复制。
> - 删除：
>   - parent.removeChild(ele)  删除（并返回）当前节点parent的指定子节点ele。
> - 判断：
>   - parent.hasChildNodes()  判断当前节点是否拥有子节点,返回布尔值

> 以上parent表示父级元素，ele表示元素



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



