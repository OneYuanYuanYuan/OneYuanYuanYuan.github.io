---
title: hexo博客使用到的插件
date: 2019-02-16 10:16:05
tags: "hexo"
categories: "hexo"
---

<!-- 标签别名 -->
{% cq %} 
hexo博客使用到的插件
{% endcq %}

<!-- more -->


### 1. 置顶文章

安装支持插件
```
npm install hexo-helper-post-top --save
```

之后在需要置顶文章的 front-matter中，添加 top: true 即可置顶。


### 2. 添加搜索功能

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


### 3. 页面动画人物

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



### 4. 字数统计和阅读时长

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



### 5. 插入图片

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



















