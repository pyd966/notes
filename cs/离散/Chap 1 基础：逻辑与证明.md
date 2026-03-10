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