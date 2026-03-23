## Addition

### Ripple-carry 

![[Pasted image 20260323144934.png]]

### Carry Lookahead Adder

![[Pasted image 20260323145109.png]]

![[Pasted image 20260323150106.png]]

这样展开之后，都变成了二级电路，理论上延迟是常数。

但是随着 $n$ 扩大，单个门的 fan-in 太大，也很不对。这时可以采用分组的办法，可以使用类似于线段树的结构。但是实际上不是这么操作的。

![[Pasted image 20260323150632.png]]
![[Pasted image 20260323152238.png]]

## Carry skip adder

![[Pasted image 20260323152405.png]]

如果某一组内传播条件均满足，那么这一组最终的进位可以直接设置成输入的进位。

只能优化常数。

### Carry select adder

![[Pasted image 20260323152912.png]]

分组，进位是 0/1 都算一遍，然后选一个正确的。两层可以做到 $O(\sqrt{n})$，多层可以做到 log。

### Prefix Adder

省流：线段树。



