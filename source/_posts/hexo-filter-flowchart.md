---
title: Hexo中插入flowchart
date: 
tags: hexo
categories: hexo

---


以下是使用中的hexo插入flowchart的方法。
2017年以后有了对应hexo的插件，感谢做插件的人。

[github参考link](https://github.com/bubkoo/hexo-filter-flowchart)

## 安装插件
npm 安装
 ```
 npm install --save hexo-filter-flowchart
 ```
 
## 编辑配置文件
在hexo的`_config.yml`文件中，添加以下内容：
```
flowchart:
  # raphael:   # optional, the source url of raphael.js
  # flowchart: # optional, the source url of flowchart.js
  options: # options used for `drawSVG`
```


## 效果
e.g.
- 内容



````
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
````



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

````
```flow
    st=>start: Start
    op=>operation: Your Operation
    cond=>condition: Yes or No?
    e=>end
    
    st->op->cond
    cond(yes)->e
    cond(no)->op
    < raw >```< endraw >
```
````



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


- test

