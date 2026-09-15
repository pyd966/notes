
这一讲我们进入具体的工程落地细节。也就是说，我们开始接触模型是如何建模 $u_t^{\theta}(x)$ 的。

## latent space

当你开始实现一个 diffusion model 的时候，遇到的第一个问题就是，我们的 image space 实在是太大了。一张图片有很多像素（真的很多），每个像素有三个通道，这是一个非常非常高维的空间 $R^d$。而我们要训练的模型是一个 $t\times R^d\to R^d$ 的函数，这实在是非常难学，而且很容易欠拟合。

但是为什么以前的模型，比如 classifier，没有遇到这个问题呢？因为它们是 $R^d\to S$，其中 $S$ 是一个类别的有限集合，这个难度要低不少。

### standard autoencoder

回到正题。我们可以发现，image 对象有很大的 redundancy。也就是说相邻像素有很高的相似度和关联性，这意味着 image 对象是 image space 的低维流形，我们可以尝试把它们压缩到低维空间。当然人为压缩是不可能的，我们根本不了解它的结构。所以我们训练一个模型来做到这一点。这个模型就叫 autoencoder，这其实是两个联合训练的模型，一个负责 encode（$\mu_{\phi}:R^d\to R^k$），一个负责 decode（$\mu_{\theta}:R^k\to R^d$）。

对于一个 autoencoder，最重要的就是 reconstruction。我们希望 $\mu_\theta(\mu_\phi(x))$ 得到的结果跟 $x$ 差别尽量小。所以我们有 reconstruction loss

$$
L_{recon}(\phi,\theta)=E_{x\sim p_{data}}[||\mu_\theta(\mu_\phi(x))-x||^2]
$$
非常好理解。那么是不是大功告成了呢？

并非如此。因为我们没有对 $p_{data}$ 通过 encoder 压缩后得到的分布 $p_{latent}$ 进行任何限制，因此我们只能保证它能 reconstruct，但它可能非常丑，极其扭曲，非常不利于后续 diffusion 的训练。

### VAE

那咋办？加一个惩罚项就好了。这就是 Variational Autoencoder (VAE) 的思路。

首先，VAE 是非确定性算法。它的 encoder 和 decoder 给出的是一个分布而非确定的结果。换言之，
$$
q_\phi(x)=N(\mu_\phi(x),\sigma_\phi^2(x)),\ p_\theta(z)=N(\mu_\theta(z),\sigma_\theta^2(z))
$$
我们在 encode 和 decode 的时候都是在这个概率分布中采样。

然后我们可以用概率的语言重写 reconstruction loss，其实就是负对数似然。
$$
\begin{aligned}
L_{VAE-rec}(\phi,\theta)&=E_{x\sim p_{data},z\sim q_\phi(x)}[-\log p_\theta(x\mid z)]\\
&=E_{x\sim p_{data},z\sim q_\phi(x)}[\dfrac1{2\sigma_\theta^2(z)}||x-\mu_\theta(z)||^2+\dfrac d2\log\sigma_\theta^2(z)]+C
\end{aligned}
$$
你可以把第一项理解为惩罚均值的偏差，第二项理解为 decoder confidence。

之后我们想一下怎么描述我们希望最后的分布长得好看。最好看的分布是高斯，所以我们用 KL 散度衡量它们之间的距离就好了。这一项叫 prior loss。
$$
\begin{aligned}
L_{VAE-prior}(\phi)&=E_{x\sim p_{data}(x)}[D_{KL}(q_\phi(x)|| N(0,I))]\\
&=E[\dfrac12 f(\sigma_\phi^2(x))+\dfrac12||\mu_\phi(x)||^2]
\end{aligned}
$$
其中，$f(x)=x-\ln x-1$。这个很好理解，第一项在惩罚 $\sigma\neq1$，第二项在惩罚 $\mu\neq0$。

最终真的 loss 就是把两项加权加起来就好了。不过这里有一个小细节：我们当前是没办法训练的，$L_{VAE-rec}$ 无法对 $\phi$ 求偏导，因为我们的采样 $z\sim q_\phi(x)$ 与 $\phi$ 有关。

可以用一个 trick。因为 $q_\phi(x)=N(\mu_\phi(x),\sigma^2_\phi(x))$，我们可以这样采样：先 $\epsilon\sim N(0,I)$，然后 $z=\mu_\phi(x)+\sigma_\phi(x)\epsilon$。这样就没问题了。
$$
L_{VAE}(\phi,\theta)=E_{x\sim p_data,\epsilon\sim N(0,I)}[\dfrac1{2\sigma_\theta^2(z)}||x-\mu_\theta(\mu_\phi(x)+\sigma_\phi(x)\epsilon))||^2+\dfrac d2\log\sigma_\theta^2(z)+\dfrac\beta2f(\sigma_\phi^2(x))+\dfrac\beta2||\mu_\phi(x)||^2]
$$
一般来说，$\beta<<1$。这里还有一些工程细节，比如通常训练时先把 $\beta\leftarrow0$，然后慢慢变大（warmup）；比如 $\sigma_\theta(z)$ 其实被设计为与 $z$ 无关的一个数 $\sigma_\theta$，甚至于就是一个常数 $\sigma$；比如这样训练出来容易图片过于 smooth（毕竟我们在拟合高斯），所以加一个 perceptual loss，额外训练一个模型计算语义和特征上的损失；也可以用 GAN 方法训练，代价是训练过程更不稳定且复杂。

## 模型架构

我们的模型严格来说是 $u_t^\theta(x\mid y)$，接受输入 $x\in R^k,y\in Y,t\in[0,1]$，输出 $R^k$ 中的一个向量。

我们先编码输入的 $t,y$。对于 $t$，我们会把它从标量变成一个高维向量：
$$
TimeEmb(t)=\sqrt{\dfrac2d}[\cos(2\pi\omega_1t),\dots,\cos(2\pi\omega_{d/2}t),\sin(2\pi\omega_1t),\dots,\sin(2\pi\omega_{d/2}t)]^T
$$
这里频率地选择一般按照 $\omega_i=\omega_{min}(\dfrac{\omega_{max}}{\omega_{min}})^{\dfrac{i-1}{d/2-1}}$ 来。

这个编码方式是很有道理的，本质上有点像傅里叶变换。我们只要接一个 MLP 模型就能很轻松地学会捕捉不同时间点，也能学会根据时间来调制一些参数。

对于 $y$ 的编码。如果 $y$ 是从有限的 class 中选择的，那么通常可以跟 diffusion model 一起训练。如果 $y$ 是一段文本，那么这样做会比较困难。通常而言我们会选择另一个 pretrained model 来做这个 embedding 工作。比如 CLIP 会把 prompt 编码成一个高维向量。如果信息更多的话，一个向量可能无法表达，这时可以编码成一个向量序列。

对于 $x$，我们先做 vae，再做 patchify，变成一个 1D token 序列。

然后就是经典的 attn。我们先过 self-attn，再过 cross-attn，再过 FFN 就好了，这个过程中用 t 来控制合并时 scale 的参数等等。

## 疑问

Q：为什么 vae 要是非确定性的？毕竟我们只是想加一个惩罚项，那么我直接计算 $p_{latent}$ 和 $N(0,I)$ 的 KL 散度不就好了？是不是数学上难以计算？能不能做一些推导？

A：好像确实是有确定性的 vae，似乎叫 Adversarial Autoencoder、Wasserstein Autoencoder。不过不确定性有一个好处：它相当于增加了一点噪声与正则化，让落在数据点周围的都能被正确 decode。

Q：为什么 vae 要单独训练？既然 vae 与之后的 diffusion 关系这么大，为什么不一起训练，然后直接用 diffusion 的 loss 来作为整体 loss 进行优化？这样 vae 应该会学会跟 diffusion 一起协同工作。

A：不行。有多方面原因。首先，你的 diffusion 会希望 vae 直接把所有 data 都映射到全零，这样它直接就不用学了；而 vae 希望保留重建能力。这就需要通过超参数调整 loss 中各项占比，训练非常不稳定。此外，参数量太大了。然后，如果 vae 不实现固定，那么 diffusion 相当于在追一个乱动的靶子，这样学习效率会低（但是其实也不是不能学，毕竟深度学习中多层神经网络也有这个问题）。

Q：KL 散度到底是什么？

Q：为什么不能省略 patchify，用一个大力 vae 替代掉？

Q：时间 $t$ 似乎只作为生成 scale 和 bias 用，这样表达能力真的够吗？