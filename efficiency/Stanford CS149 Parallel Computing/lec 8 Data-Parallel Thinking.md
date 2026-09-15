
现实生活中的并行化问题一般都比较复杂，我们先研究一些常用的 primitive，搞清楚它们该如何并行化，之后就可以用这些 primitive 去拼出自己想要的功能，就算拼不出来，也可以用类似的思想并行化。

其实这个很像函数式编程语言。

## map

给一个函数 `f: a->b`，map 就是把这个函数应用到序列中的每个元素 `map: a->b -> seq a -> seq b`。

这个并行化非常好做，直接全部并行化就好了。

## fold (left)

![[Pasted image 20260903161634.png]]

这也能并行化？当然可以！

只不过我们需要额外的条件：比如函数 f 满足结合律，并且要提供一个单位元。

并行化大概就是，均分成若干 part，每个 part 内部先 sequential 做，然后再 log 规约。

## (inclusive) scan 

![[Pasted image 20260903161834.png]]

根据机器提供硬件的不同，这个有很多实现方法。

首先，最容易想到的应该是，划分成几个部分，每个部分内部先做 scan，做完之后得到 partial sum，对这个 partial sum 形成的新 sequence 再做 scan，然后并行地加上去。

如果把 $n$ 个元素分成 $p$ 个部分，那么总计算量是 $2n+p$，总 span 是 $n/p+p+n/p$。

另一个方案是，我们直接进行 log 轮，每一轮所有元素都往前扩张一倍。

![[Pasted image 20260903162417.png]]

如果有无穷多个 processor，总计算量是 $n\log n$，总 span 是 $\log n$。虽然产生了更高的计算量，但是总 span 仍然很低。

第三个方案是，类似于树状数组。

![[Pasted image 20260903162754.png]]

我们先正着加一遍把树状数组建立起来，然后再倒着加一遍做回来。

好处是总计算量大概是 $2n$，总 span 也是 $2\log n$。坏处是常数大一些，而且 locality 很差。

最后我们的实现采用方案一和二混合起来，有很多层。

最底层，对于 intra-warp 我们采用方案二，这样可以解决 32 长度的问题。

对于 intra-block 我们采用方案一，这样可以解决 1024 长度的问题。

对于 inter-kernel，我们仍然采用方案一，不过这次发射三个 kernel 来解决。

## segmented scan

给你一个由序列组成的序列，你要对每个序列都 perform scan。

当然你可以直接 map，但是这样并行度不够高。

我最开始的想法是，先把所有序列拼到一起做 scan，然后减掉该减的数。

事实上还有更好的做法。简单来说就是用 flag 标识分界线，我们仍然跑正常的 scan 算法，但是所有跨过分界线的 add 都不做。

![[Pasted image 20260903164358.png]]

我没有完全搞懂细节，但是大概就是把几个树状数组合并到一起来做。

## sparse matrix multiplication

这个是矩阵乘向量。

我们用 $vals, cols$ 的方式存储 sparse matrix，然后做一个点乘，之后 segmented scan，然后 scatter 到对应的位置就好了。

不过很多时候我们没有 scatter，只有 gather，该咋办。

如果 scatter 是一个 permutation，那么可以用 sort。

如果有重复元素，那么我们可以先 sort 再 segmented scan。