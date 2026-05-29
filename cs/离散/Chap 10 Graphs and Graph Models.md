# Chap 10 Graphs and Graph Models

## Section 10.1

> 1. Draw graph models, stating the type of graph (from
Table 1) used, to represent airline routes where every
day there are four flights from Boston to Newark, two
flights from Newark to Boston, three flights from Newark
to Miami, two flights from Miami to Newark, one flight
from Newark to Detroit, two flights from Detroit to
Newark, three flights from Newark to Washington, two
flights from Washington to Newark, and one flight from
Washington to Miami, with
>
> a) an edge between vertices representing cities that have
a flight between them (in either direction).
>
> b) an edge between vertices representing cities for each
flight that operates between them (in either direction).
>
> c) an edge between vertices representing cities for each
flight that operates between them (in either direction),
plus a loop for a special sightseeing trip that takes off
and lands in Miami.
>
> d) an edge from a vertex representing a city where a
flight starts to the vertex representing the city where
it ends.
>
> e) an edge for each flight from a vertex representing a
city where the flight begins to the vertex representing
the city where the flight ends.

a)



> 3-9.

## Section 10.2

> 5. Can a simple graph exist with 15 vertices each of degree
five?

No.

The total degree is $15\times5=75$ is odd, so it's impossible.

> 24-25.

> 44. Determine whether each of these sequences is graphic.
For those that are, draw a graph having the given degree
sequence.
>
> b) 6, 5, 4, 3, 2, 1
> 
> f) 1, 1, 1, 1, 1, 1
>
> h) 5, 5, 4, 3, 2, 1

b) No. A graph with 6 vertices cannot have a vertice with degree 6.

f) Yes.

h) No. There're 2 vertices with degree $n-1$, so the minimal degree should be $2$.

> 55. For which values of n are these graphs regular?
> 
> a) $K_n$ b) $C_n$ c) $W_n$ d) $Q_n$

a) All.

b) $n\ge 3$

c) $n=3$

d) $n\ge1$

> 62. If $G$ is a simple graph with 15 edges and $\overline{G}$ has 13 edges,
how many vertices does $G$ have?

$\binom n2=15+13$, so $n=8$

## Section 10.3

> 8. Represent the graph in Exercise 4 with an adjacency matrix.

$$
\begin{pmatrix}
0 & 1 & 0 & 1 & 0\\
1 & 0 & 1 & 1 & 1\\
0 & 1 & 1 & 0 & 0\\
1 & 0 & 0 & 0 & 1\\
0 & 0 & 1 & 0 & 1\\
\end{pmatrix}
$$

> 15.

> 17.
>
> $$
\begin{pmatrix}
1 & 2 & 0 & 1\\
2 & 0 & 3 & 0\\
0 & 3 & 1 & 1\\
1 & 0 & 1 & 0\\
\end{pmatrix}
> $$

> 38-41.

## Section 10.4

> 27. Find the number of paths from a to e in the directed graph
in Exercise 2 of length
>
> e) $6$

e) $5$

> 28. Show that every connected graph with $n$ vertices has at
least $n − 1$ edges.

Suppose we add edges one by one.

Adding one edge can merge at most $2$ connected components.

Originally there're $n$ connected components, in the end there's only one.

So at least $n-1$ edges.

> 29. Let $G = (V, E)$ be a simple graph. Let $R$ be the relation
on $V$ consisting of pairs of vertices $(u, v)$ such that there
is a path from $u$ to $v$ or such that $u = v$. Show that $R$ is an
equivalence relation.

Reflexive: $u=u$, so $uRu$

Symmetric: $G$ is undirected, so $uRv\Rightarrow vRu$

Transitive: If $uRv,vRw$, combining the path $u\to v,v\to w$ yields a path $u\to w$, so $uRw$.

> 62. Use Exercise 61 to show that the graph $G_1$ in Figure 2
is connected whereas the graph $G_2$ in that figure is not
connected.

If there exists a path from $u\to v$, then there exists a path with length $<n$ from $u\to v$.

So we calculate $I+A+A^2+\dots+A^{n-1}$.

$I+G_1+G_1^2+\dots+G_1^{n-1}=\begin{pmatrix}1 & 1 & 1 & 1 & 1 & 1 & 1\\ 1 & 1 & 1 & 1 & 1 & 1 & 1\\ 1 & 1 & 1 & 1 & 1 & 1 & 1\\ 1 & 1 & 1 & 1 & 1 & 1 & 1\\ 1 & 1 & 1 & 1 & 1 & 1 & 1\\ 1 & 1 & 1 & 1 & 1 & 1 & 1\\ 1 & 1 & 1 & 1 & 1 & 1 & 1\\\end{pmatrix}$

$I+G_2+G_2^2+G_2^2+G_2^3+G_2^4+G_2^5=\begin{pmatrix}1 & 1 & 1 & 0 & 0 & 0\\ 1 & 1 & 1 & 0 & 0 & 0\\ 1 & 1 & 1 & 0 & 0 & 0\\ 0 & 0 & 0 & 1 & 1 & 1\\ 0 & 0 & 0 & 1 & 1 & 1\\ 0 & 0 & 0 & 1 & 1 & 1\\\end{pmatrix}$

So $G_1$ is connected, $G_2$ is not.

## Section 10.5

> 4.

Euler circuit: None

Euler path: cbafbdaecdef

> 6.

Euler circuit: None

Euler path: badefdgihaibcidc

> 31. 

Yes. aedcba

> 34.

No.

For a, c, g, e, whose degree is 2, their 2 edges must be in the circuit.

This results in a closed circuit, so it's impossbile to construct a circuit including all vertices.

> 38. Does the graph in Exercise 31 have a Hamilton path? If
so, find such a path. If it does not, give an argument to
show why no such path exists.

Yes. aedcb

> 41. Does the graph in Exercise 34 have a Hamilton path? If
so, find such a path. If it does not, give an argument to
show why no such path exists.

To find a Hamilton path, for those vertices with degree 2, there're at most 2 edges not being selected.

WLOG, suppose edge (a,b) is not selected, then edge (b,j) must be selected, WLOG suppose (i,j) is not selected, then we still can't integrate vertex p, so it's impossible.

## Section 10.6

> 3.

With Dijkstra algorithm, we can decide nodes' shortest distance by the following order.

a: 0

c: 3 a->c

b: 4 a->b

d: 6 a->c->d

e: 7 a->c->d->e

f: 11 a->c->d->f

g: 12 a->c->d->e->g

z: 16 a->c->d->e->g->z

> 17. The weighted graphs in the figures here show some major
roads in New Jersey. Part (a) shows the distances between
cities on these roads; part (b) shows the tolls.
>
> a) Find a shortest route in distance between Newark and
Camden, and between Newark and Cape May, using
these roads.

a)

Newark & Camden:

Newark -> Woodbridge -> Camden

Newark & Cape May:

Newark -> Woodbridge -> Asbury Park -> Atlantic City -> Cape May

> 26. Solve the traveling salesperson problem for this graph by
finding the total weight of all Hamilton circuits and determining
a circuit with minimum total weight.

abcdea

abceda

abdcea

abdeca

abecda

abedca

acbdea

acbeda

acdbea



## Section 10.7

> 7.

Yes

> 20.

Yes. By removing only point e, c.

> 22.

Yes. By removing only points b, d, f, h, j, l.

> 23.



> 25.

## Section 10.8

> 3.

> 8.

> 9.

> 10.

