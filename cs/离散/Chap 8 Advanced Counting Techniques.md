# Chap 8 Advanced Counting Techniques

## Section 8.1

> 24. Find a recurrence relation for the number of bit sequences
of length n with an even number of 0s.

Suppose the answer be $f(n)$.

A bit string with even 0s can be divided into 2 parts, ending with 0 or 1.

If it ends with 1, the previous $n-1$ bits form a valid bit string, $f(n-1)$

If it ends with 0, the previous $n-1$ bits form an invalid bit string, $2^{n-1}-f(n-1)$

So $f(n)=f(n-1)+(2^{n-1}-f(n-1))=2^{n-1}$

> 26. a) Find a recurrence relation for the number of ways
to completely cover a 2 × n checkerboard with 1 × 2
dominoes. [Hint: Consider separately the coverings
where the position in the top right corner of the
checkerboard is covered by a domino positioned horizontally
and where it is covered by a domino positioned
vertically.]
>
> b) What are the initial conditions for the recurrence relation
in part (a)?
> 
> c) How many ways are there to completely cover a 2 ×
17 checkerboard with 1 × 2 dominoes?

a)

Suppose the answer be $f(n)$

If the last colume is covered by a vertical domino, $f(n-1)$.

If the last colume is covered by 2 horizontal domino, $f(n-2)$

So $f(n)=f(n-1)+f(n-2)$.

b)

$f(1)=1,f(2)=2$

c)

So $f$ is simply fibonacci number.

$f(17)=2584$

> 42. Show that if $k$ is as chosen in Exercise 41, then
$R(n) − R(n − 1) = 2^{k−1}$.

Prove by induction.

When $n=1,2,3$, it's correct.

Suppose $n\le\dfrac{(k-1)k}{2}$ is correct, then prove $n\le\dfrac{k(k+1)}{2}$ is correct.

When $\dfrac{(k-1)k}{2}+2\le n\le\dfrac{k(k+1)}{2}$, $R(n)-R(n-1)=(2R(n-k)+2^k-1)-(2R(n-k-1)+2^k-1)=2(R(n-k)-R(n-k-1))=2\times2^{k-2}=2^{k-1}$

When $n=\dfrac{(k-1)k}{2}+1$, $R(n)-R(n-1)=(2R(n-k)+2^k-1)-(2R((n-1)-(k-1))+2^{k-1}-1)=2^{k-1}$

By mathematical induction, $R(n)-R(n-1)=2^{k-1}$

> 45. Show that $R(n)$ is $O(\sqrt n2^{\sqrt{2n}})$

Suppose $\dfrac{k(k-1)}{2}<n\le\dfrac{k(k+1)}{2}$.

Let $n'=\dfrac{k(k+1)}{2}$, then $R(n')\ge R(n)$.

$R(n')=\sum\limits_{i=1}^k\sum\limits_{j=1}^i2^{i-1}=\sum\limits_{i=1}^ki2^{i-1}=(k-1)2^k+1$

$k=O(\sqrt n)$, so $R(n)=O(R(n'))=O((k-1)2^k+1)=O(\sqrt n2^{\sqrt n})=O(\sqrt n2^{\sqrt{2n}})$

> 49. Let $\{a_n\}$ be a sequence of real numbers. The backward differences
of this sequence are defined recursively as shown
next. The first difference $∇a_n$ is
$∇a_n = a_n − a_{n−1}$.
The $(k + 1)$st difference $∇^{k+1}a_n$ is obtained from $∇^ka_n$ by
$∇^{k+1}an = ∇^ka_n −∇^ka_{n−1}$.
> 
> Show that $a_{n−2} = a_n − 2∇a_n +∇^2a_n.$

$\Delta a_n=a_n-a_{n-1}$

$\Delta^2a_n=a_n-2a_{n-1}+a_{n-2}$

So $a_n-2\Delta a_n+\Delta^2a_n=a_n-2(a_n-a_{n-1})+(a_n-2a_{n-1}+a_{n-2})=a_{n-2}$

## Section 8.2

> 2. Determine which of these are linear homogeneous recurrence
relations with constant coefficients. Also, find the
degree of those that are.
>
> a) $a_n=3a_{n-2}$
>
> b) $a_n=3$
>
> c) $a_n=a_{n-1}^2$
>
> d) $a_n=a_{n-1}+2a_{n-3}$
>
> e) $a_n=a_{n-1}/n$
>
> f) $a_n=a_{n-1}+a_{n-2}+n+3$
>
> g) $a_n=4a_{n-2}+5a_{n-4}+9a_{n-7}$

a) 2

b) not

c) not

d) 3

e) not

f) not

g) 7

> 4. Solve these recurrence relations together with the initial
conditions given.
>
> g) $a_{n+2}=-4a_{n+1}+5a_n$ for $n\ge0,a_0=2,a_1=8$

g)

$r^2=-4r+5$, so $r_1=-5,r_2=1$

So $a_n=c_1(-5)^n+c_21^n$

$$
\begin{cases}
c_1+c_2=2\\
-5c_1+c_2=8
\end{cases}
$$

So $c_1=-1,c_2=3$, $a_n=3-(-5)^n$

> 20. Find the general form of the solutions of the recurrence
relation $a_n = 8a_{n−2} − 16a_{n−4}$.

$r^4=8r^2-16$, so $r_1=r_2=2,r_3=r_4=-2$

$a_n=(c_1n+c_2)2^n+(c_3n+c_4)(-2)^n$

> 30. a) Find all solutions of the recurrence relation $a_n=-5a_{n-1}-6a_{n-2}+42\cdot4^n$
>
> b) Find the solution of this recurrence relation with $a_1 =
56$ and $a_2 = 278$.

a)

Solve $a_n=-5a_{n-1}-6a_{n-2}$, we get $a^{(h)}_n=c_1(-2)^n+c_2(-3)^n$

We guess a particular solution $a^{(p)}_n=C4^n$

So $C4^n=-5C4^{n-1}-6C4^{n-2}+42\cdot4^n$, so $C=16$, $a^{(p)}_n=4^{n+2}$

So $a_n=a_n^{(h)}+a_n^{(p)}=c_1(-2)^n+c_2(-3)^n+4^{n+2}$

> 35. Find the solution of the recurrence relation $a_n=4a_{n-1}-3a_{n-2}+2^n+n+3$ with $a_0 = 1$ and $a_1 = 4$.

Solve $a_n=4a_{n-1}-3a_{n-2}$, we get $a_n^{(h)}=c_1+c_23^n$

We guess $a_n^{(p)}=b2^n+cn^2+dn+e$

So $b2^n+cn^2+dn+e=4(b2^{n-1}+c(n-1)^2+d(n-1)+e)-3(b2^{n-2}+c(n-2)^2+d(n-2)+e)+2^n+n+3$

So $b=-4,c=-\dfrac14,d=-1$

So $a_n=a_n^{(h)}+a_n^{(p)}=c_1+c_23^n-2^{n+2}-\dfrac14n-1$

Let $a_0=1,a_1=4$, we get $a_n=\dfrac{29}8\cdot3^n-2^{n+2}-\dfrac14n+\dfrac{11}8$

## Section 8.3

> 22. Suppose that the function $f$ satisfies the recurrence relation
$f(n)=2f(\sqrt n)+\log n$ whenever $n$ is a perfect square
greater than $1$ and $f (2) = 1$.
>
> a) Find $f (16)$.
> 
> b) Find a big-O estimate for $f (n)$. [Hint: Make the substitution
$m = log n$.]

a)

$f(16)=2f(4)+4=2(2f(2)+2)+4=12$

b)

Suppose $m=\log n$.

$f(2^m)=2f(2^{m/2})+m=2(2f(2^{m/4})+\dfrac m2)+m=4f(2^{m/4})+m+m=\dots=O(m\log m)$

## Section 8.4

> 6. Find a closed form for the generating function for the sequence
$\{a_n\}$, where
>
> d) $a_n=1/(n+1)!$ for $n=0,1,2,\dots$
>
> f) $a_n=\binom{10}{n+1}$ for $n=0,1,2,\dots$

d)

$e^x=\sum\limits_{n=0}^{\infty}\dfrac1{n!}x^n$

$\dfrac{e^x-1}x=\sum\limits_{n=0}^{\infty}\dfrac1{(n+1)!}x^n$

f)

$(x+1)^{10}=\sum\limits_{n=0}^\infty\binom{10}{n}x^n$

$\dfrac{(x+1)^{10}-1}{x}=\sum\limits_{n=0}^\infty\binom{10}{n+1}x^n$

> 10. Find the coefficient of $x^9$ in the power series of each of
these functions.
>
> c) $(x^3+x^5+x^6)(x^3+x^4)(x+x^2+x^3+x^4+\dots)$
>
> d) $(x+x^4+x^7+x^{10}+\dots)(x^2+x^4+x^6+x^8+\dots)$
>
> e) $(1+x+x^2)^3$

c)

$=x^7(1+x^2+x^3)(1+x)(1+x+x^2+\dots)$

We can choose $(1,1,x^2),(1,x,x),(x^2,1,1)$, so the answer is $3$

d)

$=x^3(1+x^3+x^6+x^9+\dots)(1+x^2+x^4+x^6+\dots)$

We can choose $(1,x^6),(x^6,1)$, so the answer is $2$

e)

The term with maximal degree is $x^6$, so the answer is $0$.

> 16. Use generating functions to find the number of ways to
choose a dozen bagels from three varieties—egg, salty,
and plain—if at least two bagels of each kind but no more
than three salty bagels are chosen.

$F(x)=(x^2+x^3+\dots)(x^2+x^3)(x^2+x^3+\dots)$

The answer is the coefficient of $x^{12}$

$F(x)=x^6\dfrac{1+x}{(1-x)^2}=(x^6+x^7)\sum\limits_{n=0}^\infty(n+1)x^n$

So the coefficient of $x^{12}$ is $7+6=13$

> 24. a) What is the generating function for $\{a_k\}$, where $a_k$
is the number of solutions of $x_1 + x_2 + x_3 + x_4 = k$
when $x_1, x_2, x_3$, and $x_4$ are integers with $x_1 ≥ 3, 1 ≤x_2 ≤ 5, 0 ≤ x_3 ≤ 4$, and $x_4 ≥ 1$?

a)

$F(x)=(x^3+x^4+\dots)(x+x^2+\dots+x^5)(1+x+\dots+x^4)(x+x^2+\dots)=\dfrac{x^5(1-x^5)^2}{(1-x)^4}$

> 32. If $G(x)$ is the generating function for the sequence $\{a_k\}$,
what is the generating function for each of these sequences?
> 
> a) $2a_0, 2a_1, 2a_2, 2a_3, …$
> 
> b) $0, a_0, a_1, a_2, a_3, …$ (assuming that terms follow the
pattern of all but the first term)
> 
> c) $0, 0, 0, 0, a_2, a_3, …$ (assuming that terms follow the
pattern of all but the first four terms)
> 
> d) $a_2, a_3, a_4,…$
>
> e) $a_1, 2a_2, 3a_3, 4a_4,…$ [Hint: Calculus required here.]
>
> f) $a_0^2,2a_0a_1,a_1^2+2a_0a_2,2a_0a_3+2a_1a_2,2a_0a_4+2a_1a_3+a_2^2,\dots$

a)

$2G(x)$

b)

$xG(x)$

c)

$x^2(G(x)-a_0-a_1x)$

d)

$\dfrac{G(x)-a_0-a_1x}{x^2}$

e)

$G'(x)$

f)

$G^2(x)$

> 36. Use generating functions to solve the recurrence relation
$a_k = 3a_{k−1} + 4^{k−1}$ with the initial condition $a_0 = 1$.

Suppose the GF of $a_n$ is $F(x)$

Then we know $F(x)-1-3xF(x)=\sum\limits_{k=1}^\infty 4^kx^k=\dfrac x{1-4x}$

So $F(x)=\dfrac1{1-4x}$, so $a_k=4^k$

> 45. Use generating functions to prove Vandermonde’s identity:
$C(m + n, r) = \sum_{k=0}^r C(m, r − k)C(n, k)$, whenever
$m, n$, and $r$ are nonnegative integers with $r$ not exceeding
either $m$ or $n$. [Hint: Look at the coefficient of $x^r$ in
both sides of $(1 + x)^{m+n} = (1 + x)^m(1 + x)^n$.]

$[x^r](1+x)^{m+n}=\binom{m+n}{r}$

$[x^r](1+x)^m(1+x)^n=\sum\limits_{k=0}^r[x^k](1+x)^n[x^{r-k}](1+x)^m=\sum\limits_{k=0}^r\binom{n}{k}\binom{m}{r-k}$