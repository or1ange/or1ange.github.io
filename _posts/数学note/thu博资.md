---
title: thu博士资试
tags: 应用数学
---

# 题目
![alt text](https://raw.githubusercontent.com/or1ange/or1ange.github.io/master/_posts/丘赛note/d2e0a9a6e3d849bb5b0326ca46877cc.jpg)
![alt text](https://raw.githubusercontent.com/or1ange/or1ange.github.io/master/_posts/丘赛note/5508bbfc201ccb2dd5ab87fc97709a1.jpg)


#### question1
**keypoint**：young-mirsky theorm

Low rank approximation ：
$$\underset{X}{min}||A-X||_2$$
$$\text{subject to  rank} (X)=k $$

##### **(1)** $l_2norm$ proof:

**a**).When $r(X)=k \leq r(A)=r$,young-mirsky theorem have proved  conclusion that：
    $A=[U_1 U_2][\begin{matrix}
\Sigma_1&O\\
O&\Sigma_2\\
\end{matrix}][V_1 V_2]^T$

choose top k big singular value and their vetcor U&V,$X=U_1\Sigma_1 V_1^T$ is the solution to the question above.

let define $Y=U_2\Sigma_2 V_2^T$
clearly,
$||A-X||_2=||Y||_2=\sigma_{k+1}$

for every $B \in R^{m*n}$,whose $rank=k\leq r，dim N(B)=n-k$
$$dim N(B)+dim span(v_1,v2,...,v_{r+1})\geq n+1$$
so $N(B)\cap span(v_1,...,v_{r+1})\neq{\varnothing}$

we can choose $||z||$ from $span(v_1,...,v_{r+1})$ and $z= \Sigma k_iv_i,Bz=0,||z||=1(\Sigma k_i^2=1)$

$$||A-B||_2=||A-B||_2||z||_2\geq||(A-B)z||_2=||Az||_2=||\Sigma V^Tz||_2$$
$$=（\Sigma\sigma_i^2k_i^2）^{1/2}\geq \sigma_{k+1}(\Sigma k_i^2)^{1/2}=\sigma_{k+1}$$

**b**).When $r(X)=k >  r(A)=r$,i think there may be a $\color{red}{mistake}$ about question.(for sure $A\neq X$)

if such X exist,let define $||A-X||_2=2\epsilon>0$
  
$\hat X=[U_1 U_2][\begin{matrix}
\Sigma_{r}&O&O\\
O&\epsilon I_{k-r}&O\\
O&O&O\\
\end{matrix}][V_1 V_2]^T
=A+[U_1 U_2][\begin{matrix}
O&O&O\\
O&\epsilon I_{k-r}&O\\
O&O&O\\
\end{matrix}][V_1 V_2]^T$
where $\Sigma_r$ is top r big singular value  (all singular value) 

$||A-\hat{X}||=||[U_1 U_2][\begin{matrix}
O&O&O\\
O&\epsilon I_{k-r}&O\\
O&O&O\\
\end{matrix}][V_1 V_2]^T||=\epsilon<2\epsilon$

so such X don't exist.

**proved.**

**F-norm proof**:
待续
$$A$$

#### question2 
**keypoint**:iteration convergence(For short,if the Spectral radius of iteration matrix in(-1,1),the iteration converges)


**1**.show iteration process

write out the matrix process,it is clear($\textcolor{red}{skip~~it}$)

**2**.
a). prove diagonally dominant matrix $A$ is invertible

**proof**:
if $A$ isn't invertible,its Column vector is linearly related.there exist {$\alpha_i$} that $\sum \alpha_i v_i=0$.choose the abs-max $\alpha_k$,
$$|\alpha_k ||a_{kk}|=|\sum_{i\neq k}\alpha_i a_{ki}|\leq\sum_{i\neq k}|\alpha_i ||a_{ki}|$$

but 
$$|\alpha_k|\geq|\alpha_i| \\|a_{kk}|>\sum_{k\neq i}|a_{ki}|$$
so the diagonally dominant matrix $A$ is invertible

**proved.**

b).prove the iteration converges

**proof**:
define vector $x$ and eigenvalues $\lambda$ of iteration matrix
$$(D-L)^{-1}Ux=\lambda x$$
$$Ux=\lambda(D-L)x\rightarrow \lambda Dx=Ux+\lambda Lx$$
for arbitrary i:
$$\lambda a_{ii}x_i=\sum_{1<j<i}x_ja_{ij}+\lambda \sum_{j>i}x_ja_{ij}$$

let focus on the i that makes abs($x_i$) max and do change" $x:=x/|x_i|$"
$$|\lambda|| a_{ii}|\leq \sum_{1<j<i}|a_{ij}|+|\lambda| \sum_{j>i}|a_{ij}|$$
got:
$|\lambda|\leq \frac{\sum_{1<j<i}|a_{ij}|}{(| a_{ii}|- \sum_{j>i}|a_{ij}|)}\leq1$

notice: $\lambda$ is arbitrary

**proved.**

**3**.
a). prove symmetric and positive defnite $A$ is invertible

**proof**:
the same as above
$x^TAx=\lambda x^Tx>0\rightarrow \lambda>0$

so $A$ is invertible.

**maybe i need think about the question deeply**

b).
**proof:**
$U^T=L,x^TAx=\lambda x^Tx>0$

$$L^Tx=\lambda (D-L)x\rightarrow(1-\lambda)L^Tx=\lambda Ax$$

$$(1-\lambda)x^TL^Tx=\lambda x^TAx\rightarrow(1-\lambda)l=\lambda a$$

$$\lambda^2=l^2/(l^2+a(a+2l))\leq1$$

notice:for any i， $a_{ii}>0$,so $x^TDx >0，so~~~a+2l>0$  

**proved.**


#### question3

**keypoint**: i don't konw  ('qaq')

**1**.![
](https://raw.githubusercontent.com/or1ange/or1ange.github.io/master/_posts/丘赛note/8b5b733dd2c31dccccfce6284f2ca25.png)


