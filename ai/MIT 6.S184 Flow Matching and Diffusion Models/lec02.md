
在这一节中，我们将解决上一节遗留下来的问题：到底如何找到一组参数 $\theta$ 使得我们可以从 $p_{init}\to p_{data}$。

## probability path

在正式解决这个问题之前，我们需要定义一些概念作为辅助。或者换句话说，因为 $\theta$ 本身还跟网络结构有关，而我们目前只知道 $p_{init},p_{data}$，我们还不知道中间的过程。所以我们暂且抛开网络结构，研究一下怎么把中间过程表示出来。

这个中间过程就是 probability path。

我们先定义 conditional probability path，这是对 $p_{data}$ 中的一个数据点 $z$ 来定义的。

conditional probability path 是一个函数 $p_t(x\mid z)$，要求 $p_t(\cdot\mid z)$ 是一个概率分布，并且 $p_0(\cdot\mid z)=p_{init}$（与 $z$ 无关），$p_1(\cdot\mid z)=\delta_z$（关于 $z$ 的单点分布）。

其实就是把“中间过程”形式化定义了出来。问题是这里的“中间过程”有无穷种，所以具体要选哪种中间过程作为我们网络拟合的目标就成了一个 design choice。通常而言我们选择 Gaussian conditional probability path，也就是 $p_t(\cdot\mid z)=N(\alpha_t z,\beta_t^2I_d)$，其中 $\alpha_0=\beta_1=0,\alpha_1=\beta_0=1$，这里 $\alpha_t,\beta_t$ 也是 design choice。

扩展一下，变成对于 $p_{data}$ 定义，就得到了 marginal probability path.

是一个概率分布 $p_t(x)$，满足如下条件：采样 $z\sim p_{data}$，采样 $x\sim p_t(\cdot\mid z)$，那么 $x\sim p_t$。

如何得到 $p_t(x)$？事实上 $p_t(x)=\int p_t(x\mid z)p_{data}(z)dz$。这里有点奇怪，因为我们不知道 $p_{data}$。但是我们知道其中的采样值。

以上介绍的其实就是一个人为设计的插值过程。

## vector field

现在我们完全了解中间过程了，但问题是，我们的神经网络拟合的是向量场。所以下一步我们要先把向量场表示出来，再谈论参数 $\theta$ 的训练问题。

还是老一套。

conditional vector field 就是向量场 $u_t(\cdot\mid z)\in R^d$，满足采样 $x_0\sim p_{init}$，演化 $dx_t=u_t(x_t\mid z)dt$，时刻满足 $x_t\sim p_t(\cdot\mid z)$。

对于高斯分布来说这里有一个简单的公式：

![[Pasted image 20260726105545.png]]

公式不用记，只需要知道它是 $x,z$ 的加权平均就行了。换句话说，这个向量场就是直接指向 z 的方向。

同样地，有 marginal vector field.

$u_t(x)=\int u_t(x\mid z)\dfrac{p_t(x\mid z)p_{data}(z)}{p_t(x)}dz$，我们断言跟着它对应的 ODE 演化的 $x_t$ 满足 $x_t\sim p_t$。

问题是，为什么系数长成这个贝叶斯公式的样子（其实这里就是贝叶斯公式），为什么可以用这种加权平均的方式就能得到最终的向量场？按理说向量场应该挺复杂的，不像我们之前那个 probability path 一样可以直接简单加权求和。

关于第一个问题，从直觉上理解，这里其实就是用从当前 $x$ 出发，最终停在各个 $z$ 的概率来加权，是挺符合是觉得。关于第二个问题，我不知道如何从直觉上理解，不过我们可以验证确实是正确的。

这里验证部分要使用到一个数学工具，continuity equation。简单来说，如果有 $x_0\sim p_{init},\dfrac{d}{dt}x_t=u_t(x_t)$，那么 $x_t\sim p_t\iff \dfrac{d}{dt}p_t(x)=-\text{div}(p_tu_t)(x)$

现在我们找到向量场了。问题是，我们该如何学到这个向量场？尤其是在我们不知道 $p_{data}$ 的情况下（这意味着我们无法利用上面的公式直接写出 $u_t(x)$！）

## Flow Matching

训练算法叫做 Flow Matching。

显而易见地，我们可以设计出如下 loss (flow matching loss)：

$$
\begin{aligned}
L_{FM}(\theta)&=E_{t\sim Unif,x\sim p_t}[||u_t^\theta(x)-u_t^{target}(x)||^2]\\
&=E_{t\sim Unif,z\sim p_{data},x\sim p_t(\cdot\mid z)}[||u_t^\theta(x)-u_t^{target}(x)||^2]
\end{aligned}
$$
非常显然，如果我们能找到使这个 loss 最小的 $\theta$，那么我们就已经完成目标了。

但是问题是，这个 loss 是无法计算的，因为 $u_t^{target}$ 是无法计算的。

那么我们退一步，看看我们能用 conditional vector field 最好做到多好。

$$
L_{CFM}(\theta)=E_{t\sim Unif,z\sim p_{data},x\sim p_t(\cdot\mid z)}[||u_t^\theta(x)-u_t^{target}(x\mid z)||^2]
$$
这个 loss 是可以计算的，唯一的问题是，我们不知道它的最小值点算出来是不是我们想要的。

幸运的是，它们是一样的。有一个定理表明 $L_{FM}(\theta)=L_{CFM}(\theta)+C$，其中 $C$ 是常数。

![[Pasted image 20260728095011.png]]

推导之后，对于 Gaussian 而言可以得到上述公式。这其实就是在说，我们的训练过程，就是你选定一个 data point，然后对它进行加噪，拿加噪后的点对应的 vector 去跟我们已知的 velocity 作差取平方。这非常符合直觉。