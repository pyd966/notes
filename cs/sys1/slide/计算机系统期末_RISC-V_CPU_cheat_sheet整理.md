# 计算机系统期末 Cheat Sheet 整理：RISC-V + 单周期 CPU

> 范围说明：本文按 `sys.md` 要求整理。RISC-V 部分以 RV32I/RV64I base integer ISA 为主；`FENCE.I`、CSR 指令属于标准扩展 `Zifencei`/`Zicsr`，不是 RV32I/RV64I base，但课件/手册常放在同一张列表中，本文单独标出。CPU 部分按 Lec07 中的简化单周期 RISC-V datapath/control 版本整理。

## 0. 最先背下来的总表

### 0.1 RISC-V 六类 32-bit 指令格式

所有 base 指令长度 32 bit；字段位置从高位到低位：

| 类型 | bit 31..25 | 24..20 | 19..15 | 14..12 | 11..7 | 6..0 | 典型指令 |
|---|---|---|---|---|---|---|---|
| R | `funct7` | `rs2` | `rs1` | `funct3` | `rd` | `opcode` | `add/sub/and/or/slt` |
| I | `imm[11:0]` | | `rs1` | `funct3` | `rd` | `opcode` | `addi/load/jalr/ecall` |
| S | `imm[11:5]` | `rs2` | `rs1` | `funct3` | `imm[4:0]` | `opcode` | `sw/sd` |
| B | `imm[12|10:5]` | `rs2` | `rs1` | `funct3` | `imm[4:1|11]` | `opcode` | `beq/bne/blt` |
| U | `imm[31:12]` | | | | `rd` | `opcode` | `lui/auipc` |
| J | `imm[20|10:1|11|19:12]` | | | | `rd` | `opcode` | `jal` |

字段位置规律：`rd` 总在 `inst[11:7]`，`rs1` 总在 `inst[19:15]`，`rs2` 总在 `inst[24:20]`，方便硬件解码。除 CSR 的 5-bit `uimm` 外，RISC-V 立即数通常都符号扩展，符号位总在 `inst[31]`。

### 0.2 立即数拼接公式

记 `sext(...)` 为符号扩展到 `XLEN`。

| 类型 | 立即数值 | 范围/单位 | 注意 |
|---|---|---|---|
| I | `sext(inst[31:20])` | signed 12-bit, `[-2048, 2047]` | load offset、`addi` 等；shift-immediate 是特殊 I 型 |
| S | `sext(inst[31:25] || inst[11:7])` | signed 12-bit | store offset |
| B | `sext(inst[31] || inst[7] || inst[30:25] || inst[11:8] || 0)` | signed 13-bit，最低位恒 0，范围约 `[-4096, +4094]` bytes | branch target = `PC + immB` |
| U | `sext(inst[31:12] || 12'b0)` | 20-bit upper immediate | RV64 中 `lui/auipc` 的 32-bit 结果会符号扩展到 64-bit |
| J | `sext(inst[31] || inst[19:12] || inst[20] || inst[30:21] || 0)` | signed 21-bit，最低位恒 0，范围约 `±1 MiB` | `jal` target = `PC + immJ` |

## 1. 整数寄存器与调用约定

### 1.1 寄存器用途、别名、caller/callee

标准 RISC-V psABI 中，“Preserved across calls? = Yes” 等价于 callee-saved；“No” 等价于 caller-saved。

| 寄存器 | ABI 别名 | 用途 | 调用约定 |
|---|---|---|---|
| `x0` | `zero` | 常数 0；读永远为 0，写入被丢弃 | immutable |
| `x1` | `ra` | return address，`jal/jalr` 常写入返回地址 | caller-saved |
| `x2` | `sp` | stack pointer | callee-saved |
| `x3` | `gp` | global pointer | fixed/unallocatable，通常不要改 |
| `x4` | `tp` | thread pointer | fixed/unallocatable，通常不要改 |
| `x5-x7` | `t0-t2` | temporary registers | caller-saved |
| `x8` | `s0/fp` | saved register；可作 frame pointer | callee-saved |
| `x9` | `s1` | saved register | callee-saved |
| `x10-x11` | `a0-a1` | 参数 0-1；返回值 0-1 | caller-saved |
| `x12-x17` | `a2-a7` | 参数 2-7 | caller-saved |
| `x18-x27` | `s2-s11` | saved registers | callee-saved |
| `x28-x31` | `t3-t6` | temporary registers | caller-saved |

术语：

- caller-saved：调用者如果还需要该值，必须在 `call` 前自己保存。
- callee-saved：被调用者如果使用该寄存器，必须在返回前恢复。
- `ra` 容易误判：非叶子函数通常会保存自己的 `ra`，但 ABI 分类仍是 caller-saved / not preserved across calls。
- `gp/tp` 不是普通 caller/callee 寄存器；标准 ABI 要求过程不要修改它们。

## 2. RV32I 指令完整表

### 2.1 Opcode 总表

| 类别 | opcode | 格式 | 指令 |
|---|---:|---|---|
| `LOAD` | `0000011` | I | `lb/lh/lw/lbu/lhu` |
| `MISC-MEM` | `0001111` | I-like | `fence`、`pause`；`fence.i` 属扩展 |
| `OP-IMM` | `0010011` | I | `addi/slti/sltiu/xori/ori/andi/slli/srli/srai` |
| `AUIPC` | `0010111` | U | `auipc` |
| `STORE` | `0100011` | S | `sb/sh/sw` |
| `OP` | `0110011` | R | `add/sub/sll/slt/sltu/xor/srl/sra/or/and` |
| `LUI` | `0110111` | U | `lui` |
| `BRANCH` | `1100011` | B | `beq/bne/blt/bge/bltu/bgeu` |
| `JALR` | `1100111` | I | `jalr` |
| `JAL` | `1101111` | J | `jal` |
| `SYSTEM` | `1110011` | I-like | `ecall/ebreak`；CSR 属 `Zicsr` |

### 2.2 U/J/I 控制转移与上立即数

| 指令 | 格式 | opcode/funct3 | 汇编格式 | 作用 |
|---|---|---|---|---|
| `lui` | U | `0110111` | `lui rd, imm20` | `rd = sext(imm20 << 12)`；RV32 中为 32-bit 值，RV64 中符号扩展到 64-bit |
| `auipc` | U | `0010111` | `auipc rd, imm20` | `rd = PC + sext(imm20 << 12)` |
| `jal` | J | `1101111` | `jal rd, offset` | `rd = PC + 4; PC = PC + sext(Jimm)`；`j label` = `jal x0,label` |
| `jalr` | I | `funct3=000`, `opcode=1100111` | `jalr rd, offset(rs1)` | `t = rs1 + sext(imm12); rd = PC+4; PC = t & ~1` |

易错：

- `jal` 的偏移按 2 字节对齐编码，立即数最低位不存，实际 bit0 为 0。
- `jalr` 的 12-bit 立即数不是“乘 2”的格式；但最终目标地址最低位会被清 0。
- `rd=x0` 表示不保存返回地址，例如 `j`、`jr`、`ret` 等伪指令会这样用。
- `ret` = `jalr x0, 0(x1)`。

### 2.3 Branch 指令

全部 B 型，`opcode=1100011`，汇编格式 `op rs1, rs2, offset`，目标地址 `PC + sext(Bimm)`。

| 指令 | funct3 | 条件 | 比较类型 |
|---|---:|---|---|
| `beq` | `000` | `rs1 == rs2` | equality |
| `bne` | `001` | `rs1 != rs2` | equality |
| `blt` | `100` | `rs1 < rs2` | signed |
| `bge` | `101` | `rs1 >= rs2` | signed |
| `bltu` | `110` | `rs1 < rs2` | unsigned |
| `bgeu` | `111` | `rs1 >= rs2` | unsigned |

易错：

- RISC-V 没有 condition code / flags；branch 直接比较两个寄存器。
- 没有 `bgt/bgtu/ble/bleu` 真指令；伪指令通过交换操作数合成，例如 `bgt rs1,rs2,L` = `blt rs2,rs1,L`。
- 无条件跳转应使用 `jal x0,label`，不要用永真分支，因为 `jal` 范围更大且不污染条件分支预测结构。
- branch offset 范围约 `±4 KiB`，bit0 恒为 0。

### 2.4 Load/Store 指令

Load 为 I 型，汇编格式 `op rd, offset(rs1)`；Store 为 S 型，汇编格式 `op rs2, offset(rs1)`。有效地址 `addr = rs1 + sext(imm12)`。

| 指令 | 格式 | funct3 | opcode | 作用 |
|---|---|---:|---:|---|
| `lb` | I | `000` | `0000011` | load 8-bit，符号扩展到 XLEN |
| `lh` | I | `001` | `0000011` | load 16-bit，符号扩展到 XLEN |
| `lw` | I | `010` | `0000011` | RV32 load 32-bit；RV64 load 32-bit 后符号扩展到 64-bit |
| `lbu` | I | `100` | `0000011` | load 8-bit，零扩展 |
| `lhu` | I | `101` | `0000011` | load 16-bit，零扩展 |
| `sb` | S | `000` | `0100011` | store `rs2[7:0]` |
| `sh` | S | `001` | `0100011` | store `rs2[15:0]` |
| `sw` | S | `010` | `0100011` | store `rs2[31:0]` |

易错：

- `offset` 是字节偏移，不是 word index。
- store 没有 `rd`；机器码中的 `inst[11:7]` 是 `imm[4:0]`。
- load 到 `x0` 时结果丢弃，但仍然必须执行访存并产生可能的异常/副作用。
- 自然对齐访问保证不因 misalignment 报错；非对齐访问行为由 EEI/平台定义，可能慢、可能 trap、也可能支持。

### 2.5 OP-IMM：寄存器-立即数整数运算

全部 I 型，`opcode=0010011`，汇编格式 `op rd, rs1, imm`。

| 指令 | funct3 | `imm[11:5]` 约束 | 作用 |
|---|---:|---|---|
| `addi` | `000` | 任意 imm12 | `rd = rs1 + sext(imm12)`，溢出忽略 |
| `slti` | `010` | 任意 imm12 | signed 比较：`rd = (rs1 < sext(imm12)) ? 1 : 0` |
| `sltiu` | `011` | 任意 imm12 | unsigned 比较；立即数先符号扩展，再当 unsigned 比较 |
| `xori` | `100` | 任意 imm12 | `rd = rs1 ^ sext(imm12)` |
| `ori` | `110` | 任意 imm12 | `rd = rs1 | sext(imm12)` |
| `andi` | `111` | 任意 imm12 | `rd = rs1 & sext(imm12)` |
| `slli` | `001` | RV32: `0000000` | `rd = rs1 << shamt`，RV32 `shamt=imm[4:0]` |
| `srli` | `101` | RV32: `0000000` | 逻辑右移，补 0 |
| `srai` | `101` | RV32: `0100000` | 算术右移，补原符号位 |

伪指令常识：

- `nop` = `addi x0, x0, 0`。
- `mv rd, rs` = `addi rd, rs, 0`。
- `not rd, rs` = `xori rd, rs, -1`。
- `seqz rd, rs` = `sltiu rd, rs, 1`。

### 2.6 OP：寄存器-寄存器整数运算

全部 R 型，`opcode=0110011`，汇编格式 `op rd, rs1, rs2`。

| 指令 | funct3 | funct7 | 作用 |
|---|---:|---:|---|
| `add` | `000` | `0000000` | `rd = rs1 + rs2`，溢出忽略 |
| `sub` | `000` | `0100000` | `rd = rs1 - rs2`，溢出忽略 |
| `sll` | `001` | `0000000` | 逻辑左移；RV32 shift amount = `rs2[4:0]` |
| `slt` | `010` | `0000000` | signed `rs1 < rs2` |
| `sltu` | `011` | `0000000` | unsigned `rs1 < rs2` |
| `xor` | `100` | `0000000` | bitwise xor |
| `srl` | `101` | `0000000` | 逻辑右移 |
| `sra` | `101` | `0100000` | 算术右移 |
| `or` | `110` | `0000000` | bitwise or |
| `and` | `111` | `0000000` | bitwise and |

易错：

- RV32 的寄存器移位只看 `rs2[4:0]`，不是整个 `rs2`。
- `sltu rd, x0, rs` 可实现 `snez rd, rs`。
- 整数加减没有算术异常，溢出直接截断低 XLEN 位。

### 2.7 Memory ordering 与环境调用

| 指令 | 格式/字段 | 汇编格式 | 作用 |
|---|---|---|---|
| `fence` | `opcode=0001111`, `funct3=000`, fields: `fm pred succ rs1 rd` | `fence pred, succ` | 约束本 hart 的先前内存/I/O 操作与后续操作的可观察顺序 |
| `fence.tso` | `fm=1000`, `pred=RW`, `succ=RW`, `rs1=rd=0` | `fence.tso` | TSO 风格 fence；强实现可当成 `fence rw,rw` |
| `pause` | `fence` 的 hint 编码 | `pause` | hint，无架构可见状态变化 |
| `ecall` | `func12=000000000000`, `rs1=rd=0`, `funct3=000`, `opcode=1110011` | `ecall` | 向执行环境请求服务，产生精确 trap |
| `ebreak` | `func12=000000000001`, `rs1=rd=0`, `funct3=000`, `opcode=1110011` | `ebreak` | 断点/调试 trap |

`fence pred,succ` 中 `pred/succ` 是 I/O/R/W bit mask：I=device input，O=device output，R=memory read，W=memory write。例如 `fence rw,rw` 约束之前的读写先于之后的读写被观察到。

## 3. RV64I：相对 RV32I 的差异与新增

RV64I 不是简单“再加几条指令”：大多数 RV32I 指令在 RV64I 中操作 `XLEN=64` 位；另有 `*W` 指令专门做 32-bit 运算并把 32-bit 结果符号扩展到 64-bit。

### 3.1 RV32I 指令在 RV64I 中的行为变化

| 项目 | RV32I | RV64I |
|---|---|---|
| 通用寄存器宽度 | 32-bit | 64-bit |
| `add/sub/and/or/xor/slt/...` | 操作 32-bit | 操作 64-bit |
| `sll/srl/sra` register shift | shift amount = `rs2[4:0]` | shift amount = `rs2[5:0]` |
| `slli/srli/srai` immediate shift | shamt 5-bit，`imm[4:0]` | shamt 6-bit，`imm[5:0]` |
| `lw` | load 32-bit 到 32-bit rd | load 32-bit 并符号扩展到 64-bit |
| `lui` | `rd = imm20 << 12` | 32-bit 结果符号扩展到 64-bit |
| `auipc` | `rd = PC + (imm20 << 12)` | 32-bit offset 先符号扩展到 64-bit，再加 PC |

### 3.2 RV64I 新增 load/store

| 指令 | 格式 | funct3 | opcode | 作用 |
|---|---|---:|---:|---|
| `lwu` | I | `110` | `0000011` | load 32-bit，零扩展到 64-bit |
| `ld` | I | `011` | `0000011` | load 64-bit |
| `sd` | S | `011` | `0100011` | store `rs2[63:0]` |

### 3.3 RV64I OP-IMM-32：32-bit 立即数运算

`opcode=0011011`。所有结果取低 32 bit，再符号扩展到 64 bit。

| 指令 | 格式 | funct3 | funct7/imm 约束 | 作用 |
|---|---|---:|---|---|
| `addiw` | I | `000` | 任意 imm12 | `rd = sext32(rs1 + sext(imm12))` |
| `slliw` | I-special | `001` | `funct7=0000000`，`shamt=imm[4:0]`，`imm[5]=0` | 32-bit 左移后符号扩展 |
| `srliw` | I-special | `101` | `funct7=0000000`，`imm[5]=0` | 32-bit 逻辑右移后符号扩展 |
| `sraiw` | I-special | `101` | `funct7=0100000`，`imm[5]=0` | 32-bit 算术右移后符号扩展 |

`addiw rd, rs1, 0` 常用作 `sext.w rd, rs1`。

### 3.4 RV64I OP-32：32-bit register-register 运算

全部 R 型，`opcode=0111011`。忽略输入高 32 bit，结果低 32 bit 符号扩展到 64 bit。

| 指令 | funct3 | funct7 | 作用 |
|---|---:|---:|---|
| `addw` | `000` | `0000000` | 32-bit add，结果 sign-extend |
| `subw` | `000` | `0100000` | 32-bit sub，结果 sign-extend |
| `sllw` | `001` | `0000000` | 32-bit 左移；shamt = `rs2[4:0]` |
| `srlw` | `101` | `0000000` | 32-bit 逻辑右移；shamt = `rs2[4:0]` |
| `sraw` | `101` | `0100000` | 32-bit 算术右移；shamt = `rs2[4:0]` |

易错：

- `lwu` 只存在于 RV64I。
- RV64 中 `lw` 是符号扩展，`lwu` 才是零扩展。
- `*W` 指令一定把 bit31 复制到 bit63..32，即使语义上处理 unsigned 32-bit 数据也是如此。
- RV64 ABI 通常保持 32-bit 值以 sign-extended 形式存放在 64-bit 寄存器中。

## 4. 机器码编码速查

### 4.1 通用编码步骤

1. 确定指令格式 R/I/S/B/U/J。
2. 填 `opcode`。
3. 按表填 `funct3`、`funct7` 或 I-type shift 的 `imm[11:5]` 常量。
4. 把寄存器名转为 5-bit 编号，例如 `a0=x10=01010`。
5. 检查立即数范围与对齐：B/J offset 的 bit0 必须为 0；U 型汇编立即数代表高 20 bit。
6. 把立即数拆到格式指定的位置；注意 B/J 的 immediate bit order 不是连续排布。

### 4.2 常用机器码字段表

| 指令族 | opcode | funct3 | funct7 / 特殊字段 |
|---|---:|---:|---|
| `lui` | `0110111` | - | U immediate |
| `auipc` | `0010111` | - | U immediate |
| `jal` | `1101111` | - | J immediate |
| `jalr` | `1100111` | `000` | I immediate |
| `branch` | `1100011` | `beq=000,bne=001,blt=100,bge=101,bltu=110,bgeu=111` | B immediate |
| `load` | `0000011` | `lb=000,lh=001,lw=010,ld=011,lbu=100,lhu=101,lwu=110` | `ld/lwu` RV64 only |
| `store` | `0100011` | `sb=000,sh=001,sw=010,sd=011` | `sd` RV64 only |
| `op-imm` | `0010011` | `addi=000,slti=010,sltiu=011,xori=100,ori=110,andi=111,slli=001,srli/srai=101` | shift 用 `imm[11:5]` 区分 |
| `op` | `0110011` | 见 R 型表 | `funct7=0000000` 或 `0100000` |
| `op-imm-32` | `0011011` | `addiw=000,slliw=001,srliw/sraiw=101` | RV64 only |
| `op-32` | `0111011` | `addw/subw=000,sllw=001,srlw/sraw=101` | RV64 only |
| `fence` | `0001111` | `000` | `fm/pred/succ` |
| `ecall/ebreak` | `1110011` | `000` | `func12=0/1` |

### 4.3 RV32I/RV64I 逐条指令速查

| ISA | 指令 | 格式 | 汇编格式 | 作用 | 关键编码 |
|---|---|---|---|---|---|
| RV32I | `lui` | U | `lui rd, imm20` | `rd=sext(imm20<<12)` | opcode `0110111` |
| RV32I | `auipc` | U | `auipc rd, imm20` | `rd=PC+sext(imm20<<12)` | opcode `0010111` |
| RV32I | `jal` | J | `jal rd, off` | link `PC+4`，跳到 `PC+off` | opcode `1101111` |
| RV32I | `jalr` | I | `jalr rd, off(rs1)` | link `PC+4`，跳到 `(rs1+off)&~1` | opcode `1100111`, f3 `000` |
| RV32I | `beq/bne` | B | `op rs1,rs2,off` | 相等/不等跳转 | opcode `1100011`, f3 `000/001` |
| RV32I | `blt/bge` | B | `op rs1,rs2,off` | signed 小于/大于等于跳转 | f3 `100/101` |
| RV32I | `bltu/bgeu` | B | `op rs1,rs2,off` | unsigned 小于/大于等于跳转 | f3 `110/111` |
| RV32I | `lb/lh/lw` | I | `op rd,off(rs1)` | load 后符号扩展 | opcode `0000011`, f3 `000/001/010` |
| RV32I | `lbu/lhu` | I | `op rd,off(rs1)` | load 后零扩展 | f3 `100/101` |
| RV32I | `sb/sh/sw` | S | `op rs2,off(rs1)` | store 低 8/16/32 bit | opcode `0100011`, f3 `000/001/010` |
| RV32I | `addi/slti/sltiu` | I | `op rd,rs1,imm` | add/signed compare/unsigned compare | opcode `0010011`, f3 `000/010/011` |
| RV32I | `xori/ori/andi` | I | `op rd,rs1,imm` | 位运算；imm 符号扩展 | f3 `100/110/111` |
| RV32I | `slli` | I-special | `slli rd,rs1,shamt` | 左移，shamt 5 bit | f3 `001`, f7 `0000000` |
| RV32I | `srli/srai` | I-special | `op rd,rs1,shamt` | 逻辑/算术右移 | f3 `101`, f7 `0000000/0100000` |
| RV32I | `add/sub` | R | `op rd,rs1,rs2` | 加/减 | opcode `0110011`, f3 `000`, f7 `0000000/0100000` |
| RV32I | `sll/srl/sra` | R | `op rd,rs1,rs2` | 移位；shamt=`rs2[4:0]` | f3 `001/101/101`, f7 `0000000/0000000/0100000` |
| RV32I | `slt/sltu` | R | `op rd,rs1,rs2` | signed/unsigned 小于置 1 | f3 `010/011`, f7 `0000000` |
| RV32I | `xor/or/and` | R | `op rd,rs1,rs2` | 位运算 | f3 `100/110/111`, f7 `0000000` |
| RV32I | `fence` | I-like | `fence pred,succ` | 内存/I/O 顺序约束 | opcode `0001111`, f3 `000` |
| RV32I | `ecall/ebreak` | I-like | `ecall`/`ebreak` | 环境调用/断点 trap | opcode `1110011`, f3 `000`, func12 `0/1` |
| RV64I | `lwu/ld` | I | `op rd,off(rs1)` | 32-bit 零扩展 load / 64-bit load | f3 `110/011` |
| RV64I | `sd` | S | `sd rs2,off(rs1)` | store 64 bit | f3 `011` |
| RV64I | `addiw` | I | `addiw rd,rs1,imm` | 32-bit add 后 sign-extend | opcode `0011011`, f3 `000` |
| RV64I | `slliw/srliw/sraiw` | I-special | `op rd,rs1,shamt` | 32-bit shift 后 sign-extend | opcode `0011011`, f3 `001/101/101` |
| RV64I | `addw/subw` | R | `op rd,rs1,rs2` | 32-bit add/sub 后 sign-extend | opcode `0111011`, f3 `000`, f7 `0000000/0100000` |
| RV64I | `sllw/srlw/sraw` | R | `op rd,rs1,rs2` | 32-bit shift 后 sign-extend | opcode `0111011`, f3 `001/101/101` |

扩展但常见于总表：

| 扩展 | 指令 | 格式 | 汇编格式 | 作用 | 关键编码 |
|---|---|---|---|---|---|
| `Zifencei` | `fence.i` | I-like | `fence.i` | 同步本 hart 的数据写入与后续取指 | opcode `0001111`, f3 `001`, `rs1=rd=0` |
| `Zicsr` | `csrrw/csrrs/csrrc` | I-like | `op rd,csr,rs1` | CSR read-write / read-set / read-clear | opcode `1110011`, f3 `001/010/011` |
| `Zicsr` | `csrrwi/csrrsi/csrrci` | I-like | `op rd,csr,uimm` | CSR immediate 版本；`uimm` 为 5-bit 零扩展 | f3 `101/110/111` |

## 5. RISC-V 易错事项

- 所有普通立即数的符号位在 `inst[31]`；不要把 `andi/ori/xori` 的立即数当成零扩展。
- `sltiu` 的立即数也是先符号扩展，然后作为 unsigned 比较。
- B 型和 J 型立即数最低位恒 0，机器码里不存 bit0。
- B 型 bit layout：`inst[31]=imm[12]`，`inst[7]=imm[11]`，`inst[30:25]=imm[10:5]`，`inst[11:8]=imm[4:1]`。
- J 型 bit layout：`inst[31]=imm[20]`，`inst[19:12]=imm[19:12]`，`inst[20]=imm[11]`，`inst[30:21]=imm[10:1]`。
- `jalr` 会清零目标地址 bit0；其 I-immediate 不按 2 字节缩放。
- `x0` 写入无效，但使用 `x0` 作为 load 目的寄存器仍会访存并可能触发异常。
- `fence.i` 和 CSR 指令不是 RV32I/RV64I base 的一部分；分别属于 `Zifencei` 和 `Zicsr`。
- `mul/div/rem` 属 M 扩展，不是 base I。
- `ld/sd/addw/...` 不是 RV32I 指令。
- RV64 的 `slli/srli/srai` 用 6-bit shamt；RV32 用 5-bit shamt。
- RV64 的 `slliw/srliw/sraiw` 中 `imm[5]` 必须为 0；否则是 reserved encoding。
- `beq` 标准 opcode 是 `1100011`。若课件 OCR/截图里出现 `1100111`，那是 `jalr` 的 opcode，不能用于 `beq`。

## 6. 本课程单周期 CPU：组件与连接

### 6.1 课程 CPU 支持的核心指令

Lec07 的简化 datapath 重点支持：

- memory-reference：`lw/ld`、`sw/sd`
- arithmetic-logical：`add/sub/and/or/slt`，后续可扩展 `xor/srl/addi/...`
- control flow：`beq`、`jal`，部分图中扩展到 `bne/jalr/lui`

因此 CPU control 部分应按“课程 datapath 支持哪些 mux/部件”来记；完整 RV32I/RV64I ISA 需要更多控制路径。

### 6.2 Datapath 组件

| 组件 | 输入 | 输出 | 用途 |
|---|---|---|---|
| PC register | next PC, clock/reset | current PC | 保存当前指令地址 |
| Instruction memory | read address = PC | instruction[31:0] | 取指 |
| PC+4 adder | PC, constant 4 | PC+4 | 默认下一条指令地址；也用于写回 link address |
| Register file | `rs1=inst[19:15]`, `rs2=inst[24:20]`, `rd=inst[11:7]`, write data, RegWrite | ReadData1, ReadData2 | 两读一写；`x0` 恒为 0；写在时钟沿 |
| Immediate generator | instruction bits, ImmSel | sign-extended immediate | 按 I/S/B/J 等类型生成立即数 |
| ALU | A=ReadData1, B=mux(ReadData2, Imm), ALUControl | ALUResult, Zero | 算术逻辑、地址计算、branch 比较 |
| Data memory | address=ALUResult, write data=ReadData2, MemRead/MemWrite | ReadData | load/store |
| Branch target adder | PC, branch/jump immediate | PC+imm | 计算 branch/jal target |
| MUX: ALUSrcB | ReadData2 vs Imm | ALU B | R 型用寄存器，load/store/I 型用立即数 |
| MUX: MemtoReg | ALUResult / DataMem / PC+4 | register write data | R/I 型、load、jal 写回不同来源 |
| MUX: NextPC | PC+4 / branch target / jump target | next PC | 更新 PC |
| Control unit | opcode/funct3/funct7/Zero | control signals | 决定 mux、读写使能、ALU 操作 |

数据流：

1. Fetch：`PC -> Instruction memory`，同时 `PC + 4`。
2. Decode/Register read：指令字段送寄存器堆、控制器、立即数生成器。
3. Execute：ALU 做运算、地址计算或比较；branch/jump adder 计算目标。
4. Memory：load/store 访问 data memory。
5. Writeback：根据 `MemtoReg` 把 ALU/DataMem/PC+4 写回 `rd`。
6. PC update：默认 `PC+4`；branch 成立选 branch target；jump 选 jump target。

### 6.3 Immediate generator / ImmSel

课件中的 2-bit `ImmSel`：

| ImmSel | 类型 | opcode | 立即数 |
|---:|---|---:|---|
| `00` | I | `0000011`, `0010011`, `1100111` | `sext(inst[31:20])` |
| `01` | S | `0100011` | `sext(inst[31:25] || inst[11:7])` |
| `10` | B | `1100011` | `sext(inst[31] || inst[7] || inst[30:25] || inst[11:8] || 0)` |
| `11` | J | `1101111` | `sext(inst[31] || inst[19:12] || inst[20] || inst[30:21] || 0)` |

若 CPU 支持 `lui/auipc`，还需要能生成 U 型立即数 `sext(inst[31:12] || 12'b0)`；这通常要求扩展 `ImmSel` 或增加特殊通路。

## 7. 本课程 CPU：control signals

### 7.1 主控制信号含义

| Signal | 0 时 | 1 时 / 其他值 |
|---|---|---|
| `RegWrite` | 不写寄存器堆 | 在时钟沿把 write data 写入 `rd`，但 `rd=x0` 仍不改变 |
| `ALUSrcB` / `ALUSrc` | ALU 第二操作数来自 `ReadData2` | ALU 第二操作数来自 Immediate Generator |
| `Branch` / `PCSrc` | PC 走 `PC+4` | branch 类指令允许 PC 选 branch target；实际是否跳转还要看 `Zero`/条件 |
| `BranchN` | branch on equal：通常用于 `beq`，take when `Zero=1` | branch on not equal：用于 `bne`，take when `Zero=0` |
| `Jump` | 非 jump，PC 由 normal/branch 逻辑决定 | PC 选 jump target；`jal` 同时写 `PC+4` 到 `rd` |
| `MemRead` | 不读 data memory | data memory 读出 `ReadData` |
| `MemWrite` | 不写 data memory | 把 `ReadData2` 写入 `ALUResult` 指定地址 |
| `MemtoReg[1:0]` | `00`: 写回 ALUResult | `01`: 写回 DataMem；`10`: 写回 PC+4；`11`: 通常未用/保留 |
| `ALUOp[1:0]` | 给 ALU decoder 的粗粒度类别 | `00` add address；`01` sub branch compare；`10` R-type；`11` I-type ALU 扩展 |
| `ALUControl` / `ALUC` | 具体 ALU 功能码 | 由 `ALUOp + funct3 + funct7/inst[30]` 译码得到 |

`BranchN` 若存在，常见 branch decision：

```text
take_branch = Branch & (Zero XOR BranchN)
```

其中 `beq: BranchN=0`，`bne: BranchN=1`。只支持 `beq` 的简化 datapath 可没有 `BranchN`。

### 7.2 Main decoder 真值表

课件主控信号顺序常写为：

```text
{ALUSrcB, MemtoReg, RegWrite, MemRead, MemWrite, Branch, Jump, ALUOp}
```

其中 `MemtoReg` 和 `ALUOp` 各 2 bit。

| 指令类 | opcode | ALUSrcB | MemtoReg | RegWrite | MemRead | MemWrite | Branch | Jump | ALUOp |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| R-format | `0110011` | 0 | `00` | 1 | 0 | 0 | 0 | 0 | `10` |
| Load | `0000011` | 1 | `01` | 1 | 1 | 0 | 0 | 0 | `00` |
| Store | `0100011` | 1 | X | 0 | 0 | 1 | 0 | 0 | `00` |
| `beq` | `1100011` | 0 | X | 0 | 0 | 0 | 1 | 0 | `01` |
| `jal` | `1101111` | X | `10` | 1 | 0 | 0 | 0 | 1 | XX |
| I-type ALU | `0010011` | 1 | `00` | 1 | 0 | 0 | 0 | 0 | `11` |

若按课件后续“扩展到 add/jalr/lui/bne”的 datapath，则可额外记：

| 指令 | 关键控制 | 说明 |
|---|---|---|
| `addi` | `ALUSrcB=1`, `RegWrite=1`, `MemtoReg=00`, `ALUOp=11/ADD` | 写回 `rs1 + immI` |
| `bne` | `Branch=1`, `BranchN=1`, `ALUSrcB=0`, `ALUOp=01/SUB` | `Zero=0` 时跳转 |
| `jalr` | `Jump=1`, `RegWrite=1`, `MemtoReg=10`, `ImmSel=I`, `ALUSrcB=1`, ALU ADD | PC 选 `(rs1+immI)&~1`，写回 `PC+4` |
| `lui` | `RegWrite=1`, 写回源为 `Uimm` 或 ALU 计算 `x0+Uimm` | 需要 U 型 ImmGen 或额外写回 mux |

注意：

- 课件截图/OCR 中 `beq` opcode 可能显示为 `1100111`，标准正确值是 `1100011`。
- `MemtoReg=X` 表示该指令不写寄存器，写回 mux 选择无关。
- `jal` 不需要 ALU 做普通算术结果写回，`ALUOp` 可为 don't care；PC target 由 jump target adder/立即数通路给出。
- 如果实现 `jalr`，PC target 应是 `(rs1 + immI) & ~1`，需要 ALU/adder 输出进入 PC mux。
- 如果实现 `lui`，写回源需要 immediate 或 ALU 对 `x0 + Uimm` 的路径；基础表中未覆盖。

### 7.3 ALU decoder

课件中有两种写法：表格展示 4-bit ALU control，HDL 示例展示 3-bit `ALU_Control`。二者常见对应关系如下：

| ALU 功能 | 4-bit control | 3-bit control 常用写法 |
|---|---:|---:|
| AND | `0000` | `000` |
| OR | `0001` | `001` |
| ADD | `0010` | `010` |
| SUB | `0110` | `110` |
| SLT | `0111` | `111` |
| XOR | 常由本课程 ALU 自定义 | `100` 常见 |
| SRL | 常由本课程 ALU 自定义 | `101` 常见 |

ALUOp 粗译码：

| ALUOp | 使用场景 | ALU 功能 |
|---:|---|---|
| `00` | load/store 地址计算 | ADD |
| `01` | `beq/bne` 比较 | SUB，并检查 `Zero` |
| `10` | R-type | 由 `funct3` 与 `inst[30]` 决定 |
| `11` | I-type ALU 扩展 | 由 `funct3` 与 shift 的 `inst[30]` 决定 |

课件 HDL 的 `Fun = {funct3, inst[30]}` 译码例子：

| 指令 | funct3 | inst[30] | `Fun` | ALU |
|---|---:|---:|---:|---|
| `add` | `000` | 0 | `0000` | ADD |
| `sub` | `000` | 1 | `0001` | SUB |
| `and` | `111` | 0 | `1110` | AND |
| `or` | `110` | 0 | `1100` | OR |
| `slt` | `010` | 0 | `0100` | SLT |
| `srl` | `101` | 0 | `1010` | SRL |
| `sra` | `101` | 1 | `1011` | SRA，如果 ALU 实现了 |
| `xor` | `100` | 0 | `1000` | XOR |

### 7.4 各指令 datapath 走法

R-type `add/sub/and/or/slt rd,rs1,rs2`：

- register file 读 `rs1/rs2`。
- `ALUSrcB=0`，ALU B 来自 `ReadData2`。
- `ALUOp=10`，ALU decoder 根据 funct 选具体运算。
- `MemtoReg=00`，`RegWrite=1`，写 ALUResult 到 `rd`。
- `PC = PC + 4`。

Load `lw/ld rd, imm(rs1)`：

- 读 `rs1`；ImmGen 生成 I-imm。
- `ALUSrcB=1`，ALU 做 `rs1 + imm` 得地址。
- `MemRead=1`，读 data memory。
- `MemtoReg=01`，`RegWrite=1`，写 memory data 到 `rd`。
- `PC = PC + 4`。

Store `sw/sd rs2, imm(rs1)`：

- 读 `rs1` 作为 base，读 `rs2` 作为 store data。
- ImmGen 生成 S-imm。
- ALU 做 `rs1 + imm` 得地址。
- `MemWrite=1`，把 `ReadData2` 写入 data memory。
- 不写寄存器，`RegWrite=0`。
- `PC = PC + 4`。

Branch `beq rs1,rs2,offset`：

- 读 `rs1/rs2`。
- `ALUSrcB=0`，ALU 做 `rs1 - rs2`。
- 若 `Zero=1` 且 `Branch=1`，PC 选 `PC + Bimm`；否则 `PC+4`。
- 不读写 data memory，不写寄存器。

Jump `jal rd,offset`：

- ImmGen 生成 J-imm。
- 写回 `PC+4` 到 `rd`，所以 `MemtoReg=10`，`RegWrite=1`。
- `Jump=1`，PC 选 `PC + Jimm`。

## 8. 单周期 CPU 性能与结构易错

- 单周期 CPU：一条指令在一个时钟周期完成；周期长度必须覆盖最慢指令。
- 课件例子延迟：instruction memory 200ps，register read/write 100ps，ALU/adders 200ps，data memory 200ps。
- `ld/lw` critical path：instruction memory -> register file read -> ALU address -> data memory -> register file write，约 800ps。
- 因周期由最慢指令决定，R-type、branch 等较短路径也被迫使用同样长周期，浪费时间。
- 单周期 datapath 中一个部件每周期只能做一个功能；因此通常需要 separate instruction memory 和 data memory，否则同一周期取指与访存冲突。
- `RegWrite`、`MemWrite` 等写使能必须配合时钟沿；组合逻辑先稳定，时钟沿再写状态元件。
- `Zero` 只表示 ALU 输出为 0；对 `beq` 正好代表相等。若支持 `blt/bge`，需要 signed/unsigned less-than 等额外比较结果或 ALU flags。

## 9. 推荐压缩到 cheat sheet 的布局

如果只能带一页，优先级如下：

1. 第一块：寄存器 ABI 表，尤其 `ra/sp/s0/a0-a7/s2-s11/t*` 的 caller/callee。
2. 第二块：六类格式图 + 立即数拼接公式，特别 B/J。
3. 第三块：RV32I/RV64I opcode/funct3/funct7 指令表。
4. 第四块：RV64I 差异：`lw/lwu/ld/sd/*W`、shift amount、`lui/auipc` sign-extension。
5. 第五块：CPU control 真值表 + ALUOp/ALUControl 表。
6. 第六块：datapath 五阶段走法和关键 mux：`ALUSrcB`、`MemtoReg`、`Branch/Jump`。

## 10. 参考资料

- `sys.md`：用户整理的考试范围要求。
- `Lec07_CPU (1).pdf`：本课程 CPU datapath/control slides。
- `riscv-unprivileged.pdf`：RISC-V Unprivileged ISA manual，尤其 Sections 2.2-2.8、Chapter 4、Chapter 36 instruction listings。
- RISC-V psABI：整数寄存器调用约定表；在线版本为 [RISC-V ABIs Specification](https://riscv-non-isa.github.io/riscv-elf-psabi-doc/)。
