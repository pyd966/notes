
光学理论知识是不够的，我们来看看工程侧该如何实现，有什么需要注意的点。这里我们以用 pytorch 实现的 gpt-2 为例，这是一个最经典的 transformer-based LLM，它的位置编码没有使用 RoPE，而是直接学一个位置嵌入加到词嵌入中。因为它用的位置嵌入跟 token 在上下文窗口中的相对位置有关，这就导致 kv cache 不适用。

## core

为了清楚地看到工程侧在主线之外进行了哪些配套服务，我们先讲一下主线部分包含的内容。

主线部分就是输入 tokenized $[B,T]$，输出 $[B,T,C]$ 的 logits，表示预测下一个位置的概率。

很明显，为了跑通全流程，我们还需要在前后做一些处理。

## pipeline

在进入 core 前，应该通过 tokenizer。这里直接使用 tiktoken。

在离开 core 后，为了正常进行训练，还需要计算 loss。

为了进行采样，我们需要对 logits 进行后处理。先通过 softmax 变成概率，然后从中采样。

## dataloader

我们使用的 dataset 是很大的，为了方便调整遍历策略，我们专门设置一个 dataloader 负责这件事。

像这里，我们使用的遍历策略就是，从头读按顺序读到尾，不过为了让每个 token 在上下文窗口中的不同位置都出现过，我们会随机一个值，作为开头位置的偏移。

## eval

现在，我们可以进行完整的训练了，但对训练的成果仍一无所知。这是很糟糕的，我们无法得知自己是否偏离路径。

我们从 dataset 中切分出 validation set。每隔若干 train step，我们进行一次 eval，用 validation set 计算一遍 loss。

然而只有 loss 只能说明模型对 dataset 拟合较好，不能说明模型的智能程度。

因此，我们使用 benchmark 对模型能力进行评测。这里使用的是 fineweb，给出题干，它要求模型从四个选项中选出最可能发生的后续事情。我们依次把题干和四个选项拼起来，看谁的 loss 最低，就说明模型选择了哪个选项。随后计算 accuracy，来衡量模型的能力。

## stability & initialization

kaiming initialization。

以及 weight decay（本质上就是 L2 正则化），以及随时间变化的 learning rate。

都是为了泛化，以及训练的稳定性。

## efficiency

重头戏。

首先，gpt-2 官方的 batch 很大，而我们的显存无法承受。但是 batch size 是很重要的超参数，我们不想修改它。这时可以使用一个小技巧，用时间换空间。简单来说，你把 big batch 拆分成好几步，每步跑一个 small batch，中间不清空 grad 就行了。

显然，这会导致训练变慢。接下来我们把精力放到提速上。

首先，训练时可以使用量化策略来加速。这在 pytorch 中就是一行代码。

其次，torch 提供了 compile 函数，可以进行一些算子融合。

最后，我们可以使用多卡并行。这里使用的是 Data Parallelism，会涉及到卡间通信、同步等等问题。

## log

把一些重要的过程性内容（每轮 loss, val loss, eval score）记录到文件中。

## save

每个一定步骤保存一个 checkpoint。