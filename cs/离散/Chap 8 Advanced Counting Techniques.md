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