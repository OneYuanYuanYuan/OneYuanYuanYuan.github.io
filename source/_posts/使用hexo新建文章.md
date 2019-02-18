---
title: 使用hexo新建文章
tags: hexo
date: 2019-02-17 17:15:25
---



<<!-- more -->


---
> 转载说明
> 作者：小胖丫头不改名
> 链接：https://www.jianshu.com/p/265b2c653e6f
> 來源：简书
---


##  1: 新建文章
在hexo所在目录下，打开terminal，在命令行输入：
```
hexo new a
```
a是文章标题，也可以加上双引号,如“a”。
通过这行命令，我们新建出来了一个page，而且是一个post page，page还有其他种，稍后我们会提到。
正确的结果：我们会在_posts里看见多了一个a.md文件。
因此我们也知道了，默认情况下，hexo为我们创建的是markdown文件。刷新页面（http://localhost:4000/）我们能看见新添一个名字叫a的文章，没有任何内容。
而这个_posts文件夹，算是一个比较特殊的文件夹，因为它装着所有你发布出去的文章。
打开a.md文件，我们会看到
```
---
title: 1
date: 2017-09-15 19:00:41
tags:
---

在这里随便写点什么

```

然后刷新页面,就会看到你写的内容。与此同时，hexo也会自动为这个post生成一个页面，当我们点击标题，就会进入那个页面。



## 2:  草稿箱

上一步我们新建出来的，叫做post page。除了post page，我们还可以新建draft page，也就是草稿。很多时候我们需要先写成草稿，而暂时不发布出去。draft page就可以满足我们的要求，我们的网站上是看不到草稿文件的。
在terminal输入
```
hexo new draft b
```

我们会在source下看见一个新的文件夹，_drafts，这个里面会装我们所有的草稿文件。
那写好了的草稿，如何可以在不发布的情况下，预览一下文章在网站上的样子呢？
```
hexo server --draft
```

当然，你要先shut down原来开着那个server，才可以开启新的server。如此一来，我们就可以预览草稿文件啦



## 3: 发布草稿
当你准备好了要发布草稿时:
```
hexo publish b
```

你会发现_drafts里的b.md不见了，跑到了_posts里面,也就说明你的草稿发布成功了。


## 4: normal page
我目前还不知道该如何用中文称呼这类页面。我们可以把post和draft统称为blog pages，在这之外的一种就是normal pages， 类似一个网站上的“关于”，“了解我们”之类的页面。
这类page要如何新建呢？
```
hexo new page c
```
和前两种不同，这个命令会在source文件夹内创建出c文件夹，与_posts，_drafts并列。文件夹里面有一个index.md文件。
刷新页面，你会发现c并没有出现在页面内，那它在哪儿呢？
在网址后面加上c/， 即http://localhost:4000/c/，就可以看到了。
正因为c不是一个blog page，所以它也不会出现在blog列表中，而是要通过URL去access。



## 5: 一个小tip
现在我们了解到page一共有三种，post，draft，normal。

那为什么一开始的时候我们用
```
hexo new a
```
就直接生成了post page呢？
因为默认的设置。
打开熟悉的_config.yml文件，找到
```
default_layout: post
```
这句表示默认的页面会新建成post格式的。
所以，如果你习惯先把文章写成草稿，那就把它改成draft就好。
```
default_layout: draft
```


## 6 资源文件夹

资源（Asset）代表 source 文件夹中除了文章以外的所有文件，例如图片、CSS、JS 文件等。比方说，如果你的Hexo项目中只有少量图片，那最简单的方法就是将它们放在 source/images 文件夹中。然后通过类似于 ![](/images/image.jpg) 的方法访问它们。

对于那些想要更有规律地提供图片和其他资源以及想要将他们的资源分布在各个文章上的人来说，可以通过将 config.yml 文件中的 post_asset_folder 选项设为 true 来打开。
```
post_asset_folder: true
```




