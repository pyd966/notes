## 习题

> 48. 用高斯消法解下列方程组：
>
> $$
> (4)\begin{cases}
> x_1-2x_2+3x_3-4x_4=4\\
> x_2-x_3+x_4=-3\\
> x_1+3x_2-3x_4=1\\
> 7x_2-3x_3-x_4=3
> \end{cases}
> $$
> $$
> (5)\begin{cases}
> x_1+2x_2-x_3+2x_4=3\\
> x_1+x_2-x_3+x_4=2\\
> x_1-x_2-x_3-x_4=1\\
> 3x_1+2x_2-3x_3+2x_4=5
> \end{cases}
> $$
> $$
> (6)\begin{cases}
> x_1-x_2+x_3-x_4=0\\
> 2x_1+4x_2-5x_3+7x_4=0\\
> 3x_1+3x_2-4x_3+6x_4=0\\
> 3x_1-3x_2+3x_3-2x_4=0
> \end{cases}
> $$

$(4)$

$$
\begin{pmatrix}
1 & -2 & 3 & -4 & 4\\
0 & 1 & -1 & 1 & -3\\
1 & 3 & 0 & -3 & 1\\
0 & 7 & -3 & -1 & 3
\end{pmatrix}
\overset{\textcircled{3}-\textcircled{1}}{\xrightarrow{}}
\begin{pmatrix}
1 & -2 & 3 & -4 & 4\\
0 & 1 & -1 & 1 & -3\\
0 & 5 & -3 & 1 & -3\\
0 & 7 & -3 & -1 & 3
\end{pmatrix}
\overset{\textcircled{3}-5\times\textcircled{2}}{\xrightarrow{}}
\begin{pmatrix}
1 & -2 & 3 & -4 & 4\\
0 & 1 & -1 & 1 & -3\\
0 & 0 & 2 & -4 & 12\\
0 & 7 & -3 & -1 & 3
\end{pmatrix}
$$

$$
\overset{\textcircled{4}-7\times\textcircled{2}}{\xrightarrow{}}
\begin{pmatrix}
1 & -2 & 3 & -4 & 4\\
0 & 1 & -1 & 1 & -3\\
0 & 0 & 2 & -4 & 12\\
0 & 0 & 4 & -8 & 24
\end{pmatrix}
\overset{\textcircled{4}-2\times\textcircled{3}}{\xrightarrow{}}
\begin{pmatrix}
1 & -2 & 3 & -4 & 4\\
0 & 1 & -1 & 1 & -3\\
0 & 0 & 2 & -4 & 12\\
0 & 0 & 0 & 0 & 0
\end{pmatrix}
\overset{\textcircled{1}+2\times\textcircled{2}}{\xrightarrow{}}
$$

$$
\begin{pmatrix}
1 & 0 & 1 & -2 & -2\\
0 & 1 & -1 & 1 & -3\\
0 & 0 & 2 & -4 & 12\\
0 & 0 & 0 & 0 & 0
\end{pmatrix}
\overset{\textcircled{3}\div 2}{\xrightarrow{}}

\begin{pmatrix}
1 & 0 & 1 & -2 & -2\\
0 & 1 & -1 & 1 & -3\\
0 & 0 & 1 & -2 & 6\\
0 & 0 & 0 & 0 & 0
\end{pmatrix}
\overset{\textcircled{1}-\textcircled{3}}{\xrightarrow{}}

\begin{pmatrix}
1 & 0 & 0 & 0 & -8\\
0 & 1 & -1 & 1 & -3\\
0 & 0 & 1 & -2 & 6\\
0 & 0 & 0 & 0 & 0
\end{pmatrix}
$$

$$
\overset{\textcircled{2}+\textcircled{3}}{\xrightarrow{}}

\begin{pmatrix}
1 & 0 & 0 & 0 & -8\\
0 & 1 & 0 & -1 & 3\\
0 & 0 & 1 & -2 & 6\\
0 & 0 & 0 & 0 & 0
\end{pmatrix}
$$

令 $x_4=k$，可以解得

$$
\begin{cases}
x_1=-8\\
x_2=3+k\\
x_3=6+2k\\
x_4=k
\end{cases}
$$

也就是说 $(x_1,x_2,x_3,x_4)=(-8,3,6,0)+k(0,1,2,1)$。

$(5)$

$$
\begin{pmatrix}
1 & 2 & -1 & 2 & 3\\
1 & 1 & -1 & 1 & 2\\
1 & -1 & -1 & -1 & 1\\
3 & 2 & -3 & 2 & 5\\
\end{pmatrix}
\overset{\textcircled{2}-\textcircled{1}}{\xrightarrow{}}

\begin{pmatrix}
1 & 2 & -1 & 2 & 3\\
0 & -1 & 0 & -1 & -1\\
1 & -1 & -1 & -1 & 1\\
3 & 2 & -3 & 2 & 5\\
\end{pmatrix}
\overset{\textcircled{3}-\textcircled{1}}{\xrightarrow{}}

\begin{pmatrix}
1 & 2 & -1 & 2 & 3\\
0 & -1 & 0 & -1 & -1\\
0 & -3 & 0 & -3 & -2\\
3 & 2 & -3 & 2 & 5\\
\end{pmatrix}
\overset{\textcircled{3}-3\times\textcircled{2}}{\xrightarrow{}}
$$

$$
\begin{pmatrix}
1 & 2 & -1 & 2 & 3\\
0 & -1 & 0 & -1 & -1\\
0 & 0 & 0 & 0 & 1\\
3 & 2 & -3 & 2 & 5\\
\end{pmatrix}
$$

考虑式 $\textcircled{3}$，无解。

$(6)$

$$
\begin{pmatrix}
1 & -1 & 1 & -1 & 0\\
2 & 4 & -5 & 7 & 0\\
3 & 3 & -4 & 6 & 0\\
3 & -3 & 3 & -2 & 0\\
\end{pmatrix}
\overset{\textcircled{2}-2\times\textcircled{1}}{\xrightarrow{}}
\begin{pmatrix}
1 & -1 & 1 & -1 & 0\\
0 & 6 & -7 & 9 & 0\\
3 & 3 & -4 & 6 & 0\\
3 & -3 & 3 & -2 & 0\\
\end{pmatrix}
\overset{\textcircled{3}-3\times\textcircled{1}}{\xrightarrow{}}

\begin{pmatrix}
1 & -1 & 1 & -1 & 0\\
0 & 6 & -7 & 9 & 0\\
0 & 6 & -7 & 9 & 0\\
3 & -3 & 3 & -2 & 0\\
\end{pmatrix}
\overset{\textcircled{4}-3\times\textcircled{1}}{\xrightarrow{}}
$$

$$
\begin{pmatrix}
1 & -1 & 1 & -1 & 0\\
0 & 6 & -7 & 9 & 0\\
0 & 6 & -7 & 9 & 0\\
0 & 0 & 0 & 1 & 0\\
\end{pmatrix}
\overset{\textcircled{3}-\textcircled{2}}{\xrightarrow{}}

\begin{pmatrix}
1 & -1 & 1 & -1 & 0\\
0 & 6 & -7 & 9 & 0\\
0 & 0 & 0 & 0 & 0\\
0 & 0 & 0 & 1 & 0\\
\end{pmatrix}
\overset{}{\xrightarrow{}}

\begin{pmatrix}
1 & -1 & 1 & -1 & 0\\
0 & 6 & -7 & 9 & 0\\
0 & 0 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & 0\\
\end{pmatrix}
\overset{\textcircled{2}\div 6}{\xrightarrow{}}
$$

$$
\begin{pmatrix}
1 & -1 & 1 & -1 & 0\\
0 & 1 & -\frac76 & \frac32 & 0\\
0 & 0 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & 0\\
\end{pmatrix}
\overset{\textcircled{1}+\textcircled{2}}{\xrightarrow{}}
\begin{pmatrix}
1 & 0 & -\dfrac16 & \dfrac12 & 0\\
0 & 1 & -\frac76 & \frac32 & 0\\
0 & 0 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & 0\\
\end{pmatrix}
\overset{\textcircled{1}-\frac12\textcircled{3}}{\xrightarrow{}}
\begin{pmatrix}
1 & 0 & -\frac16 & 0 & 0\\
0 & 1 & -\frac76 & \frac32 & 0\\
0 & 0 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & 0\\
\end{pmatrix}
\overset{\textcircled{2}-\frac32\times\textcircled{3}}{\xrightarrow{}}
$$

$$
\begin{pmatrix}
1 & 0 & -\frac16 & 0 & 0\\
0 & 1 & -\frac76 & 0 & 0\\
0 & 0 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & 0\\
\end{pmatrix}
$$

取 $x_3$ 为自由变量，设 $x_3=k$，可以解得，

$$
\begin{cases}
x_1=\frac16k\\
x_2=\frac76k\\
x_3=k\\
x_4=0
\end{cases}
$$

即 $(x_1,x_2,x_3,x_4)=(\frac16k,\frac76k,k,0)$，或者 $(x_1,x_2,x_3,x_4)=k(\frac16,\frac76,1,0)$。