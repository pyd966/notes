RISC-V:

1. 各个寄存器的用途、别名，是 caller 还是 callee
2. RV32I & RV64I 的所有指令，它们的汇编格式、作用、以及它们翻译成机器码的格式。其中它们如何处理立即数（比如是否进行符号扩展，填充到立即数的哪些位）也是重要的、哪些 R64I 跟 R32I 表现不同的也是重要的。以及六种大类的指令的指令格式，以及每条指令归属哪个大类。
3. 其他易错事项。

![image-20260615085920042](C:\Users\24053\AppData\Roaming\Typora\typora-user-images\image-20260615085920042.png)

![image-20260615090050697](C:\Users\24053\AppData\Roaming\Typora\typora-user-images\image-20260615090050697.png)

![image-20260615090237416](C:\Users\24053\AppData\Roaming\Typora\typora-user-images\image-20260615090237416.png)

## CPU

1. 我们这一版 CPU 设计的所有 control signal，它们的不同值代表什么？

2. 我们这一版 CPU 都由哪些组件构成，怎么连接的？![image-20260615091649316](C:\Users\24053\AppData\Roaming\Typora\typora-user-images\image-20260615091649316.png)

   ![image-20260615091924357](C:\Users\24053\AppData\Roaming\Typora\typora-user-images\image-20260615091924357.png)![image-20260615092008976](C:\Users\24053\AppData\Roaming\Typora\typora-user-images\image-20260615092008976.png)![image-20260615092207329](C:\Users\24053\AppData\Roaming\Typora\typora-user-images\image-20260615092207329.png)