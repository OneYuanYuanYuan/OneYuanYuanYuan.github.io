---
title: 使用hexo写博客
date: 2019-02-18 09:34:07
tags: "hexo"
categories: "hexo"
---

<!-- 标签别名 -->
{% cq %} 
使用hexo写博客
{% endcq %}

<!-- more -->



### 1. 设置文字居中

设置方法：
```
<center>这一行需要居中</center>
```

### 2. 添加标签和分类

```
---
title: Hexo的Next主题配置
date: 2019-02-15 17:15:49
tags: "hexo"
categories: "hexo"
top: true
description: 
---
```


### 3. 置顶文章

安装支持插件
```
npm install hexo-helper-post-top --save
```

之后在需要置顶文章的 front-matter中，添加 top: true 即可置顶。


### 4.引用站内文章
```
{% post_link 文章文件名（不要后缀） 文章标题（可选） %}
```


### 5. 文章加密访问

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

### 6. 添加阅读全文按钮

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



### 7. 文本居中的引用
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

![](/使用hexo写博客/引用.png)



### 8. 插入图片

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



![](/使用hexo写博客/if_apple_2003193.png)

