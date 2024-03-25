---
title: 凸优化（基础知识）
tags: 计算方法

---

## 范数
#### 内积的性质：

1.非负性：$ \lt x,x\gt \geq 0 $ ,if and only if $x=0,\lt x,x\gt=0$

2.对称性：$\lt x,y \gt =\lt y,x\gt$

3.齐次性：$\lt ax,y\gt=a\lt x,y\gt$

4.可加性：$\lt x+y,z\gt=\lt x,z\gt+\lt y,z\gt$

#### 欧式范数

$|**x**|:= (<**x**,**x**>) ^(1/2)$


#### 柯西-施瓦兹不等式

$|\lt x,y \gt |\leq||x||*||y||$

*proof*：

不妨令x,y为单位向量
  
  *$0\leq||x-y||^2=\lt x-y,x-y\gt=2-2\lt x,y\gt$*

得到：
    $<x,y>\leq1，将x/||x||，y/||y||代入其中，再根据齐次性，得到<x,y>\leq||x||*||y||，以-x代替x得到<x.y>\geq-||x||*||y||$
    *proved*
