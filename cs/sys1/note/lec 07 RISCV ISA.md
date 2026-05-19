![[Pasted image 20260511162717.png]]

![[Pasted image 20260511162728.png]]

![[Pasted image 20260513200034.png]]

![[Pasted image 20260513200430.png]]

![[Pasted image 20260513201700.png]]

注意这里的 load 非常奇怪，如果真的想 load 一个 32 位进去的话，需要一次 lui 和一次 addi

![[Pasted image 20260513202007.png]]

![[Pasted image 20260513202146.png]]

![[Pasted image 20260513202402.png]]

![[Pasted image 20260513202514.png]]

![[Pasted image 20260513202527.png]]

![[Pasted image 20260513202736.png]]

![[Pasted image 20260513203101.png]]

![[Pasted image 20260513203619.png]]

![[Pasted image 20260513204007.png]]

![[Pasted image 20260518143055.png]]

RISC-V 没有对齐。

![[Pasted image 20260518143756.png]]

![[Pasted image 20260518143950.png]]

但是 addi 是符号位扩展，所以建议使用 addui。

或者也可以看一下你低位到底会不会符号扩展成负数，如果会的话在 lui 的时候多加 1 就行了。

![[Pasted image 20260518144845.png]]

![[Pasted image 20260518145136.png]]

![[Pasted image 20260518145544.png]]

![[Pasted image 20260518145841.png]]

![[Pasted image 20260518150234.png]]