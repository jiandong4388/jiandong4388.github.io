---
title: '矩阵取对数和 Fisher 变换之间关系'
date: 2022-09-27
permalink: /posts/2022/09/blog-post-1/
tags:
  - log matrix
  - Fisher 变换
  - 级数展开
  - 积分法
---

_考虑一个 $n \times n$  满秩（可逆）矩阵 $A$， 如何求解 $\log A$ ?_  
__一种方法是进行级数展开：__  
$ \log(A)= log(I+B)=\sum _{k=1}^{\infty }{(-1)^{k+1}{\frac {B^{k}}{k}}}=B-{\frac {B^{2}}{2}}+{\frac {B^{3}}{3}}-{\frac {B^{4}}{4}}+\cdots $  
_另外一种方法是积分法（注意：使用该方法的条件是  的特征值不为负值）：_ 
$\log A=\int^1_0(A-I)[t(A-I)+I]^{-1}dt.$  

例子：考虑如下矩阵：
 $A = \left( \begin{aligned}  &1,0\\   &1,1 \end{aligned} \right)$, 求  $\log A$.

- 采用第一种方法：  
$A= I+B\\ $  
这里   
$B= \left(\begin{aligned}  &0,0\\ &1,0\end{aligned}\right)\\ $  
因此有：  
$\log A=\log(I+B) = \sum _{k=1}^{\infty }{(-1)^{k+1}{\frac {B^{k}}{k}}}=B-{\frac {B^{2}}{2}}+{\frac {B^{3}}{3}}-{\frac {B^{4}}{4}}+\cdots $  

注意到：  
$B^k= \left(\begin{aligned}  &0,0\\ &1,0\end{aligned}\right) \left(\begin{aligned}  &0,0\\ &1,0\end{aligned}\right)\cdot B^{k-2}= \left(\begin{aligned}  &0,0\\ &0,0\end{aligned}\right),k=2,3,\cdots\\$  
所以  
$\log A=B= \left(\begin{aligned}  &0,0\\ &1,0\end{aligned}\right)\\$  
采用第二种方法，首先验证矩阵 $A$ 的特征值为 $1$ 不是负数，满足条件， 
 
Fisher 变换
考虑两个随机变量之间的相关关系为 $\rho\in(0,1)$ ,则 Fisher 变换（也称Fisher Z-变换）：
${\displaystyle z={1 \over 2}\ln \left({1+\rho\over 1-\rho}\right).}$

对数相关矩阵和Fisher 变换之间的关系：
为解释二者之间的联系，我们考虑一个二维随机变量 
${\displaystyle z={1 \over 2}\ln \left({1+\rho\over 1-\rho}\right).}$，
形成的相关矩阵（记 $(X,Y)$  之间的相关系数为  $\rho\in (0,1)$）:
$\left( \begin{aligned}  &1,\rho\\   &\rho,1 \end{aligned} \right) $  

则（这里采用积分的方法，因为特征根为  不为负）：
    \begin{align*} \log  \left( \begin{aligned}  &1,\rho\\   &\rho,1 \end{aligned} \right) &=\int^1_0\left( \left( \begin{aligned}  &1,\rho\\   &\rho,1 \end{aligned} \right)- \left( \begin{aligned}  &1,0\\   &0,1 \end{aligned} \right)\right)\left[t\left( \left( \begin{aligned}  &1,\rho\\   &\rho,1 \end{aligned} \right)- \left( \begin{aligned}  &1,0\\   &0,1 \end{aligned} \right)\right)+ \left( \begin{aligned}  &1,0\\   &0,1 \end{aligned} \right)\right]^{-1}dt\\ &=\int^1_0\left(  \begin{aligned}  &0,\rho\\   &\rho,0 \end{aligned} \right)\left( \begin{aligned}  &1,t\rho\\   &t\rho,1 \end{aligned} \right)^{-1}dt\\ &=\int^1_0\left(  \begin{aligned}  &0,\rho\\   &\rho,0 \end{aligned} \right)\left( \begin{aligned}  &\frac{1}{1-t^2\rho^2},\frac{-t\rho}{1-t^2\rho^2}\\   &\frac{1}{1-t^2\rho^2},\frac{1}{1-t^2\rho^2}\end{aligned} \right)dt\\ &=\int^1_0\left( \begin{aligned}  &-\frac{t\rho^2}{1-t^2\rho^2},\frac{\rho}{1-t^2\rho^2}\\   &\frac{\rho}{1-t^2\rho^2},-\frac{1\rho^2}{1-t^2\rho^2}\end{aligned} \right)dt\\ &=\left( \begin{aligned}  &\frac{1}{2}\ln(1-\rho^2),\frac{1}{2}\ln(\frac{1+\rho}{1-\rho})\\   &\frac{1}{2}\ln(\frac{1+\rho}{1-\rho}),\frac{1}{2}\ln(1-\rho^2)\end{aligned} \right).\\ \end{align*}

至此，得到对数相关矩阵的结果。注意到副对角线正是Fisher 变换。这个结论在Arvhakov & Hansen的Econometrica 2021的文章中也有提到。

__参考文献：
Archakov, I., & Hansen, P. R. (2021). A new parametrization of correlation matrices.Econometrica,89(4), 1699-1715.
Higham, N. J. (2008).Functions of matrices: theory and computation. Society for Industrial and Applied Mathematics.
