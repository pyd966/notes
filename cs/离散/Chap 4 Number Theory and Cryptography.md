# Chap 4 Number Theory and Cryptography

## Section 4.1

> 47. Show that if $a, b, k$, and $m$ are integers such that $k ≥ 1,m ≥ 2$, and $a ≡ b (\bmod m)$, then $ak ≡ bk(\bmod m)$.

$a\equiv b(\bmod m)$ indicates $m\mid(a-b)$, so $m\mid k(a-b)$, which means $ka\equiv kb(\bmod m)$

## Section 4.2

> 25. Use Algorithm 5 to find $7^{644} \bmod 645$.

$644=512+128+4=2^9+2^7+2^2$

$7^1\equiv7(\bmod 645)$

$7^2\equiv49(\bmod 645)$

$7^4\equiv466(\bmod 645)$

$7^8\equiv436(\bmod 645)$

$7^{16}\equiv466(\bmod 645)$

So $7^{128}\equiv436(\bmod 645), 7^{512}\equiv 436(\bmod 645)$

So $7^{644}\equiv 7^{512}\times7^{128}\times7^{4}\equiv436(\bmod 645)$

> 31. Show that a positive integer is divisible by 3 if and only
if the sum of its decimal digits is divisible by 3.

Suppose $x=\sum\limits_{n=0}^ma_n10^n$

Then

$$
\begin{aligned}
x&\equiv\sum_{n=0}^ma_n10^n\\
&\equiv\sum_{n=0}^ma_n+\sum_{n=1}^ma_n(10^n-1)\ (\bmod3)
\end{aligned}
$$

while $10^n-1\equiv1^n-1\equiv0(\bmod 3)$

So $x\equiv\sum\limits_{n=0}^ma_n(\bmod 3)$

## Section 4.3

> 13. Prove or disprove that there are three consecutive odd
positive integers that are primes, that is, odd primes of
the form $p, p + 2$, and $p + 4$.

Yes. For example $3,5,7$.

> 23. What is the value of $𝜙(p^k)$ when $p$ is prime and $k$ is a
positive integer?

For integers in $[1,p^k]$, only those that are multiple of $p$ are not relatively prime to $p^k$. And these numbers take account of $\dfrac1p$

So $\phi(p^k)=p^k(1-\dfrac1p)=p^k-p^{k-1}$.

## Section 4.4

> 9. Solve the congruence $4x ≡ 5 (\bmod 9)$ using the inverse
of $4$ modulo $9$ found in part (a) of Exercise 5.

$4^{-1}\equiv7(\bmod 9)$

So $4x\equiv 5(\bmod9)\Rightarrow x\equiv5\times4^{-1}\equiv8(\bmod 9)$

> 21. Use the construction in the proof of the Chinese remainder
theorem to find all solutions to the system of congruences
$x ≡ 1 (\bmod 2), x ≡ 2 (\bmod 3), x ≡ 3 (\bmod 5)$, and
$x ≡ 4 (\bmod 11)$.

$M=2\times3\times5\times11=330$

$m_1=3\times5\times11=165,m_2=2\times5\times11=110,m_3=2\times3\times11=66,m_4=2\times3\times5=30$

$y_1\equiv m_1^{-1}\equiv1(\bmod 2),y_2\equiv m_2^{-1}\equiv2(\bmod 3),y_3\equiv m_3^{-1}\equiv1(\bmod 5),y_4\equiv m_4^{-1}\equiv 7(\bmod 11)$

$x\equiv x_1m_1y_1+x_2m_2y_2+x_3m_3y_3+x_4m_4y_4\equiv323(\bmod 330)$

So $x=323+330k,k\in Z$