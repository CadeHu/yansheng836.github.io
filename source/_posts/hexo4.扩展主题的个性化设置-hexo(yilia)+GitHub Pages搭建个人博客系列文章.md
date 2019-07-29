---
title: hexo4.扩展主题的个性化设置-hexo(yilia)+GitHub Pages搭建个人博客系列文章
date: 2019-07-29 16:31:23
tags:
 - hexo
toc: true
---

<div style="text-align:center">
<img src="https://s2.ax1x.com/2019/07/29/e8DVS0.th.jpg" width="" height="" title="hexo"></div>

虽然`yilia`主题已经集成了挺多功能的，界面也很不错。但是在某些方面好像还是略有欠缺。这篇博客主要是介绍一些外加的扩展功能。

<!-- more -->

## 一、增加侧边导航栏的SubNav图标

参考：[修改Yilia左下角SubNav的社交图标](https://blog.zscself.com/posts/70677220/)

[Font Awesome:一套绝佳的图标字体库和CSS框架](http://fontawesome.dashgame.com/)

1. 这里只是添加csdn和gitee图标，其他可以参照上面两个链接进行设置。在`H:\Hexo\themes\yilia\source\main.0cf68a.css`文件中添加下面的代码（最好是在gitbub附近，分类管理）

```css
/* 1.这是github的默认图标 */
.icon-github:before {
    content:"\E735"
}
/* 添加码云和CSDN的标签的图标 */
.icon-gitee:before {
    content:"码"
}
.icon-csdn:before {
    content:"C"
}

/* 2.这是之前github的 */
#header .header-nav .social a.github {
    background:#afb6ca;
    border:1px solid #afb6ca
}
#header .header-nav .social a.github:hover {
    border:1px solid #909ab6
}

/* 下面两个是新增的csdn和gitee */
#header .header-nav .social a.csdn {
    background:#C71D23;
    border:1px solid #C71D23;
}
#header .header-nav .social a.csdn:hover {
    border:1px solid #C71D23;
}
#header .header-nav .social a.gitee {
    background:#C71D23;
    border:1px solid #C71D23;
}
#header .header-nav .social a.gitee:hover {
    border:1px solid #C71D23;
}
```

2. 在`H:\Hexo\themes\yilia\_config.yml`的中导航栏`subnav`中添加对应代码，添加后如下

```yml
subnav:
  github: "https://github.com/username"
  gitee: "https://gitee.com/username"
  csdn: "https://blog.csdn.net/username"
```



## 二、新增侧边栏归档、分类、标签内容--有bug（分类、标签）

参考：hexo-theme-next的wiki：[创建分类页面](https://github.com/iissnan/hexo-theme-next/wiki/%E5%88%9B%E5%BB%BA%E5%88%86%E7%B1%BB%E9%A1%B5%E9%9D%A2)

1. 添加一个分类页面，并在菜单中显示页面链接。
   新建一个页面，命名为 categories 。命令如下：
   `hexo new page categories`
2. 编辑刚新建的页面，将页面的类型`type`设置为 categories ，主题将自动为这个页面显示所有分类。

```markdown
title: 分类
date: 2014-12-22 12:39:04
type: "categories"
```

3. 注意：如果有启用多说 或者 Disqus 评论，默认页面也会带有评论。需要关闭的话，请添加字段 comments 并将值设置为 false，如：

```markdown
title: 分类
date: 2014-12-22 12:39:04
type: "categories"
comments: false
```

4. 在菜单中添加链接。编辑主题的` _config.yml` ，将 menu中的 `#categories: /categories `注释去掉，如

```yml
menu:
  home: /
  categories: /categories
  archives: /archives
  tags: /tags
Add a custom footer
```



## 三、设定站点建立时间--有bug（没有实现）

参考：[https://github.com/iissnan/hexo-theme-next/wiki/%E8%AE%BE%E5%AE%9A%E7%AB%99%E7%82%B9%E5%BB%BA%E7%AB%8B%E6%97%B6%E9%97%B4](https://github.com/iissnan/hexo-theme-next/wiki/设定站点建立时间)

这个时间将在站点的底部显示，例如 `? 2013 - 2015`

编辑**主題**的 `_config.yml`，新增字段 `since`。

```
since: 2013
```



## 四、添加字数统计和阅读时长功能

参考：[hexo下yilia主题添加字数统计和阅读时长功能](https://blog.csdn.net/weixin_34259232/article/details/91182835)

1. 安装 hexo-wordcount
   在博客目录下打开Git Bash Here,输入命令:
   `npm i --save hexo-wordcount`
2. 文件配置
   在`theme\yilia\layout\_partial\post`下创建word.ejs文件：

```ejs
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

 然后在`themes/yilia/layout/_partial/article.ejs`中添加:

```ejs
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

3. 开启功能
   在站点的_config.yml中添加下面代码:

```yml
# 是否开启字数统计
#不需要使用，直接设置值为false，或注释掉
word_count: True
```

## 五、添加“不蒜子”访问量统计功能

官网：不蒜子 - 极简网页计数器：<http://busuanzi.ibruce.info/>

参考：[Hexo博客添加访问量统计]([https://joeybling.github.io/2019/03/13/Hexo%E5%8D%9A%E5%AE%A2%E6%B7%BB%E5%8A%A0%E8%AE%BF%E9%97%AE%E9%87%8F%E7%BB%9F%E8%AE%A1/](https://joeybling.github.io/2019/03/13/Hexo博客添加访问量统计/))

<font color="red">注意：本地测试时，访问量是不准确的！</font>

1. 配置是否开启不蒜子访问量统计功能

在`themes/yilia/_config.yml`添加属性

```yml
# 是否开启访问量统计功能(不蒜子)
busuanzi:
 enable: true
```

2. 引入不蒜子并添加站点访问量

 在`themes/yilia/layout/_partial/footer.ejs`末尾(</footer>之前)添加如下代码

```ejs
<% if (theme.busuanzi && theme.busuanzi.enable){ %>
        <!-- 不蒜子统计 -->
        <span id="busuanzi_container_site_pv">
                本站总访问量<span id="busuanzi_value_site_pv"></span>次
        </span>
        <span class="post-meta-divider">|</span>
        <span id="busuanzi_container_site_uv" style='display:none'>
                本站访客数<span id="busuanzi_value_site_uv"></span>人
        </span>
        <script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
  <% } %>
```

3. 添加文章访问量

我找到的添加位置主要有两种，下面会上图，可以选择自己喜欢的，推荐第一种。
3.1 这种形式是：外面不显示，只在文章里面才显示，位置为右上角时间的右边。

在`themes/yilia/layout/_partial/post/date.ejs`开头添加如下代码

```ejs
<% if (theme.busuanzi && theme.busuanzi.enable && !index){ %>
        <!-- 不蒜子统计 -->
        <span id="busuanzi_container_page_pv" style='display:none' class="<%= class_name %>">
              <i class="icon-smile icon"></i> 阅读数：<span id="busuanzi_value_page_pv"></span>次
        </span>
<% } %>
```

主页样式：![enG0f0.jpg](https://s2.ax1x.com/2019/07/26/enG0f0.jpg)

文章样式（注意右上角）：![enGDpV.jpg](https://s2.ax1x.com/2019/07/26/enGDpV.jpg)



3.2 这种形式是：显示在标签的后面，即不仅文章里面会显示，外面主页也会显示，个人感觉体验略差。
参考：[hexo yilia 文章浏览量统计](https://codegitz.github.io/2018/04/13/hexo-yilia-文章浏览量统计/)

需要修改的文件：`H:\Hexo\themes\yilia\layout\_partial\article.ejs`

```ejs
     <%- partial('post/tag') %>

    <!-- 文末访问量统计（开始） -->
    <span id="busuanzi_container_page_pv">
        |阅读量:<span id="busuanzi_value_page_pv"></span>次
    </span>
    <!-- 文末访问量统计（结束） -->
```

主页和文章样式（注意标签后面，因为之前忘记截图了，这是我自己标记的位置，不是实际显示效果）：![enGwYq.jpg](https://s2.ax1x.com/2019/07/26/enGwYq.jpg)



## 六、设置文章置顶功能

参考：解决Hexo博客文章置顶问题：<https://zhwhong.cn/2017/03/23/deal-with-hexo-article-top-problem/>

（这篇博客用的是另一个基于yilia的主题，感觉还是挺不错的，github：<https://github.com/MOxFIVE/hexo-theme-yelee>，但是也停止更新很久了……）

原理：在Hexo生成首页HTML时，将top值高的文章排在前面，达到置顶功能。

修改Hexo文件夹下的`node_modules/hexo-generator-index/lib/generator.js`，在生成文章之前进行文章top值排序。



<font color="red">注意：一般情况下，git默认是忽略该文件的，所以应该先将该文件加到仓库，提交一次进行备份，然后再进行修改，不然不能实现备份该文件功能，可参考下面的示例代码进行操作：</font>

```shell
# 为了方便起见，不修改.gitignored文件，直接将该文件强制加入仓库。
# 注意：修改后，再添加该文件时也要强制添加
git add -f node_modules/hexo-generator-index/lib/generator.js

# 参看是否添加成功，应该会变成绿色，表示已加入暂存区
git status

# 提交一次
git commit -m "back up node_modules/hexo-generator-index/lib/generator.js"
```



下面是`generator.js`修改后的代码：

```js
'use strict';

var pagination = require('hexo-pagination');

module.exports = function(locals) {
  var config = this.config;
  var posts = locals.posts.sort(config.index_generator.order_by);

  posts.data = posts.data.sort(function(a, b) {
      if(a.top && b.top) {
          if(a.top == b.top) return b.date - a.date;
          else return b.top - a.top;
      }
      else if(a.top && !b.top) {
          return -1;
      }
      else if(!a.top && b.top) {
          return 1;
      }
      else return b.date - a.date;
  });

  var paginationDir = config.pagination_dir || 'page';

  return pagination('', posts, {
    perPage: config.index_generator.per_page,
    layout: ['index', 'archive'],
    format: paginationDir + '/%d/',
    data: {
      __index: true
    }
  });
};
```

------

补充另一种：置顶方式：通过插件来实现。参考：[Hexo—Yilia主题的归档页置顶](https://www.writebug.site/2018/04/29/Hexo——Yilia主题的归档页置顶/)

1. blog目录下执行以下命令：

```shell
npm uninstall hexo-generator-index --save
npm install hexo-generator-index-pin-top --save
```

2. 然后在文章头添加 top:true 如：

```markdown
---
title: 终于装好Hexo啦
date: 2018-04-19 00:04:46
tags: 心情
top: true
categories:
- 你好，世界
---
```



## 七、添加背景音乐

参考：[hexo+yilia个性化之-添加背景音乐](https://www.writebug.site/2018/04/21/hexo-yilia%E4%B8%AA%E6%80%A7%E5%8C%96%E4%B9%8B-%E6%B7%BB%E5%8A%A0%E8%83%8C%E6%99%AF%E9%9F%B3%E4%B9%90/)

1. 到网易云官网获取音乐外链：搜索音乐-->生成外链播放器-->复制代码
2. 打开路径 `themes/yilia/layout/_partial/left-col.ejs`，在`</nav>`上面添加代码，就像下面这样。

```ejs
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=228 height=86 src="//music.163.com/outchain/player?type=2&id=1371939273&auto=0&height=66"></iframe>
</nav>
```

3. 根据需要设置宽高属性，宽建议228。



## 八、为博客设置404页面

参考：github官网介绍：<https://help.github.com/cn/articles/creating-a-custom-404-page-for-your-github-pages-site>

在`/source/`目录下新建`404.md`在头部添加属性`permalink: /404.html`，页面内容可以自定义。

例1：

```markdown
---
# example 404.md
title: 404 Not Found：该页无法显示
permalink: /404.html
---

# 404

Page not found! :(
```



推荐使用腾讯公益404页面（注意要把首页链接换成自己的）：

```mariadb
---
title: 404 Not Found：该页无法显示
date: 2019-07-26 21:51:29
permalink: /404.html
---

<!DOCTYPE html>
<html>
    <head>
         <meta charset="UTF-8" />
         <title>404</title>                           
    </head>
    <body>
         <script type="text/javascript" src="//qzonestyle.gtimg.cn/qzone/hybrid/app/404/search_children.js" homePageName="返回首页" homePageUrl="https://www.yansheng.xyz/"></script>
	</body>
</html>
```

然后转换、部署就可以了。

```shell
hexo clean
hexo g
hexo d
```



## 九、为头像增加旋转效果

参考：[hexo模版yilia头像增加旋转效果/](https://qianlei6148.github.io/2018/10/01/hexo模版yilia头像增加旋转效果/)

1.在`themes\yilia\source\`文件夹下
增加一个css文件`avatarrotation.css`用来旋转360度
内容如下：

```css
.left-col #header .profilepic img {
	/* 控制旋转速度时间*/
  -webkit-transition: -webkit-transform 1.0s ease-out;
  -moz-transition: -moz-transform 1.0s ease-out;
  transition: transform 1.0s ease-out;
}
.left-col #header .profilepic img:hover {
	/* 鼠标经过360% */
  -webkit-transform: rotateZ(360deg);
  -moz-transform: rotateZ(360deg);
  transform: rotateZ(360deg);
}
```

2.然后在`themes\yilia\layout\_partial\head.ejs`文件中添加进去创建的`css`文件：
找到`<%- partial('css') %>`，在它的下面添加代码，把刚才写的文件添加进去，**注意！！是在它的下面添加，不然旋转速度将不会生效**

```ejs
<% if (theme.avatarrotation){ %>
	<link rel="stylesheet" type="text/css" href="/./avatarrotation.css">
<% } %>
```

如果`css`不生效，查看`css`中的`href`位置是否写错了，可根据你具体存放的位置写路径。

3.最后在`主题文件_config.yml`中添加

```yml
#头像是否旋转(如果不要旋转取false)
avatarrotation: true
```

重新发布，最终就可以旋转了！



## 十、安装`hexo-admin`插件

github官网：<https://github.com/jaredly/hexo-admin>

### 0.插件介绍

hexo-admin 是一个Hexo博客引擎的管理用户界面插件。这个插件最初是作为本地编辑器设计的，在本地运行hexo使用hexo-admin编写文章，<font color="red">左边写右边预览</font>，然后通过hexo g或hexo d（hexo g是本地渲染，hexo d是将渲染的静态页面发布到GitHub）将生成的静态页面发布到GitHub等静态服务器。如果你使用的是非静态托管服务器，比如自己买的主机搭建的hexo，那么一定要设置hexo-admin  的密码，否则谁都可以编辑你的文章。



### 1.安装管理员并启动

```shell
npm install --save hexo-admin
hexo server -d
open http://localhost:4000/admin/
```



### 2.密码保护

如果您在实时服务器上使用Hexo admin，则需要一些密码保护。要启用此功能，只需在hexo中添加一些配置变量`_config.yml`：

```yml
admin:
  username: myfavoritename
  password_hash: be121740bf988b2225a313fa1f107ca1
  secret: a secret something
```

这`password_hash`是您密码的bcrypt哈希值。本`secret`是用来做饼干的安全，所以这是一个好主意，有它漫长而复杂。

Hexo管理员设置中的实用程序可以散列您的密码并`admin` 为您生成该部分。启动Hexo并转到`Settings > Setup authentification` 并填写您的信息。将生成的YAML复制到您的`_config.yml`。

一旦到位，启动您的hexo服务器，然后`/admin/`将要求您输入密码。



### 3.自定义帖子元数据

要使用管理界面添加和编辑您自己的帖子元数据，请将元数据变量和自定义变量添加到您的hexo中`_config.yml`：

```yml
metadata:
  author_id: defaultAuthorId
  language:
```

您可以提供将用于初始化新帖子元数据的默认值。这些可以是基元或数组。

---

hexo(yilia)+GitHub Pages搭建个人博客系列文章：
1.<a href="https://www.yansheng.xyz/2019/07/29/hexo1.博客备份-hexo(yilia)+GitHub Pages搭建个人博客系列文章/">hexo1.博客备份-hexo(yilia)+GitHub Pages搭建个人博客系列文章</a>
2.<a href="https://www.yansheng.xyz/2019/07/29/hexo2.基本框架搭建-hexo(yilia)+GitHub Pages搭建个人博客系列文章">hexo2.基本框架搭建-hexo(yilia)+GitHub Pages搭建个人博客系列文章</a>
3.<a href="https://www.yansheng.xyz/2019/07/29/hexo3.主题简单个性化设置-hexo(yilia)+GitHub Pages搭建个人博客系列文章">hexo3.主题简单个性化设置-hexo(yilia)+GitHub Pages搭建个人博客系列文章</a>
4.hexo4.扩展主题的个性化设置-hexo(yilia)+GitHub Pages搭建个人博客系列文章