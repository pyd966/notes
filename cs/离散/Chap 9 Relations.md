# Chap 9 Relations

## Section 9.1

> 7. Determine whether the relation $R$ on the set of all integers
is reflexive, symmetric, antisymmetric, and/or transitive,
where $(x, y) ∈ R$ if and only if
>
> a) $x\neq y$
>
> c) $x=y+1$ or $x=y-1$
>
> h) $x\ge y^2$

a)

symmetric

c)

symmetric

h)

antisymmetric, transitive.

> 26. Let $R$ be the relation $R = \{(a, b) ∣ a < b\}$ on the set of
integers. Find
>
> a) $R^{−1}$. b) $\overline R$.

a)

$R^{-1}=\{(a,b)\mid a>b\}$

$\overline R=\{(a,b)\mid a\ge b\}$

> 32. Let $R$ be the relation $\{(1, 2), (1, 3), (2, 3), (2, 4), (3, 1)\}$,
and let $S$ be the relation $\{(2, 1), (3, 1), (3, 2), (4, 2)\}$. 
>
> Find $S ◦ R$.

$S\circ R=\{(1,1),(1,2),(2,1),(2,2)\}$

> 49. How many relations are there on a set with n elements
that are
> 
> a) symmetric? b) antisymmetric?
>
> c) asymmetric? d) irreflexive?
>
> e) reflexive and symmetric?
>
> f) neither reflexive nor irreflexive?

a) $2^{(n+1)n/2}$

b) $2^n\cdot 3^{n(n-1)/2}$

c) $3^{n(n-1)/2}$

d) $2^{n(n-1)}$

e) $2^{(n-1)n/2}$

f) $2^{n(n-1)}(2^n-2)$

> 53. Show that the relation $R$ on a set $A$ is symmetric if and
only if $R = R^{−1}$, where $R^{−1}$ is the inverse relation.

If $R$ is symmetric, then $\forall (a,b)\in R$ we know $(b,a)\in R$, so $(a,b),(b,a)\in R^{-1}$.

So $R\subseteq R^{-1}$, similarly $R^{-1}\subseteq R$, so $R=R^{-1}$.

If $R=R^{-1}$, then $\forall (a,b)\in R$, $(b,a)\in R^{-1}$.

Because $R=R^{-1}$, so $(b,a)\in R$, so $R$ is symmetric.

## Section 9.3

> 13. Let R be the relation represented by the matrix
>
> $$
M_R=
\begin{pmatrix}
0 & 1 & 1\\
1 & 1 & 0\\
1 & 0 & 1\\
\end{pmatrix}
> $$
> 
> Find the matrix representing
> 
> a) $R^{−1}$. b) $\overline R$. c) $R^2$.

a)

$R^{-1}=\begin{pmatrix}0 & 1 & 1\\ 1 & 1 & 0\\ 1 & 0 & 1\\\end{pmatrix}$

b)

$\overline R=\begin{pmatrix}1 & 0 & 0\\ 0 & 0 & 1\\ 0 & 1 & 0\\\end{pmatrix}$

c)

$R^2=\begin{pmatrix}1 & 1 & 1\\ 1 & 1 & 1\\ 1 & 1 & 1\\\end{pmatrix}$

> 14. Let R1 and R2 be relations on a set A represented by the
matrices
>
> $$
M_{R_1}=\begin{pmatrix}
0 & 1 & 0\\
1 & 1 & 1\\
1 & 0 & 0\\
\end{pmatrix}
> $$
>
> $$
M_{R_2}=\begin{pmatrix}
0 & 1 & 0\\
0 & 1 & 1\\
1 & 1 & 1\\
\end{pmatrix}
> $$
>
> Find the matrices that represent
>
> a) $R_1 ∪ R_2$. b) $R_1 ∩ R_2$. c) $R_2 ◦ R_1$.
> 
> d) $R_1 ◦ R_1$. e) $R_1 ⊕ R_2$.

a)

$R_1\cup R_2=\begin{pmatrix}0 & 1 & 0\\ 1 & 1 & 1\\ 1 & 1 & 1\\\end{pmatrix}$

b)

$R_1\cap R_2=\begin{pmatrix}0 & 1 & 0\\ 0 & 1 & 1\\ 1 & 0 & 0\\\end{pmatrix}$

c)

$R_2\circ R_1=\begin{pmatrix}0 & 1 & 1\\ 1 & 1 & 1\\ 0 & 1 & 0\\\end{pmatrix}$

d)

$R_1\circ R_1=\begin{pmatrix}1 & 1 & 1\\ 1 & 1 & 1\\ 0 & 1 & 0\end{pmatrix}$

e)

$R_1\oplus R_2=\begin{pmatrix}0 & 0 & 0\\ 1 & 0 & 0\\ 0 & 1 & 1\\\end{pmatrix}$

> 31. Determine whether the relations represented by the directed
graphs shown in Exercises 23–25 are reflexive, irreflexive,
symmetric, antisymmetric, and/or transitive.

23 irreflexive, transitive.

24 reflexive, antisymmetric, transitive.

25 irreflexive, antisymmetrix, transitive.

## Section 9.4

> 2. Let R be the relation $\{(a, b) ∣ a ≠ b\}$ on the set of integers.
What is the reflexive closure of $R$?

$R\cup\Delta=\{(a,b)\mid a,b\in Z\}$

> 6.

Ignored

> 9. Find the directed graphs of the symmetric closures of the
relations with directed graphs shown in Exercises 5–7.
>
> $(6)$

$(6)$

Ignored.

> 11. Find the directed graph of the smallest relation that is
both reflexive and symmetric that contains each of the
relations with directed graphs shown in Exercises 5–7.
>
> $(6)$

$(6)$

Ignored.

> 20. Let $R$ be the relation that contains the pair $(a, b)$ if $a$ and $b$
are cities such that there is a direct nonstop airline flight
from $a$ to $b$. When is $(a, b)$ in
>
> a) $R^2$? b) $R^3$? c) $R^∗$?

a)

$R^2$ contains the pair $(a,b)$ iff there exists an indirect line from $a$ to $b$ consisting of 2 direct airline flights.

b)

$R^3$ contains the pair $(a,b)$ iff there exists an indirect line from $a$ to $b$ consisting of 3 direct airline flights.

c)

$R^*$ contains the pair $(a,b)$ iff there exists a line (direct or indirect) from $a$ to $b$.

> 28. Use Warshall’s algorithm to find the transitive closures
of the relations in Exercise 26.
>
> (a) $\{(a, c), (b, d), (c, a), (d, b), (e, d)\}$

(a)

$\{(a,a),(a,c),(b,b),(b,d),(c,a),(c,c)(d,b),(d,d),(e,b),(e,d)\}$

> 29. Find the smallest relation containing the relation
$\{(1, 2), (1, 4), (3, 3), (4, 1)\}$ that is
>
> a) reflexive and transitive.
>
> b) symmetric and transitive.
>
> c) reflexive, symmetric, and transitive.

a)

$\{(1,1),(1,2),(1,4),(2,2),(3,3),(4,1),(4,2),(4,4)\}$

b)

$\{(1,1)(1,2),(1,4),(2,1),(2,2)(2,4),(3,3),(4,1),(4,2),(4,4)\}$

c)

$\{(1,1),(1,2),(1,4),(2,1),(2,2),(3,3),(4,1),(4,2),(4,4)\}$

## Section 9.5

> 3. Which of these relations on the set of all functions from $Z$
to $Z$ are equivalence relations? Determine the properties
of an equivalence relation that the others lack.
>
> a) $\{(f, g) ∣ f (1) = g(1)\}$
>
> b) $\{(f, g) ∣ f (0) = g(0) or f (1) = g(1)\}$
>
> c) $\{(f, g) ∣ f (x) − g(x) = 1 \forall x ∈ Z\}$
> 
> d) $\{(f, g) \mid $ for some $C ∈ Z$, for all $x ∈ Z, f (x) − g(x) = C\}$
> 
> e) $\{(f, g) ∣ f (0) = g(1)$ and $f (1) = g(0)\}$

a), d) are equivalence relations.

b) is not transitive.

c) is not reflexive, symmetric and transitive.

e) is not reflexive and transitive.

> 10. Suppose that $A$ is a nonempty set and $R$ is an equivalence
relation on $A$. Show that there is a function $f$ with $A$ as its
domain such that $(x, y) ∈ R$ if and only if $f (x) = f (y)$.

Let $f(x)=[x]_R$, it's easy to verify it.

> 16. Let $R$ be the relation on the set of ordered pairs of positive
integers such that $((a, b), (c, d)) ∈ R$ if and only if
$ad = bc$. Show that $R$ is an equivalence relation.

relexive: $ab=ab$, so $((a,b),(a,b))\in R$

symmetric: if $((a,b),(c,d))\in R$, then $ad=bc$, then $((c,d),(a,b))\in R$.

transitive: if $((a,b),(c,d)),((c,d),(e,f))\in R$, then $ad=bc,cf=de$, so $acdf=bcde$, so $af=be$, so $((a,b),(e,f))\in R$.

> 36. What is the congruence class $[4]_m$ when $m$ is
>
> b) $3$?

b)

$x\in[4]_m\iff x\equiv 4(\bmod m)\iff x=4+3k(k\in Z)$

> 39. a) What is the equivalence class of $(1, 2)$ with respect to
the equivalence relation in Exercise 15?
>
> b) Give an interpretation of the equivalence classes for
the equivalence relation $R$ in Exercise 15. [Hint: Look
at the difference $a − b$ corresponding to $(a, b)$.]

a)

$(1,2)R(a,b)\iff 1+b=2+a\iff a-b=-1$.

So the equivalence class is $\{(a,b)\mid a-b=-1\}$

b)

$(x,y)\in [(a,b)]\iff x+b=y+a\iff x-y=a-b$.

So equivalence classes look like $S(k)=\{(x,y)\mid x-y=k\}$, they can be interpreted by a single integer.

> 41. Which of these collections of subsets are partitions of
$\{1, 2, 3, 4, 5, 6\}$?
> 
> a) $\{1, 2\}, \{2, 3, 4\}, \{4, 5, 6\}$
> 
> b) $\{1\}, \{2, 3, 6\}, \{4\}, \{5\}$
> 
> c) $\{2, 4, 6\}, \{1, 3, 5\}$ 
> 
> d) $\{1, 4, 5\}, \{2, 6\}$

b), c)

## Section 9.6

> 5. Which of these are posets?
> 
> a) $(Z,=)$ b) $(Z,≠)$ c) $(Z,≥)$ d) $(Z, \nmid)$

a), c)

> 10.

Ignored.

> 23. Draw the Hasse diagram for divisibility on the set
>
> a) $\{1, 2, 3, 4, 5, 6, 7, 8\}$. 
> 
> c) $\{1, 2, 3, 6, 12, 24, 36, 48\}$.

Ignored.

> 32. Answer these questions for the partial order represented
by this Hasse diagram.
>
> a) Find the maximal elements.
>
> b) Find the minimal elements.
>
> c) Is there a greatest element?
>
> d) Is there a least element?
>
> e) Find all upper bounds of $\{a, b, c\}$.
>
> f) Find the least upper bound of $\{a, b, c\}$, if it exists.
>
> g) Find all lower bounds of $\{f, g, h\}$.
>
> h) Find the greatest lower bound of $\{f, g, h\}$, if it exists.

a)

l, m.

b)

a, b, c.

c)

no.

d)

no.

e)

$\{k,l,m\}$.

f)

k.

g)

$\varnothing$

h)

Dont exist.
