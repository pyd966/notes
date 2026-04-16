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