## Section 3.1

> 2. Determine which characteristics of an algorithm described
in the text (after Algorithm 1) the following procedures
have and which they lack.
>
>a) procedure double(n: positive integer)
>
>while n > 0
>
>n := 2n
>
>b) procedure divide(n: positive integer)
>
>while n ≥ 0
>
>m := 1∕n
>
>n := n − 1
>
>c) procedure sum(n: positive integer)
>
>sum := 0
>
>while i < 10
>
>sum := sum + i
>
>d) procedure choose(a, b: integers)
>
>x := either a or b

(a)

Finiteness. The program will never stop for $n=1$.

(b)

Definiteness. When $n=0$, m:=1/n has no meaning.

(c)

Finiteness. The variable $i$ does not change in the loop, so it's an infinite loop.

(d)

Definiteness. The assigning statement is ambiguous.

> 4. Describe an algorithm that takes as input a list of n integers
and produces as output the largest difference obtained
by subtracting an integer in the list from the one
following it.

```
procedure solve(a_1,a_2,\dots,a_n: integers)
max:=a_1-a_2
for i:=2 to n-1
    if max < a_i-a_{i+1} then max:= a_i-a_{i+1}
return max
```

## Section 3.2

> 8. Find the least integer $n$ such that $f (x)$ is $O(x^n)$ for each of
these functions.
>
> $(c)$ $f (x) = (x^4 + x^2 + 1)∕(x^4 + 1)$

$(c)$

$n=0$

$f(x)=\dfrac{x^4+x^2+1}{x^4+1}=1+\dfrac{1}{x^2+x^{-2}}\le 1+\dfrac{1}{x^2}\le2\times x^0$, so $f(x)=O(x^0)$.

If $n<0$, for any $C$, we choose $k=\sqrt[-n]{C}$, then if $x>k$, we can get $f(x)\ge 1\ge C\cdot k^{n}\ge C\cdot x^{n}$.

So that's not possible.

So the least $n=0$.

> 26. Give a big-O estimate for each of these functions. For the
function $g$ in your estimate $f (x)$ is $O(g(x))$, use a simple
function $g$ of smallest order.
>
>a) $(n^3+n^2 \log n)(\log n+1) + (17 \log n+19)(n^3+2)$

(a)

Choose $k=1$, when $n>k$

$$
\begin{aligned}
f(n)&=18n^3\log n+20n^3+n^2\log^2n+n^2\log n+34\log n+38\\
&\le 111n^3\log n+n^2\log^2n\\
&\le 112n^3\log n
\end{aligned}
$$

So $f(n)=O(n^3\log n)$

> 54. Show that $x^5y^3 + x^4y^4 + x^3y^5$ is $Ω(x^3y^3)$.

When $x,y\ge 1$

$$
\begin{aligned}
f(x,y)&=x^5y^3+x^4y^4+x^3y^5\\
&\ge 3x^3y^3
\end{aligned}
$$

So $f(x,y)=\Omega(x^3y^3)$

> 56. Show that $⌈xy⌉$ is $Ω(xy)$.

When $x,y\ge 0$, $f(x,y)\ge xy$, so $f(x,y)=\Omega(xy)$

## Section 3.3

> 7. Suppose that an element is known to be among the first
four elements in a list of $32$ elements. Would a linear
search or a binary search locate this element more
rapidly?

Yes.

The actual time used is $O(k)$, where $k$ indicates the target's position.

So if the element is in the first four, a linear search will run more rapidly.

> 10. a) Show that this algorithm determines the number of $1$
bits in the bit string $S$:
>
>procedure bit count(S: bit string)
>
>count := 0
>
>while S ≠ 0
>
>count := count + 1
>
>S := S ∧ (S − 1)
>
>return count {count is the number of 1s in S}
>
>Here $S − 1$ is the bit string obtained by changing the
rightmost $1$ bit of $S$ to a $0$ and all the $0$ bits to the
right of this to 1s. [Recall that $S ∧ (S − 1)$ is the bitwise
AND of $S$ and $S − 1$.]
>
>b) How many bitwise AND operations are needed to find
the number of $1$ bits in a string $S$ using the algorithm
in part (a)?

(a)

We analyze $S\leftarrow S\land(S-1)$.

$S-1$ is the bit string that are the same as $S$ except changing the rightmost $1$ to $0$ and the bits to the right of this to $1$.

So $S\land(S-1)$ is the bit string that are the sam as $S$ except changing the rightmost $1$ to $0$.

So the statement $count\leftarrow count+1$ will be run for exactly the number of $1$s in the $S$ times.

So $count$ will eventually becomes the number of $1$ bits in the bit string.

(b)

Suppose the number of $1$ in string $S$ is $k$, then exactly $T(k)=k$ is needed.