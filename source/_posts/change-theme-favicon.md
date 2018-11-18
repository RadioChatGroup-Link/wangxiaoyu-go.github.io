---
title: 更换Hexo的网页图标/小图片Hexo change page favicon
date: 2018-11-18 20:35:58
tags: hexo, ThemeNext
categories: hexo

---
## 说明
本文介绍的是主题theme配置文件中的修改方式，也就是说仅适用于被修改的主题。
另外还有在hexo根目录下设置favicon的方式，虽然这种方法适用于所有在主题的无需再单独设置的好处，以下原因没有使用：
1.考虑到网页小图标favicon的颜色style等还是要和theme结合比较美观
2.试了在hexo根目录配置文件中设定的方式，并没有成功

关于所说明的网页小图标/小图片，即favicon，效果如下，
修改前（next主题）：
![](next-icon.PNG)
修改后：
![](yu-icon.PNG)

## 制作favicon图标

1. 准备好用作网页小图标favicon的图片
2. 搜索`favicon 在线`，可以看到一些在线图片转favicon的工具
   我用的是这个（link）： [bitbug](http://www.bitbug.net/)
3. 利用工具做成图标。
   我做了16x16，与32x32的。

## 图片位置与编辑配置文件
1. 图片位置
打开next主题的`_config.yml`文件，`favicon:`有以下内容：
```
favicon:
  small: /images/favicon-16x16-next.png
  medium: /images/favicon-32x32-next.png
```
也就是说当前使用的图标位置路径是 主题下的 source/images 。
把刚才制作好的图标放到这里。

2. 编辑配置文件
在next主题的`_config.yml`文件，修改新的图片作为favicon的对象：
```
favicon:
  small: /images/favicon16.ico
  medium: /images/favicon32.ico
```

然后在本地环境就能看到效果了。
其他还是执行`hexo g -d`发布网站到master分支上。


