
## score function

我们定义 (conditional) score 是 probability path 取 log 后的梯度，也就是 $\nabla\log p_t(x\mid z)$。通过计算可以发现在 Gaussian 情况下，score function 也是 $x,z$ 的加权和。

类似地，我们可以定义 marginal score function，也就是 $\nabla\log p_t(x)$。

它们有如下的关系：$\nabla\log p_t(x)=\int\nabla\log p_t(x\mid z)\dfrac{p_t(x\mid z)p_{data}(z)}{p_t(x)}dz$

这里要注意，score function 与 vector field 是不一样的。score function 更短视一些，只是一味地走向周围的局部概率最大的位置。而 vector field 会从整体考虑，让最后形成的概率分布与要求的一致。

然而它们也有联系。比如上文提到，score function 是 $x,z$ 的加权和，并且 vector field 也是 $x,z$ 的加权和。通过简单的代数运算，我们知道 $u_t^{target}(x\mid z)=a_t\nabla\log p_t(x\mid z)+b_tx$，其中 $a_t=(\beta_t^2\dfrac{\dot\alpha_t}{\alpha_t}),b_t=\dfrac{\dot\alpha_t}{\alpha_t}$。

并且我们发现两个 score function 之间的关系，跟两个 vector field 之间的关系非常像。所以我们猜测 $u_t^{target}(x)=a_t\nabla\log p_t(x)+b_tx$，这个猜测事实上也是正确的。

上面其实就是在说，在 Gaussian setting 下，score function 和 vector field 没有本质区别。所以在 diffusion model 中我们讨论更多的其实是 score function。

## score matching

想必读者不会对 score matching 跟 flow matching 非常相似感到惊讶。

我们 score matching loss 定义为 $L_{SM}(\theta)=E_{t\sim Unif,z\sim p_{data},x\sim p_t(x\mid z)}||s_t^\theta(x)-\nabla p_t(x)||^2$，而 conditional score matching loss （也叫做 denoising score matching loss） 定义为 $L_{DSM}(\theta)=E_{t\sim Unif,z\sim p_{data},x\sim p_t(x\mid z)}||s_t^\theta(x)-\nabla p_t(x\mid z)||^2$。同样我们可以证明它们只差一个常数。

用来训练和推理的算法都是一样的。

## SDEs

我们假装自己已经有了一个如上述训练的 ODE，现在我们的目标是把它变成一个 SDE（为什么要这么做？）

换句话说，我们已知当 $X_0\sim p_{init}$，并且 $\dfrac{d}{dt}X_t=u_t(X_t)$ 时会有 $X_t\sim p_t$，我们希望找到一个 SDE 也服从这个概率分布 $p_t$。

我们断言，$X_0\sim p_{init},\dfrac{d}{dt}X_t=[u_t(X_t)+\dfrac{\sigma_t^2}{2}\nabla\log p_t(X_t)]dt+\sigma_tdW_t$，那么 $X_t\sim p_t$。

证明需要用到 Fokker-Planck Equation，不展开。

![[Pasted image 20260731210046.png]]

知道这个之后，对于 Gaussian setting，我们有 

![[Pasted image 20260731210147.png]]

也就是说只要知道 score function 或者 vector field 就行了，实践中一般用 score function。

那么为什么我们要把好好的 ODE 变成 SDE 呢？理论上来说，它们都会采样到完全一样的概率分布（当然，实际走的路径会有不同）。

因为实践中，我们不会完全符合理论。比如训练时和推理时产生的精度误差等等，都会导致 SDE 更好一些。而且 SDE 事实上提供了更多的 design space，毕竟 $\sigma_t$ 是我们自己选的。

也就是说，一旦我们训练出一个 ODE，就可以完全无痛地通过调整 $\sigma_t$ 得到一族 SDE 模型，并且获得更好的数值稳定性（或者叫鲁棒性？）。