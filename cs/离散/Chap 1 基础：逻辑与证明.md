## Section 1.1

> 2. 下列哪些是命题？这些命题的真值是什么？
>
> $a)$ 别过去
>
> $b)$ 几点了？
>
> $c)$ 在缅因州没有黑苍蝇
>
> $d)$ $4+x=5$
>
> $e)$ 月亮是由绿色的奶酪构成的
>
> $f)$ $2^n\ge100$

是命题：$c),e)$；不是命题：$a),b),d),f)$。

$c),e)$ 均为假命题。 

> 8. 假设智能手机 A 有 256MB RAM 和 32GB ROM，并且其相机的分辨率是 8MP；智能手机 B 有 288MB RAM 和 64GB ROM，并且其相机的分辨率是 4MP；而智能手机 C 有 128MB RAM 和 32 GB ROM，并且其相机的分辨率是 5MP。试判定下面每个命题的真值。
>
> $d)$ 如果智能手机 B 比智能手机 C 具有更多的 RAM 和更多的 ROM，则它也具有更高分辨率的相机。
>
> $e)$ 智能手机 A 比智能手机 B 具有更多的 RAM 当且仅当智能手机 B 比智能手机 A 具有更多的 RAM。

$d)$

记三个子命题分别为 $p,q,r$，则 $p,q,r$ 分别为 真真假，所以该命题为假命题。

$e)$

记两个命题分别为 $p,q$，则它们分别为 假真，所以该命题为假命题。

> 16. 令 $p,q,r$ 为如下命题：
>
> $p:$ 你的期末考试得了 A。
>
> $q:$ 你做了本书每一道练习。
>
> $r:$ 这门课你得了 A。
>
> 用 $p,q,r$ 和逻辑联结词（包括否定）写出下列命题：
>
> $e)$ 期末考试得 A 并且做本书的每道练习，足以使你这门课得 A。

$e)$ $(p\land q)\rightarrow r$

> 24. 把下列语句写成“如果 $p$，则 $q$”得形式。
>
> $a)$ 要想晋升，帮老板洗车是很有必要的。
>
> $b)$ 吹南风预示着春天要来了。
>
> $c)$ 保修单有效的充分条件是你的计算机购买时间不超过一年。
>
> $d)$ Willy 只要行骗就会被抓住。
>
> $e)$ 你可以访问网站仅当你支付了订阅费。
>
> $f)$ 当选是源于了解合适的人群。
>
> $g)$ 每当坐船 Carol 就会晕船。

$a)$

$p:$ 想晋升； $q:$ 帮老板洗车

$b)$

$p:$ 吹南风； $q:$ 春天要来了

$c)$

$p:$ 你的计算机购买时间不超过一年； $q:$ 保修单有效

$d)$

$p:$ Willy 行骗； $q:$ Willy 被抓住

$e)$

$p:$ 你可以访问网站； $q:$ 你支付了订阅费

$f)$

$p:$ 当选； $q:$ 了解合适的人群

$g)$

$p:$ Carol 坐船； $q:$ Carol 晕船

> 30. 叙述下列各条件语句的逆命题、逆否命题和反命题。
>
> $b)$ 只要是阳光充足的夏天，我就去海滩。

$b)$

逆命题：如果我去海滩，那么这是阳光充足的夏天。

逆否命题：如果我不去海滩，那么就不是阳光充足的夏天。

否命题：如果不是阳光充足的夏天，我就不去海滩。

> 34. 构造下列各复合命题的真值表。
>
> $f)$ $(p\leftrightarrow q)\oplus(p\leftrightarrow\neg q)$

|$p$|$q$|$p\leftrightarrow q$|$p\leftrightarrow\neg q$|$(p\leftrightarrow q)\oplus(p\leftrightarrow\neg q)$|
|---|---|---|---|---|
|F|F|T|F|T|
|F|T|F|T|T|
|T|F|F|T|T|
|T|T|T|F|T|

> 52. 试问断言“本语句为假”是命题吗？

不是，因为这个断言不能判断真假。

如果该断言为真，那么由断言本身，该断言为假；如果该断言为假，那么由断言本身，该断言为真。

## Section 1.2

> 4. 要想使用机场的无线网络，你必须支付每日的使用费，除非你是该服务的一个订户。用 $w:$“你能使用机场的无线网络”，$d:$“你支付每日的使用费”和 $r:$“你是该服务的一个订户”来表达你的答案。

$w\rightarrow(d\lor r)$

> 10. 下列系统规范说明一致吗？“每当对系统软件进行升级时，用户不能访问文件系统。如果用户能访问文件系统，那么他们能保存新文件。如果用户不能保存新文件，那么系统软件未被升级。”

$p:$ 系统软件进行升级

$q:$ 用户可以访问文件系统

$r:$ 用户可以保存新文件

$p\rightarrow\neg q$， $q\rightarrow r$， $\neg r\rightarrow\neg p$

只要取 $p,q,r$ 分别为 TFT 即可验证该系统规范说明一致。

> 22. 当你规划一个聚会时需要知道该邀请什么人。在你可能邀请的人中有三个棘手的朋友。你知道如果 Jasmine 参加，她对 Samir 在场会感到不快；Samir 仅当 Kanti 到场才会出席；而 Kanti 不会出席除非 Jasmine 也在场。你如何邀请三人的组合而不使某人不愉快。

记 $p,q,r$ 分别表示邀请 Jasmine, Samir, Kanti。

则 $p\rightarrow\neg q,q\rightarrow r,r\rightarrow p$。

若 $q$ 为 T，则 $r,p$ 均为 T，这导出 $q$ 为 F 矛盾。

故 $q$ 为 F，若 $r$ 为 T，则 $p$ 为 T；若 $r$ 为 F，则 $p$ 均可。

故邀请的组合可以是 TFT, FFF, TFF。

## Section 1.3

> 6. 用真值表证明德·摩根第一定律。
>
> $\neg(p\land q)\equiv\neg p\lor\neg q$。

|$p$|$q$|$\neg p$|$\neg q$|$p\land q$|$\neg(p\land q)$|$\neg p\lor\neg q$|
|--|--|--|--|--|--|--|
|F|F|T|T|F|T|T|
|F|T|T|F|F|T|T|
|T|F|F|T|F|T|T|
|T|T|F|F|T|F|F|

> 8. 用德·摩根律求下列命题的否定。
>
> $a)$ Kwame 将在工业界找一份工作或者去研究生院读书。
>
> $b)$ Yoshiko 掌握 Java 和微积分。

$a)$ Kwame 既没有在工业界找到一份工作，也没有去研究生院读书。

$b)$ Yoshiko 没有掌握 Java，或者没有掌握微积分。

> 10. 对于下面的每一个复合命题，用条件-析取式（例 3）找出不含条件的等价复合命题。
>
> $a)$ $\neg p\rightarrow\neg q$
>
> $b)$ $(p\lor q)\rightarrow\neg p$
>
> $c)$ $(p\rightarrow\neg q)\rightarrow(\neg p\rightarrow q)$

$a)$

$\neg p\rightarrow\neg q\equiv \neg(\neg p)\lor\neg q\equiv p\lor\neg q$

$b)$

$(p\lor q)\rightarrow\neg p\equiv\neg(p\lor q)\lor\neg p\equiv(\neg p\land\neg q)\lor\neg p\equiv\neg p$

$c)$

$(p\rightarrow\neg q)\rightarrow(\neg p\rightarrow q)\equiv(\neg p\lor\neg q)\rightarrow(\neg(\neg p)\lor q)\equiv\neg(\neg p\lor\neg q)\lor(p\lor q)\equiv (p\land q)\lor(p\lor q)\equiv p\lor q$

> 12. 用真值表证明下列条件语句为永真式。
>
> $b)$ $[(p\rightarrow q)\land(q\rightarrow r)]\rightarrow(p\rightarrow r)$

|$p$|$q$|$r$|$p\rightarrow q$|$q\rightarrow r$|$p\rightarrow r$|$(p\rightarrow q)\land(q\rightarrow r)$|$[(p\rightarrow q)\land(q\rightarrow r)]\rightarrow(p\rightarrow r)$|
|--|--|--|--|--|--|--|--|
|F|F|F|T|T|T|T|T|
|F|F|T|T|T|T|T|T|
|F|T|F|T|F|T|F|T|
|F|T|T|T|T|T|T|T|
|T|F|F|F|T|F|F|T|
|T|F|T|F|T|T|F|T|
|T|T|F|T|F|F|F|T|
|T|T|T|T|T|T|T|T|

> 34. Show that $(p ∨ q) ∧ (¬p ∨ r) → (q ∨ r)$ is a tautology.

$$
\begin{aligned}
(p\lor q)\land(\lnot p\lor r)\rightarrow(q\lor r)&\equiv
\lnot((p\lor q)\land(\lnot p\lor r))\lor (q\lor r)\\
&\equiv(\lnot(p\lor q)\lor\lnot(\lnot p\lor r))\lor q\lor r\\
&\equiv((\lnot p\land\lnot q)\lor(p\land\lnot r))\lor q\lor r\\
&\equiv((\lnot p\lor (p\land\lnot r))\land(\lnot q\lor(p\land\lnot r)))\lor q\lor r\\
&\equiv(((\lnot p\lor p)\land(\lnot p\lor\lnot r))\land((\lnot q\lor p)\land(\lnot q\lor\lnot r)))\lor q\lor r\\
&\equiv((\lnot p\lor\lnot r)\land(\lnot q\lor p)\land(\lnot q\lor\lnot r))\lor q\lor r\\
&\equiv(q\lor r\lor\lnot p\lor\lnot r)\land(\lnot q\lor p\lor q\lor r)\land(\lnot q\lor\lnot r\lor q\lor r)\\
&\equiv T
\end{aligned}
$$

> 36. Show that $(p ∧ q) → r$ and $(p → r) ∧ (q → r)$ are not logically equivalent.

Assign TFF to $p,q,r$, we can get $(p\land q)\rightarrow r=T$ while $(p\rightarrow r)\land(q\rightarrow r)=F$.

> 44. Find a compound proposition involving the propositional variables $p$, $q$, and $r$ that is true when $p$ and $q$ are true and $r$ is false, but is false otherwise.

$p\land q\land\lnot r$

> 55. Find a compound proposition logically equivalent to $p → q$ using only the logical operator $↓$.

$$
\begin{aligned}
p\rightarrow q&\equiv \lnot p\lor q\\
&\equiv (p\downarrow p)\lor q\\
&\equiv ((p\downarrow p)\downarrow q)\downarrow((p\downarrow p)\downarrow q)
\end{aligned}
$$

> [supplement] Find the Full Disjunctive (Conjunctive) Normal Form from truth table of following formula $((\lnot p\land q)\rightarrow(p\leftrightarrow r))\lor(q\rightarrow\lnot r)$

Truth table:

|$p$|$q$|$r$|$\lnot p\land q$|$p\leftrightarrow r$|$q\rightarrow\lnot r$|$(\lnot p\land q)\rightarrow(p\leftrightarrow r)$|$((\lnot p\land q)\rightarrow(p\leftrightarrow r))\lor(q\rightarrow\lnot r)$|
|--|--|--|--|--|--|--|--|
|F|F|F|F|T|T|T|T|
|F|F|T|F|F|T|T|T|
|F|T|F|T|T|T|T|T|
|F|T|T|T|F|F|F|F|
|T|F|F|F|F|T|T|T|
|T|F|T|F|T|T|T|T|
|T|T|F|F|F|T|T|T|
|T|T|T|F|T|F|T|T|

Full Disjunctive Normal Form:

$(\lnot p\land\lnot q\land\lnot r)\lor(\lnot p\land\lnot q\land r)\lor(\lnot p\land q\land\lnot r)\lor(p\land\lnot q\land\lnot r)\lor(p\land\lnot q\land r)\lor(p\land q\land\lnot r)\lor(p\land q\land r)$

Full Conjunctive Normal Form:

$p\lor\lnot q\lor\lnot r$

## Section 1.4

> 6. Let $N(x)$ be the statement “$x$ has visited North Dakota,”where the domain consists of the students in your school.Express each of these quantifications in English.
> 
> $c)$ $¬∃xN(x)$
> 
> $d)$ $∃x¬N(x)$
> 
> $e)$ $¬∀xN(x)$
> 
> $f)$ $∀x¬N(x)$

$c)$

There does not exist a student in my school that has visited North Dakota.

$d)$

There exists a student in my school that hasn't visited North Dakota.

$e)$

Not all students in my school have visited North Dakota.

$f)$

All students in my school haven't visited North Dakota.

> 9. Let $P(x)$ be the statement “$x$ can speak Russian” and let $Q(x)$ be the statement “$x$ knows the computer language C++.” Express each of these sentences in terms of $P(x),Q(x)$, quantifiers, and logical connectives. The domain for quantifiers consists of all students at your school.
>
> $b)$ There is a student at your school who can speak Russian but who doesn’t know C++.
>
> $d)$ No student at your school can speak Russian or knows C++.

$b)$

$\exist x (P(x)\land\lnot Q(x))$

$d)$

$\lnot\exist x(P(x)\lor Q(x))$

> 20. Suppose that the domain of the propositional function
$P(x)$ consists of $−5, −3, −1, 1, 3$, and $5$. Express these
statements without using quantifiers, instead using only
negations, disjunctions, and conjunctions.
>
> $e)$ $∃x(¬P(x)) ∧ ∀x((x < 0) → P(x))$

$e)$

$(\lnot P(-5)\lor\lnot P(-3)\lor\lnot P(-1)\lor\lnot P(1)\lor\lnot P(3)\lor\lnot P(5))\land(P(-5)\land P(-3)\land P(-1))$

Equivalently, $(P(-5)\land P(-3)\land P(-1))\land (\lnot P(1)\lor\lnot P(3)\lor\lnot P(5))$

> 24. Translate in two ways each of these statements into logical
expressions using predicates, quantifiers, and logical
connectives. First, let the domain consist of the students
in your class and second, let it consist of all people.
>
> $b)$ Somebody in your class has seen a foreign movie.
>
> $d)$ All students in your class can solve quadratic equations.

$b)$

$P(x):$ $x$ has seen a foreign movie.

$Q(x):$ $x$ is in my class.

First: $\exist x P(x)$

Second: $\exist x(Q(x)\land P(x))$

$d)$

$P(x):$ $x$ can solve quadratic equations

$Q(x):$ $x$ is in my class.

First: $\forall x P(x)$

Second: $\forall x(Q(x)\rightarrow P(x))$

> 36. Express the negation of each of these statements in terms
of quantifiers without using the negation symbol.
> 
> $a)$ $∀x(−2 < x < 3)$
> 
> $b)$ $∀x(0 ≤ x < 5)$
> 
> $c)$ $∃x(−4 ≤ x ≤ 1)$
> 
> $d)$ $∃x(−5 < x < −1)$

$a)$

$\exist x(x\le-2\lor x\ge 3)$

$b)$

$\exist x(x<0\lor x\ge 5)$

$c)$

$\forall x(x<-4\lor x>1)$

$d)$

$\forall x(x\le-5\lor x\ge-1)$

> 42. Express each of these system specifications using predicates,
quantifiers, and logical connectives.
> 
> $b)$ No directories in the file system can be opened and
no files can be closed when system errors have been
detected.

$b)$

$Err\rightarrow(\forall x(Dir(x)\rightarrow\lnot Open(x))\land\forall x(File(x)\rightarrow\lnot Close(x)))$

> 46. Determine whether $∀x(P(x) ↔ Q(x))$ and $∀x P(x) ↔
∀xQ(x)$ are logically equivalent. Justify your answer.

No.

Assign $P(x)=\begin{cases}0&,x=0\\ 1&,x=1\end{cases}$ and $Q(x)=\begin{cases}1&,x=0\\ 0&,x=1\end{cases}$.

Then the first statement is false while the second is true.

> 51. Establish these logical equivalences, where $x$ does not occur
as a free variable in $A$. Assume that the domain is
nonempty.
>
> $a)$ $∀x(P(x) → A) ≡ ∃xP(x) → A$

$a)$

$$
\begin{aligned}
\forall x(P(x)\rightarrow A)&\equiv \forall x(\lnot P(x)\lor A)\\
&\equiv\forall x(\lnot P(x))\lor A\\
&\equiv\lnot\exist x P(x)\lor A\\
&\equiv\exist xP(x)\rightarrow A
\end{aligned}
$$

## Section 1.5

> 6. Let $C(x, y)$ mean that student $x$ is enrolled in class $y$,
where the domain for $x$ consists of all students in your
school and the domain for $y$ consists of all classes being
given at your school. Express each of these statements by
a simple English sentence.
>
> $e)$ $∃x∃y∀z((x ≠ y) ∧ (C(x, z) → C(y, z)))$
>
> $f)$ $∃x∃y∀z((x ≠ y) ∧ (C(x, z) ↔ C(y, z)))$

$e)$

There exist two different students and courses that student A enrolls form a subset of student B.

$f)$

There exist two different students whose course tables are identical.

> 12. Let $I(x)$ be the statement “$x$ has an Internet connection”
and $C(x, y)$ be the statement “$x$ and $y$ have chatted over
the Internet,” where the domain for the variables $x$ and $y$
consists of all students in your class. Use quantifiers to
express each of these statements.
>
> $d)$ No one in the class has chatted with Bob.
>
> $h)$ Exactly one student in your class has an Internet connection.
>
> $k)$ Someone in your class has an Internet connection but
has not chatted with anyone else in your class.
>
> $n)$ There are at least two students in your class who have
not chatted with the same person in your class.

$d)$

$\lnot\exist xC(x, Bob)$

$h)$

$\exist x(I(x)\land\forall y(x\neq y\rightarrow\lnot I(y)))$

$k)$

$\exist x(I(x)\land\forall y(x\neq y\rightarrow\lnot C(x,y)))$

$n)$

$\exist x\exist y(x\neq y\land (\forall z((z\neq x\land z\neq y)\rightarrow(\lnot C(x,z)\lor\lnot C(y,z)))))$

> 14. Use quantifiers and predicates with more than one variable
to express these statements.
>
> $c)$ Some student in this class has visited Alaska but has
not visited Hawaii.
> 
> $d)$ All students in this class have learned at least one programming
language.
> 
> $e)$ There is a student in this class who has taken every
course offered by one of the departments in this
school.
>
> $f)$ Some student in this class grew up in the same town
as exactly one other student in this class.

$c)$

$P(x,y):$ student $x$ has visited place $y$

$\exist x(P(x,Alaska)\land\lnot P(x,Hawaii))$

$d)$

$P(x,y):$ student $x$ has learned programming language $y$

$\forall x\exist y P(x,y)$

$e)$

$P(x,y):$ student $x$ has taken course $y$

$Q(y,z):$ course $y$ is offered by department $z$

$\exist x(\exist z(\forall y Q(y,z))\rightarrow P(x,y))$

$f)$

$P(x,y):$ student $x$ grew up in town $y$

$\exist x\exist y(x\neq y\land(\exist z(P(x,z)\land P(y,z)\land\forall w((w\neq x\land w\neq y)\rightarrow\lnot P(w,z)))))$

> 24. Translate each of these nested quantifications into an English
statement that expresses a mathematical fact. The
domain in each case consists of all real numbers.
>
> $a)$ $∃x∀y(x + y = y)$
>
> $d)$ $∀x∀y((x ≠ 0) ∧ (y ≠ 0) ↔ (xy ≠ 0))$

$a)$

Addictive identity exists.

$d)$

The multiplication of 2 non-zero real numbers is non-zero.

> 32. Express the negations of each of these statements so that
all negation symbols immediately precede predicates.
>
> $d)$ $∀y∃x∃z(T(x, y, z) ∨ Q(x, y))$

$d)$

$$
\begin{aligned}
\lnot\forall y\exist x\exist z(T(x,y,z)\lor Q(x,y))&\equiv\exist y\lnot\exist x\exist z(T(x,y,z)\lor Q(x,y))\\
&\equiv\exist y\forall x\lnot\exist z(T(x,y,z)\lor Q(x,y))\\
&\equiv\exist y\forall x\forall z\lnot(T(x,y,z)\lor Q(x,y))\\
&\equiv\exist y\forall x\forall z(\lnot T(x,y,z)\land\lnot Q(x,y))
\end{aligned}
$$

> 34. Find a common domain for the variables $x, y$, and
$z$ for which the statement $∀x∀y((x ≠ y) → ∀z((z = x) ∨
(z = y)))$ is true and another domain for which it is false.

true: $\{0,1\}$

false: $R$

> 38. Express the negations of these propositions using quantifiers,
and in English.
>
> $b)$ There is a student in this class who has never seen a
computer.
>
> $d)$ There is a student in this class who has been in at least
one room of every building on campus.

$b)$

All students in class have seen a computer

$P(x):$ student $x$ has seen a computer

$\forall x P(x)$

$d)$

For every student, there is a building, whose rooms he/her has never been to.

$P(x,y):$ student $x$ has been to room $y$

$Q(y,z):$ room $y$ is in building $z$

$\forall x\exist z\forall y(\lnot Q(y,z)\lor\lnot P(x,y))$

> 42. Use quantifiers to express the distributive laws of multiplication
over addition for real numbers.

$\forall x\forall y\forall z(x(y+z)=xy+xz)$

## Section 1.6

> 12. Show that the argument form with premises $(p ∧ t) →
(r ∨ s), q → (u ∧ t), u → p$, and $¬s$ and conclusion $q → r$
is valid by first using Exercise 11 and then using rules of
inference from Table 1.

First, from exercise 11, we know that if the argument with premises $(p\land t)\rightarrow(r\lor s),q\rightarrow(u\land t),u\rightarrow p,\lnot s,q$ and conclusion $r$ is valid, then the original argument is also valid.

$q$, premise

$q\rightarrow(u\land t)$, premise

$u\land t$, modus ponens using 1,2

$u$, simplification using 3

$u\rightarrow p$, premise

$p$, modus ponens using 4,5

$t$, simplification using 3

$p\land t$, conjunction using 6,7

$(p\land t)\rightarrow(r\lor s)$, premise

$r\lor s$, modus ponens using 8,9

$\lnot s$, premise

$r$, disjuctive syllogism using 10,11

> 14. For each of these arguments, explain which rules of inference
are used for each step.
>
> $d)$ “There is someone in this class who has been to
France. Everyone who goes to France visits the
Louvre. Therefore, someone in this class has visited
the Louvre.”

d)

$p(x):$ $x$ is in the class

$q(x):$ $x$ has been to France.

$r(x):$ $x$ visits the Louvre.

Premises: $\exist x(p(x)\land q(x)),\forall x(q(x)\rightarrow r(x))$

Conclusion: $\exist x(p(x)\land r(x))$

$\exist x(p(x)\land q(x))$, premise

$p(c)\land q(c)$, existantial instantiation using 1

$\forall x(q(x)\rightarrow r(x))$, premise

$q(c)\rightarrow r(c)$, universal instantiation using 3

$q(c)$, simplification using 2

$r(c)$, modus ponens using 4,5

$p(c)$, simplification using 2

$p(c)\land r(c)$, conjuction using 6,7

$\exist x(p(x)\land r(x))$, existantial generalization using 9

> 18. What is wrong with this argument? Let $S(x, y)$ be “$x$ is
shorter than $y$.” Given the premise $∃sS(s, Max)$, it follows
that $S(Max, Max)$. Then by existential generalization
it follows that $∃xS(x, x)$, so that someone is shorter
than himself.

The second step is wrong.

We cannot specify which $s$ is instantized while using existantial instantiation.

> 24. Identify the error or errors in this argument that supposedly
shows that if $∀x(P(x) ∨ Q(x))$ is true then
$∀xP(x) ∨ ∀xQ(x)$ is true.
>
> (1) $∀x(P(x) ∨ Q(x))$ Premise
>
> (2) $P(c) ∨ Q(c)$ Universal instantiation from (1)
> 
> (3) $P(c)$ Simplification from (2)
> 
> (4) $∀xP(x)$ Universal generalization from (3)
> 
> (5) $Q(c)$ Simplification from (2)
> 
> (6) $∀xQ(x)$ Universal generalization from (5)
> 
> (7) $∀x(P(x) ∨ ∀xQ(x))$ Conjunction from (4) and (6)

Steps (4) and (6) are wrong.

We cannot get a universal proposition when it's only true for some certain $c$ rather than all $c$.

> 29. Use rules of inference to show that if $∀x(P(x) ∨ Q(x)),
∀x(¬Q(x) ∨ S(x)), ∀x(R(x) → ¬S(x))$, and $∃x¬P(x)$ are
true, then $∃x¬R(x)$ is true.

Let's first change these premises into conclusion form.

Premises: $\forall x(\lnot P(x)\to Q(x)),\forall x(Q(x)\to S(x)),\forall x(S(x)\to\lnot R(x)),\exist x\lnot P(x)$

Conclusion: $\exist x\lnot R(x)$

$\forall x(\lnot P(x)\to Q(x))$, premise

$\exist x\lnot P(x)$, premise

$\lnot P(c)$, existantial instantiation using 2

$Q(c)$, universal modus ponens using 1,3

$\forall x(Q(x)\to S(x))$, premise

$S(c)$, universal modus ponens using 4,5

$\forall x(S(x)\to\lnot R(x))$, premise

$\lnot R(c)$, universal modus ponens using 6,7

$\exist x\lnot R(x)$, existantial generalization using 8

> 34. The Logic Problem, taken from WFF’N PROOF, The
Game of Logic, has these two assumptions:
>
> (1) “Logic is difficult or not many students like logic.”
>
> (2) “If mathematics is easy, then logic is not difficult.”
> 
> By translating these assumptions into statements involving
propositional variables and logical connectives, determine
whether each of the following are valid conclusions
of these assumptions:
>
> a) That mathematics is not easy, if many students like
logic.

a)

$P:$ logic is difficult

$Q:$ may students like logic

$R:$ mathematics is easy.

Premises: $P\lor\lnot Q,R\to\lnot P$

Conclusion: $Q\to\lnot R$

From exercise 11, we know that if we can prove the following argument form, the original is also valid.

Premises: $P\lor\lnot Q,R\to\lnot P,Q$

Conclusion: $\lnot R$

$Q$, premise

$P\lor\lnot Q$, premise

$P$, disjunctive syllogism using 1,2

$R\to\lnot P$, premise

$\lnot R$, modus tollens using 3,4

## Section 1.7

> 7. Use a direct proof to show that every odd integer is the
difference of two squares. [Hint: Find the difference of
the squares of $k + 1$ and $k$ where $k$ is a positive integer.]

Suppose $x$ is an odd integer, let's say $x=2k+1$.

Then $(k+1)^2-k^2=2k+1=x$, so $x$ is indeed the difference of two squares.

> 8. Prove that if $n$ is a perfect square, then $n + 2$ is not a perfect
square.

We use contradiction.

Suppose $n+2$ is a perfect square, and $n$ is also a perfect square.

Then $n=x^2,n+2=y^2$, where $x,y$ are integers, so $2=y^2-x^2=(y-x)(y+x)$

Because $x,y$ are both integers, so $(y-x,y+x)=(1,2)/(2,1)/(-1,-2)/(-2,-1)$.

Solve the equations given by any of these four cases, you'll find $x,y$ cannot be integers. This contradicts with our premises.

So the original proposition is correct.

> 36. Is this reasoning for finding the solutions of the equation
$\sqrt{2x^2-1}=x$ correct? 
>
> (1) $\sqrt{2x^2-1}=x$ is given;
> 
> (2) $2x^2-1=x^2$ obtained by squaring both sides of (1);
> 
> (3) $x^2-1=0$, obtained by subtracting x2 from both
sides of (2); 
>
> (4) $(x − 1)(x + 1) = 0$, obtained by factoring
the left-hand side of $x^2-1$; 
> 
> (5) $x = 1$ or $x = −1$,
which follows because $ab = 0$ implies that $a = 0$ or
$b = 0$.

No.

(2) is not equivalent to (1).

In fact, when $x=-1$, (2) is correct while (1) is not.

## Section 1.8

> 24. Use forward reasoning to show that if $x$ is a nonzero
real number, then $x^2+\dfrac1{x^2}\ge2$ [Hint: Start with the inequality
$(x − \dfrac1x)^2 ≥ 0$, which holds for all nonzero real
numbers $x$.]

If $x$ is a nonzero real number, then $(x-\dfrac1x)^2\ge0$, which gives $x^2-2+\dfrac1{x^2}\ge0$, which gives $x^2+\dfrac1{x^2}\ge 2$.