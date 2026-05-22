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

