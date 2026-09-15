
在前面几节中，我们已经掌握训练一个生成图片的模型。遗憾的是，这个模型拟合的是所有图片的分布。换言之，你无法控制它生成的内容，只能抽卡。这一节我们就来研究如何控制其生成的图片，也就是提供 guidance。

## vanilla guidance

现在我们获得的数据不再是简单的图片 $x$，而变成了图片和 prompt 的二元组 $(x,y)$。我们学习的目标也变成了学习在 $y$ 控制下的向量场 $u_t^{\theta}(\cdot\mid y)$，我们希望高斯分布经过这个向量场之后可以变成分布 $p_{data}(\cdot\mid y)$。

一个简单的想法是微调我们的训练 loss。$L_{CFM}^{guided}(\theta)=E_{(x,y)\sim p_{data},t\sim Unif,z\sim p_t(\cdot\mid x)}[||u_t^{\theta}(z\mid y)-u_t^{target}(z\mid x)||^2]$。容易发现，在理论上我们可以保证这样学出来的 $u_t^{\theta}(\cdot\mid y)$ 最终可以变成 $p_{data}(\cdot\mid y)$。因此这是一个理论上完美的答案。

理论是美好的，现实是残酷的。

实际训练中，由于我们的数据不够多，对于那些数据量不够大的 $y$，模型很难真的学会它们的向量场。比如说，猫的图片有很多，但是戴墨镜的猫就少之又少。进而模型会学会把戴墨镜的猫的向量场变得很像猫的向量场。换言之，对指令的遵循不够强。

## classifier guidance

我们进行一些数学推导。

$p_t(x\mid y)=\dfrac{p_t(x)p_t(y\mid x)}{p_t(y)}$，两边取对数，再对 $x$ 求梯度。

$\nabla\log p_t(x\mid y)=\nabla\log p_t(x)+\nabla\log p_t(y\mid x)$。

不过我们还是不太习惯 score function 的形式。但因为 $u_t^{target}(x\mid y)=a_t\nabla\log p_t(x\mid y)+b_tx$，所以上式可以变换为

$u_t^{target}(x\mid y)=u_t^{target}(x)+a_t\nabla p_t(y\mid x)$。

观察这个式子，右侧第一项是无条件的 case，第二项要求我们训练一个 classifier 来判断某个图片 $x$ 可以属于 prompt $y$ 的概率。

我们之前不是对 prompt 遵循不够强吗，那么我们干脆就把 prompt 部分的系数提高，乘一个 $w\ge 1$。

$\tilde u_t(x\mid y)=u_t^{target}(x)+wa_t\nabla\log p_t(y\mid x)$

实践表明，这确实解决了问题。但是从理论上讲，我们已经偏离了目标分布，而是学到了一个类似于锐化后的结果（目前还没有公式能表示我们到底学到什么分布）。也就是说，这是一个很好的启发式方法。

## classifier-free guidance

上面方法的唯一问题是，训练一个 classifier 很麻烦。所以我们想能不能去掉它。

事实上

$$
\begin{aligned}
\tilde u_t(x\mid y)&=u_t^{target}(x)+wa_t\nabla\log p_t(y\mid x)\\
&=u_t^{target}(x)+wa_t(\nabla\log p_t(x\mid y)-\nabla\log p_t(x))\\
&=(1-w)u_t^{target}(x)+wu_t^{target}(x\mid y)\\
&=(1-w)u_t^{target}(x\mid\varnothing)+wu_t^{target}(x\mid y)
\end{aligned}
$$
这里我们使用了一个特殊的 prompt $\varnothing$ 来表示不提供任何 guidance。训练时可以通过按照一定的概率 $p$ 把采样出的 $(x,y)\sim p_{data}$ 中 $y$ 替换为 $\varnothing$ 来训练。

这样我们只用训练一个模型就好了，只不过需要两次 call 罢了。

但是这里还遗留下一个问题：对于那些模型从来没见过的 prompt（比如 穿宇航服的猫），模型是如何学会泛化的？毕竟关于不同的 $y$ 我们的训练没有提任何要求。
