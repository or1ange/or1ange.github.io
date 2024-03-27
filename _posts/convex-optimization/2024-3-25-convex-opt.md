---
title: 凸优化
tags: 计算方法

---


# 基础知识
## 范数
#### 内积的性质：

1.非负性：$\lt x,x\gt \geq 0 $, if  and only if  x=0, $ \lt x,x\gt=0 $

2.对称性：$\lt x,y \gt =\lt y,x\gt$

3.齐次性：$\lt ax,y\gt=a\lt x,y\gt$

4.可加性：$\lt x+y,z\gt=\lt x,z\gt+\lt y,z\gt$

#### $l_p$范数


$$||x||_p：=（|x_1|^p+|x_2|^p+...+|x_n|^p）^{1/p}$$

when $p=2$,

$$||x||:= (<x,x>)^{1/2}$$

when $p=\infty$,

$$||x||_{\infty}=max|x_i|$$



#### 柯西-施瓦兹不等式
$$|\lt x,y \gt |\leq||x||*||y||$$

*proof*：

不妨令x,y为单位向量
    $$0\leq||x-y||^2=\lt x-y,
    x-y\gt=2-2\lt x,y\gt$$

得到
    $$<x,y>\leq1$$
$将x/||x||，y/||y||代入其中，再根据齐次性，得到<x,y>\leq||x||*||y||，以-x代替x得到<x.y>\geq-||x||*||y||$

*proved*

#### 矩阵范数
the same as vectors,
$A_{m*n}的1-范数是A中所有元素绝对值的总和，F范数是(tr（A*A^T）)^{1/2},是(奇异值平方和)^{1/2},2-范数是最大奇异值$

but the differently,

**算子范数**：

![alt text](https://raw.githubusercontent.com/or1ange/or1ange.github.io/master/_posts/convex-optimization/image.jpg)

where $|*|_{m} $ is  the   norm   from  $ R^{m}$ 



when m=n=p,got $l_p$ norm。$l_2$ norm is often used,the $l_2$ norm of matrix is its **max singular value**

for all 算子norm：

$||Ax||_{m}\leq||A||_{m,n}||x||_{n}$

**ker-norm(核范数)**：
$||A||_{*}=\sum\sigma_i$,where
$\sigma_i$ is the **nozero singular value**. 

We often constrain $||*||_{*}$to  ensure matrix **low-rank** like constraining $||*||_{1}$ to ensure vetcors **sparsity**(保证稀疏性)

**矩阵内积(Frobenius内积)**
$<A,B>:=tr(AB^{T})=\sum\sum a_{ij}b_{ij}$

柯西-施瓦兹不等式 is also satisfied.
$$|<A,B>|\leq||A||_{F}*||B||_{F}$$

## 导数（derivative）
**gradient**

![alt text](image-1.jpg)

![alt text](image-2.jpg)

![alt text](image-3.jpg)

we usually see gradient as a vetcor

![alt text](image-4.jpg)

![alt text](image-5.jpg)

**proof**:
定义一个函数:$g（t）=f(x+t(y-x)),t\in [0,1]$

$f(y)-f(x)-\nabla f(x)^T(y-x)=\int_{0}^{1} g^1(t)- g^1(0) dt$
$=\int_{0}^{1} (\nabla f(x+t(y-x))-\nabla f(x))(y-x)^Tdt$
$\leq\int_{0}^{1} |\nabla f(x+t(y-x))-\nabla f(x)|*|x-y|dt$

$\leq \int_{0}^{1} Lt|y-x|^2dt=\frac{L}{2}|y-x|^2$

**proved.**

tips:**L-光滑** 表明$f$的增长速度被一个二次函数所控制。



![alt text](image-7.jpg)

**proof**:

$f(x^*)\leq f(y)\leq f(x)+\nabla f(x)^T(y-x)+\frac{L}{2}||y-x||^2$
the right-side have  $inf$ ,when $y=x-\frac{\nabla f(x)}{L}$
$f(x^*)<f(x)-\frac{1}{2L}||\nabla f(x)||^2$

**proved.**

# 无约束优化
### 线搜索方法

$x^{k+1}=x^{k}+a_kd^{k}$,这里**d**代表搜索方向，**a**是步长。

搜索方向必须满足：$d^{T}\nabla f(x^{k})<0$ (**down**)

我们把更多的注意力放在步长**a**的选择上，

精确线性搜索准则（**exact line search criteria**）:

$$a_k=arg min_{a>0}f(x^k+ad^k)$$

实际应用中，计算**a_k**是需要巨大成本的，所以非精确线性搜索准则（ **no-exact line search criteria**）更受到大家欢迎：


#### **Armijo criteria**:
$$f(x^k+ad^k)\leq f(x^k)+c_1a\nabla f(x^k)^Td^k,where~~ c_1\in(0,1)$$

tips: when $a$ or $c_1$ is small ,Armijo criteria is easy to st.
To speed up convergence,**a（step-length）** can't be too small!

here is a easy way to find good **$a_k$**

![alt text](image-6.jpg)

#### **Goldstein criteria**:

$$f(x^k+ad^k)\leq f(x^k)+ca  \nabla f(x^k)^Td^k$$
$$f(x^k+ad^k)\geq f(x^k)+(1-c)a  \nabla f(x^k)^Td^k$$

where $c\in(0,0.5)$

tips:base on **Armijo criteria**,discard some **a（step-length）** which is too small.

#### **Wolfe criteria**:
$$f(x^k+ad^k)\leq f(x^k)+c_1a  \nabla f(x^k)^Td^k$$

$$\nabla f(x^k+ad^k)^Td^k\geq c_2\nabla f(x^k)^Td^k$$

where $c_1,c_2\in(0,1),c_1<c_2$

tips:2nd is more important.

when $x^k $ is $ x^*$,$\nabla f(x^k)=0$,(2nd is st.)

$\nabla f(x^k+ad^k)\geq c_2\nabla f(x^k)$

 when **$c_1$ is small,$c_2$ is big**, this criteria is more easy to st.


### 梯度类方法（gradient method）
#### 最速下降法
$$x_{k+1}=x_k-a_k\nabla f(x^k)$$
$$a_k=argmin_{a\geq 0}f(x^k+a\nabla f(x^k))$$

#### the convergence analysis（收敛性分析）
let define:
 $$f(X)=\frac{1}{2}x^TQx-b^Tx$$
$$V(X)=f(x)+\frac{1}{2}x^{*T}Qx^*=\frac{1}{2}(x-x^*)^TQ(x-x^*),where:QX^*=b $$

proof:
    $V(x^{k+1})=\frac{1}{2}(x^{k+1}-x^*)^TQ(x^{k+1}-x^*)$
    $=\frac{1}{2}$

待续

### 共轭类方法（Conjugate Gradient Method）

如果存在一个线性方程组$Ax=b$,我们可以通过解下面这个最值问题得到它的解。
$$arg~min_{X}~~ g(x)=\frac{1}{2}X^TAX-b^TX$$

因为$g(x)$是凸函数，它的解$x^*$满足以下条件$ Ax^*-b=g^{1}(x^*)=0 $
#### Conjugate Direction Method
如果$$p_i^TAp_j=0~~~for~~ all ~~i\ne j$$
我们就定义“{$p_i$}是关于矩阵A**共轭**的”。


给定初始迭代起点$x_0\in R^n$ 和 共轭方向 {$p_1,p_1,..,p_n$},共轭梯度方法如下:

$$x_{k+1}=x_{k}+\alpha_{k+1}p_{k+1}\\
\alpha_{k+1}=arg~~min_{\alpha}~~g(x_k+\alpha p_{k+1})\\
\alpha_{k+1}=-(Ax_k-b)^Tp_{k+1} /(p_{k+1}^TAp_{k+1})$$

**证明:**

1.$x^*-x_0=\sigma_1p_1+...+\sigma_np_n$

2.$p_k^TA（x^*-x_0）=\sigma_k p_k^TAp_k$

3.$p_k^TA（x_{k-1}-x_0）=0$

$$\sigma_k p_k^TAp_k=p_k^TA（x^*-x_0）=p_k^TA（x^*-x_{k-1}）\\
=p_k^T（b-Ax_{k-1}）
\\=\alpha_k p_k^TAp_k$$

$\alpha_k=\sigma_k$

第一处等号由3.得到，第三处等号见上述共轭梯度方法第三式。


**得证.**
