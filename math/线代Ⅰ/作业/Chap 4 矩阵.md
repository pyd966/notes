## 习题

> 7. 计算下列的矩阵乘积：
>
> $(3)\begin{pmatrix}x_1& x_2\end{pmatrix}\begin{pmatrix}a_{11}& a_{12}\\a_{21}&a_{22}\end{pmatrix}\begin{pmatrix}x_1\\ x_2\end{pmatrix}$
>
> $(4)\begin{pmatrix}2\\1\end{pmatrix}\begin{pmatrix}a&b\end{pmatrix}$
>
> $(8)\begin{pmatrix}a_1 & 0 & 0\\ 0 & a_2 & 0\\0 & 0 & a_3\end{pmatrix}\begin{pmatrix}0&1&0\\0&0&1\\1&0&0\end{pmatrix}$

$(3)$

$$
\begin{aligned}
\begin{pmatrix}x_1& x_2\end{pmatrix}\begin{pmatrix}a_{11}& a_{12}\\a_{21}&a_{22}\end{pmatrix}\begin{pmatrix}x_1\\ x_2\end{pmatrix}=\begin{pmatrix}x_1&x_2\end{pmatrix}\begin{pmatrix}a_{11}x_1+a_{12}x_2\\a_{21}x_1+a_{22}x_2\end{pmatrix}=a_{11}x_1^2+(a_{12}+a_{21})x_1x_2+a_{22}x_2^2
\end{aligned}
$$

$(4)$

$$
\begin{pmatrix}
2a & 2b\\
a & b\\
\end{pmatrix}
$$

$(8)$

$$
\begin{pmatrix}
0 & a_1 & 0\\
0 & 0 & a_2\\
a_3 & 0 & 0\\
\end{pmatrix}
$$

> 8. 计算 $QP,(PAQ)^k$（$k$ 为正整数），其中 $P,A,Q$ 为
>
> $$P=\begin{pmatrix}2&3\\1&2\end{pmatrix},A=\begin{pmatrix}2&0\\0&-1\end{pmatrix},Q=\begin{pmatrix}2&-3\\-1&2\end{pmatrix}$$

$$
QP=\begin{pmatrix}2&-3\\-1&2\end{pmatrix}\begin{pmatrix}2&3\\1&2\end{pmatrix}=\begin{pmatrix}1&0\\0&1\end{pmatrix}
$$

$$
PAQ=\begin{pmatrix}2&3\\1&2\end{pmatrix}\begin{pmatrix}2&0\\0&-1\end{pmatrix}\begin{pmatrix}2&-3\\-1&2\end{pmatrix}=\begin{pmatrix}2&3\\1&2\end{pmatrix}\begin{pmatrix}4&-6\\1&-2\end{pmatrix}=\begin{pmatrix}11 &-18\\6 &-10\end{pmatrix}
$$

我们声称，$(PAQ)^k=\begin{pmatrix}2^{k+2}-3\times(-1)^k&6\times(-1)^k-6\times2^k\\2^{k+1}-2\times(-1)^k& 4\times(-1)^k-3\times2^k\end{pmatrix}$

采用归纳法证明，当 $k=1$ 时容易验证成立。

下证若 $k=n$ 成立，则 $k=n+1$ 也成立。

$$
\begin{aligned}
(PAQ)^{n+1}&=(PAQ)^n\times(PAQ)\\
&=\begin{pmatrix}2^{n+2}-3\times(-1)^n&6\times(-1)^n-6\times2^n\\2^{n+1}-2\times(-1)^n& 4\times(-1)^n-3\times2^n\end{pmatrix}\begin{pmatrix}11&-18\\6&-10\end{pmatrix}\\
&=\begin{pmatrix}2^{n+2}-3\times(-1)^{n+1}& 6\times(-1)^{n+1}-6\times2^{n+1}\\2^{n+2}-2\times(-1)^{n+1}& 4\times(-1)^{n+1}-3\times2^{n+1}\end{pmatrix}
\end{aligned}
$$

所以结论成立。

> 13. 求所有与 $A$ 可交换的矩阵，其中
>
> $(1)A=\begin{pmatrix}1&1\\0&1\end{pmatrix}$
>
> $(2)A=\begin{pmatrix}1&0&0\\0&1&2\\0&1&-2\end{pmatrix}$

$(1)$

设为 $B=(b_{i,j})_{2\times2}$

则 $AB=\begin{pmatrix}b_{11}+b_{21}&b_{12}+b_{22}\\b_{21}&b_{22}\end{pmatrix}$

$BA=\begin{pmatrix}b_{11}&b_{11}+b_{12}\\b_{21}&b_{21}+b_{22}\end{pmatrix}$

可以列出四个方程，最终得到 $b_{21}=0,b_{11}=b_{22}$。

也就是说，形如 $\begin{pmatrix}b_1&b_2\\0&b_1\end{pmatrix}$ 的矩阵都是可以的。

$(2)$

设为 $B=(b_{i,j})_{3\times3}$

则 $AB=\begin{pmatrix}b_{11}&b_{12}&b_{13}\\ b_{21}+2b_{31}& b_{22}+2b_{32} & b_{23}+2b_{33}\\ b_{21}-2b_{31}& b_{22}-2b_{32}& b_{23}-2b_{33}\end{pmatrix}$


$BA=\begin{pmatrix}b_{11}& b_{12}+b_{13}& 2b_{12}-2b_{13}\\ b_{21}& b_{22}+b_{23}& 2b_{22}-2b_{23}\\ b_{31}& b_{32}+b_{33}& 2b_{32}-2b_{33}\end{pmatrix}$

可以列出九个方程，最终解得矩阵形如 $\begin{pmatrix}x&0&0\\0&3y+z& 2y\\0& y& z\end{pmatrix}$

> 15. 设 $f(x),g(x)\in F[x],A,B\in M_n(F)$，证明：
>
> $$f(A)g(A)=g(A)f(A)$$
>
> $(1)$ 如果 $AB=BA$，则 $f(A)g(B)=g(B)f(A)$
>
> $(2)$ 设 $f(x)=1+x+\dots+x^{m-1},g(x)=1-x,A=\begin{pmatrix}a&b\\0&a\end{pmatrix}$，计算 $f(A)g(A)=?$

先证明。

设 $f(x)=a_px^p+\dots+a_0x^0,g(x)=b_qx^q+\dots+b_0x^0(a_p,b_q\neq0)$。

则 $f(A)g(A)=(\sum\limits_{i=0}^pa_iA^i)(\sum\limits_{j=0}^qb_jA^j)=\sum\limits_{i=0}^p\sum\limits_{j=0}^qa_ib_jA^iA^j=\sum\limits_{i=0}^p\sum\limits_{j=0}^qa_ib_jA^{i+j}$

$g(A)f(A)=(\sum\limits_{j=0}^qb_jA^j)(\sum\limits_{i=0}^pa_iA^i)=\sum\limits_{j=0}^q\sum\limits_{i=0}^pb_ja_iA^jA_i=\sum\limits_{i=0}^p\sum\limits_{j=0}^qa_ib_jA^{i+j}$

所以 $f(A)g(A)=g(A)f(A)$。

$(1)$

先证明引理 $A^iB^j=B^jA^i(i,j\in N^+)$。

$A^iB^j=\underbrace{A\cdots A}_{i个}\underbrace{B\cdots B}_{j个}=B\underbrace{A\cdots A}_{i个}\underbrace{B\cdots B}_{j-1个}=\dots=\underbrace{B\cdots B}_{j个}\underbrace{A\cdots A}_{i个}=B^jA^i$

而 $f(A)g(B)=\sum\limits_{i=0}^p\sum\limits_{j=0}^qa_ib_jA^iB^j,g(B)f(A)=\sum_{i=0}^p\sum_{j=0}^qa_ib_jB^jA^i$。

由上述引理，$f(A)g(B)=g(B)f(A)$

$(2)$

$f(A)g(A)=(\sum\limits_{i=0}^{m-1}A^i)(A^0-A)=\sum\limits_{i=0}^{m-1}A^i-\sum_{i=0}^{m-1}A^{i+1}=A^0-A^m$。

下面声称，$A^k=\begin{pmatrix}a^k&ka^{k-1}b\\0&a^k\end{pmatrix}$

采用归纳法，$k=1$ 时成立，下面证明当 $k=n$ 成立时 $k=n+1$ 也成立。

$A^{n+1}=A^nA=\begin{pmatrix}a^n&na^{n-1}b\\0&a^n\end{pmatrix}\begin{pmatrix}a&b\\0&a\end{pmatrix}=\begin{pmatrix}a^{n+1}&(n+1)a^nb\\0&a^{n+1}\end{pmatrix}$

所以，$f(A)g(A)=A^0-A^m=\begin{pmatrix}1-a^m&-ma^{m-1}b\\0&1-a^m\end{pmatrix}$

> 19. 设 $B=\{\alpha_1,\alpha_2,\alpha_3\}$ 是三维向量空间 $V$ 的一组基，$\sigma\in L(V,V)$ 关于基 $B$ 所对应的矩阵为 $A$，求 $\text{Im}\sigma,\text{Ker}\sigma$。
>
> $(1)A=\begin{pmatrix}1&0&2\\-1&2&1\\1&2&5\\\end{pmatrix}$
>
> $(2)A=\begin{pmatrix}1&-2&1\\-1&2&-1\\-2&4&-2\\\end{pmatrix}$

$(1)$

记 $\beta_1=\alpha_1-\alpha_2+\alpha_3,\beta_2,\beta_3$ 同理。

$\text{Im}\sigma=L(\beta_1,\beta_2,\beta_3)$，可以发现 $\beta_3=2\beta_1+\dfrac32\beta_2$，同时 $\beta_1,\beta_2$ 线性无关。

所以 $\text{Im}\sigma=L(\beta_1,\beta_2)$。

解方程 $AX=O$，得到 $X=k(-2,-\dfrac32,1)$，所以 $\text{Ker}\sigma=L(-2\alpha_1-\dfrac32\alpha+2+\alpha_3)$。

$(2)$

同上记 $\beta_1,\beta_2,\beta_3$。

$\text{Im}=L(\beta_1,\beta_2,\beta_3)$，可以发现 $\beta_2=-2\beta_1,\beta_3=\beta_1$。

所以 $\text{Im}\sigma=L(\beta_1)$。

解方程 $AX=O$，得到 $X=k_1(-1,0,1)+k_2(2,1,0)$，所以 $\text{Ker}\sigma=L(-\alpha_1+\alpha_3,2\alpha_1+\alpha_2)$。

> 21. 设方阵 $A$ 满足 $A^2-A-2E=O$，证明：
>
> $(1)$ $A$ 和 $E-A$ 都是可逆矩阵，并求它们的逆矩阵；
>
> $(2)$ $A+E$ 和 $A-2E$ 不可能同时都是可逆的。

$(1)$

由 $A^2-A-2E=O$ 可知 $A(A-E)=2E$，即 $A(\dfrac{A-1}{2})=E$，由定义知 $A$ 可逆，$A^{-1}=\dfrac{A-1}{2}$。

同理可得 $(E-A)(-\dfrac{A}{2})=E$，所以 $E-A$ 可逆，$(E-A)^{-1}=-\dfrac{A}2$。

$(2)$

由 $A^2-A-2E=O$ 可知 $(A+E)(A-2E)=O$。

反证法，如果二者均可逆，则 $(A+E)(A-2E)$ 也可逆，但是零矩阵 $O$ 是不可逆的。

> 23. 设 $A,B$ 是同阶非奇异矩阵（即可逆矩阵），证明下列等式彼此等价：
>
> $$
> AB=BA;\ AB^{-1}=B^{-1}A\\
> B^{-1}A^{-1}=A^{-1}B^{-1};\ A^{-1}B=BA^{-1}
> $$

$(1)\Rightarrow(4)$

$$
\begin{aligned}
&AB=BA\\
&\Rightarrow A^{-1}AB=A^{-1}BA\\
&\Rightarrow B=A^{-1}BA\\
&\Rightarrow BA^{-1}=A^{-1}B
\end{aligned}
$$

$(4)\Rightarrow(3)$

$$
\begin{aligned}
&A^{-1}B=BA^{-1}\\
&\Rightarrow B^{-1}A^{-1}B=A^{-1}\\
&\Rightarrow B^{-1}A^{-1}=A^{-1}B^{-1}
\end{aligned}
$$

$(3)\Rightarrow(2)$

$$
\begin{aligned}
&B^{-1}A^{-1}=A^{-1}B^{-1}\\
&\Rightarrow AB^{-1}A^{-1}=B^{-1}\\
&\Rightarrow AB^{-1}=B^{-1}A
\end{aligned}
$$

$(2)\Rightarrow(1)$

$$
\begin{aligned}
&AB^{-1}=B^{-1}A\\
&\Rightarrow BAB^{-1}=A\\
&\Rightarrow BA=AB
\end{aligned}
$$

> 31. 用初等变换法求下列矩阵的逆矩阵：
>
> $(4)\begin{pmatrix}2&3&4&1\\ 3&4&1&2\\ 4&1&2&3\\ 1&-1&1&-1\end{pmatrix}$
>
> $(6)\begin{pmatrix}1&2&3&4\\ 4&1&2&3\\ 3&4&1&2\\ 2&3&4&1\end{pmatrix}$

$(4)$

$$
A = \begin{pmatrix}
2 & 3 & 4 & 1 \\
3 & 4 & 1 & 2 \\
4 & 1 & 2 & 3 \\
1 & -1 & 1 & -1
\end{pmatrix}
$$

增广矩阵 $[A | I]$:

$$
\left(\begin{array}{cccc|cccc}
2 & 3 & 4 & 1 & 1 & 0 & 0 & 0 \\
3 & 4 & 1 & 2 & 0 & 1 & 0 & 0 \\
4 & 1 & 2 & 3 & 0 & 0 & 1 & 0 \\
1 & -1 & 1 & -1 & 0 & 0 & 0 & 1
\end{array}\right)
$$

变换过程：

$$
\xrightarrow{[1] \leftrightarrow [4]}
\left(\begin{array}{cccc|cccc}
1 & -1 & 1 & -1 & 0 & 0 & 0 & 1 \\
3 & 4 & 1 & 2 & 0 & 1 & 0 & 0 \\
4 & 1 & 2 & 3 & 0 & 0 & 1 & 0 \\
2 & 3 & 4 & 1 & 1 & 0 & 0 & 0
\end{array}\right)
$$

$$
\xrightarrow{[2] \leftarrow [2] - 3[1],\ [3] \leftarrow [3] - 4[1],\ [4] \leftarrow [4] - 2[1]}
\left(\begin{array}{cccc|cccc}
1 & -1 & 1 & -1 & 0 & 0 & 0 & 1 \\
0 & 7 & -2 & 5 & 0 & 1 & 0 & -3 \\
0 & 5 & -2 & 7 & 0 & 0 & 1 & -4 \\
0 & 5 & 2 & 3 & 1 & 0 & 0 & -2
\end{array}\right)
$$

$$
\xrightarrow{[2] \leftarrow [2] \times \frac{1}{7}}
\left(\begin{array}{cccc|cccc}
1 & -1 & 1 & -1 & 0 & 0 & 0 & 1 \\
0 & 1 & -\frac{2}{7} & \frac{5}{7} & 0 & \frac{1}{7} & 0 & -\frac{3}{7} \\
0 & 5 & -2 & 7 & 0 & 0 & 1 & -4 \\
0 & 5 & 2 & 3 & 1 & 0 & 0 & -2
\end{array}\right)
$$

$$
\xrightarrow{[1] \leftarrow [1] + [2],\ [3] \leftarrow [3] - 5[2],\ [4] \leftarrow [4] - 5[2]}
\left(\begin{array}{cccc|cccc}
1 & 0 & \frac{5}{7} & -\frac{2}{7} & 0 & \frac{1}{7} & 0 & \frac{4}{7} \\
0 & 1 & -\frac{2}{7} & \frac{5}{7} & 0 & \frac{1}{7} & 0 & -\frac{3}{7} \\
0 & 0 & -\frac{4}{7} & \frac{24}{7} & 0 & -\frac{5}{7} & 1 & -\frac{13}{7} \\
0 & 0 & \frac{24}{7} & -\frac{4}{7} & 1 & -\frac{5}{7} & 0 & \frac{1}{7}
\end{array}\right)
$$

$$
\xrightarrow{[3] \leftarrow [3] \times \left(-\frac{7}{4}\right)}
\left(\begin{array}{cccc|cccc}
1 & 0 & \frac{5}{7} & -\frac{2}{7} & 0 & \frac{1}{7} & 0 & \frac{4}{7} \\
0 & 1 & -\frac{2}{7} & \frac{5}{7} & 0 & \frac{1}{7} & 0 & -\frac{3}{7} \\
0 & 0 & 1 & -6 & 0 & \frac{5}{4} & -\frac{7}{4} & \frac{13}{4} \\
0 & 0 & \frac{24}{7} & -\frac{4}{7} & 1 & -\frac{5}{7} & 0 & \frac{1}{7}
\end{array}\right)
$$

$$
\xrightarrow{[1] \leftarrow [1] - \frac{5}{7}[3],\ [2] \leftarrow [2] + \frac{2}{7}[3],\ [4] \leftarrow [4] - \frac{24}{7}[3]}
\left(\begin{array}{cccc|cccc}
1 & 0 & 0 & 4 & 0 & -\frac{3}{4} & \frac{5}{4} & -\frac{7}{4} \\
0 & 1 & 0 & -1 & 0 & \frac{1}{2} & -\frac{1}{2} & \frac{1}{2} \\
0 & 0 & 1 & -6 & 0 & \frac{5}{4} & -\frac{7}{4} & \frac{13}{4} \\
0 & 0 & 0 & 20 & 1 & -5 & 6 & -11
\end{array}\right)
$$

$$
\xrightarrow{[4] \leftarrow [4] \times \frac{1}{20}}
\left(\begin{array}{cccc|cccc}
1 & 0 & 0 & 4 & 0 & -\frac{3}{4} & \frac{5}{4} & -\frac{7}{4} \\
0 & 1 & 0 & -1 & 0 & \frac{1}{2} & -\frac{1}{2} & \frac{1}{2} \\
0 & 0 & 1 & -6 & 0 & \frac{5}{4} & -\frac{7}{4} & \frac{13}{4} \\
0 & 0 & 0 & 1 & \frac{1}{20} & -\frac{1}{4} & \frac{3}{10} & -\frac{11}{20}
\end{array}\right)
$$

$$
\xrightarrow{[1] \leftarrow [1] - 4[4],\ [2] \leftarrow [2] + [4],\ [3] \leftarrow [3] + 6[4]}
\left(\begin{array}{cccc|cccc}
1 & 0 & 0 & 0 & -\frac{1}{5} & \frac{1}{4} & \frac{1}{20} & \frac{9}{20} \\
0 & 1 & 0 & 0 & \frac{1}{20} & \frac{1}{4} & -\frac{1}{5} & -\frac{1}{20} \\
0 & 0 & 1 & 0 & \frac{3}{10} & -\frac{1}{4} & \frac{1}{20} & -\frac{1}{20} \\
0 & 0 & 0 & 1 & \frac{1}{20} & -\frac{1}{4} & \frac{3}{10} & -\frac{11}{20}
\end{array}\right)
$$

逆矩阵为：

$$
A^{-1} = \begin{pmatrix}
-\frac{1}{5} & \frac{1}{4} & \frac{1}{20} & \frac{9}{20} \\
\frac{1}{20} & \frac{1}{4} & -\frac{1}{5} & -\frac{1}{20} \\
\frac{3}{10} & -\frac{1}{4} & \frac{1}{20} & -\frac{1}{20} \\
\frac{1}{20} & -\frac{1}{4} & \frac{3}{10} & -\frac{11}{20}
\end{pmatrix}
$$

$(6)$

$$
B = \begin{pmatrix}
1 & 2 & 3 & 4 \\
4 & 1 & 2 & 3 \\
3 & 4 & 1 & 2 \\
2 & 3 & 4 & 1
\end{pmatrix}
$$

增广矩阵 $[B | I]$:

$$
\left(\begin{array}{cccc|cccc}
1 & 2 & 3 & 4 & 1 & 0 & 0 & 0 \\
4 & 1 & 2 & 3 & 0 & 1 & 0 & 0 \\
3 & 4 & 1 & 2 & 0 & 0 & 1 & 0 \\
2 & 3 & 4 & 1 & 0 & 0 & 0 & 1
\end{array}\right)
$$

变换过程：

$$
\xrightarrow{[2] \leftarrow [2] - 4[1],\ [3] \leftarrow [3] - 3[1],\ [4] \leftarrow [4] - 2[1]}
\left(\begin{array}{cccc|cccc}
1 & 2 & 3 & 4 & 1 & 0 & 0 & 0 \\
0 & -7 & -10 & -13 & -4 & 1 & 0 & 0 \\
0 & -2 & -8 & -10 & -3 & 0 & 1 & 0 \\
0 & -1 & -2 & -7 & -2 & 0 & 0 & 1
\end{array}\right)
$$

$$
\xrightarrow{[2] \leftrightarrow [4]}
\left(\begin{array}{cccc|cccc}
1 & 2 & 3 & 4 & 1 & 0 & 0 & 0 \\
0 & -1 & -2 & -7 & -2 & 0 & 0 & 1 \\
0 & -2 & -8 & -10 & -3 & 0 & 1 & 0 \\
0 & -7 & -10 & -13 & -4 & 1 & 0 & 0
\end{array}\right)
$$

$$
\xrightarrow{[2] \leftarrow [2] \times (-1)}
\left(\begin{array}{cccc|cccc}
1 & 2 & 3 & 4 & 1 & 0 & 0 & 0 \\
0 & 1 & 2 & 7 & 2 & 0 & 0 & -1 \\
0 & -2 & -8 & -10 & -3 & 0 & 1 & 0 \\
0 & -7 & -10 & -13 & -4 & 1 & 0 & 0
\end{array}\right)
$$

$$
\xrightarrow{[1] \leftarrow [1] - 2[2],\ [3] \leftarrow [3] + 2[2],\ [4] \leftarrow [4] + 7[2]}
\left(\begin{array}{cccc|cccc}
1 & 0 & -1 & -10 & -3 & 0 & 0 & 2 \\
0 & 1 & 2 & 7 & 2 & 0 & 0 & -1 \\
0 & 0 & -4 & 4 & 1 & 0 & 1 & -2 \\
0 & 0 & 4 & 36 & 10 & 1 & 0 & -7
\end{array}\right)
$$

$$
\xrightarrow{[3] \leftarrow [3] \times \left(-\frac{1}{4}\right)}
\left(\begin{array}{cccc|cccc}
1 & 0 & -1 & -10 & -3 & 0 & 0 & 2 \\
0 & 1 & 2 & 7 & 2 & 0 & 0 & -1 \\
0 & 0 & 1 & -1 & -\frac{1}{4} & 0 & -\frac{1}{4} & \frac{1}{2} \\
0 & 0 & 4 & 36 & 10 & 1 & 0 & -7
\end{array}\right)
$$

$$
\xrightarrow{[1] \leftarrow [1] + [3],\ [2] \leftarrow [2] - 2[3],\ [4] \leftarrow [4] - 4[3]}
\left(\begin{array}{cccc|cccc}
1 & 0 & 0 & -11 & -\frac{13}{4} & 0 & -\frac{1}{4} & \frac{5}{2} \\
0 & 1 & 0 & 9 & \frac{5}{2} & 0 & \frac{1}{2} & -2 \\
0 & 0 & 1 & -1 & -\frac{1}{4} & 0 & -\frac{1}{4} & \frac{1}{2} \\
0 & 0 & 0 & 40 & 11 & 1 & 1 & -9
\end{array}\right)
$$

$$
\xrightarrow{[4] \leftarrow [4] \times \frac{1}{40}}
\left(\begin{array}{cccc|cccc}
1 & 0 & 0 & -11 & -\frac{13}{4} & 0 & -\frac{1}{4} & \frac{5}{2} \\
0 & 1 & 0 & 9 & \frac{5}{2} & 0 & \frac{1}{2} & -2 \\
0 & 0 & 1 & -1 & -\frac{1}{4} & 0 & -\frac{1}{4} & \frac{1}{2} \\
0 & 0 & 0 & 1 & \frac{11}{40} & \frac{1}{40} & \frac{1}{40} & -\frac{9}{40}
\end{array}\right)
$$

$$
\xrightarrow{[1] \leftarrow [1] + 11[4],\ [2] \leftarrow [2] - 9[4],\ [3] \leftarrow [3] + [4]}
\left(\begin{array}{cccc|cccc}
1 & 0 & 0 & 0 & -\frac{9}{40} & \frac{11}{40} & \frac{1}{40} & \frac{1}{40} \\
0 & 1 & 0 & 0 & \frac{1}{40} & -\frac{9}{40} & \frac{11}{40} & \frac{1}{40} \\
0 & 0 & 1 & 0 & \frac{1}{40} & \frac{1}{40} & -\frac{9}{40} & \frac{11}{40} \\
0 & 0 & 0 & 1 & \frac{11}{40} & \frac{1}{40} & \frac{1}{40} & -\frac{9}{40}
\end{array}\right)
$$

逆矩阵为：

$$
B^{-1} = \begin{pmatrix}
-\frac{9}{40} & \frac{11}{40} & \frac{1}{40} & \frac{1}{40} \\
\frac{1}{40} & -\frac{9}{40} & \frac{11}{40} & \frac{1}{40} \\
\frac{1}{40} & \frac{1}{40} & -\frac{9}{40} & \frac{11}{40} \\
\frac{11}{40} & \frac{1}{40} & \frac{1}{40} & -\frac{9}{40}
\end{pmatrix}
$$

> 33. 利用逆矩阵（或用初等变换法），解下列矩阵方程：
>
> $(2)\begin{pmatrix}2&3&-1\\ 1&2&0\\ -1&2&-2\end{pmatrix}X=\begin{pmatrix}2&1\\ -1&0\\ 3&1\end{pmatrix}$
>
> $(3)A\begin{pmatrix}1&0&0\\1&1&0\\1&1&1\end{pmatrix}=\begin{pmatrix}1&-2&1\\0&1&-1\end{pmatrix}$

$(2)$

矩阵方程：

$$
A=\begin{pmatrix}
2 & 3 & -1\\
1 & 2 & 0\\
-1 & 2 & -2\\
\end{pmatrix}
$$

$$
B=\begin{pmatrix}
2 & 1\\
-1 & 0\\
3 & 1\\
\end{pmatrix}
$$

增广矩阵 $[A | B]$

$$
\left(\begin{array}{ccc|cc}
2 & 3 & -1 & 2 & 1 \\
1 & 2 & 0 & -1 & 0 \\
-1 & 2 & -2 & 3 & 1
\end{array}\right)
$$

变换过程：

$$
\xrightarrow{[1]\leftrightarrow[2]}
\left(\begin{array}{ccc|cc}
1 & 2 & 0 & -1 & 0 \\
2 & 3 & -1 & 2 & 1 \\
-1 & 2 & -2 & 3 & 1
\end{array}\right)
$$

$$
\xrightarrow{[2]\leftarrow[2]-2[1],\ [3]\leftarrow[3]+[1]}
\left(\begin{array}{ccc|cc}
1 & 2 & 0 & -1 & 0 \\
0 & -1 & -1 & 4 & 1 \\
0 & 4 & -2 & 2 & 1
\end{array}\right)
$$

$$
\xrightarrow{[2]\leftarrow -[2]}
\left(\begin{array}{ccc|cc}
1 & 2 & 0 & -1 & 0 \\
0 & 1 & 1 & -4 & -1 \\
0 & 4 & -2 & 2 & 1
\end{array}\right)
$$

$$
\xrightarrow{[1]\leftarrow[1]-2[2],\ [3]\leftarrow[3]-4[2]}
\left(\begin{array}{ccc|cc}
1 & 0 & -2 & 7 & 2 \\
0 & 1 & 1 & -4 & -1 \\
0 & 0 & -6 & 18 & 5
\end{array}\right)
$$

$$
\xrightarrow{[3]\leftarrow[3]/(-6)}
\left(\begin{array}{ccc|cc}
1 & 0 & -2 & 7 & 2 \\
0 & 1 & 1 & -4 & -1 \\
0 & 0 & 1 & -3 & -\frac{5}{6}
\end{array}\right)
$$

$$
\xrightarrow{[1]\leftarrow[1]+2[3],\ [2]\leftarrow[2]-[3]}
\left(\begin{array}{ccc|cc}
1 & 0 & 0 & 1 & \frac{1}{3} \\
0 & 1 & 0 & -1 & -\frac{1}{6} \\
0 & 0 & 1 & -3 & -\frac{5}{6}
\end{array}\right)
$$

解得：

$$
X = \begin{pmatrix}
1 & \frac{1}{3} \\
-1 & -\frac{1}{6} \\
-3 & -\frac{5}{6}
\end{pmatrix}
$$

$(3)$

$$
B=\begin{pmatrix}
1 & 0 & 0\\
1 & 1 & 0\\
1 & 1 & 1\\
\end{pmatrix}
$$

$$
C=\begin{pmatrix}
1 & -2 & 1\\
0 & 1 & -1\\
\end{pmatrix}
$$

可以知道

$$
B^{-1}=\begin{pmatrix}
1 & 0 & 0\\
-1 & 1 & 0\\
0 & -1 & 1
\end{pmatrix}
$$

则 $A=CB^{-1}$

可得

$$
A=\begin{pmatrix}
3 & -3 & 1\\
-1 & 2 & -1\\
\end{pmatrix}
$$

> 35. 用初等变换法，求下列矩阵的秩：
>
> $(2)\begin{pmatrix}1&3&-2&5&4\\1&4&1&3&5\\1&4&2&4&3\\2&7&-3&6&13\\\end{pmatrix}$

$(2)$

进行初等行变换，最终得到

$$
\begin{pmatrix}
1&0&0&22&-21\\
0&1&0&-5&7\\
0&0&1&1&-2\\
0&0&0&0&0\\
\end{pmatrix}
$$

容易发现，这个矩阵的秩是 $3$。

因为初等行变换不改变矩阵的秩，所以 $r(A)=3$。

> 44. 设
>
> $$
> A=\begin{pmatrix}1&2&0&0&0\\2&5&0&0&0\\0&0&-2&1&0\\0&0&0&-2&1\\0&0&0&0&-2\\\end{pmatrix}\ B=\begin{pmatrix}1&0&1&0\\-1&2&3&0\\1&2&0&4\\0&1&2&4\\0&0&1&4\\\end{pmatrix}
> $$
>
> 用矩阵分块的方法：$(1)$ 计算 $A^2,AB$；$(2)$ 求 $A^{-1}$。

$A_{1,1}=\begin{pmatrix}1 & 2\\ 2 & 5\\\end{pmatrix},A_{1,2}=(0)_{2\times3},A_{2,1}=(0)_{3\times2},A_{2,2}=\begin{pmatrix}-2 & 1 & 0\\ 0 & -2 & 1\\ 0 & 0 & -2\\\end{pmatrix}$

$B_{1,1}=\begin{pmatrix}1 & 0\\ -1 & 2\\\end{pmatrix},B_{1,2}=\begin{pmatrix}1 & 0\\3 & 0\\\end{pmatrix},B_{2,1}=\begin{pmatrix}1 & 2\\0 & 1\\0 & 0\\\end{pmatrix},B_{2,2}=\begin{pmatrix}0 & 4\\2 & 4\\1 & 4\\\end{pmatrix}$

$(1)$

$A^2=\begin{pmatrix}A_{1,1} & O\\ O & A_{2,2}\\\end{pmatrix}^2=\begin{pmatrix}A_{1,1}^2 & O\\O & A_{2,2}^2\end{pmatrix}=\begin{pmatrix}5 & 12 & 0 & 0 & 0\\12 & 29 & 0 & 0 & 0\\ 0 & 0 & 4 & -4 & 1\\0 & 0 & 0 & 4 & -4\\ 0 & 0 & 0 & 0 & 4\\\end{pmatrix}$

$AB=\begin{pmatrix}A_{1,1} & O\\ O & A_{2,2}\\\end{pmatrix}\begin{pmatrix}B_{1,1} & B_{1,2}\\ B_{2,1} & B_{2,2}\\\end{pmatrix}=\begin{pmatrix}A_{1,1}B_{1,1} & A_{1,1}B_{1,2}\\ A_{2,2}B_{2,1} & A_{2,2}B_{2,2}\\\end{pmatrix}=\begin{pmatrix}-1 & 4 & 7 & 0\\-3 & 10 & 17 & 0\\-2 & -3 & 2 & -4\\0 & -2 & -3 & -4\\ 0 & 0 & -2 & -8\\\end{pmatrix}$

$(2)$

经验证可知 $A_{1,1}^{-1}=\begin{pmatrix}5 & -2\\-2 & 1\\\end{pmatrix},A_{1,2}^{-1}=\begin{pmatrix}-\frac12 & -\frac14 & -\frac18\\0 & -\frac12 & -\frac14\\0 & 0 & -\frac12\end{pmatrix}$。

而 $A$ 是对角块矩阵，$A^{-1}=\begin{pmatrix}A_{1,1}^{-1} & O\\O & A_{2,2}^{-1}\end{pmatrix}=\begin{pmatrix}5 & -2 & 0 & 0 & 0\\-2 & 1 & 0 & 0 & 0\\0 & 0 & -\frac12 & -\frac14 & -\frac18\\0 & 0 & 0 & -\frac12 & -\frac14\\0 & 0 & 0 & 0 & -\frac12\\\end{pmatrix}$

> 53. 已知 $R^3$ 的基 $B_1=\{\alpha_1,\alpha_2,\alpha_3\}$ 和 $B_2=\{\beta_1,\beta_2,\beta_3\}$ 为
>
> $$
> \alpha_1=(1,2,1),\ \alpha_2=(2,3,3),\ \alpha_3=(3,7,1)\\
> \beta_1=(3,1,4),\ \beta_2=(5,2,1),\ \beta_3=(1,1,-6)\\
> $$
>
> $(1)$ 求 $\gamma=(3,6,2)$ 在基 $B_1$ 下的坐标；
>
> $(2)$ 求基 $B_1$ 变为基 $B_2$ 的变换矩阵；
>
> $(3)$ 利用变换矩阵，求 $\gamma$ 在基 $B_2$ 下的坐标。

$(1)$

可以发现 $\gamma=-2\alpha_1+\alpha_2+\alpha_3$，所以 $(\gamma)_{B_1}=(-2,1,1)$。

$(2)$

取自然基 $B_3=\{e_1,e_2,e_3\}$。

基 $B_3$ 变换为 $B_1$ 的矩阵为 $P_1=\begin{pmatrix}\alpha_1,\alpha_2,\alpha_3\end{pmatrix}$，同理，基 $B_3$ 变换为 $B_2$ 的矩阵为 $P_2=\begin{pmatrix}\beta_1,\beta_2,\beta_3\end{pmatrix}$。

$(\alpha_1,\alpha_2,\alpha_3)=(e_1,e_2,e_3)P_1,(\beta_1,\beta_2,\beta_3)=(e_1,e_2,e_3)P_2$。

可以得到 $(e_1,e_2,e_3)=(\alpha_1,\alpha_2,\alpha_3)P_1^{-1}$。

代入得 $(\beta_1,\beta_2,\beta_3)=(\alpha_1,\alpha_2,\alpha_3)P_1^{-1}P_2$。

变换矩阵 $P_1^{-1}P_2=\begin{pmatrix}-27 & -71 & -41\\9 & 20 & 9\\4 & 12 & 8\\\end{pmatrix}$

$(3)$

$(\gamma)_{B_2}=(P_1^{-1}P_2)^{-1}(\gamma)_{B_1}=P_2^{-1}P_1\begin{pmatrix}-2\\1\\1\end{pmatrix}=\begin{pmatrix}\dfrac{153}4 & -\dfrac{53}2 & \dfrac{83}4\end{pmatrix}^T$