# Chap 5 Mathematical Induction

## Section 5.1

> 46. Prove that a set with $n$ elements has $\dfrac{n(n − 1)(n − 2)}6$
subsets containing exactly three elements whenever $n$ is
an integer greater than or equal to $3$.

We know that a set has $\dbinom{n}{3}=\dfrac{n(n-1)(n-2)}{6}$ subsets containing 3 elements.

> 47. Devise a greedy algorithm that uses the minimum number
of towers possible to provide cell service to $d$ buildings
located at positions $x_1, x_2,…, x_d$ from the start of the
road. [Hint: At each step, go as far as possible along the
road before adding a tower so as not to leave any buildings
without coverage.]

While there exists a building that is not covered, we find the leftmost one $x_p$, and place a tower at position $x_p+1$, then delete all the buildings that are now covered by this new tower, and then go back to the check step.

> 48. Use mathematical induction to prove that the algorithm
you devised in Exercise 47 produces an optimal solution,
that is, that it uses the fewest towers possible to provide
cellular service to all buildings.

We perform mathematical inducement with the building number $d$.

Basic step: When $d=1$, obviously it yields optimal result: $1$ tower.

Inducement step:

Suppose $1\le d\le k$ is correct, then prove $d=k+1$.

Suppose $x_1$ is the leftmost building, our algorithm will place $x_1+1$ as our leftmost tower. We prove that $x_1+1$ is in the optimal solution.

If $x_1+1$ is not in the optimal solution, we replace the leftmost tower in the optimal solution with $x_1+1$, it's easy to know that the buildings covered by the leftmost tower will not decrese, so it still forms a valid solution. Thus we get a valid solution with $x_1+1$ in it.

After deleting the buildings covered by $x_1+1$, the remaining buildings are less than or euqal to $k$.

By inducement hypothesis, our algorithm can get the optimal solution for the ramaining buildings.

Put $x_1+1$ into the solution, we can get an optimal solution for $k+1$.

## Section 5.2

> 8. Suppose that a store offers gift certificates in denominations
of 25 dollars and 40 dollars. Determine the possible
total amounts you can form using these gift certificates.
Prove your answer using strong induction.

Let $P(n): 5n$ can be reached. We prove $P(n)$ is true when $n=5,8,10,13,15,16,18,20,21,23,24,25,26$ and $n\ge 28$

Basic step: check $n=\dots,28,29,30,31,32$ is true.

Inducement step:

Suppose for $28\le k<n$, $P(k)$ is true, now prove $P(n)$, where $n\ge33$

$n-5\ge 28$, so $P(n-5)$ is true. Then $5n=5(n-5)+25$, so $P(n)$ is true.

> 18. Use strong induction to show that when a simple polygon
$P$ with consecutive vertices $v_1, v_2, …, v_n$ is triangulated
into $n − 2$ triangles, the $n − 2$ triangles can be
numbered $1, 2,…, n − 2$ so that $v_i$ is a vertex of triangle
$i$ for $i = 1, 2,…, n − 2$.

Lemma: for $n\ge 4$, there exists a triange in its triangulations, which has consecutive vertices.

We use strong inducement to prove the theorem.

Basic step: $n=3$ is ok.

Inducement step: 

Suppose $n\le k$ is ok, we prove $n=k+1$ is ok.

Find the triangle in the lemma, WLOG suppose it is $\triangle v_1v_2v_3$.

Deleting this triangle, the ramaining polygen has $v_1,v_3,v_4,\dots,v_n$. Suppose $u_1=v_1,u_2=v_3,u_3=v_4,\dots,u_{n-1}=v_n$, its triangulations be $P'$

By inducement hypothesis, the $n-3$ triangles can be numbered $1,2,\dots,n-3$, such that triangle $j$ contains vertice $u_j$.

Now we construct the original index of triangles.

Let triangle $1$ be number $1$ in $P'$

Let triangle $2$ be $\triangle v_1v_2v_3$

Let triangle $3,\dots,n-2$ be number $2,\dots,n-3$ in $P'$.

It's easy to verify that this is a valid solution.

> 39. Can you use the well-ordering property to prove the statement:
“Every positive integer can be described using no
more than fifteen English words”? Assume the words
come from a particular dictionary of English. [Hint:
Suppose that there are positive integers that cannot be
described using no more than fifteen English words. By
well ordering, the smallest positive integer that cannot
be described using no more than fifteen English words
would then exist.]

No. In fact it's wrong.

Let $S$ be the set of all phases that consists of no more than 15 words. Let $T$ be the set of all positve numbers.

So $S$ is finite, while $T$ is infinite. So there cannot be a onto mapping from $S$ to $T$.

