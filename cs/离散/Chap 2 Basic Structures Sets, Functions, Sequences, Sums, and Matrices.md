# Chap 2 Basic Structures: Sets, Functions, Sequences, Sums, and Matrices

## Section 2.1

> 13. Determine whether each of these statements is true or
false.
>
>$a) x ∈ \{x\}$ 
>
>$b) \{x\} ⊆ \{x\}$ 
>
>$c) \{x\} ∈ \{x\}$
>
>$d) \{x\} ∈ \{\{x\}\}$
>
> $e) \varnothing ⊆ \{x\}$ 
>
> $f) \varnothing ∈ \{x\}$

$(a)$ true

$(b)$ true

$(c)$ false

$(d)$ true

$(e)$ true

$(f)$ false

> 20. Find two sets $A$ and $B$ such that $A ∈ B$ and $A ⊆ B$.

$A=\{1\},B=\{1,\{1\}\}$

> 24. Can you conclude that $A = B$ if $A$ and $B$ are two sets with
the same power set?

Yes.

In every power set $P$, there exists one set $S\in P$ that satisfies $\forall T\in P,T\subseteq S$. Let's call $S$ the representative of $S$. In fact, $S$ is the original set used to generate $P$.

Because $P(A)=P(B)$, so their representatives must be the same, which gives $A=B$.

> 26. Determine whether each of these sets is the power set of
a set, where $a$ and $b$ are distinct elements.
>
>$a) \varnothing$ 
>
> $b) \{\varnothing, \{a\}\}$
>
> $c) \{\varnothing, \{a\}, \{\varnothing, a\}\}$ 
>
>$d) \{\varnothing, \{a\}, \{b\}, \{a, b\}\}$

a) False.

b) Yes, $P(\{a\})$

c) False

d) Yes, $P(\{a,b\})$

> 34. Let $A = \{a, b, c\}, B = \{x, y\}$, and $C = \{0, 1\}$. Find
> 
> $a) A × B × C$.
> 
> $c) C × A × B$.

a) 

$\{(a,x,0),(a,x,1),(a,y,0),(a,y,1),(b,x,0),(b,x,1),(b,y,0),(b,y,1),(c,x,0),(c,x,1),(c,y,0),(c,y,1)\}$

b)

$\{(0,a,x),(0,a,y),(0,b,x),(0,b,y),(0,c,x),(0,c,y),(1,a,x),(1,a,y),(1,b,x),(1,b,y),(1,c,x),(1,c,y)\}$

## Section 2.2

> 19. Show that if $A, B$, and $C$ are sets, then $\overline{A ∩ B ∩ C} = \bar A ∪
\bar B ∪ \bar C$
>
> a) by showing each side is a subset of the other side.
> 
> b) using a membership table.

a)

$$
\begin{aligned}
\overline{A\cap B\cap C}&=\{x\mid x\in\overline{A\cap B\cap C}\}\\
&=\{x\mid \lnot(x\in A\cap B\cap C)\}\\
&=\{x\mid \lnot(x\in A\land x\in B\land x\in C)\}\\
&=\{x\mid x\not\in A\lor x\not\in B\lor x\not\in C\}\\
&=\{x\mid x\in\bar A\lor x\in\bar B\lor x\in\bar C\}\\
&=\{x\mid x\in\bar A\cup\bar B\cup\bar C\}\\
&=\bar A\cup\bar B\cup\bar C
\end{aligned}
$$

b)

|$A$|$B$|$C$|$A\cap B\cap C$|$\overline{A\cap B\cap C}$|$\bar A\cup\bar B\cup\bar C$|
|--|--|--|--|--|--|
|0|0|0|0|1|1|
|0|0|1|0|1|1|
|0|1|0|0|1|1|
|0|1|1|0|1|1|
|1|0|0|0|1|1|
|1|0|1|0|1|1|
|1|1|0|0|1|1|
|1|1|1|1|0|0|

> 54. Let $A_i = \{…,−2,−1, 0, 1,…, i\}$. Find
>
> a) $\bigcup\limits_{i=1}^nA_i$
>
> b) $\bigcap\limits_{i=1}^nA_i$

a)

$\bigcup\limits_{i=1}^nA_i=\{\dots,-2,-1,\dots,n\}$

b)

$\bigcap\limits_{i=1}^n A_i=\{\dots,-2,-1,0,1\}$

> 63. Show how bitwise operations on bit strings can be
used to find these combinations of $A = \{a, b, c, d, e\},
B = \{b, c, d, g, p, t, v\}, C = \{c, e, i, o, u, x, y, z\}$, and
$D = \{d, e, h, i, n, o, t, u, x, y\}$.
>
> $c) (A ∪ D) ∩ (B ∪ C)$

c)

Let $A'=$ `11111000000000000000000000`

$B'=$ `01110010000000010001010000`

$C'=$ `00101000100000100000100111`

$D'=$ `00011001100001100001100110`

So $(A\cup D)\cap(B\cup C)=(A'\mid D')\&(B'\mid C')=$ `01111000100000100001100110` $=\{b,c,d,e,i,o,t,u,x,y\}$

## Section 2.3

> 22. Determine whether each of these functions is a bijection
from $R$ to $R$.
>
> $c) f (x) = \dfrac{(x + 1)}{(x + 2)}$

c)

No. Equation $1=f(x)$ yields no solution. So it cannot be a surjection.

> 36. If $f$ and $f ◦g$ are one-to-one, does it follow that $g$ is one-to-one? Justify your answer.

Yes.

Suppose $g$ is not one-to-one, then $\exist x\neq y,g(x)=g(y)$.

So $(f\circ g)(x)=f(g(x))=f(g(y))=(f\circ g)(y)$, which means $f\circ g$ is not one-to-one. That contradicts with our premise.

So $g$ is one-to-one.

> 42. Let $f$ be a function from the set $A$ to the set $B$. Let $S$ and
$T$ be subsets of $A$. Show that
>
> $a) f (S ∪ T) = f (S) ∪ f (T).$

a)

If $y\in f(S\cup T)$, there exists $x\in S\cup T$ such that $y=f(x)$.

So $x\in S\lor x\in T$.

If $x\in S$, then $y=f(x)\in f(S)$.

If $x\in T$, then $y=f(x)\in f(T)$.

So $y\in f(S)\cup f(T)$, which yields $f(S\cup T)\subseteq f(S)\cup f(T)$

If $y\in f(S)\cup f(T)$, that means $y\in f(S)\lor y\in f(T)$.

If $y\in f(S)$, then $y\in f(S\cup T)$.

If $y\in f(T)$, then $y\in f(S\cup T)$

So $y\in f(S\cup T)$, which yields $f(S)\cup f(T)\subseteq f(S\cup T)$

Together, they give $f(S\cup T)=f(S)\cup f(T)$

> 74. Suppose that $f$ is a function from $A$ to $B$, where $A$ and $B$
are finite sets with $|A| = |B|$. Show that $f$ is one-to-one if
and only if it is onto.

If it's one-to-one, let's suppose it's not onto.

Then the cardinality of the range of $f$ must be less than $|B|=|A|$, which means at least two preimages are mapped to the same image.

So it's onto.

If it's onto, let's suppose it's not one-to-one;

Then the cardinality of the range of $f$ must be less than $|A|=|B|$, which means at least one element in $B$ has no preimage.

So it's one-to-one.

Together, they yield expected result.

> 76. Prove or disprove each of these statements about the floor
and ceiling functions.
>
> c) $⌈ ⌈x∕2⌉ ∕2⌉ = ⌈x∕4⌉$ for all real numbers $x$.
>
> d) $\lfloor\sqrt{\lceil x\rceil}\rfloor=\lfloor\sqrt x\rfloor$ for all positive real numbers $x$.

c)

True.

Suppose $x=4k+\epsilon$, where $0\le\epsilon<4$.

So $\lceil\lceil\dfrac x2\rceil/2\rceil=\lceil\lceil2k+\dfrac\epsilon2\rceil/2\rceil=\lceil(2k+\lceil\dfrac\epsilon2\rceil)/2\rceil=k+\lceil\dfrac{\lceil\frac\epsilon2\rceil}{2}\rceil$

While $\lceil\dfrac x4\rceil=k+\lceil\dfrac\epsilon4\rceil$

So we only need to prove $\lceil\dfrac{\lceil\frac\epsilon2\rceil}2\rceil=\lceil\dfrac\epsilon4\rceil$

When $\epsilon=0$, both give $0$.

When $0<\epsilon\le 2$, both give $1$.

When $2<\epsilon\le 4$, both give $1$.

So the equation is indeed true.

d)

False.

Assign $x=3.5$, the left gives $2$ while the right gives $1$.