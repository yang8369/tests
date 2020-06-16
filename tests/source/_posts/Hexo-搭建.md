---

title: Hexo-Yilia搭建

copyright: true
date: 2020-6-6 11:27:15

toc: true
tags: [Hexo,Yilia]
categories: [Hexo,博客搭建]
declare: true
---



## 配置Hexo - Yilia

 Hexo 博客框架中文官网+文档：https://hexo.bootcss.com/ 

根据大佬的 博客 开始 搭建 自己的 小博客 

 [https://janycode.github.io/2016/05/26/08_%E6%A1%86%E6%9E%B6%E6%8A%80%E6%9C%AF/00_Hexo/01-Hexo+GitHub%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2/](https://janycode.github.io/2016/05/26/08_框架技术/00_Hexo/01-Hexo+GitHub搭建博客/) 

<!--more--> 

经过不断的查询 错误 终于搭建好博客的基本数据

勉强从小白 度过

再添加主题，这里我选择 比较 清新的 主题 Yilia 

 感谢大佬的主题分享，http://litten.me/ 

主题下载地址  https://github.com/litten/hexo-theme-yilia 

再从大佬的博客中完善 Yilia 
原文链接：https://blog.csdn.net/dta0502/article/details/89607895

原文链接:  https://anyway1314.cn/post/25766.html 



## 一、GitHub下载Yilia主题

```
 $ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia 
```

下载的位置是在 Hexo/thems/yilia

## 二、分类的构建

### 1、添加categiories链接

打开yilia/_config.yml文件，menu处做出以下修改

```
menu:
  主页: /
  分类: /categories
  归档: /archives

```

### 2、分类页面的构建

- 新建categories页面

```
hexo new page categories
```

该命令在source目录下生成一个categories目录，categories目录下有一个index.md文件。

修改categories/index.md为：

```
---
title: 文章分类
date: 2019-12-04 18:20:29
type: "categories"
layout: "categories"
comments: false
---
```

生成html

```
hexo g
hexo s
```

访问 http://localhost:4000/categories/ ，即可看到categories页面，只不过现在的页面只有标题。

### 3、修改 yilia 主题

修改yilia\source\main.0cf68a.css，将下面的内容添加进去：

```
category-all-page {
    margin: 30px 40px 30px 40px;
    position: relative;
    min-height: 70vh;
  }
  .category-all-page h2 {
    margin: 20px 0;
  }
  .category-all-page .category-all-title {
    text-align: center;
  }
  .category-all-page .category-all {
    margin-top: 20px;
  }
  .category-all-page .category-list {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  .category-all-page .category-list-item-list-item {
    margin: 10px 15px;
  }
  .category-all-page .category-list-item-list-count {
    color: $grey;
  }
  .category-all-page .category-list-item-list-count:before {
    display: inline;
    content: " (";
  }
  .category-all-page .category-list-item-list-count:after {
    display: inline;
    content: ") ";
  }
  .category-all-page .category-list-item {
    margin: 10px 10px;
  }
  .category-all-page .category-list-count {
    color: $grey;
  }
  .category-all-page .category-list-count:before {
    display: inline;
    content: " (";
  }
  .category-all-page .category-list-count:after {
    display: inline;
    content: ") ";
  }
  .category-all-page .category-list-child {
    padding-left: 10px;
    }
```



### 4、多层分类

新建yilia/layout/categories.ejs，输入：

```
<article class="article article-type-post show">
  <header class="article-header" style="border-bottom: 1px solid #ccc">
  <h1 class="article-title" itemprop="name">
    <%= page.title %>
  </h1>
  </header>

  <% if (site.categories.length){ %>
  <div class="category-all-page">
    <h2>共计&nbsp;<%= site.categories.length %>&nbsp;个分类</h2>
    <%- list_categories(site.categories, {
      show_count: true,
      class: 'category-list-item',
      style: 'list',
      depth: 2,
      separator: ''
    }) %>
  </div>
  <% } %>
</article>

```



### 5、修改自己的文章

```
---

title: HTML入门笔记

copyright: true
date: 2018-11-23 21:07:15

toc: true
tags: [HTML,前端]
categories: [前端,HTML]
---


```



## 三、yilia下的_config.yml完善

subnav中添加github、知乎、mail等链接。

smart_menu处去掉friends：

```
smart_menu:
  innerArchive: '所有文章'
  friends: false
  aboutme: '关于我'


```

aboutme处添加自己的介绍：

```
aboutme: 东南大学在读研究生
```



## 四、点击所有文章提示缺失模块

### 1、问题

点击所有文章提示缺失模块

### 2、解决办法

* 确保node版本大于6.2
* 在博客根目录（注意不是yilia根目录）执行以下命令：npm install hexo-generator-json-content --save
* 在hexo的blog根目录_config.yml里添加配置（保持格式，不要改动任何空格缩进），关掉hexo s之后执行hexo g重新生成：

```
jsonContent:
  meta: false
  pages: false
  posts:
    title: true
    date: true
    path: true
    text: false
    raw: false
    content: false
    slug: false
    updated: false
    comments: false
    link: false
    permalink: false
    excerpt: false
    categories: false
    tags: true
```

## 五、头像/图标设置

### 1、存放位置

头像、图标图片的存放位置是/themes/yilia/source/下任意位置，可以自己新建一个文件夹存放，我存放在assets文件夹下。

### 2、配置设置

配置文件为/themes/yilia/_config.yml。

* 设置头像为配置文件中avatar一项

* 设置图标为配置文件中favicon一项

由于设置路径的根目录/themes/yilia/source/，因此，我的头像存放的地址是/themes/yilia/source/assets/me.png，设置则为avatar: /assets/me.png。

图标同理。

## 六、添加评论

### 1、注册learncloud账号，创建应用(需要先实名认证账号)

### 2、应用设置里找到 `App ID` 和 `App Key`

### 3、打开yilia主题目录下的`_config.yml`,修改设置

```
valine:
  enable: true
  appid: '' #Leancloud应用的App ID
  appkey: '' #Leancloud应用的App Key
  #这里的appid和appkey如果配置失败可以试试改成app_id和app_key
  verify: false #验证码
  notify: false #评论回复提醒
  avatar: mm #评论列表头像样式：
  avatar_cdn: '' #头像CDN
  placeholder: '友情提醒，留下正确的邮箱地址可以第一时间获取评论反馈' #评论框占位符
  pageSize: 10 #评论分页
  visitor: true #阅读统计
```



### 4、找到`yilia\layout\_partial\`目录下的`article.ejs`、添加代码:

在你的hexo目录/theme/yilia/layout/_partial/article.ejs文件中最后一行“<% } %>”之前添加如下内容：

```
<% if (theme.valine && theme.valine.appid && theme.valine.appkey){ %>
    <section id="comments" class="comments">
      <style>
        .comments{margin:30px;padding:10px;background:#fff}
        @media screen and (max-width:800px){.comments{margin:auto;padding:10px;background:#fff}}
      </style>
      <%- partial('post/valine', {
        key: post.slug,
        title: post.title,
        url: config.url+url_for(post.path)
        }) %>
    </section>
<% } %>

```





## 5、在Hexo\themes\yilia\layout\_partial\postt目录下新建`valine.ejs`,内容如下:



```
<div id="vcomment"></div>
<script src="//cdn.jsdelivr.net/npm/jquery/dist/jquery.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/leancloud-storage/dist/av-min.js"></script>
<script src='//cdn.jsdelivr.net/npm/valine/dist/Valine.min.js'></script>
<script>
   var notify = '<%= theme.valine.notify %>' == true ? true : false;
   var verify = '<%= theme.valine.verify %>' == true ? true : false;
   new Valine({
            av: AV,
            el: '#vcomment',
            notify: notify,
            verify: verify,
            app_id: "<%= theme.valine.appid %>",
            app_key: "<%= theme.valine.appkey %>",
            placeholder: "<%= theme.valine.placeholder %>",
            avatar: "<%= theme.valine.avatar %>",
            avatar_cdn: "<%= theme.valine.avatar_cdn %>",
            pageSize: "<%= theme.valine.pageSize %>"
    });
</script>

```



## 七、侧边栏添加音乐

### 1、网易云音乐外链播放器生成

登录网页版网易云音乐，打开一首歌，点击 “生成外链播放器”。

### 2、侧栏添加背景音乐

打开/hexo/themes/yilia/layout/_partial/left-col.ejs文件，把音乐HTML代码粘贴进去，可以添加样式，改变大小，这是我的代码：

```
<nav class="header-nav">
    <div class="social">
        <% for (var i in theme.subnav){ %>
            <a class="<%= i %>" target="_blank" href="<%- url_for(theme.subnav[i]) %>" title="<%= i %>"><i class="icon-<%= i %>"></i></a>
        <%}%>
    </div>

    <!--音乐播放插件-->
    <div style="margin-top:30px;">
        <iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=240 height=52 src="//music.163.com/outchain/player?type=2&id=33035954&auto=1&height=32"></iframe>
    </div>
</nav>

```

## 八、添加页面访问量

### 1、添加站点访问量

下面是个人改变完成后的\themes\yilia\layout\_partial\footer.ejs文件：

```<footer id="footer">
  <div class="outer">
    <div id="footer-info">
    	<div class="footer-left">
    		&copy; <%= date(new Date(), 'YYYY') %> <%= config.author || config.title %>
    	</div>
      	<div class="footer-right">
    
    
            <script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
      		<span id="busuanzi_container_site_pv">
                本站总访问量：<span id="busuanzi_value_site_pv"></span>次
            </span>
            <span class="post-meta-divider">|</span>
            <span id="busuanzi_container_site_uv">
                本站访客数：<span id="busuanzi_value_site_uv"></span>人
            </span>
    
    
      	</div>
    </div>
  </div>
</footer>
```

其中空格间那部分是额外添加的，这部分处于页脚的右边（原来是主题的说明，这里已删去）。

### 2、添加文章访问量

下面是个人改变完成后的\themes\yilia\layout\_partial\article.ejs文件：

```      <header class="article-header">
        <%- partial('post/title', {class_name: 'article-title'}) %>
        <% if (!post.noDate){ %>
        <%- partial('post/date', {class_name: 'archive-article-date', date_format: null}) %>
        <% } %>
    
    
        <% if ( !index ){ %>
          <span class="archive-article-date">
              阅读量 <span id="busuanzi_value_page_pv"></span>
          </span>
        <% } %>
    
    
      </header>
```

正如参考文章所说，空格间那部分是额外添加的，保证了每篇文章都有阅读量统计，同时这里加一个if判断，如果是首页不显示该文章的访问量。

## 九、Hexo-Yilia网站运行时间

在hexo/themes/yelee/layout/_partial/footer.ejs文件中<div class="footer-left">内（具体位置可自选）加入如下代码：

			<span id="timeDate">载入天数...</span><span id="times">载入时分秒...</span>
			<script>
				var now = new Date(); 
				function createtime() { 
					var grt= new Date("11/23/2018 20:00:00");//此处修改你的建站时间或者网站上线时间 
					now.setTime(now.getTime()+250); 
					days = (now - grt ) / 1000 / 60 / 60 / 24; dnum = Math.floor(days); 
					hours = (now - grt ) / 1000 / 60 / 60 - (24 * dnum); hnum = Math.floor(hours); 
					if(String(hnum).length ==1 ){hnum = "0" + hnum;} minutes = (now - grt ) / 1000 /60 - (24 * 60 * dnum) - (60 * hnum); 
					mnum = Math.floor(minutes); if(String(mnum).length ==1 ){mnum = "0" + mnum;} 
					seconds = (now - grt ) / 1000 - (24 * 60 * 60 * dnum) - (60 * 60 * hnum) - (60 * mnum); 
					snum = Math.round(seconds); if(String(snum).length ==1 ){snum = "0" + snum;} 
					document.getElementById("timeDate").innerHTML = "本站已安全运行 "+dnum+" 天 "; 
					document.getElementById("times").innerHTML = hnum + " 小时 " + mnum + " 分 " + snum + " 秒"; 
				} 
				setInterval("createtime()",250);
			</script>

注意：日期格式11/23/2018 20:00:00。

## 十、字数、阅读时长添加

### 1、安装hexo-wordcount

在博客目录下打开Git Bash，输入命令

```
npm i –save hexo-wordcount
```

### 2、文件配置

在theme\yilia\layout\_partial\post下创建word.ejs文件：

```
<div style="margin-top:10px;">
    <span class="post-time">
      <span class="post-meta-item-icon">
        <i class="fa fa-keyboard-o"></i>
        <span class="post-meta-item-text">  字数统计: </span>
        <span class="post-count"><%= wordcount(post.content) %>字</span>
      </span>
    </span>

    <span class="post-time">
      &nbsp; | &nbsp;
      <span class="post-meta-item-icon">
        <i class="fa fa-hourglass-half"></i>
        <span class="post-meta-item-text">  阅读时长: </span>
        <span class="post-count"><%= min2read(post.content) %>分</span>
      </span>
    </span>
</div>

```

 然后在 `themes/yilia/layout/_partial/article.ejs`中添加 

```
<div class="article-inner">
    <% if (post.link || post.title){ %>
      <header class="article-header">
        <%- partial('post/title', {class_name: 'article-title'}) %>
        <% if (!post.noDate){ %>
        <%- partial('post/date', {class_name: 'archive-article-date', date_format: null}) %>
        <!-- 需要添加的位置 -->
        <!-- 开始添加字数统计-->
        <% if(theme.word_count && !post.no_word_count){%>
          <%- partial('post/word') %>
          <% } %>
        <!-- 添加完成 -->

        <% } %>
      </header>

```



### 3、开启功能

在站点的（不是主题的）_config.yml中添加下面代码

```
# 是否开启字数统计
#不需要使用，直接设置值为false，或注释掉
word_count: True
```



## 十一、添加版权信息

### 1、添加代码

在themes/yilia/layout/_partial/article.ejs中标注的位置添加代码：

```
<div class="article-entry" itemprop="articleBody">
	<% if (post.excerpt && index){ %>
		<%- post.excerpt %>
		<% if (theme.excerpt_link) { %>
			<a class="article-more-a" href="<%- url_for(post.path) %>#more"><%= theme.excerpt_link %> >></a>
		<% } %>
	<% } else { %>
		<%- post.content %>
	<% } %>
	<-- 在此处添加代码-->
	<% if ((theme.reward_type === 2 || (theme.reward_type === 1 && post.reward)) && !index){ %>
	<div class="page-reward">
		<a href="javascript:;" class="page-reward-btn tooltip-top">
		<div class="tooltip tooltip-east">

```

 添加的代码如下： 

```
<%
  var sUrl = url.replace(/index\.html$/, '');
  sUrl = /^(http:|https:)\/\//.test(sUrl) ? sUrl : 'https:' + sUrl;
%>
<% if ((theme.declare_type === 2 || (theme.declare_type === 1 && post.declare)) && !index){ %>
  <div class="declare">
    <strong>本文作者：</strong>
    <% if(config.author != undefined){ %>
      <%= config.author%>
    <% }else{%>
      <font color="red">请在博客根目录“_config.yml”中填入正确的“author”</font>
    <%}%>
    <br>
    <strong>本文链接：</strong>
    <%= sUrl%>
    <br>
    <strong>版权声明：</strong>
    本作品采用
    <a rel="license" href="<%= theme.licensee_url%>"><%= theme.licensee_name%></a>
    进行许可。转载请注明出处！
    <% if(theme.licensee_img != undefined){ %>
      <br>
      <a rel="license" href="<%= theme.licensee_url%>"><img alt="知识共享许可协议" style="border-width:0" src="<%= theme.licensee_img%>"/></a>
    <% } %>
  </div>
<% } else {%>
  <div class="declare" hidden="hidden"></div>
<% } %>

```

### 2、版权添加样式

在yilia/source/main.0cf68a.css添加如下代码：

```
.declare {
  background-color: #eaeaea;
  margin-top: 2em;
  border-left: 3px solid #ff1700;
  padding: .5em 1em; }

```



### 3、添加配置文件

修改themes/yilia/_config.yml：

```
## 版权声明
declare_type: 1
licensee_url: https://creativecommons.org/licenses/by-nc-sa/4.0/          # 当前应用的版权协议地址。
licensee_name: '知识共享署名-非商业性使用-相同方式共享 4.0 国际许可协议'  # 版权协议的名称
licensee_img: https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png      # 版权协议的Logo

```


在需要进行版权声明的文章的md文件头部，设置属性declare: true。

版权基础设定：

* 0-关闭声明；

* 1-文章对应的md文件里有declare: true属性，才有版权声明；

* 2-所有文章均有版权声明

### 4、修改博客的url

修改主目录下的_config.yml中的url,改成自己的地址。

```
url: https://dta0502.github.io/
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

```



## 十二、鼠标点击小红心的设置

在hexo/themes/yilia/source文件目录下添加love.js文件。

```
!function(e,t,a){function r(){for(var e=0;e<s.length;e++)s[e].alpha<=0?(t.body.removeChild(s[e].el),s.splice(e,1)):(s[e].y--,s[e].scale+=.004,s[e].alpha-=.013,s[e].el.style.cssText="left:"+s[e].x+"px;top:"+s[e].y+"px;opacity:"+s[e].alpha+";transform:scale("+s[e].scale+","+s[e].scale+") rotate(45deg);background:"+s[e].color+";z-index:99999");requestAnimationFrame(r)}function n(){var t="function"==typeof e.onclick&&e.onclick;e.onclick=function(e){t&&t(),o(e)}}function o(e){var a=t.createElement("div");a.className="heart",s.push({el:a,x:e.clientX-5,y:e.clientY-5,scale:1,alpha:1,color:c()}),t.body.appendChild(a)}function i(e){var a=t.createElement("style");a.type="text/css";try{a.appendChild(t.createTextNode(e))}catch(t){a.styleSheet.cssText=e}t.getElementsByTagName("head")[0].appendChild(a)}function c(){return"rgb("+~~(255*Math.random())+","+~~(255*Math.random())+","+~~(255*Math.random())+")"}var s=[];e.requestAnimationFrame=e.requestAnimationFrame||e.webkitRequestAnimationFrame||e.mozRequestAnimationFrame||e.oRequestAnimationFrame||e.msRequestAnimationFrame||function(e){setTimeout(e,1e3/60)},i(".heart{width: 10px;height: 10px;position: fixed;background: #f00;transform: rotate(45deg);-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);}.heart:after,.heart:before{content: '';width: inherit;height: inherit;background: inherit;border-radius: 50%;-webkit-border-radius: 50%;-moz-border-radius: 50%;position: fixed;}.heart:after{top: -5px;}.heart:before{left: -5px;}"),n(),r()}(window,document);

```

在hexo/themes/yilia/layout/_partial/footer.ejs文件的最后， 添加以下代码：

```
<!--页面点击小红心-->
<script type="text/javascript" src="/love.js"></script>
```



## 十三、Hexo-Yilia代码块行号显示错乱问题

这是因为yilia/source/main.0cf68a.css文件中的pre标签的样式造成的，将white-space: pre-wrap;注释掉即可，这个问题是自动换行造成的，使用不自动换行的white-space: pre;即可，这样样式代码块部分会自动出现底部滚动条，行号错乱问题就没有了。

然后改一下滚动块样式：

```
::-webkit-scrollbar-track:hover{background-color:rgba(255, 255, 255, 0.75)}
```



