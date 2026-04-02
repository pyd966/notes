## Binary number representation

只是简单介绍了一下进制的知识。
## Representation of numeric data

### Representation of integers

sign-and-magnitude, 1's complement, 2's complement, 2's biased notation
### Expanding & Truncating

#### Sign Extension

符号扩展。补符号位。
### Truncating

一般是直接截断，重新理解。i

## Floating Point

![[Pasted image 20260330142255.png]]

![[Pasted image 20260330142634.png]]

![[Pasted image 20260330142627.png]]

![[Pasted image 20260401173341.png]]

![[Pasted image 20260401173407.png]]

![[Pasted image 20260401173419.png]]

![[Pasted image 20260401201203.png]]

![[Pasted image 20260401173439.png]]

![[Pasted image 20260401173456.png]]

![[Pasted image 20260401173508.png]]

![[Pasted image 20260401173539.png]]

### computation

先往大的对齐，算精确结果，然后规则化，然后舍入，也许还要再规则化一下。

![[Pasted image 20260401173704.png]]

![[Pasted image 20260401174044.png]]

注意结合律不成立，但是交换律成立

## BCD

![[Pasted image 20260401174717.png]]
8421 5421 2421

Excess3 就是 8421 加3，好处是两个数相加时产生正确的进位，不过当前位还要修正

Gray 码有很多，特点是相邻只有 1 个 bit 不同

## Non-numeric data

![[Pasted image 20260401175438.png]]

![[Pasted image 20260401175651.png]]