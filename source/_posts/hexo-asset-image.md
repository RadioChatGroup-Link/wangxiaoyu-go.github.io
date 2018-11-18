---
title: Hexo中插入图片hexo asset image
date: 
tags: hexo
categories: hexo

---


介绍一下使用中的hexo插入图片的方法。

[github参考link](https://github.com/CodeFalling/hexo-asset-image)

## 安装插件
npm 安装
 ```
 npm install hexo-asset-image --save
 ```
 
## 编辑配置文件
在hexo的`_config.yml`文件中，做以下修改
```
post_asset_folder: true
```
做了这个修改的效果是，
新建文章post时，会自动生成和文章名相同的文件夹。
这个文件夹存放当前文章所用图片的地方。

以 `$ hexo new "wenzhang"` 为例，结构如下：

```
wenzhang
├── picture1.jpg
├── picture2.jpg
└── picture3.jpg
wenzhang.md
```

## 图片插入时的语法

按照markdown的插入图片的语法来写，
图片名称就是图片路径。
e.g.
`！[picture1](picture1.JPG)`

注意，如果hexo是在[GigHub Pages](https://pages.github.com/)上搭的，图片格式要大写。


