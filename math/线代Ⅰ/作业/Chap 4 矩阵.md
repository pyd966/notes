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