# 计算机系统 I Cheat Sheet

> 面向：逻辑门/布尔代数/组合电路/时序电路/ISA/RISC-V/单周期 CPU。  
> 重点：RV32I + RV64I 基础整数指令、立即数编码、单周期 CPU 数据通路。

## 0. RISC-V 先记住这些

- RISC-V 基础指令固定 32 bit；低两位通常为 `11`。寄存器字段位置固定：`rd=inst[11:7]`，`rs1=inst[19:15]`，`rs2=inst[24:20]`。
- `x0` 永远读出 0，写入被丢弃。常用 ABI：`ra=x1`，`sp=x2`，`gp=x3`，`tp=x4`，`t0-t2=x5-x7`，`s0/fp=x8`，`s1=x9`，`a0-a7=x10-x17`，`s2-s11=x18-x27`，`t3-t6=x28-x31`。
- `rd` 写回的位宽等于 `XLEN`：RV32I 为 32 bit，RV64I 为 64 bit。
- 除特别说明外，12 bit 立即数都符号扩展；不要把 `addi/andi/ori/xori/load/store/jalr` 的立即数当无符号数。
- `SLTIU`、`SLTU`、`BLTU/BGEU` 是无符号比较，但参与比较的立即数仍先符号扩展到 `XLEN`。
- `LUI/AUIPC` 的 U-immediate 是 `sext(imm20 << 12)`。RV64 中如果 bit 31 为 1，会把 bit 63:32 扩成 1；低 12 位永远为 0。
- `JAL/JALR` 写 `PC+4` 到 `rd`；`JALR` 目标地址是 `(rs1 + sext(imm12)) & ~1`，最低位被清零。
- `BEQ/BNE/BLT/BGE/BLTU/BGEU` 不写寄存器，跳转目标是 `PC + sext(B_imm)`，不是 `PC+4+offset`。
- RISC-V 是 load-store ISA：算术/逻辑只操作寄存器；内存只通过 load/store 访问。
- RISC-V 采用小端序；多字节数的低有效字节在低地址。

## 1. 指令格式

位编号从左到右是 `31 ... 0`。

| 类型 | inst[31:25] | inst[24:20] | inst[19:15] | inst[14:12] | inst[11:7] | inst[6:0] | 用途 |
|---|---|---|---|---|---|---|---|
| R | `funct7` | `rs2` | `rs1` | `funct3` | `rd` | `opcode` | 寄存器-寄存器 ALU |
| I | `imm[11:0]` | 合在 imm 中 | `rs1` | `funct3` | `rd` | `opcode` | load、立即数 ALU、`jalr`、shift-immediate |
| S | `imm[11:5]` | `rs2` | `rs1` | `funct3` | `imm[4:0]` | `opcode` | store |
| B | `imm[12,10:5]` | `rs2` | `rs1` | `funct3` | `imm[4:1,11]` | `opcode` | conditional branch |
| U | `imm[31:12]` | 合在 imm 中 | 合在 imm 中 | 合在 imm 中 | `rd` | `opcode` | `lui`、`auipc` |
| J | `imm[20,10:1,11,19:12]` | 合在 imm 中 | 合在 imm 中 | 合在 imm 中 | `rd` | `opcode` | `jal` |

## 2. 立即数生成

`sext(x)` 表示符号扩展到 `XLEN`。B/J 的最低位硬接 0，所以跳转偏移量以 2 字节为单位编码。

| 类型 | 从指令中拼出的立即数 | 最终值 | 典型指令 | 细节 |
|---|---|---|---|---|
| I | `{inst[31:20]}` | `sext(inst[31:20])` | `addi/load/jalr` | 12 bit 有符号数；shift-immediate 例外，imm 字段拆成 `funct6/7 + shamt` |
| S | `{inst[31:25], inst[11:7]}` | `sext(...)` | `sb/sh/sw/sd` | store 地址偏移，仍是有符号数 |
| B | `{inst[31], inst[7], inst[30:25], inst[11:8], 0}` | `sext(...)` | branches | `inst[31]` 是符号位；目标 `PC + B_imm` |
| U | `{inst[31:12], 12'b0}` | `sext(inst[31:12] << 12)` | `lui/auipc` | RV64 中 bit31 会扩展到高 32 位 |
| J | `{inst[31], inst[19:12], inst[20], inst[30:21], 0}` | `sext(...)` | `jal` | 目标 `PC + J_imm` |

## 3. RV32I 完整指令表

字段写法：R 型机器码为 `funct7 rs2 rs1 funct3 rd opcode`；I 型为 `imm[11:0] rs1 funct3 rd opcode`；S/B/U/J 见上面的格式表。

### 3.1 R 型整数 ALU

| 指令 | 汇编格式 | opcode | funct3 | funct7 | 执行效果/细节 |
|---|---|---:|---:|---:|---|
| `add` | `add rd, rs1, rs2` | `0110011` | `000` | `0000000` | `rd = rs1 + rs2`，溢出忽略，取低 `XLEN` 位 |
| `sub` | `sub rd, rs1, rs2` | `0110011` | `000` | `0100000` | `rd = rs1 - rs2`，溢出忽略 |
| `sll` | `sll rd, rs1, rs2` | `0110011` | `001` | `0000000` | 逻辑左移；RV32 只用 `rs2[4:0]` 作 shamt |
| `slt` | `slt rd, rs1, rs2` | `0110011` | `010` | `0000000` | 有符号比较，真则 1，否则 0 |
| `sltu` | `sltu rd, rs1, rs2` | `0110011` | `011` | `0000000` | 无符号比较，真则 1，否则 0 |
| `xor` | `xor rd, rs1, rs2` | `0110011` | `100` | `0000000` | 按位异或 |
| `srl` | `srl rd, rs1, rs2` | `0110011` | `101` | `0000000` | 逻辑右移，左侧补 0；RV32 用 `rs2[4:0]` |
| `sra` | `sra rd, rs1, rs2` | `0110011` | `101` | `0100000` | 算术右移，左侧补符号位；RV32 用 `rs2[4:0]` |
| `or` | `or rd, rs1, rs2` | `0110011` | `110` | `0000000` | 按位或 |
| `and` | `and rd, rs1, rs2` | `0110011` | `111` | `0000000` | 按位与 |

### 3.2 I 型整数 ALU

| 指令 | 汇编格式 | opcode | funct3 | imm/funct | 执行效果/细节 |
|---|---|---:|---:|---|---|
| `addi` | `addi rd, rs1, imm12` | `0010011` | `000` | `imm[11:0]` | `rd = rs1 + sext(imm12)`；溢出忽略 |
| `slti` | `slti rd, rs1, imm12` | `0010011` | `010` | `imm[11:0]` | 有符号比较 `rs1 < sext(imm12)` |
| `sltiu` | `sltiu rd, rs1, imm12` | `0010011` | `011` | `imm[11:0]` | 无符号比较；立即数先符号扩展再按无符号解释 |
| `xori` | `xori rd, rs1, imm12` | `0010011` | `100` | `imm[11:0]` | `rd = rs1 ^ sext(imm12)`；`xori rd, rs1, -1` 可取反 |
| `ori` | `ori rd, rs1, imm12` | `0010011` | `110` | `imm[11:0]` | `rd = rs1 \| sext(imm12)` |
| `andi` | `andi rd, rs1, imm12` | `0010011` | `111` | `imm[11:0]` | `rd = rs1 & sext(imm12)` |
| `slli` | `slli rd, rs1, shamt` | `0010011` | `001` | `0000000 shamt[4:0]` | RV32 逻辑左移，shamt 5 bit |
| `srli` | `srli rd, rs1, shamt` | `0010011` | `101` | `0000000 shamt[4:0]` | RV32 逻辑右移 |
| `srai` | `srai rd, rs1, shamt` | `0010011` | `101` | `0100000 shamt[4:0]` | RV32 算术右移 |

### 3.3 Load

| 指令 | 汇编格式 | opcode | funct3 | 执行效果/细节 |
|---|---|---:|---:|---|
| `lb` | `lb rd, imm12(rs1)` | `0000011` | `000` | 从 `rs1+sext(imm12)` 读 1 字节，符号扩展到 `XLEN` |
| `lh` | `lh rd, imm12(rs1)` | `0000011` | `001` | 读 2 字节，符号扩展 |
| `lw` | `lw rd, imm12(rs1)` | `0000011` | `010` | 读 4 字节；RV32 直接写入，RV64 符号扩展到 64 bit |
| `lbu` | `lbu rd, imm12(rs1)` | `0000011` | `100` | 读 1 字节，零扩展 |
| `lhu` | `lhu rd, imm12(rs1)` | `0000011` | `101` | 读 2 字节，零扩展 |

### 3.4 Store

| 指令 | 汇编格式 | opcode | funct3 | 执行效果/细节 |
|---|---|---:|---:|---|
| `sb` | `sb rs2, imm12(rs1)` | `0100011` | `000` | 把 `rs2[7:0]` 写到内存 `rs1+sext(imm12)` |
| `sh` | `sh rs2, imm12(rs1)` | `0100011` | `001` | 写 `rs2[15:0]` |
| `sw` | `sw rs2, imm12(rs1)` | `0100011` | `010` | 写 `rs2[31:0]` |

### 3.5 Branch

| 指令 | 汇编格式 | opcode | funct3 | 执行效果/细节 |
|---|---|---:|---:|---|
| `beq` | `beq rs1, rs2, offset` | `1100011` | `000` | 若 `rs1 == rs2`，`PC = PC + sext(B_imm)` |
| `bne` | `bne rs1, rs2, offset` | `1100011` | `001` | 若 `rs1 != rs2` 跳转 |
| `blt` | `blt rs1, rs2, offset` | `1100011` | `100` | 有符号 `rs1 < rs2` 跳转 |
| `bge` | `bge rs1, rs2, offset` | `1100011` | `101` | 有符号 `rs1 >= rs2` 跳转 |
| `bltu` | `bltu rs1, rs2, offset` | `1100011` | `110` | 无符号 `rs1 < rs2` 跳转 |
| `bgeu` | `bgeu rs1, rs2, offset` | `1100011` | `111` | 无符号 `rs1 >= rs2` 跳转 |

### 3.6 Jump / Upper Immediate

| 指令 | 汇编格式 | 类型 | opcode | funct3 | 执行效果/细节 |
|---|---|---|---:|---:|---|
| `jal` | `jal rd, offset` | J | `1101111` | n.a. | `rd = PC+4`，`PC = PC + sext(J_imm)`；`jal x0, label` 是无链接跳转 |
| `jalr` | `jalr rd, imm12(rs1)` | I | `1100111` | `000` | `rd = PC+4`，`PC = (rs1 + sext(imm12)) & ~1` |
| `lui` | `lui rd, imm20` | U | `0110111` | n.a. | `rd = sext(imm20 << 12)`；低 12 位清 0 |
| `auipc` | `auipc rd, imm20` | U | `0010111` | n.a. | `rd = PC + sext(imm20 << 12)`；用于 PC-relative 地址 |

### 3.7 System / Fence

如果课程没考到 OS/特权级，通常只要能认出机器码和基本用途。

| 指令 | 汇编格式 | 类型 | opcode | funct3 | imm/funct | 执行效果/细节 |
|---|---|---|---:|---:|---|---|
| `fence` | `fence pred, succ` | I | `0001111` | `000` | `fm pred succ` | 内存/IO 访问顺序屏障 |
| `fence.i` | `fence.i` | I | `0001111` | `001` | `000000000000` | 使之后的取指能看到之前写入 instruction memory 的内容；现代规范中属于 `Zifencei`，很多课程仍和 RV32I 一起讲 |
| `ecall` | `ecall` | I | `1110011` | `000` | `000000000000` | 环境调用 |
| `ebreak` | `ebreak` | I | `1110011` | `000` | `000000000001` | 断点/调试陷入 |

## 4. RV64I 相对 RV32I 的增量

RV64I 可以看成把基础整数 ISA 的 `XLEN` 改为 64 bit：普通 `add/sub/logic/compare/load address` 都按 64 bit 做；寄存器移位量用 6 bit。它还新增 64-bit load/store 与 32-bit word 运算。`*W` 指令的核心规则：只计算低 32 位，然后把 bit31 符号扩展到 64 位。

### 4.1 RV64I 新增/变化的 Load/Store

| 指令 | 汇编格式 | opcode | funct3 | 执行效果/细节 |
|---|---|---:|---:|---|
| `lwu` | `lwu rd, imm12(rs1)` | `0000011` | `110` | 读 32 bit，零扩展到 64 bit |
| `ld` | `ld rd, imm12(rs1)` | `0000011` | `011` | 读 64 bit |
| `sd` | `sd rs2, imm12(rs1)` | `0100011` | `011` | 写 `rs2[63:0]` |

### 4.2 RV64I Word 型 R 指令

| 指令 | 汇编格式 | opcode | funct3 | funct7 | 执行效果/细节 |
|---|---|---:|---:|---:|---|
| `addw` | `addw rd, rs1, rs2` | `0111011` | `000` | `0000000` | 低 32 位加法，结果 `sext32` 到 64 bit |
| `subw` | `subw rd, rs1, rs2` | `0111011` | `000` | `0100000` | 低 32 位减法，结果 `sext32` |
| `sllw` | `sllw rd, rs1, rs2` | `0111011` | `001` | `0000000` | 对 `rs1[31:0]` 左移，shamt=`rs2[4:0]`，结果 `sext32` |
| `srlw` | `srlw rd, rs1, rs2` | `0111011` | `101` | `0000000` | 对 32 bit 逻辑右移，结果 `sext32` |
| `sraw` | `sraw rd, rs1, rs2` | `0111011` | `101` | `0100000` | 对 32 bit 算术右移，结果 `sext32` |

### 4.3 RV64I Word 型 I 指令和 64-bit Shift Immediate

| 指令 | 汇编格式 | opcode | funct3 | imm/funct | 执行效果/细节 |
|---|---|---:|---:|---|---|
| `addiw` | `addiw rd, rs1, imm12` | `0011011` | `000` | `imm[11:0]` | `(rs1 + sext(imm12))[31:0]` 再 `sext32` |
| `slliw` | `slliw rd, rs1, shamt` | `0011011` | `001` | `0000000 shamt[4:0]` | 32 bit 左移，结果 `sext32` |
| `srliw` | `srliw rd, rs1, shamt` | `0011011` | `101` | `0000000 shamt[4:0]` | 32 bit 逻辑右移，结果 `sext32` |
| `sraiw` | `sraiw rd, rs1, shamt` | `0011011` | `101` | `0100000 shamt[4:0]` | 32 bit 算术右移，结果 `sext32` |
| `slli` | `slli rd, rs1, shamt` | `0010011` | `001` | `000000 shamt[5:0]` | RV64 普通 64 bit 左移，shamt 6 bit |
| `srli` | `srli rd, rs1, shamt` | `0010011` | `101` | `000000 shamt[5:0]` | RV64 普通 64 bit 逻辑右移 |
| `srai` | `srai rd, rs1, shamt` | `0010011` | `101` | `010000 shamt[5:0]` | RV64 普通 64 bit 算术右移 |

## 5. 常用伪指令速查

伪指令不是机器码中的真实 opcode，但做题读汇编很有用。

| 伪指令 | 等价真实指令 | 含义 |
|---|---|---|
| `nop` | `addi x0, x0, 0` | 空操作 |
| `li rd, imm` | 小数常用 `addi rd,x0,imm`；大数用 `lui/addi` | 装入立即数 |
| `mv rd, rs` | `addi rd, rs, 0` | 寄存器复制 |
| `not rd, rs` | `xori rd, rs, -1` | 按位取反 |
| `neg rd, rs` | `sub rd, x0, rs` | 取负 |
| `seqz rd, rs` | `sltiu rd, rs, 1` | `rs==0` 则 1 |
| `snez rd, rs` | `sltu rd, x0, rs` | `rs!=0` 则 1 |
| `j label` | `jal x0, label` | 无链接跳转 |
| `jr rs` | `jalr x0, 0(rs)` | 跳到寄存器地址 |
| `ret` | `jalr x0, 0(ra)` | 函数返回 |
| `call label` | 通常 `auipc ra, hi20; jalr ra, lo12(ra)` | 远距离调用 |

## 6. 构造大立即数的坑

`addi` 的低 12 位是有符号数。如果要构造 32 bit 常量 `C`：

```text
hi20 = (C + 0x800) >> 12
lo12 = sign_extend(C[11:0])
lui  rd, hi20
addi rd, rd, lo12
```

为什么要加 `0x800`：当低 12 位的 bit11 为 1 时，`addi` 会把 `lo12` 当负数加进去，所以 `lui` 的高 20 位要先进 1。

## 7. 单周期 CPU 数据通路

配套图：![RISC-V single-cycle datapath](./riscv_single_cycle_datapath.svg)

### 7.1 部件连接总览

- `PC -> Instruction Memory`：取出 `inst[31:0]`。
- `PC -> PC+4 Adder`：产生顺序下一条指令地址，同时作为 `JAL/JALR` 的 link value 写回 `rd`。
- `inst` 字段进入：
  - `Control`：根据 `opcode/funct3/funct7` 产生控制信号。
  - `Register File`：读 `rs1/rs2`，写 `rd`。
  - `Immediate Generator`：根据 `ImmSel` 产生 I/S/B/U/J 立即数。
- `Register File ReadData1`、`PC`、常数 0 通过 `ALU A MUX` 选入 ALU A 端。
- `Register File ReadData2`、`Immediate` 通过 `ALU B MUX` 选入 ALU B 端。
- `ALU`：
  - 算 R/I 运算结果。
  - 算 load/store 地址。
  - 算 `AUIPC = PC + U_imm`。
  - 算 `LUI = 0 + U_imm`。
  - 算 `JALR` 原始目标 `rs1 + I_imm`。
- `Data Memory`：地址来自 ALU；store 写入 `rs2`；load 输出进入写回 MUX。
- `Comparator/Branch logic`：比较 `rs1/rs2` 并结合 `funct3` 判断是否分支。
- `Target Adder`：算 `PC + B_imm` 或 `PC + J_imm`。
- `Next PC MUX`：在 `PC+4`、branch target、JAL target、JALR target 中选择。
- `Writeback MUX`：在 `ALU result`、`Memory data`、`PC+4` 中选择写回 `rd`。

### 7.2 主要控制信号

| 信号 | 作用 | 常见取值 |
|---|---|---|
| `RegWrite` | 是否写 `rd` | R/I/load/LUI/AUIPC/JAL/JALR 为 1；store/branch 为 0 |
| `ImmSel` | 立即数类型 | I/S/B/U/J |
| `ALUSrcA` | ALU A 端来源 | `rs1`、`PC`、`0` |
| `ALUSrcB` | ALU B 端来源 | `rs2` 或 `imm` |
| `ALUControl` | ALU 操作 | add/sub/and/or/xor/slt/sltu/sll/srl/sra |
| `MemRead` | 读数据内存 | load |
| `MemWrite` | 写数据内存 | store |
| `WBSel` | 写回数据来源 | ALU / Mem / PC+4 |
| `PCSel` | 下一 PC 来源 | PC+4 / branch / jal / jalr |
| `BranchUnsigned` | 分支比较是否无符号 | `bltu/bgeu` 为 1 |

### 7.3 各类指令经过哪些部件

| 指令类 | 执行路径 |
|---|---|
| R-type ALU | `PC -> IMem -> RegFile(rs1,rs2) -> ALU(rs1 op rs2) -> WB MUX(ALU) -> RegFile(rd)`；`PC <- PC+4` |
| I-type ALU | `IMem -> RegFile(rs1) + ImmGen(I) -> ALU(rs1 op sext(imm)) -> WB(ALU) -> rd`；shift-immediate 用 shamt，不把整个 imm 当数值 |
| Load | `RegFile(rs1) + ImmGen(I) -> ALU(address) -> DataMem(read) -> WB(Mem) -> rd`；按 `funct3` 决定读宽度和符号/零扩展 |
| Store | `RegFile(rs1,rs2) + ImmGen(S) -> ALU(address) -> DataMem(write rs2 low bits)`；不写 `rd` |
| Branch | `RegFile(rs1,rs2) -> Comparator`；同时 `ImmGen(B) + PC -> Target Adder`；条件成立则 `PC <- target`，否则 `PC <- PC+4` |
| `jal` | `ImmGen(J) + PC -> target`；`WB(PC+4) -> rd`；`PC <- target` |
| `jalr` | `RegFile(rs1) + ImmGen(I) -> ALU target`；清 bit0；`WB(PC+4) -> rd`；`PC <- target & ~1` |
| `lui` | `ImmGen(U) -> ALU(0 + U_imm) -> WB(ALU) -> rd`；`PC <- PC+4` |
| `auipc` | `PC + ImmGen(U) -> ALU -> WB(ALU) -> rd`；`PC <- PC+4` |

### 7.4 单周期 CPU 的性能结论

- 每条指令一个 clock cycle，所以 `CPI = 1`。
- 时钟周期必须长到能容纳最慢指令的完整路径。
- 通常 load 是关键路径：`Instruction Memory -> Register File -> ALU -> Data Memory -> Register File`。
- 单周期实现简单，但短指令也被迫等待最长路径；现实 CPU 会用多周期/流水线改善。

## 8. ISA 设计记忆点

- ISA 是软硬件之间的契约：定义程序员可见的指令、寄存器、内存模型、寻址方式等；同一个 ISA 可以有多种微架构实现。
- 指令通常由 `opcode + operands` 组成；operand 可以是寄存器、立即数或内存地址。
- RISC 倾向：固定长度指令、少量寻址方式、load-store、大量寄存器、简单控制。CISC 倾向：指令复杂、长度可变、寻址方式多、代码密度高。
- 多操作数指令更方便、指令数少，但编码更长；少操作数指令编码短，但需要更多数据移动。
- 常见寻址：
  - immediate：操作数就是常数。
  - register：操作数在寄存器。
  - direct：指令中给出内存地址。
  - indirect：寄存器/内存中保存目标地址。
  - PC-relative：目标地址 = PC + offset。
  - base/indexed：基址/索引寄存器 + displacement。

## 9. 信息表示

### 9.1 整数

- n 位无符号范围：`0 ... 2^n - 1`。
- n 位二补码范围：`-2^(n-1) ... 2^(n-1)-1`；最高位权重为 `-2^(n-1)`。
- 二补码取负：按位取反加 1；或从最低位起保留连续的 0 和第一个 1，左边全部取反。
- 符号扩展：复制最高位；零扩展：高位补 0。
- 截断到 k 位：保留低 k 位；无符号数等价于模 `2^k`。
- 加法溢出只对有符号解释有意义：同号相加结果异号则溢出。无符号溢出看进位/结果回绕。

### 9.2 浮点 IEEE 754

- 单精度：`S` 1 bit，`E` 8 bit，`F` 23 bit，bias=127。
- 双精度：`S` 1 bit，`E` 11 bit，`F` 52 bit，bias=1023。
- 规格化数：`(-1)^S * 1.F * 2^(E-bias)`。
- 非规格化数：`E=0`，值为 `(-1)^S * 0.F * 2^(1-bias)`，用于靠近 0 的数。
- `E=all 1, F=0` 是 `+/-inf`；`E=all 1, F!=0` 是 NaN。
- 舍入常用 round to nearest, ties to even。

## 10. 逻辑门与布尔代数

### 10.1 基本恒等式

| 规律 | AND 形式 | OR 形式 |
|---|---|---|
| 恒等 | `A·1=A` | `A+0=A` |
| 零/一 | `A·0=0` | `A+1=1` |
| 幂等 | `A·A=A` | `A+A=A` |
| 互补 | `A·A'=0` | `A+A'=1` |
| 交换 | `AB=BA` | `A+B=B+A` |
| 结合 | `(AB)C=A(BC)` | `(A+B)+C=A+(B+C)` |
| 分配 | `A(B+C)=AB+AC` | `A+BC=(A+B)(A+C)` |
| 吸收 | `A+AB=A` | `A(A+B)=A` |
| 德摩根 | `(AB)'=A'+B'` | `(A+B)'=A'B'` |

### 10.2 标准形式与化简

- 最小项 minterm：每个变量都出现一次的乘积项；SOP 是“与项之和”。
- 最大项 maxterm：每个变量都出现一次的和项；POS 是“或项之积”。
- 卡诺图合并规则：按 1、2、4、8... 个相邻格合并；可以环绕；合并越大，消去变量越多。
- don't care 可以按需要当 0 或 1，用来形成更大的圈。
- NAND 和 NOR 都是 functionally complete：只用 NAND 或只用 NOR 可以实现任意布尔函数。
- XOR：`A xor B = A'B + AB'`；XNOR：`AB + A'B'`。

## 11. 组合逻辑

- 组合逻辑输出只由当前输入决定，没有状态。
- 设计流程：规格说明 -> 真值表/布尔式 -> 化简 -> 门级实现 -> 检查延迟/成本。
- n 输入 decoder 有 `2^n` 个输出；常用于地址译码、生成 minterms。
- encoder 与 priority encoder：普通 encoder 假设只有一个输入为 1；priority encoder 处理多个 1 并选择优先级最高者。
- MUX：`2^n:1` MUX 需要 n 个选择信号；可用来实现布尔函数，把变量接到选择端，数据端接 0/1/剩余变量。
- 半加器：`sum=A xor B`，`carry=AB`。
- 全加器：`sum=A xor B xor Cin`，`Cout=AB + ACin + BCin`。
- ripple-carry adder 简单但慢，延迟随位数线性增加；carry-lookahead 用 generate/propagate 加速。
- 二补码减法：`A - B = A + (~B) + 1`。
- 有符号加法溢出：最高位进位与最高位出位不同，或“同号输入得异号输出”。

## 12. 时序逻辑

- 时序逻辑输出由当前输入和状态共同决定；状态保存在 latch/flip-flop/register 中。
- latch 对电平敏感；flip-flop 对边沿敏感。
- D flip-flop：时钟边沿采样 `D`，输出为 `Q`；寄存器是多个 DFF 并联。
- setup time：时钟边沿前输入必须稳定的时间；hold time：时钟边沿后输入仍需稳定的时间。
- 时钟周期约束：`Tclk >= Tcq + Tcomb(max) + Tsetup + Tskew`。
- hold 约束：`Tcq(min) + Tcomb(min) >= Thold + Tskew`。
- FSM：
  - Moore：输出只依赖当前状态，通常更稳定。
  - Mealy：输出依赖当前状态和输入，反应更快但更易有毛刺。
- FSM 设计：画状态图 -> 状态编码 -> 下一状态表/输出表 -> DFF 输入方程 -> 逻辑实现。

## 13. 算术单元

- ALU 通常包含 add/sub、逻辑运算、比较、移位，控制信号决定操作。
- `slt` 可由减法结果和溢出修正得到；无符号比较关注 borrow/carry。
- 左移 k 位相当于乘 `2^k`，逻辑右移无符号相当于除 `2^k` 向下取整；算术右移保持符号。
- 乘法硬件可用移位加法；除法可用移位减法/恢复除法等。若课程只到基础 ALU，优先记加法器、溢出、移位和比较。

## 14. 考前高频小抄

- `PC+4` 是下一条顺序指令；branch/jump offset 都相对当前 `PC`。
- RISC-V branch/jump 立即数编码分散，写机器码时先写出目标偏移的二进制，再按位塞回指令字段。
- `lui` 不是简单“高 20 位装入”：精确定义是 `sext(imm20 << 12)`。
- `auipc` 用当前 `PC`，不是 `PC+4`。
- `jalr` 会清最低位，因此奇地址目标会被变成偶地址。
- `x0` 作 `rd` 可丢弃结果；作 `rs1/rs2` 可提供常数 0。
- `beq x0,x0,label` 总是跳；`bne x0,x0,label` 永不跳。
- `sltu rd,x0,rs` 可判断 `rs != 0`。
- `addi rd,rs,0` 是 move；`xori rd,rs,-1` 是 not。
- load 的符号扩展/零扩展看指令名有没有 `u`；store 没有符号扩展概念，只写低若干位。
