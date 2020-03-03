---
slug: 2019-03-14-20-23-19
title: flex-block配置说明
date: 2019-03-13 20:23:19
subtitle:
categories: QAQ
tags:
  - hexo
  - 主题
  - 个人博客
cover: https://qiniu.miiiku.xyz/attach/2019/03/f9f691c1c8626ad38f4d403371e05938753e2884.jpg
---


# flex-block

一个基于`Hexo`的主题

模仿加瞎改`Ghost`里的一个主题`nurui`


# 可自定义的相关页面

## 目前可以扩展的页面菜单有:

| type       | value       | name   |
|------------|-------------|--------|
| categories | /categories | 分类   |
| tags       | /tags       | 标签   |
| links      | /links      | 友链   |
| messages   | /messages   | 留言板 |

## 如何添加:

🌰 添加友链页面


``` bash
hexo new page links
```

找到新建的页面并修改`Front-matter`，添加如下内容

``` markdown
type: links
```

修改`_config.yml`配置菜单，找到`menu`选项添加如下内容

```
links: /links
```

## 添加其他自定义页面，如`关于`页面

``` bash
hexo new page about
```

# `Front-matter`相关

## 除开以有的[字段](https://hexo.io/zh-cn/docs/front-matter)，目前有效的相关属性

| key        | layout          | desc                                                   |
|------------|-----------------|--------------------------------------------------------|
| subtitle   | post,page,draft | 小标题，文章或页面的小标题，文章缺省值为文章的发布时间 |
| categories | post,draft      | 分类，文章的分类                                       |
| cover      | post,page,draft | 封面，文章或页面的封面，banner图                       |
| type       | page            | 页面类型，取值详见**可自定义的相关页面**              |

建议复制以下代码替换`scaffolds/`下默认的模版

### post.md,draft.md
``` markdown
---
title: {{ title }}
subtitle:
date: {{ date }}
categories:
tags:
cover:
---
```

### page.md
``` markdown
---
title: {{ title }}
subtitle:
date: {{ date }}
cover:
type:
---
```

# 自定义数据

## 友链数据

在目录的`source/_data`下新建一个**links.yml**

一行一条数据，格式如下:

``` yml
- { "name" : "", "describe" : "", "link" : "", "cover" : "" }
```


# SEO优化相关

**查找并修改`Hexo`下的`_config.yml`**

``` yml
# Site

# <meta name="description" content=[config.description]>
description: 

# <meta name="keywords" content=[config.keywords]>
keywords: 

# <meta name="author" content=[config.author]>
author: 

# <meta name="copyright" content=[config.copyright]>
copyright:
```


# 配置项:

## 代码高亮

hexo默认提供了highlightjs代码高亮，如何开启？

**查找并修改`Hexo`下的`_config.yml`**

``` yml
highlight:
  enable: true
  line_number: true
  auto_detect: true
  tab_replace:
  hljs: true
  theme: monokai
```

其中`enable`为开启代码高亮，`hljs`设置为hljs为class，`theme`为highlight代码高亮主题，不设置默认为default

具体的主题可以在[https://highlightjs.org/](https://highlightjs.org/)查看

## 长标题

进入`flex-block`配置文件`_config.yml`找到`large_legnth`

``` yml
# large cover
# long: [article, link]
# short: [category, tag]
large_legnth:
  long: 20
  short: 5
```

**long:** 作用于`文章`和`友链`卡片

**short:** 作用于`分类`和`标签`卡片

设置Card封面的大小，如 `long: 20` 表示如果文章标题长度大于20，文章卡片显示为长文章

*如果启用了友链，则会判断`友链名称`和`友链描述`两个字段长度*

## dplayer

进入`flex-block`配置文件`_config.yml`找到`dplayer`

``` yml
# dplayer 视频播放
# docs: http://dplayer.js.org/
dplayer:
  enable: true
  theme: "#b7daff"
  autoplay: false
  loop: false
  mutex: true
```

详情查看[http://dplayer.js.org/](http://dplayer.js.org/)

## waterfall 瀑布流

进入`flex-block`配置文件`_config.yml`找到`waterfall`

``` yml
# waterfall 瀑布流
# docs: https://github.com/miiiku/waterfall
# Specific configuration information go to `layout/plug-in/waterfall.ejs`
waterfall: true
```

如果要进行详细的配置，请找到并编辑`layout/plug-in/waterfall.ejs`


详情查看[https://github.com/bigbite/waterfall.js](https://github.com/bigbite/waterfall.js)

## zoom 图片预览

进入`flex-block`配置文件`_config.yml`找到`zoom`

``` yml
# zoom 图片预览
# docs: https://github.com/miiiku/zoom
zoom:
  enable: true
  margin: 15
  padding: 15
  radius: 5
  specify:
  filter: "gallery" # filter Front-matter photos
```

详情查看[https://github.com/miiiku/zoom](https://github.com/miiiku/zoom)

## Valine评论

进入`flex-block`配置文件`_config.yml`找到`comment`

``` yml
# valine 评论
# docs: https://valine.js.org
# You can get your appid and appkey from https://leancloud.cn
# 这里appId和appKey一定一定要改成自己的，没有的话去https://leancloud.cn这个网站注册创建一个
valine:
  enable: true
  appId: # your appid
  appKey: # your appkey
  avatar: mm
  placeholder: 随便说点什么叭～
  notify: false
  visitor: false
  pageSize: 10
```

如果想给某一页面/文章取消评论，在`md`文件的`front-matter`中增加`comments: false`

详情查看[https://valine.js.org/configuration.html](https://valine.js.org/configuration.html)


## 一言

进入`flex-block`配置文件`_config.yml`找到`hitokoto`

``` yml
# 一言
# docs: https://hitokoto.cn/api
# type: [a, b, c, d, e, f, g]
hitokoto:
  enable: false
  type: a
```

详情查看[https://hitokoto.cn/api](https://hitokoto.cn/api)


# 内建标签

## 插入视频 dplayer

``` markdown
<!-- url 必填 cover 可选 -->
{% dplayer url [cover] %}
```

**注意: 需要开启`dplayer`插件才能正常使用本内置标签**

## 插入瀑布流 waterfall

``` markdown
{% waterfall [options] %}
![imgname](imgsrc)
![imgname](imgsrc)
![imgname](imgsrc)
{% endwaterfall %}
```

具体可选参数查看[https://github.com/miiiku/waterfall](https://github.com/miiiku/waterfall)

🌰: 如设置布局为`水平布局`，每个元素的类名为`item-image`，原参数的`驼峰命名`改为`横线连接`

``` markdown
{% waterfall direction=h item-class=item-image %}
![imgname](imgsrc)
...
{% endwaterfall %}
```

**注意: 需要开启`waterfall`插件才能正常使用本内置标签**


# 其他

## favicon

替换掉主题文件下的`source/favicon.ico`

## logo

``` yml
logo:
```

高度不超过50，宽度不超过200为最佳

## banner

``` yml
banner:
```

宽图为最佳

## 统计

``` yml
google_analytics: 

gauges_analytics: 

baidu_analytics: 

tencent_analytics: 
```

接入常用网站统计第三方
