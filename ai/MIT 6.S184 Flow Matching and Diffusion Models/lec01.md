## Sec 01

这门课的目标是，构建一个生成式人工智能，并掌握背后的底层数学理论。为此，我们需要先严格定义生成。

生成分成有条件的跟无条件的。对于无条件生成而言，就是对一个概率函数进行采样。对于有条件生成而言就是条件概率。

生成式人工智能，就是从给定的分布（比如高斯分布）开始，一步步调整到目标分布的算法。

问题：1. 如果我不从给定的分布开始呢？ 2. 为什么一定要有一个初始分布，不能一步直接生成？

第一个问题，如果模型被训练为从高斯噪声生成狗图，你却喂了一张猫图，那么无法得到正常结果。从理论上分析是因为微分方程的初始条件是要有限制的，从直观感受是模型学到的知识集中在高斯噪声的流形到狗的流形的路径上，而一张猫图不在这上面，模型会随便外推生成奇怪的结果。

第二个问题，理论上当然可以，实际上根本算不了，因为这个映射的性质很病态。而分成多步，其实就是把非线性传输分解成无穷个线性变换，使得网络需要拟合的函数变得性质很好。

## Sec 02 Flow Model

一些数学概念：trajectory, vector field, ODE, flow. 以及 Euler method 用数值方法解 ODE。

并不是每个 ODE 都有唯一解，但是在 ML 的领域可以认为我们只会遇到有唯一解的情况。

那么什么是 flow model 呢？

这里我们把 neural network 建模为一个 vector field: $u^\theta_f:R^d\times[0,1]\to R^d$。flow model 的一次生成过程，就是先从初始分布进行采样 $X_0\sim p_{init}=N(0,1)$，然后按照 ODE $\dfrac{d}{dt}X_t=u_f^\theta(X_t)$ 进行演化，最终得到 $X_1$。我们希望 $X_1\sim p_{data}$。

问题是，对于任意的分布 $p_{data}$，一定存在一个 vector field 满足条件吗？

## Sec 03 Diffusion Model

仍然有之前的一些数学概念。不过新增了 diffusion coefficient, SDE 和 Brownian motion。

Brownian motion: 就是一个随机过程 $W_t\in R^d$，满足 $W_0=0$, $W_t-W_s\sim N(0,t-s)(t>s)$，并且增量是彼此独立的（对于任意的 $t_1<t_2<\dots<t_N$ 都有 $W_{t_2}-W_{t_1},\dots,W_{t_N}-W_{t_{N-1}}$ 彼此独立）。

SDE: $dX_t=u_f(X_t)dt+\sigma(t)dW_t$。

如果这行方程有点费解，我们可以重写它：

$X_{t+h}=X_t+u_f(X_t)h+\sigma(t)(W_{t+h}-W_t)+R_t(h)$，其中 $R_t(h)$ 是误差项，满足 $\lim\limits_{h\to0}\dfrac{\text{E}[||R_t(h)||^2])}{h}=0$。

可是这样的话，随着 h 的减小，随机项部分会开始占据主导。这是为什么？

同样，我们认为只会遇到有唯一解的情况。

Diffusion model 就是用 SDE 去完成从 $p_{init}\to p_{data}$ 的转变。

