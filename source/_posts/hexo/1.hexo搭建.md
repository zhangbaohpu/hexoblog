---
title: 1.hexo搭建
date: 2021-03-28 11:12:39
categories: hexo
tags: hexo
top: true
toc: true
cover: true
---

# 1.hexo

## 1.1介绍

官方文档：https://hexo.io/zh-cn/docs/

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](http://daringfireball.net/projects/markdown/)（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

还有hexo的跨平台自适应效果，pc，app，ipad都能完美适配，体验是非常好的。

## 1.2 安装

- window

  window可以装个git，使用git提供的客户端，使用以下命令。

  **1.安装node**

  下载地址：https://nodejs.org/zh-cn/

  `node -v`：查看node版本，`npm -v`：查看npm版本

  `npm install -g cnpm --registry=http://registry.npm.taobao.org`：安装淘宝cnpm管理器，`cnpm -v`：查看cnpm版本

  **2.安装hexo**

  `cnpm install -g hexo-cli `：安装hexo框架，`hexo -v`：查看hexo版本

# 2.搭建博客

## 2.1初始化

通过hexo的命令创建博客，自己选择一个工作空间，`hexo init 目录名`：没有则自动创建

- 创建项目

​       `hexo init blogtest`：blogtest为项目名，可自己定义，出现Start blogging with Hexo!，则表示创建完成

​		![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405113252599.png)

## 2.2 启动项目

进入项目根目录

`hexo -s`：启动项目，默认端口4000，指定端口：`hexo -s -p 8080`

![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405113623910.png)

访问localhost:8080，即hexo默认主题

![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405154743228.png)

核心目录/文件如下：

- scaffolds:模板、脚架目录

- source：源文件夹(内容核心)，所有的文章和分类、标签等都是通过该文件夹下的内容进行发布的

- source/_post：所有发布的文章都在该文件夹中

- source/xxx：菜单xxx页面，如分类source/categories用于存放分类页，但分类页md文件是无需内容的，hexo会自动索引

- _themes：当前hexo项目的各类主题存放文件夹，把所需的主题目录添加到该文件夹中并更改项目_

- config.yml相应配置即可更换主题

- themes/{themeName}/_config.yml：主题配置文件，主题的各种样式、配置都可在该文件中更改

- config.yml：项目配置文件，设置项目的通用配置(主题外的配置，如标题、分页、搜索、作者、发布地址等)

## 2.3 hexo命令

上面有使用hexo的创建项目，及启动项目的命令，下面总结几个常用的。

`hexo init [folder]`：新建项目，如果当前目录没有folder，则会自动创建

`hexo clean`：清除缓存文件 (`db.json`) 和已生成的静态文件 (`public`)

`hexo generate(or g)`：生成网站静态文件

`hexo server(or s)`：启动本地服务器，localhost：4000查看网站效果

# 3.第一篇博客

以默认主题创建第一篇博客。

`hexo n "我的第一篇博客"`：创建一个以`我的第一篇博客`为名，以md为后缀的文章。

![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405163651213.png)

然后就可以编写博客内容了，md格式编辑器可自行选择，我使用typora，个人体验非常不错。编写完后不用重启项目，他会自动生效，直接访问即可。

![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405164643467.png)





# 4.部署到gitee

一切准备就绪后，我们还只是在本地访问，为了放在公网，分享给其他人浏览使用，我们把项目部署到gitee上，当然github也是可以的，但受访问速度限制，两个我都试了，gitee明显快的多。

## 4.1创建gitee仓库

- 在gitee上创建仓库

  登录自己的gitee账号，然后创建一个和自己<font style="color:red">账号同名的仓库</font>

  ![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405172216757.png)

- 记录git地址

  https://gitee.com/zhangbaohpu/zhangbaohpu.git

## 4.2配置gitee仓库地址

有了gitee仓库，然后我们就可以把本地项目部署到gitee上了。

- 修改hexo的配置文件_config.yml

  在配置文件中修改deploy参数

  ```yaml
  # Deployment
  ## Docs: https://hexo.io/docs/one-command-deployment
  deploy:
    type: git
    repo: https://gitee.com/zhangbaohpu/zhangbaohpu.git
    branch: master
  ```

  顺便修改几个参数：

  `language: zh-CN`：语言，默认是en，

  `per_page: 12`：分页大小，默认10，这个是后面一个主题用12比较好

- 安装git部署插件

  在项目根目录执行以下命令安装

  `cnpm install --save hexo-deployer-git`: #在blog目录下安装git部署插件

  ![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405174224705.png)

## 4.3部署与更新

gitee相关准备完毕后，就可以部署项目了

- 部署到gitee

  `hexo d`：部署到gitee仓库

  ![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405174410576.png)

<font style="color:red">特别说明:</font>

如果是第一次部署，到这里就应该可以通过访问http://zhangbaohpu.gitee.io/看到效果了，但项目的每一次部署都是需要手动更新gitee的，比如写一篇新博客，然后发布到gitee上，在我们执行完 `hexo d` 后，需要在gitee中手动更新，更新入口如下：

![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405175757688.png)

在项目的服务中标签下，有一个Gitee Go，我们点进去

![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405175907784.png)

然后下面有一个更新按钮，这里就是我们每次写完一篇博客发布到gitee后，手动操作的地方。访问如下：

![](http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/blog/hexo/1/image-20210405180112309.png)

这样我们就可以愉快的写博客了，几乎零成本。<img src="http://zhangbaohpu.oss-cn-shanghai.aliyuncs.com/picture/emoji/collection/20171117100031.gif" style="zoom: 80%;" />

不过这样缺点还是有的，就是主题看着不太好看，当然hexo提供了主题市场，可以挑选自己喜欢，然后替换，下一节讲解如何替换主题。

