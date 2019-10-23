---
title: Hexo中插入flowchart
date:  2018-11-19 02:05:46 
tags: hexo
categories: hexo

---


以下是使用中的hexo插入flowchart的方法。


[github参考link](https://github.com/bubkoo/hexo-filter-flowchart)

## 安装插件
npm 安装
 ```
 npm install --save hexo-filter-flowchart
 ```
 
## 修改配置文件
在hexo的`_config.yml`文件（根目录的并非主题的）中，添加以下内容：
```
flowchart:
  # raphael:   # optional, the source url of raphael.js
  # flowchart: # optional, the source url of flowchart.js
  options: # options used for `drawSVG`
```


## 效果
e.g.
 - 内容

```
` ` `flow 
st=>start: Start|past:>http://www.google.com[blank]
e=>end: End:>http://www.google.com
op1=>operation: My Operation|past
op2=>operation: Stuff|current
sub1=>subroutine: My Subroutine|invalid
cond=>condition: Yes
or No?|approved:>http://www.google.com
c2=>condition: Good idea|rejected
io=>inputoutput: catch something...|request

st->op1(right)->cond
cond(yes, right)->c2
cond(no)->sub1(left)->op1
c2(yes)->io->e
c2(no)->op2->e
` ` `
```

<i class="fa fa-thumb-tack" style="font-size:1em;"> </i> *flow前后的三个点之间加了空格(环境限制无法嵌套引用flow)，实际使用时需要去掉空格*




- 效果

```flow 
st=>start: Start|past:>http://www.google.com[blank]
e=>end: End:>http://www.google.com
op1=>operation: My Operation|past
op2=>operation: Stuff|current
sub1=>subroutine: My Subroutine|invalid
cond=>condition: Yes
or No?|approved:>http://www.google.com
c2=>condition: Good idea|rejected
io=>inputoutput: catch something...|request

st->op1(right)->cond
cond(yes, right)->c2
cond(no)->sub1(left)->op1
c2(yes)->io->e
c2(no)->op2->e
```

e.g.
 - 内容

```
` ` `flow
    st=>start: Start
    op=>operation: Your Operation
    cond=>condition: Yes or No?
    e=>end
    
    st->op->cond
    cond(yes)->e
    cond(no)->op
` ` `
```


<i class="fa fa-thumb-tack" style="font-size:1em;"></i>  *flow前后的三个点之间加了空格(环境限制无法嵌套引用flow)，实际使用时需要去掉空格*


- 效果

```flow
st=>start: Start
op=>operation: Your Operation
cond=>condition: Yes or No?
e=>end

st->op->cond
cond(yes)->e
cond(no)->op
```


<br>
本地环境就能看到效果了。
其他还是执行`hexo g`, `hexo d`发布网站到master分支上。


