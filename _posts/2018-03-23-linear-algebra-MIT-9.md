---
layout: post
title: 线代笔记——第9课 线性无关，基和维数
categories: [线性代数]
tags: 学习笔记 线性代数 MIT公开课
---

　　向量的线性无关意为着什么？如何用线性无关的概念来帮助我们描述包括零空间在内的子空间？

### 一、线性无关（Independence）

　　矩阵$$\boldsymbol{A}$$为m×n矩阵，其中m＜n（因此$$\boldsymbol{Ax=b}$$中未知数个数多于方程数）。
则$$\boldsymbol{A}$$中具有至少一个自由变量，那么$$\boldsymbol{Ax=b}$$一定具有非零解。$$\boldsymbol{A}$$的列向量
可以线性组合得到零向量，所以$$\boldsymbol{A}$$的列向量是线性相关的。

　　若$$c_1x_1+c_2x_2+\dots+c_nx_n=0$$仅在$$c_1=c_2=\dots=c_n=0$$时才成立，则称向量$$x_1,x_2\dots x_n$$是线性无关的。
若这些向量作为列向量构成矩阵**A**，则方程$$\boldsymbol{Ax=b}$$只有零解$$x=0$$，或称矩阵**A**的零空间只有零向量。
换而言之，若存在非零向量c，使得$$Ac=0$$，则这个矩阵**A**的列向量线性相关。

　　在$$\boldsymbol{R}^2$$中，两个向量只要不在一条直线上就是线性无关的。（在$$\boldsymbol{R}^3$$中，三个向量线性无关的条件是他们不在一个平面上。）
若选定空间$$\boldsymbol{R}^2$$中的三个向量，则他们必然是线性相关的。例如，如下的三个向量$$\boldsymbol{v_1,v_2,v_3}$$是线性相关的。

$$
\boldsymbol{A} = \begin{bmatrix} 2 & 1 & 2.5\\ 1 & 2 & -1\\ \end{bmatrix}\quad
$$

　　由我们研究方程组得到的结论，此时矩阵构成的方程$$\boldsymbol{Ax}=0$$必有非零解，即三个向量线性相关。

　　如果矩阵**A**的列向量为线性无关，则**A**所有的列均为主元列，没有自由列，矩阵的秩为n。若**A**的列向量
列为线性相关，则矩阵的秩小于n，并且存在自由列。

### 二、张成空间（Spanning a space）

　　当一个空间是由向量$$v_1,v_2...v_k$$的所有线性组合组成时，我们成这些向量张成了这个空间。例如矩阵的列向量张成
了该矩阵的列空间。

　　如果向量$$v_1,v_2...v_k$$张成空间**S**，则**S**是包含这些向量的最小空间。

### 三、基与维数（Basis & Dimension）

　　向量空间的基是具有如下两个性质的一组向量$$v_1,v_2...v_d$$：    
　　　　* $$v_1,v_2...v_d$$线性无关     
　　　　* $$v_1,v_2...v_d$$张成该向量空间   
　　空间的基告诉我们了空间的一切信息。

　　例：$$R^3$$空间有一组基
$$\begin{bmatrix} 1 \\ 0\\ 0\\ \end{bmatrix}\quad$$,
$$\begin{bmatrix} 0 \\ 1\\ 0\\ \end{bmatrix}\quad$$,
$$\begin{bmatrix} 0 \\ 0\\ 1\\ \end{bmatrix}\quad$$，
因为$$c_1\begin{bmatrix} 1 \\ 0\\ 0\\ \end{bmatrix}\quad+
c_2\begin{bmatrix} 0 \\ 1\\ 0\\ \end{bmatrix}\quad+
c_3\begin{bmatrix} 0 \\ 0\\ 1\\ \end{bmatrix}\quad=
\begin{bmatrix} 0 \\ 0\\ 0\\ \end{bmatrix}\quad$$只有零解，并且这三个向量可以张成$$R^3$$空间。

　　而$$\begin{bmatrix} 1 \\ 1\\ 2\\ \end{bmatrix}\quad$$,
$$\begin{bmatrix} 2 \\ 2\\ 5\\ \end{bmatrix}\quad$$,
$$\begin{bmatrix} 3 \\ 3\\ 8\\ \end{bmatrix}\quad$$则不能构成一组基，因为以它们为列向量组成的矩阵，
有两个相同的行，消元肯定有自由列存在，因此这三个向量并非线性无关。

　　若以$$R^n$$空间中的n个向量为列向量构成的矩阵为可逆矩阵，则这些向量可以构成$$R^n$$空间中的一组基。

### 四、子空间的基（Basis for a subspace）

　　向量$$\begin{bmatrix} 1 \\ 1\\ 2\\ \end{bmatrix}\quad$$,
$$\begin{bmatrix} 2 \\ 2\\ 5\\ \end{bmatrix}\quad$$可以张成$$R^3$$中的一个平面，但是它们无法成为$$R^3$$空间的一组基。

　　空间的每一组基都具有相同的向量数，这个数值就是空间的维数（dimension）。所以$$R^n$$空间的每组基都包含n个向量。
　　
### 五、列空间和零空间的基

$$
\boldsymbol{A} = \begin{bmatrix} 1 & 2 & 3 & 1\\ 1 & 1 & 2 & 1\\ 1 & 2 & 3 & 1\\ \end{bmatrix}\quad
$$

　　**讨论列空间：**矩阵**A**的四个列向量张成了矩阵**A**的列空间，其中第3列和第4列与前两列线性相关，而前两个列向量线性无关。因此前两列为主元列。他们组成
了列空间 C(A)的一组基。矩阵的秩为 2。

　　实际上对于任何矩阵**A**均有：

　　　　矩阵的秩 r=矩阵主元列的数目=列空间的维数

　　注意：矩阵具有秩（rank）而不是维数（dimension），而空间有维数而不是秩。

　　当知道了列空间的维数，可以从矩阵列向量中随意选取足够数量的线性无关的向量，它们每一组都可以构成列空间的一组基。

　　**讨论零空间：**本例中矩阵的列向量不是线性无关的，因此其零空间 N(A)不止包含零向量。因为可以看出第 3 列是第 1 列和第 2 列的加和。所以向量
$$\begin{bmatrix} -1\\ -1\\ 1\\ 0\\ \end{bmatrix}\quad$$必然在零空间 N(A)之内。同样还可以对 $$x_4$$ 赋值为 1，从而得到
$$\begin{bmatrix} 1\\ 0\\ 0\\ 1\\ \end{bmatrix}\quad$$也在零空间之内。它们就
是 $$Ax=0$$ 的两个特解。

　　零空间的维数=自由列的数目=n-r，因此本例中 N(A)的维数为 4-2=2。这两个
特解就构成了零空间的一组基。

