---
title: 使用hexo建立博客
date: 2019-02-18 09:07:24
tags:
categories: "hexo"
---


<!-- 标签别名 -->
{% cq %} 
使用Hexo在GitHub上搭建个人博客
{% endcq %}

<!-- more -->

```
参考
https://hexo.io/zh-cn/
```


## 1. 安装

安装git
安装Node.js

下来只需要使用 npm 即可完成 Hexo 的安装。
```
npm install -g hexo-cli
```

## 2. 新建一个网站


1. init
```
hexo init [folder]
```
新建一个网站。如果没有设置 folder ，Hexo 默认在目前的文件夹建立网站。


2. new
```
hexo new [layout] <title>
```
新建一篇文章。如果没有设置 layout 的话，默认使用 _config.yml 中的 default_layout 参数代替。如果标题包含空格的话，请使用引号括起来。


3. generate
```
hexo generate
```
生成静态文件。

选项	描述
-d, --deploy	文件生成后立即部署网站
-w, --watch	监视文件变动
该命令可以简写为

```
hexo g
```


4. publish

```
hexo publish [layout] <filename>
```
发表草稿。只有当新建的文章是草稿时，才需要使用

使用
```
hexo new [layout] <title>
```
新建文章时，默认的default_layout参数是post，因此可以不使用此命令。
如果参数是draft，或者
```hexo new draft <title> ```
则需要先publish。
参考：{% post_link 使用hexo新建文章 %}


5. server

```
hexo server
```

启动服务器。默认情况下，访问网址为： http://localhost:4000/。

如果您想要更改端口，或是在执行时遇到了 EADDRINUSE 错误，可以在执行时使用 -p 选项指定其他端口，如下：

```
hexo server -p 5000
```



6. clean

```
hexo clean
```
清除缓存文件 (db.json) 和已生成的静态文件 (public)。

在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令



## 3. 发布到github

### 配置

1. 先修改'_config.yml'配置文件，下面是一个示例

```yml
deploy:
  type: git
  repo: https://github.com/xxx/xxx.github.io.git
```
这里需要在github里的个人账户下，新建一个与账户名同名的仓库xxx.github.io。这里的xxx必须与账户名一致。



2. 安装自动发布的插件

安装 hexo-deployer-git。

```
npm install hexo-deployer-git --save
```


以上2条命令都可以，发布可能有延时，稍等即可。


### 部署
您可执行下列的其中一个命令，让 Hexo 在生成完毕后自动部署网站，两个命令的作用是相同的。

```
hexo generate --deploy
hexo deploy --generate

# 简写
# 上面两个命令可以简写为
hexo g -d
hexo d -g
```






