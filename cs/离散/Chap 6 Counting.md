# Chap 6 Counting

## Section 6.1

> 41. A palindrome is a string whose reversal is identical to
the string. How many bit strings of length $n$ are palindromes?

If $n$ is odd, there are $\dfrac{n+1}2$ free bits; If $n$ is even, there are $\dfrac n2$.

So there are $\lceil\dfrac n2\rceil$ free bits, thus the number of palindrome bit strings is $2^{\lceil n/2\rceil}$

> 58. The name of a variable in the C programming language is
a string that can contain uppercase letters, lowercase letters,
digits, or underscores. Further, the first character in
the string must be a letter, either uppercase or lowercase,
or an underscore. If the name of a variable is determined
by its first eight characters, how many different variables
can be named in C? (Note that the name of a variable may
contain fewer than eight characters.)

For the first character, there are $26+26+1=53$ ways. For the rest of them, there are $26+26+10+1=63$ ways.

For a variable of length $n$, there are $53\times63^{n-1}$ ways.

So the total number if $\sum\limits_{n=1}^853\times63^{n-1}=\dfrac{53}{62}\times(63^8-1)=212133166402880$

> 70. a) Suppose that a store sells six varieties of soft drinks:
cola, ginger ale, orange, root beer, lemonade, and
cream soda. Use a tree diagram to determine the number
of different types of bottles the store must stock to
have all varieties available in all size bottles if all varieties
are available in 12-ounce bottles, all but lemonade
are available in 20-ounce bottles, only cola and
ginger ale are available in 32-ounce bottles, and all
but lemonade and cream soda are available in 64-
ounce bottles?
> b) Answer the question in part (a) using counting rules.

a)

Ignored.

b)

$6+5+2+4=17$

## Section 6.2

> 12. Let $(x_i, y_i), i = 1, 2, 3, 4, 5$, be a set of five distinct points
with integer coordinates in the xy plane. Show that the
midpoint of the line joining at least one pair of these
points has integer coordinates.

For any $i,j$, the midpoint sits at $(\dfrac{x_i+x_j}2,\dfrac{y_i+y_j}2)$.

To make its coordinates integer, $2\mid x_i+x_j,2\mid y_i+y_j$.

Group them by $(x_i\% 2,y_i\% 2)$, there are only 4 possibilities, but there are 5 points.

So at least two of them are identical. Suppose $x_i\%2=x_j\%2,y_i\%2=y_j\%2$.

Thus $2\mid x_i+x_j,2\mid y_i+y_j$, so their midpoint satisfies the requirement.

> 40. Find the least number of cables required to connect eight
computers to four printers to guarantee that for every
choice of four of the eight computers, these four computers
can directly access four different printers. Justify
your answer.

$20$.

First prove $<20$ is impossible.

If one printer connects to less than $5$, then there are $4$ computers that don't connect to it, we can choose these $4$ computers, they cannot access $4$ different printers.

Then give a solution.

For example

$$
P_1\to\{C_1,C_2,C_3,C_4,C_5\}\\
P_2\to\{C_2,C_3,C_4,C_5,C_6\}\\
P_3\to\{C_3,C_4,C_5,C_6,C_7\}\\
P_4\to\{C_4,C_5,C_6,C_7,C_8\}\\
$$

Every choice of four computers will hit at least one computer in each printer group, so we can get full access.

> 42. Prove that at a party where there are at least two people,
there are two people who know the same number of other
people there.

Let $d_i$ be the number of other people that person $i$ knows. Obviously $0\le d_i\le n-1$.

But there cannot be $d_i=0$ and $d_j=n-1$ at the same time.

WLOG, let's suppose $1\le d_i\le n-1$.

There are $n$ people, but there're only $n-1$ possibilities of $d_i$.

So there exists $i,j$ such that $d_i=d_j$.

> 44. Is the statement in Exercise 43 true if 24 is replaced by
> 
> a) 2? b) 23? c) 25? d) 30?

If 24 is replaced by $d$, we can do the proof as follows.

Let $a_i$ be the number of games played on or before the $i$th hour. Then $0\le a_i\le 125$, and they're distinct increasing numbers.

So are $a_0+d,a_1+d,\dots,a_{75}+d$. $d\le a_i+d\le 125+d$.

Consider $a_0,\dots,a_{75},a_0+d,\dots,a_{75}+d$, there're 152 numbers and $126+d$ possibilities.

So when $126+d<152$, which means $d\le 25$, it's correct.

a,b,c is true.

But d is still true.

Suppose there is an arrangement that $a_0,\dots,a_{75},a_0+d,\dots,a_{75}+d$ are distinct.

Divide them in groups by their remainder divided by 30.

$\{0,30,60,90,120\},\{1,31,61,91,121\},\dots,\{5,35,65,95,125\},\{6,36,66,96\},\dots,\{29,59,89,119\}$

We can choose up to $\lfloor\dfrac L2\rfloor$ numbers in a size $L$ group.

So we can choose up to $2\times30=60$ numbers, which is less than $75$, so it's impossible.

## Section 6.3

> 20. How many bit strings of length 10 have
> 
> a) exactly three 0s?
> 
> b) more 0s than 1s?
> 
> c) at least seven 1s?
> 
> d) at least three 1s?

The number of a bit string of length 10 that has exactly $r$ 0s is $\dbinom{10}r$

a)

$\dbinom{10}3=120$

b)

$\sum\limits_{i=6}^{10}\dbinom{10}i=386$

c)

$\sum\limits_{i=0}^3\dbinom{10}i=176$

d)

$\sum\limits_{i=0}^7\dbinom{10}i=968$

> 44. Find a formula for the number of ways to seat $r$ of $n$ people
around a circular table, where seatings are considered
the same if every person has the same two neighbors
without regard to which side these neighbors are sitting
on.

For a circular permutation, we can transform it into a normal one by spliting it between 2 people.

So there're $r$ ways to split, plus we can reverse the order (when $r\ge3$), thus one circular permutation corresponds to $2r$ normal one.

By division rule, the formula is $\begin{cases}\dfrac{P(n,r)}{2r}&,r\ge3\\\dfrac{n(n-1)}{2}&,r=2\\ n&,r=1\\ 1&,r=0\end{cases}$.

> 46. How many ways are there for a horse race with four
horses to finish if ties are possible? [Note: Any number
of the four horses may tie.]

$(1,1,1,1): P(4,4)=24$

$(2,1,1): C(4,2)\times P(2,2)=12$

$(1,2,1): C(4,2)\times P(2,2)=12$

$(1,1,2): C(4,2)\times P(2,2)=12$

$(2,2): C(4,2)\times C(2,2)=6$

$(1,3): C(4,3)=4$

$(3,1): C(4,3)=4$

$(4): 1$

Altogether, there're $75$ ways.

## Section 6.4

> 18. Show that if n is a positive integer, then $1=\binom n0<\binom n1<\dots<\binom n{\lfloor n/2\rfloor}=\binom n{\lceil n/2\rceil}>\dots>\binom n{n-1}>\binom nn=1$

Obviously $1=\binom n0=\binom nn$.

$\lfloor\dfrac n2\rfloor+\lceil\dfrac n2\rceil=n$, so $\binom n{\lceil n/2\rceil}=\binom n{\lfloor n/2\rfloor}$

$\dfrac{\binom n{i+1}}{\binom ni}=\dfrac{n-i}{i+1}$

When $1\le i<\lfloor\dfrac n2\rfloor$, $\dfrac{n-i}{i+1}>1$, so $\binom ni<\binom{n}{i+1}$

When $\lceil\dfrac n2\rceil\le i<n$, $\dfrac{n-i}{i+1}<1$, so $\binom ni>\binom n{i+1}$

> 26. Prove the identity $\binom nr\binom rk=\binom nk\binom{n-k}{r-k}$
, whenever $n, r$, and
$k$ are nonnegative integers with $r ≤ n$ and $k ≤ r$,
>
> a) using a combinatorial argument.
> 
> b) using an argument based on the formula for the number
of r-combinations of a set with n elements.

a)

Our goal is to choose $r$ people from $n$ people, and then choose $k$ pivot member from $r$ people.

The left side counts the ways of doing so directly.

But we can also first choose $k$ pivot member from $n$ people, then choose the rest $r-k$ normal member from $n-k$ people, which is the right side.

b)

$$
\begin{aligned}
\binom nr\binom rk&=\dfrac{n!}{r!(n-r)!}\cdot\dfrac{r!}{k!(r-k)!}\\
&=\dfrac{n!}{(n-r)!k!(r-k)!}\\
&=\dfrac{n!}{k!(n-k)!}\cdot\dfrac{(n-k)!}{(r-k)!(n-r)!}\\
&=\binom nk\binom{n-k}{r-k}\\
\end{aligned}
$$

> 30. Let $n$ and $k$ be integers with $1 ≤ k ≤ n$. Show that
>
> $$
\sum_{k=1}^n\binom nk\binom n{k-1}=\binom{2n+2}{n+1}/2-\binom{2n}n
> $$

From Vandermonde Identity

$$
\begin{aligned}
\sum_{k=1}^n\binom nk\binom n{k-1}&=\sum_{k=1}^n\binom n{n-k}\binom n{k-1}\\
&=\binom{2n}{n-1}\\
&=\dfrac{(2n)!}{(n-1)!(n+1)!}\\
\end{aligned}
$$

while

$$
\begin{aligned}
\binom{2n+2}{n+1}/2-\binom{2n}n&=\dfrac{(2n+2)!}{2(n+1)!(n+1)!}-\dfrac{(2n)!}{n!n!}\\
&=\dfrac{(2n)!}{(n-1)!(n+1)!}
\end{aligned}
$$

> 34. Give a combinatorial proof that $\sum\limits_{k=1}^nk\binom nk^2=n\binom{2n-1}{n-1}$.
[Hint: Count in two ways the number of ways to select a
committee, with n members from a group of n mathematics
professors and n computer science professors, such
that the chairperson of the committee is a mathematics
professor.]

Suppose we're to select a committee of $n$ people from $2n$ people, of whom $n$ are math profs and $n$ are computer profs. After that, we select a math profs as the  chairman of the committee.

To do so, suppose there're $k$ math profs in the commitee, then the way is $k\binom nk\binom n{n-k}=k\binom nk^2$. So the total $\sum\limits_{k=1}^nk\binom nk^2$.

But we can select the chairman first, then choose the rest $n-1$ members, which yields $n\binom{2n-1}{n-1}$.

## Section 6.5

> 10. A croissant shop has plain croissants, cherry croissants,
chocolate croissants, almond croissants, apple croissants,
and broccoli croissants. How many ways are there to
choose
> 
> a) a dozen croissants?
> 
> b) three dozen croissants?
> 
> c) two dozen croissants with at least two of each kind?
> 
> d) two dozen croissants with no more than two broccoli
croissants?
>
> e) two dozen croissants with at least five chocolate croissants
and at least three almond croissants?
>
> f) two dozen croissants with at least one plain croissant,
at least two cherry croissants, at least three chocolate
croissants, at least one almond croissant, at least
two apple croissants, and no more than three broccoli
croissants?

a)

$\binom{12+6-1}{6-1}=6188$

b)

$\binom{36+6-1}{6-1}=749398$

c)

The same as choose $24-2\times6=12$.

$\binom{12+6-1}{6-1}=6188$

d)

$\binom{24+5-1}{5-1}+\binom{23+5-1}{5-1}+\binom{22+5-1}{5-1}=52975$

e)

The same as choose $24-5-3=16$

$\binom{16+6-1}{6-1}=20349$

f)

The same as choose $24-1-2-3-1-2=15$, bu no more than $3$ broccoli ones.

$\binom{15+5-1}{5-1}+\binom{14+5-1}{5-1}+\binom{13+5-1}{5-1}+\binom{12+5-1}{5-1}=11136$

> 16. How many solutions are there to the equation
$x_1 + x_2 + x_3 + x_4 + x_5 + x_6 = 29$,
where $x_i, i = 1, 2, 3, 4, 5, 6$, is a nonnegative integer such
that
>
> a) $x_i > 1$ for $i = 1, 2, 3, 4, 5, 6$?
> 
> b) $x_1 ≥ 1, x_2 ≥ 2, x_3 ≥ 3, x_4 ≥ 4, x_5 > 5$, and $x_6 ≥ 6$?
> 
> c) $x_1 ≤ 5$?
> 
> d) $x_1 < 8$ and $x_2 > 8$?

a)

The same as $\sum x_i=29-2\times6=17,x_i\ge0$.

$\binom{17+6-1}{6-1}=26334$

b)

The same as $\sum x_i=29-1-2-3-4-6-6=7,x_i\ge0$

$\binom{7+6-1}{6-1}=792$

c)

$\sum\limits_{i=0}^5\binom{29-i+5-1}{5-1}=179976$

d)

The same as $\sum x_i=29-9=20,x_i\ge0,x_1\le 7$

We can calculate $x_1\ge 8$, $\binom{20-8+6-1}{6-1}=6188$

Then calculate $x_1\ge0$, $\binom{20+6-1}{6-1}=53130$

To make $x_1<8$, $53130-6188=46942$

> 28. How many positive integers less than 1,000,000 have exactly
one digit equal to 9 and have a sum of digits equal
to 13?

The integer can have at most $6$ digits.

$9+4$: $P(6,2)=30$

$9+3+1$: $P(6,3)=120$

$9+2+2$: $\binom61\times\binom52=60$

$9+2+1+1$: $\binom 61\times\binom 51\times\binom 42=180$

$9+1+1+1+1$: $\binom61\times\binom54=30$

Total: $420$

> 34. How many different strings can be made from the letters
in AARDVARK, using all the letters, if all three As must
be consecutive?

Consider 3 consecutive As as one letter.

$\dfrac{6!}{2!}=360$

> 48. A shelf holds 12 books in a row. How many ways are
there to choose five books so that no two adjacent books
are chosen? [Hint: Represent the books that are chosen by
bars and the books not chosen by stars. Count the number
of sequences of five bars and seven stars so that no two
bars are adjacent.]

$\binom{7+1}{5}=56$

> 52. How many ways are there to distribute five distinguishable
objects into three indistinguishable boxes?

$5$: $1$

$4+1$: $\binom54=5$

$3+2$: $\binom53=10$

$3+1+1$: $\binom53\times\binom21/2=10$

$2+2+1$: $\binom52\times\binom32/2=15$

Total: $41$

> 56. How many ways are there to distribute five indistinguishable
objects into three indistinguishable boxes?

$5=5+0+0$

$5=4+1+0$

$5=3+2+0$

$5=3+1+1$

$5=2+2+1$

Total: $5$

> 63. Suppose that a weapons inspector must inspect each of
five different sites twice, visiting one site per day. The inspector
is free to select the order in which to visit these
sites, but cannot visit site X, the most suspicious site, on
two consecutive days. In how many different orders can
the inspector visit these sites?

Without the X condition, $\dfrac{10!}{2!^5}=113400$

If we let the two X be consecutive, $\dfrac{9!}{2!^5}=22680$

So with the X condition, $113400-22680=90720$

## Section 6.6

> 6. Find the next larger permutation in lexicographic order
after each of these permutations.
>
> f) 23587416

f)

23587461

> 7. Use Algorithm 1 to generate the 24 permutations of the
first four positive integers in lexicographic order.

1234, 1243, 1324, 1342, 1423, 1432,

2134, 2143, 2314, 2341, 2413, 2431,

3124, 3142, 3214, 3241, 3412, 3421,

4123, 4132, 4213, 4231, 4312, 4321

> 9. Use Algorithm 3 to list all the 3-combinations of
$\{1, 2, 3, 4, 5\}$.

123, 124, 125, 134, 135,

145, 234, 235, 245, 345