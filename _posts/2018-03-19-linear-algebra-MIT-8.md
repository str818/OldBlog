---
layout: post
title: 线代笔记——第8课 求解Ax=b:可解性与结构
categories: [线性代数]
tags: 学习笔记 线性代数 MIT公开课
---
### 一、可解的条件（Solvability conditions on b）
　　取
$$
\boldsymbol{A} = \begin{bmatrix} 1 & 2 & 2 & 2\\ 2 & 4 & 6 & 8\\ 3 & 6 & 8 & 10\\ \end{bmatrix}\quad
$$
，则方程为
$$
\begin{bmatrix}	1 & 2 & 2 & 2\\ 2 & 4 & 6 & 8\\ 3 & 6 & 8 & 10\\ \end{bmatrix}\quad
\begin{bmatrix}	x_1\\ x_2\\ x_3\\ x_4\\ \end{bmatrix}\quad
= \begin{bmatrix} b_1\\ b_2\\ b_3\\ \end{bmatrix}\quad
$$
。

　　矩阵A的第三行为第一行和第二行的和，因此$$Ax=b$$中b的第3个分量也要等于其第1和第2两个分量的和。
若b不满足$$b_3=b_1+b_2$$则方程组无解。

　　检验$$Ax=b$$是否可解的方法是对増广矩阵进行消元。如果矩阵A的行被完全消去的话，则对应的b的分量也要得0.在本例中，矩阵A的第三行被消去：

$$
\begin{bmatrix}	1 & 2 & 2 & 2 & b_1\\ 2 & 4 & 6 & 8 & b_2\\ 3 & 6 & 8 & 10 & b_3\\ \end{bmatrix}\quad
\rightarrow\dots\rightarrow
\begin{bmatrix}	1 & 2 & 2 & 2 & b_1\\ 0 & 0 & 2 & 4 & b_2-2b_1\\ 0 & 0 & 0 & 0 & b_3-b_2-b_1\\ \end{bmatrix}\quad
$$

　　如果$$Ax=b$$有解，则$$b_3-b_1-b_2=0$$。在本例中另$$b=\begin{bmatrix} 1\\ 5\\ 6\\ \end{bmatrix}\quad$$。

　　只有当b处于矩阵的列空间C(A)之中时，方程才有解。本课推导出矩阵A的行向量若经过线性组合成为了零向量，则对应的b经同样的线性组合后也要等于0，
因此看起来有了两条关于b的限制条件，但实际上这两点是等价的。

### 二、通解（Complete solution）

　　为求得$$Ax=b$$的所有解，我们首先检验方程是否可解，然后找到一个特解。将特解和矩阵零空间的向量相加即为方程的通解。

### 三、特解（A particular solution）

　　求$$Ax=b$$特解的方法是将自由变量均赋值为0，求解其主变量。

　　本例中，令$$x_2=x_4=0$$得到方程组：
	$$x_1+2x_3=1$$　　$$2x_3 = 3$$
	
　　可解得$$x_3=3/2,x_1=-2$$,因此特解为$$x_p=\begin{bmatrix} -2\\ 0\\ 3/2\\ 0\\ \end{bmatrix}\quad$$。

### 四、与零空间进行线性组合（Combined with nullspace）

　　$$Ax=b$$的通解为$$x_c = x_p + x_n$$,其中$$x_n$$为矩阵零空间中的一般向量。将$$Ax_p=b$$和$$Ax_n=0$$相加可得$$A(x_p + x_n)=b$$。

　　上一课得到了矩阵零空间N(A)就是其特解$$\begin{bmatrix} -2\\ 1\\ 0\\ 0\\ \end{bmatrix}\quad$$和$$\begin{bmatrix} 2\\ 0\\ -2\\ 1\\ \end{bmatrix}\quad$$
的线性组合的集合。因此方程$$Ax=\begin{bmatrix} 1\\ 5\\ 6\\ \end{bmatrix}\quad$$的通解即为：

$$x_c =\begin{bmatrix} -2\\ 0\\ 3/2\\ 0\\ \end{bmatrix}\quad + c_1 \begin{bmatrix} -2\\ 1\\ 0\\ 0\\ \end{bmatrix}\quad + c_2 \begin{bmatrix} 2\\ 0\\ -2\\ 1\\ \end{bmatrix}\quad$$

其中$$c_1$$和$$c_2$$为任意实数。    

　　矩阵中的零空间N(A)是$$R^4$$空间中的二维子空间，方程的解$$Ax=b$$构成了穿过$$x_p$$点并和矩阵零空间平行的“平面”。但该“平面”并不是$$R^4$$的子空间。

### 五、秩（Rank）

　　矩阵的秩等于矩阵的主元数。如果m×n矩阵的秩为r，则必有r≤m且r≤n。

　　满秩的情形：

　　* **列满秩**：$$r=n$$。每列都有主元，x的每一个分量都是主变量，没有自由变量。零空间N(A)之内只有零向量。
方程无解或者有唯一解$$x_p$$。

　　例如$$A=\begin{bmatrix} 1 & 3\\ 2 & 1\\ 6 & 1\\ 5 & 1\\ \end{bmatrix}\quad \rightarrow 
\begin{bmatrix} 1 & 0\\ 0 & 1\\ 0 & 0\\ 0 & 0\\ \end{bmatrix}\quad = R$$

　　* **行满秩**：$$r=m$$。没行都有主元，无论b取何值，方程$$Ax=b$$都有解。主变量r个，自由变量n-r个。

　　例如$$A=\begin{bmatrix} 1 & 2 & 6 & 5\\ 3 & 1 & 1 & 1\\ \end{bmatrix}\quad \rightarrow 
\begin{bmatrix} 1 & 0 & * & *\\ 0 & 1 & * & *\\ \end{bmatrix}\quad = R$$

　　* **满秩**：$$r=m=n$$。矩阵可逆，零空间只有零向量，无论b取何值，方程$$Ax=b$$都有唯一解。

　　例如$$A=\begin{bmatrix} 1 & 2 \\ 3 & 1 \\ \end{bmatrix}\quad \rightarrow 
\begin{bmatrix} 1 & 0 \\ 0 & 1 \\ \end{bmatrix}\quad = R$$为单位阵。

　　**秩决定了方程组解的数量。**

![秩](\images\posts\Math\LinearAlgebra\8_1.png){:height="70%" width="70%"}


