---
title: DatabaseSystemConcepts・Chapter4.1~4.3 Intermediate SQL
date: 
tags: 
    - database
    - 数据库系统概念
categories: 
    - Learning Notes    
---
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






mermaid



```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```
 
```mermaid
graph LR;
A[aa bb]-->B(wo);
A-->C((我是C));
B-->D>我是D];
C-->D;
D-->E{我是E};
C-->E;
2-->E;
_-->E;
```

