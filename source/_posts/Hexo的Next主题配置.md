---
title: Hexo的Next主题配置
date: 2019-02-15 17:15:49
tags: "hexo"
categories: "hexo"
top: true
description: 
---

<!-- 标签别名 -->
{% cq %} 
配置Next主题
{% endcq %}

<!-- more -->


```
参考
https://hexo.io/zh-cn/
http://theme-next.iissnan.com/
```



## 下载主题
1. 下载next主题
进入博客下的./themes文件夹，使用git clone下载主题, 加上--depth=1只下载最近的版本，不下载历史提交记录。
这样可以减少文件大小。
```bash
git clone https://github.com/theme-next/hexo-theme-next.git hexo-theme-next --depth=1
```




2. 修改主题
进入hexo-theme-next文件夹下，打开_config.yml文件, 选择主题。Next有4个主题。
```
# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes
#scheme: Muse
#scheme: Mist
scheme: Pisces
#scheme: Gemini
```

3. 启动本地预览服务
```
hexo s
```
在网页中输入localhost:4000查看当前主题。
如果需要放到xxx.github.io上，则使用如下命令：
```
hexo generate --deploy
```



## 优化


### 1. 头像设置

###### 待更新



### 2. 网站logo设置

###### 待更新



### 3. 侧栏设置

###### 待更新



### 4. 修改语言

在根目录的_config.yml中，文件开头的语言选择为中文(可选语言，可查看主题下的language目录)
```
# Site
title: 
subtitle:
description:
keywords:
author: 
language: zh-CN 
timezone:
```

### ==5. 设置RSS==

1、先安装 hexo-generator-feed 插件
```
npm install hexo-generator-feed --save
```

2、打开 站点配置文件 找到Extensions在下面添加
```
# RSS订阅
feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
```
3、打开 主题配置文件 找到rss，设置为
```
rss: /atom.xml
```



### 6. 添加分类模块

1. 添加关于页面
```
hexo new page "about"
```
在source文件夹下就会有about文件夹，编辑index.md，然后进入主题的_config.yml中，menu下的#about注释去掉

2. 添加目录云、标签云页面
```
hexo new page "tags"
hexo new page "categories"
```
然后设置同上，去掉主题配置文件中的注释，调整菜单顺序



### 7. 添加搜索功能

1、安装 hexo-generator-searchdb 插件
```
npm install hexo-generator-searchdb --save
```

2、打开 站点配置文件 找到Extensions在下面添加
```
# 搜索
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```

3、打开 主题配置文件 找到Local search，将enable设置为true



### 8. 添加阅读全文按钮

在文章中只要写成如下格式即可：
其中摘要部分是除了文件头的title,date,tags之外的内容，如果没有，则无法实现此功能。

```
这是摘要

<!-- more -->

这是全文
```
需要注意的是，点击 阅读全文 之后，文章会自动定位到 所在位置，想要修改成从头阅读需要修改 主题配置文件 _config.yml 文件：
```
# Automatically scroll page to section which is under <!-- more --> mark.
scroll_to_more: false
```



### 9. 设置网站缩略图标

把你的图片（png或jpg格式，不是favicon.ico）放在themes/next/source/images里，然后打开 主题配置文件 找到favicon，将small、medium、apple_touch_icon三个字段的值都设置成/images/图片名.jpg就可以了，其他字段都注释掉。

```
favicon:
  #small: /images/favicon-16x16-next.png
  #medium: /images/favicon-32x32-next.png
  #apple_touch_icon: /images/apple-touch-icon-next.png
  #safari_pinned_tab: /images/logo.svg
  small: /images/favicon-my.png
  medium: /images/favicon-my.png
  apple_touch_icon: /images/favicon-my.png
  safari_pinned_tab: /images/favicon-my.svg
  #android_manifest: /images/manifest.json
  #ms_browserconfig: /images/browserconfig.xml
```



### 10. 设置文章字体的颜色、大小

如果想设置某一句的颜色或大小，只需用html语法写出来就行了
```
<font color="#FF0000"> 我可以设置这一句的颜色哈哈 </font> 
<font size=6> 我还可以设置这一句的大小嘻嘻 </font> 
<font size=5 color="#FF0000"> 我甚至可以设置这一句的颜色和大小呵呵</font>
```



### 11. 设置文字居中

设置方法：
```
<center>这一行需要居中</center>
```



### 12. 添加评论系统

开启Valine
注册Leancloud
我们的评论系统其实是放在Leancloud上的，因此首先需要去注册一个账号

Leancloud官网，点我注册

注册完以后需要创建一个应用，名字可以随便起，然后 进入应用->设置->应用key

获取你的appid 和 appkey 


拿到你的appid和appkey之后，打开主题配置文件 搜索 valine，填入appid 和 appkey

```
valine:
  enable: true
  appid:  your app id
  appkey: your app key
  notify: false # mail notifier , https://github.com/xCss/Valine/wiki
  verify: false # Verification code
  placeholder: ヾﾉ≧∀≦)o来啊，快活啊! 
  guest_info: nick,mail,link
  pageSize: 10
```
  
最后！记得在Leancloud -> 设置 -> 安全中心 -> Web 安全域名 把你的域名加进去

==如需取消某个 页面/文章 的评论，在 md 文件的 front-matter 中增加 comments: false==


### 13. 添加文章访问计数

不蒜子统计
http://theme-next.iissnan.com/third-party-services.html#analytics-busuanzi

编辑 主题配置文件 中的busuanzi_count的配置项。

当enable: true时，代表开启全局开关。若site_uv、site_pv、page_pv的值均为false时，不蒜子仅作记录而不会在页面上显示。
```
# Show Views/Visitors of the website/page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi
busuanzi_count:
  enable: true
  total_visitors: true
  total_visitors_icon: user
  total_views: true
  total_views_icon: eye
  post_views: true
  post_views_icon: eye
```

### 14. 添加站点访问计数

https://blog.csdn.net/qw8880000/article/details/80235391


修改next主题的模板文件
```
把访问量统计放在网页的footer，打开 themes/next/layout/_partial/footer.swig，将下面这段代码添加到里面, 可调整添加位置
    <script async src="//dn-lbstatics.qbox.me/busuanzi/2.3/busuanzi.pure.mini.js"></script>

    <span id="busuanzi_container_site_pv">总访问量<span id="busuanzi_value_site_pv"></span>次</span>
    <span class="post-meta-divider">|</span>
    <span id="busuanzi_container_site_uv">总访客<span id="busuanzi_value_site_uv"></span>人</span>
    <span class="post-meta-divider">|</span>

```



### 15. 分享服务 ==异常，功能未实现==

http://theme-next.iissnan.com/third-party-services.html#share-system

JiaThis
编辑 主题配置文件， 添加/修改字段 jiathis，值为 true。
```
# JiaThis 分享服务
jiathis: true
```



### 16. 给next主题添加打赏

http://theme-next.iissnan.com/theme-settings.html#reward


将微信和支付宝的收款码图片放在\themes\next\source\images目录下，修改主题配置文件。找到reward, 修改如下：
```
reward:
  enable: true
  comment: 谢谢阅读！
  wechatpay: /images/wechat-reward-image.jpg
  alipay: /images/alipay-reward-image.jpg
  #bitcoin: /images/bitcoin.jpg
```


### 16. 站点建立时间

这个时间将在站点的底部显示，例如 © 2013 - 2015。 编辑 主题配置文件，新增字段 since。
```
配置示例
since: 2013
```



### 17. 去掉文章目录标题的自动编号

但是默认的主题会给文章标题带上编号，去掉方法如下：
打开主题配置文件，找到
将number改为false即可



### 18. 文章加密访问

打开 themes/*/layout/_partials/head/head.swig文件,在<meta/>之后插入代码：
```
<script>
    (function(){
        if('{{ page.password }}'){
            if (prompt('请输入密码') !== '{{ page.password }}'){
                alert('密码错误');
                history.back();
            }
        }
    })();
</script>
写文章时加上password: *：

---
title: 2018
date: 2018-10-25 16:10:03
password: 123456
---
```

### 19. Hexo Next背景动画

1. 打开Git进入自己文件夹下/themes/next文件夹下
```
cd themes/next  
```

2. 运行git clone https://github.com/theme-next/theme-next-canvas-nest source/lib/canvas-nest即:
```
git clone https://github.com/theme-next/theme-next-canvas-nest source/lib/canvas-nest
```

3. 进入 thems/next/_config.yml文件下修改 canvas_nest: true(注意: 冒号后面要空格)




### 20. 鼠标点击效果

##### 实现点击出现桃心效果

在/themes/*/source/js/src下新建文件click.js，接着把以下粘贴到click.js文件中。
代码如下：
```
!function(e,t,a){function n(){c(".heart{width: 10px;height: 10px;position: fixed;background: #f00;transform: rotate(45deg);-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);}.heart:after,.heart:before{content: '';width: inherit;height: inherit;background: inherit;border-radius: 50%;-webkit-border-radius: 50%;-moz-border-radius: 50%;position: fixed;}.heart:after{top: -5px;}.heart:before{left: -5px;}"),o(),r()}function r(){for(var e=0;e<d.length;e++)d[e].alpha<=0?(t.body.removeChild(d[e].el),d.splice(e,1)):(d[e].y--,d[e].scale+=.004,d[e].alpha-=.013,d[e].el.style.cssText="left:"+d[e].x+"px;top:"+d[e].y+"px;opacity:"+d[e].alpha+";transform:scale("+d[e].scale+","+d[e].scale+") rotate(45deg);background:"+d[e].color+";z-index:99999");requestAnimationFrame(r)}function o(){var t="function"==typeof e.onclick&&e.onclick;e.onclick=function(e){t&&t(),i(e)}}function i(e){var a=t.createElement("div");a.className="heart",d.push({el:a,x:e.clientX-5,y:e.clientY-5,scale:1,alpha:1,color:s()}),t.body.appendChild(a)}function c(e){var a=t.createElement("style");a.type="text/css";try{a.appendChild(t.createTextNode(e))}catch(t){a.styleSheet.cssText=e}t.getElementsByTagName("head")[0].appendChild(a)}function s(){return"rgb("+~~(255*Math.random())+","+~~(255*Math.random())+","+~~(255*Math.random())+")"}var d=[];e.requestAnimationFrame=function(){return e.requestAnimationFrame||e.webkitRequestAnimationFrame||e.mozRequestAnimationFrame||e.oRequestAnimationFrame||e.msRequestAnimationFrame||function(e){setTimeout(e,1e3/60)}}(),n()}(window,document);
```

在\themes\*\layout\_layout.swig文件末尾添加：
```
<!-- 页面点击小红心 -->
<script type="text/javascript" src="/js/src/clicklove.js"></script>
```

##### 点击爆炸效果

首先在themes\*\source\js 里面建一个叫fireworks.js的文件，代码如下：
```
"use strict";function updateCoords(e){pointerX=(e.clientX||e.touches[0].clientX)-canvasEl.getBoundingClientRect().left,pointerY=e.clientY||e.touches[0].clientY-canvasEl.getBoundingClientRect().top}function setParticuleDirection(e){var t=anime.random(0,360)*Math.PI/180,a=anime.random(50,180),n=[-1,1][anime.random(0,1)]*a;return{x:e.x+n*Math.cos(t),y:e.y+n*Math.sin(t)}}function createParticule(e,t){var a={};return a.x=e,a.y=t,a.color=colors[anime.random(0,colors.length-1)],a.radius=anime.random(16,32),a.endPos=setParticuleDirection(a),a.draw=function(){ctx.beginPath(),ctx.arc(a.x,a.y,a.radius,0,2*Math.PI,!0),ctx.fillStyle=a.color,ctx.fill()},a}function createCircle(e,t){var a={};return a.x=e,a.y=t,a.color="#F00",a.radius=0.1,a.alpha=0.5,a.lineWidth=6,a.draw=function(){ctx.globalAlpha=a.alpha,ctx.beginPath(),ctx.arc(a.x,a.y,a.radius,0,2*Math.PI,!0),ctx.lineWidth=a.lineWidth,ctx.strokeStyle=a.color,ctx.stroke(),ctx.globalAlpha=1},a}function renderParticule(e){for(var t=0;t<e.animatables.length;t++){e.animatables[t].target.draw()}}function animateParticules(e,t){for(var a=createCircle(e,t),n=[],i=0;i<numberOfParticules;i++){n.push(createParticule(e,t))}anime.timeline().add({targets:n,x:function(e){return e.endPos.x},y:function(e){return e.endPos.y},radius:0.1,duration:anime.random(1200,1800),easing:"easeOutExpo",update:renderParticule}).add({targets:a,radius:anime.random(80,160),lineWidth:0,alpha:{value:0,easing:"linear",duration:anime.random(600,800)},duration:anime.random(1200,1800),easing:"easeOutExpo",update:renderParticule,offset:0})}function debounce(e,t){var a;return function(){var n=this,i=arguments;clearTimeout(a),a=setTimeout(function(){e.apply(n,i)},t)}}var canvasEl=document.querySelector(".fireworks");if(canvasEl){var ctx=canvasEl.getContext("2d"),numberOfParticules=30,pointerX=0,pointerY=0,tap="mousedown",colors=["#FF1461","#18FF92","#5A87FF","#FBF38C"],setCanvasSize=debounce(function(){canvasEl.width=2*window.innerWidth,canvasEl.height=2*window.innerHeight,canvasEl.style.width=window.innerWidth+"px",canvasEl.style.height=window.innerHeight+"px",canvasEl.getContext("2d").scale(2,2)},500),render=anime({duration:1/0,update:function(){ctx.clearRect(0,0,canvasEl.width,canvasEl.height)}});document.addEventListener(tap,function(e){"sidebar"!==e.target.id&&"toggle-sidebar"!==e.target.id&&"A"!==e.target.nodeName&&"IMG"!==e.target.nodeName&&(render.play(),updateCoords(e),animateParticules(pointerX,pointerY))},!1),setCanvasSize(),window.addEventListener("resize",setCanvasSize,!1)}"use strict";function updateCoords(e){pointerX=(e.clientX||e.touches[0].clientX)-canvasEl.getBoundingClientRect().left,pointerY=e.clientY||e.touches[0].clientY-canvasEl.getBoundingClientRect().top}function setParticuleDirection(e){var t=anime.random(0,360)*Math.PI/180,a=anime.random(50,180),n=[-1,1][anime.random(0,1)]*a;return{x:e.x+n*Math.cos(t),y:e.y+n*Math.sin(t)}}function createParticule(e,t){var a={};return a.x=e,a.y=t,a.color=colors[anime.random(0,colors.length-1)],a.radius=anime.random(16,32),a.endPos=setParticuleDirection(a),a.draw=function(){ctx.beginPath(),ctx.arc(a.x,a.y,a.radius,0,2*Math.PI,!0),ctx.fillStyle=a.color,ctx.fill()},a}function createCircle(e,t){var a={};return a.x=e,a.y=t,a.color="#F00",a.radius=0.1,a.alpha=0.5,a.lineWidth=6,a.draw=function(){ctx.globalAlpha=a.alpha,ctx.beginPath(),ctx.arc(a.x,a.y,a.radius,0,2*Math.PI,!0),ctx.lineWidth=a.lineWidth,ctx.strokeStyle=a.color,ctx.stroke(),ctx.globalAlpha=1},a}function renderParticule(e){for(var t=0;t<e.animatables.length;t++){e.animatables[t].target.draw()}}function animateParticules(e,t){for(var a=createCircle(e,t),n=[],i=0;i<numberOfParticules;i++){n.push(createParticule(e,t))}anime.timeline().add({targets:n,x:function(e){return e.endPos.x},y:function(e){return e.endPos.y},radius:0.1,duration:anime.random(1200,1800),easing:"easeOutExpo",update:renderParticule}).add({targets:a,radius:anime.random(80,160),lineWidth:0,alpha:{value:0,easing:"linear",duration:anime.random(600,800)},duration:anime.random(1200,1800),easing:"easeOutExpo",update:renderParticule,offset:0})}function debounce(e,t){var a;return function(){var n=this,i=arguments;clearTimeout(a),a=setTimeout(function(){e.apply(n,i)},t)}}var canvasEl=document.querySelector(".fireworks");if(canvasEl){var ctx=canvasEl.getContext("2d"),numberOfParticules=30,pointerX=0,pointerY=0,tap="mousedown",colors=["#FF1461","#18FF92","#5A87FF","#FBF38C"],setCanvasSize=debounce(function(){canvasEl.width=2*window.innerWidth,canvasEl.height=2*window.innerHeight,canvasEl.style.width=window.innerWidth+"px",canvasEl.style.height=window.innerHeight+"px",canvasEl.getContext("2d").scale(2,2)},500),render=anime({duration:1/0,update:function(){ctx.clearRect(0,0,canvasEl.width,canvasEl.height)}});document.addEventListener(tap,function(e){"sidebar"!==e.target.id&&"toggle-sidebar"!==e.target.id&&"A"!==e.target.nodeName&&"IMG"!==e.target.nodeName&&(render.play(),updateCoords(e),animateParticules(pointerX,pointerY))},!1),setCanvasSize(),window.addEventListener("resize",setCanvasSize,!1)};
```
在\themes\*\layout\includes footer.swig文件中添加如下代码，自己想放那也可以放那里。
```
{% if theme.fireworks %}
    <canvas class="fireworks" style="position: fixed;left: 0;top: 0;z-index: 1; pointer-events: none;" ></canvas> 
    <script type="text/javascript" src="//cdn.bootcss.com/animejs/2.2.0/anime.min.js"></script> 
    <script type="text/javascript" src="/js/fireworks.js"></script>
  {% endif %}
```
打开主题配置文件_config.yml，在里面最后写下：
```
# Fireworks  点击爆炸效果
fireworks: true
```



### 21. 页面动画人物

安装模块:
博客根目录选择cmd命令窗口或者git bash 输入以下代码，安装插件

操作：
```
npm install --save hexo-helper-live2d
```

下载模型
作者动画展示网站https://huaji8.top/post/live2d-plugin-2.0/

```
live2d-widget-model-chitose
live2d-widget-model-epsilon2_1
live2d-widget-model-gf
live2d-widget-model-haru/01 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haru/02 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haruto
live2d-widget-model-hibiki
live2d-widget-model-hijiki
live2d-widget-model-izumi
live2d-widget-model-koharu
live2d-widget-model-miku
live2d-widget-model-ni-j
live2d-widget-model-nico
live2d-widget-model-nietzsche
live2d-widget-model-nipsilon
live2d-widget-model-nito
live2d-widget-model-shizuku
live2d-widget-model-tororo
live2d-widget-model-tsumiki
live2d-widget-model-unitychan
live2d-widget-model-wanko
live2d-widget-model-z16
```
选好对应的模型，使用 npm install 模型的包名来安装

比如我选择的的是live2d-widget-model-hijiki 模型包

在hexo博客根目录选择cmd命令窗口或者git bash 输入以下代码
```
npm install live2d-widget-model-hijiki
```
执行安装就完事了

配置
请向Hexo的 _config.yml 文件添加配置.

操作：
打开个人Hexo博客文件根目录下的 _config.yml 文件，在最后添加一下代码
示例:
```
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  debug: false
  model:
    use: live2d-widget-model-hijiki
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: true
```

插件部署与应用就完成了，接下来就是部署hexo博客和个人主页



### 22. 字数统计和阅读时长

1. 安装 hexo-wordcount
```
npm install --save hexo-wordcount
```
先安装插件。

post添加
打开hexo\themes\hexo-theme-next\layout\macro路径下的post.swig文件，找到这段代码后
```
{% if not is_index and theme.busuanzi_count.enable and theme.busuanzi_count.post_views %}
    <span class="post-meta-divider">|</span>
    <span class="post-meta-item-icon"
    {% if not theme.post_meta.item_text %} title="{{ __('post.views') }}" {% endif %}>
    <i class="fa fa-{{ theme.busuanzi_count.post_views_icon }}"></i>
    {% if theme.post_meta.item_text %} {{__('post.views') + __('symbol.colon') }} {% endif %}
    <span class="busuanzi-value" id="busuanzi_value_page_pv" ></span>
    </span>
            

```

```

在endif上面，即本文代码块那个空行处添加以下代码

<span class="post-meta-divider">|</span>
<span title="{{__('post.wordcount') }}"><span class="post-meta-item-icon"><i class="fa fa-file-word-o"></i></span>字数： {{ wordcount(post.content) }}</span>


```



### 23. 显示当前浏览进度

修改themes/*/_config.yml，把 false 改为 true：
```
# Back to top in sidebar
b2t: true

# Scroll percent label in b2t button
scrollpercent: true
```



### 24. 置顶文章

安装支持插件
```
npm install hexo-helper-post-top --save
```

之后在需要置顶文章的 front-matter中，添加 top: true 即可置顶。



### 25. 代码区copy功能
```
[参考](https://www.jianshu.com/p/3e9d614c1e77)
```


### 26.引用站内文章
```
{% post_link 文章文件名（不要后缀） 文章标题（可选） %}
```



### 27. 文本居中的引用
此标签将生成一个带上下分割线的引用，同时引用内文本将自动居中。 文本居中时，多行文本若长度不等，视觉上会显得不对称，因此建议在引用单行文本的场景下使用。 例如作为文章开篇引用 或者 结束语之前的总结引用。

使用方式
HTML方式：使用这种方式时，给 img 添加属性 class="blockquote-center" 即可。
标签方式：使用 centerquote 或者 简写 cq。
此标签要求 NexT 的版本在 0.4.5 或以上。 若你正在使用的版本比较低，可以选择使用 HTML 方式。

 标签调用方法
 ```
<!-- HTML方式: 直接在 Markdown 文件中编写 HTML 来调用 -->
<!-- 其中 class="blockquote-center" 是必须的 -->
<blockquote class="blockquote-center">blah blah blah</blockquote>

<!-- 标签 方式，要求版本在0.4.5或以上 -->
{% centerquote %}blah blah blah{% endcenterquote %}

<!-- 标签别名 -->
{% cq %} blah blah blah {% endcq %}
```


### 28. 插入图片

1. 安装插件
```
npm install hexo-asset-image --save
```

2. 配置
将_config.yml文件中的配置项post_asset_folder设为true后，执行命令
``` 
hexo new post_name
```
在source/_posts中会生成文章post_name.md和同名文件夹post_name。将图片资源放在post_name中，文章就可以使用相对路径引用图片资源了。

```
_posts/post_name/image.jpg

![](image.jpg)
```
上述是markdown的引用方式，图片只能在文章中显示，但无法在首页中正常显示。







#####

添加文章末尾版权声明
找到post.swig文件，在footer.post-footer中添加如下代码。

copy时去掉{% raw %}和{% endraw %}
```
<footer class="post-footer">
    {% if not is_index %}
        <div class="copyright" style="clear:both;">
           <p><span>本文标题:</span><a href="{{ url_for(post.path) }}">{{ post.title }}</a></p>
           <p><span>文章作者:</span><a href="/" title="访问 {{ theme.author }} 的个人博客">{{ theme.author }}</a></p>
           <p><span>发布时间:</span>{{ post.date.format("YYYY年M月D日 - HH时MM分") }}</p>
           <p><span>本文字数:</span><span class="page-count">本文一共有{{ wordcount(page.content) }}字</span></p>
           <p><span>原始链接:</span><a href="{{ url_for(post.path) }}" title="{{ post.title }}">{{ post.permalink }}</a></p>
           <p><span>许可协议:</span><i class="fa fa-creative-commons"></i> <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/" title="Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)">Attribution-NonCommercial 4.0</a></p>
           <p><span>转载请保留以上信息。</span></p>
        </div>
      {% endif %}
</footer>
```
然后需要修改一下样式，找到posts.styl,加入如下样式
````
.post-footer .copyright{
  padding-top: 1.5em;
  padding-left: 1em;
  font-size: 12px;
  line-height: 1em;
  border:1px solid #ccc;
}
```




### ==注意==

#### 1. 如果发现本机已经调试过的页面，发布后，在xxx.github.io上没有变化，可尝试删除.deploy_git文件夹, 使用hexo d重新部署
如果只是本机的配置修改后，没有更新，则重新生成hexo
```
hexo clean
hexo g
hexo s
```







### n. ==修改文章内链接文本样式==

打开文件 themes/next/source/css/_common/components/post/post.styl，在末尾添加
```
.post-body p a {
  color: #0593d3;
  border-bottom: none;
  border-bottom: 1px solid #0593d3;
  &:hover {
    color: #fc6423;
    border-bottom: none;
    border-bottom: 1px solid #fc6423;
  }
}
```
其中选择 .post-body 是为了不影响标题，选择 p 是为了不影响首页“阅读全文”的显示样式,颜色可以自己定义。




