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

## Multiplication

### Implementation 1

列竖式转化成加法，采用循环做法，同时压缩一下空间。

![[Pasted image 20260330135703.png]]

关于符号：你可以直接进行符号位扩展，算出来就是对的。也可以把最高位的 sign bit 当成是减法。

### Implementation 2 Booth's Algorithm

加速一下，连续的 1 可以只用一次加法一次减法。

![[Pasted image 20260330135855.png]]

这里为了压缩空间也是放到一起存了。有一点小细节自己想一下。

### Implementation 3 Array Multiplier

![[Pasted image 20260330135932.png]]

不言而喻一目了然。

### Implementation 4

![[Pasted image 20260330140026.png]]

## Division

### Implementation 1

依旧列竖式。

![[Pasted image 20260330140438.png]]

![[Pasted image 20260330140446.png]]

依然可以省一波空间。

![[Pasted image 20260330141053.png]]

![[Pasted image 20260330141109.png]]

![[Pasted image 20260330141223.png]]

### Implementation 2

可以略去恢复步骤。

![[Pasted image 20260330141259.png]]

![[Pasted image 20260330141321.png]]

对于有符号数，转化成无符号数考虑就行了。

对于符号，商的符号是两个参与运算的数的符号的异或，余数的符号是被除数的符号。

## Floating point addition

![[Pasted image 20260401180057.png]]

![[Pasted image 20260401180111.png]]

## Floating point multiplication

![[Pasted image 20260401180737.png]]

![[Pasted image 20260401180750.png]]

![[Pasted image 20260401181027.png]]