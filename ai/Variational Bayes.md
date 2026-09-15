## Background

在机器学习中，我们常常碰到这样的问题：给你一些 $(x,z)$，其中 $x$ 可能是某些数据，而 $z$ 是与 $x$ 有关的某些量（比如，一张图片与其所属的标签），你的目标是训练一个模型，可以根据 $x$ 推断出 $z$，或者根据 $z$ 生成 $x$。

这问题并不困难。我们只要建立一个模型 $p_\theta(z|x)$，然后找到 $\theta^*=\arg\max_\theta\sum\limits_{i=1}^n\log p_\theta(z_i|x_i)$ 即可。类似地，我们也可以建立模型 $q_\phi(x|z)$，甚至于我们可以直接学习联合关系 $r_\alpha(x,z)$。

这些问题简单，是因为它们是 监督学习 问题，我们事先知道每个 $x$ 对应的 $z$。

然而在一些更困难的问题中，我们可能无法观测到 $z$ 这个 hidden variable。比如说我们有一堆二维点 $x_i$，我们怀疑这些点是从三个高斯分布采样的，想要判断出每个点属于哪个高斯分布 $z_i$，以及对应高斯分布的参数；再比如说，VAE，我们要把一些高维图像 $x_i$ 压缩到低维 $z_i$，但是我们并不知道每个图像压缩之后是什么样子。

variational bayes 就是在这类问题中使用的。或者更具体来说，它是把 statistical inference 问题变成 optimization 问题。

variational bayes 是一族方法，我们这里只介绍其中最简单的一种，被称作 Mean-Field Approximation。

## Formulation

我们形式化地看一下它到底解决什么问题。

首先，我们先验地相信，数据 $x$ 生成的过程，其实是背后由一个变量 $z$ 主导的，其中 $z\sim p(z)$，然后 $x\sim p(x|z)$。

我们假设我们已经知道 $p(z),p(x|z)$，我们想要做的是计算 $p(z|x)$。虽然计算公式存在，这是很难做到的。

具体来说，因为 $p(z|x)=\dfrac{p(x,z)}{p(x)}=\dfrac{p(z)p(x|z)}{p(x)}$，而 $p(x)=\int p(z)p(x|z)dz$，因为 $z$ 是连续的，所以这个积分很难计算，导致分母 $p(x)$ 未知。

## Solution

那咋办？我们用另一个模型 $q_\phi(z|x)$ 尝试去近似 $p(z|x)$ 就好了。

考虑 loss function，我们要衡量 $q$ 去近似 $p$ 的效果，那么我们选用反向 KL 散度。

$$
\begin{aligned}
KL(q||p)&=\int q_\phi(z|x)\log\dfrac{q_\phi(z|x)}{p(z|x)}dz\\
&=\int q_\phi(z|x)\log\dfrac{q_\phi(z|x)p(x)}{p(x,z)}dz\\
&=\int q_\phi(z|x)\log p(x)dz+\int q_\phi(z|x)\log\dfrac{q_\phi(z|x)}{p(x,z)}dz\\
&=\log p(x)\int q_\phi(z|x)dz+\int q_\phi(z|x)\log\dfrac{q_\phi(z|x)}{p(x|z)p(z)}dz\\
&=\log p(x)+\int q_\phi(z|x)\log\dfrac{q_\phi(z|x)}{p(z)}dz-\int q_\phi(z|x)\log p(x|z)dz\\
&=\log p(x)+KL(q_\phi(z|x)||p(z))-E_{q_\phi(z|x)}[\log p(x|z)]
\end{aligned}
$$
其中第一项是常数，第二项衡量的是我们的 $x\rightarrow z$ 得到的分布有多么接近 $p(z)$，第三项衡量的其实是重建 loss，也就是我们先 $z\sim q_\phi(z|x)$，然后看一下真实的 $x$ 的概率在这个 $z$ 的视角下到底有多大 $p(x|z)$。并且忽略掉第一项，剩下的都是我们可以计算的。

（这里我们其实就是在隐式使用 bayes 公式，这大概就是为什么名字里有 bayes）

因为 $\log p(x)-KL(q||p)=E_q[\log p(x|z)]-KL(q_\phi(z|x)||p(z))$，我们的目标是最小化 $KL(q||p)$，也就是最大化 $\log p(x)-KL(q||p)$，也就是最大化 $E_q[\log p(x|z)]-KL(q_\phi(z|x)||p(z))$。我们把最后这个叫做 $ELBO$。

$ELBO$ 有一个有趣的性质：$\log p(x)\ge ELBO$，也就是说随着我们最大化  $ELBO$，我们也在最大化 $\log p(x)$ 的下界（尽管精确值难以计算）。

## Why Reverse KL?

理论上，确实正向 KL 更自然一些，因为它衡量的是以 $p$ 为基准，去算如果用 $q$ 来衡量 $p$ 会额外浪费多少 bit。然而，正向 KL 推导的结果是无法计算的。

$$
\begin{aligned}
KL(p||q)&=\int p(z|x)\log\dfrac{p(z|x)}{q_\phi(z|x)}dz\\
&=-\int p(z|x)\log p(x)dz+\int p(z|x)\log\dfrac{p(x,z)}{q_\phi(z|x)}dz\\
&=-\log p(x)+\int\dfrac{p(z)p(x|z)}{p(x)}\log\dfrac{p(z)p(x|z)}{q_\phi(z|x)}dz\\
\end{aligned}
$$

然后你会发现这里多出一个 $p(x)$ 是我们无法处理的，并且后面也没法把它跟别人合并。

此外，reverse KL 跟 forward KL 还有一个微妙的区别。Reverse KL 是“零强制”，也就是如果 $p=0$ 那么 $q=0$；而 forward KL 是反过来，如果 $p\neq0$ 那么 $q\neq0$。

然而这不是我们选用 reverse KL 的原因。最本质原因还是因为用 forward 算不了。

## VAE

VAE 的推导过程没有区别。

只不过我还是更喜欢推导之后结果的另一种直观理解方式。也就是说第一项是衡量 reconstruction loss，第二项衡量我们的分布到底好不好看。

## Reference

1. [Eric Jang: A Beginner's Guide to Variational Methods: Mean-Field Approximation](https://blog.evjang.com/2016/08/variational-bayes.html)
2. [A Quick Primer on KL Divergence](https://adamlineberry.io/vae-series/kl-divergence/)
3. [From Autoencoder to Beta-VAE](https://lilianweng.github.io/posts/2018-08-12-vae/)
