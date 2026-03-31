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