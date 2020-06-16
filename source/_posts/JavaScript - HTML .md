---

title: HTML 

copyright: true
date: 2020-6-7 12:15:15

toc: true
tags: [HTML,JS]
categories: [网页技术,JavaScript-HTML]
declare: true
---


## HTML

### 1.元素节点的操作 

#### 1.2常用节点属性

可以通过点语法或方括号访问

- id           设置/获取元素id属性
- name         设置/获取元素name属性
- style        设置/获取元素的内联样式
- className    设置/获取元素的class属性
- title
- value
- checked
- type
- src
- ...
- tagName      获取元素元素的标签名
- innerHTML    设置/获取元素的内容（包含html代码）
- innerText    设置或获取位于元素标签内的文本
- outerHTML    设置或获取元素及其内容（包含html代码）
- outerText    设置(包括标签)或获取(不包括标签)元素的文本
- ...



<!--more--> 

##### 盒模型相关

> - offsetTop: 当前元素离<定位父级>元素顶部的距离。
> - offsetLeft: 当前元素离<定位父级>元素左边的距离。

> 以上两个属性如果没定位的父级，则相对于根元素html的距离

> - offsetWidth: 当前元素的宽度（border + padding + content）
> - offsetHeight: 当前元素的高度（border + padding + content）

#### 1.3  操作html属性

> - ele.getAttribute(attr) //获取元素的属性值（自定义属性获取）
> - ele.setAttribute(attr,val); //设置元素的属性
> - ele.removeAttribute(attr) //删除属性attr
> - ele.hasAttribute(attr) //判断是否存在属性attr

#### 1.4 根据元素关系获取其他元素

> - parentElement           获取父级节点元素
> - children                获取元素的全部子元素
> - firstElementChild       获取第一个子元素
> - lastElementChild        获取最后一个子元素
> - previousElementSibling  获取前一个元素
> - nextElementSibling      获取下一个元素

#### 1.5 获取css样式（非内联样式）

> 得到当前元素计算后的所有样式

> - getComputedStyle(ele,pseudo) （标准）
>   - ele:要获取样式的元素
>   - pseudo:伪元素样式字符(可选)，可获取伪元素样式
> - ele.currentStyle （IE8-）

#### 1.6 table对象(了解)

##### 1.6.1 table对象属性&方法

> - rows    返回包含表格中所有行的一个数组
> - tBodies 返回包含表格中所有 tbody 的一个数组
> - insertRow(index)    在表格中插入一个新行。
> - deleteRow(index)    从表格删除一行。

##### 1.6.2 tr对象属性&方法

> - cells   返回包含表格中所有单元格的一个数组
> - rowIndex            返回该行在表中的位置
> - sectionRowIndex     返回在 tBody 、tHead 或 tFoot 中行的位置。
> - insertCell(index)   在一行中的指定位置插入一个空的列
> - deleteCell(index)   删除行中的指定的单元格

##### 1.6.3 td/th对象属性&方法

> - cellIndex   返回单元格在表格行的单元格集合中的位置。





